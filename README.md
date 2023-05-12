
### posts

-   id serial (primary key)
-   user_id integer (null, fkey users)
-   topic_id integer (fkey topics)
-   post_number integer
-   raw text
-   cooked text
-   created_at timestamp
-   updated_at timestamp
-   reply_to_post_number integer (null)
-   reply_count integer (default 0, denormal post_replies)
-   quote_count integer (default 0, denormal quoted_posts)
-   deleted_at timestamp (null)
-   off_topic_count integer (default 0, denormal post_actions)
-   like_count integer (default 0, denormal post_actions)
-   incoming_link_count integer (default 0, denormal topic_links)
-   bookmark_count integer (default 0, denormal post_actions)
-   score double (null)
-   reads integer (default 0, denormal post_timings)
-   post_type integer (default 1)
-   sort_order integer (null)
-   last_editor_id integer (null, fkey users)
-   hidden boolean (default false)
-   hidden_reason_id integer (null)
-   notify_moderators_count integer (default 0, denormal post_actions)
-   spam_count integer (default 0, denormal post_actions)
-   illegal_count integer (default 0, denormal post_actions)
-   inappropriate_count integer (default 0, denormal post_actions)
-   last_version_at timestamp
-   user_deleted boolean (default false)
-   reply_to_user_id integer (null, fkey users)
-   percent_rank double (null, default 1.0)
-   notify_user_count integer (default 0, denormal post_actions)
-   like_score integer (default 0, denormal post_actions)
-   deleted_by_id integer (null, fkey users)
-   edit_reason varchar(0) (null)
-   word_count integer (null, denormal posts)
-   version integer (default 1, fkey post_revisions.number)
-   cook_method integer (default 1)
-   wiki boolean (default false)
-   baked_at timestamp (null)
-   baked_version integer (null)
-   hidden_at timestamp (null)
-   self_edits integer (default 0)
-   reply_quoted boolean (default false)
-   via_email boolean (default false)
-   raw_email text (null)
-   public_version integer (default 1)
-   action_code varchar(0) (null)
-   locked_by_id integer (null, fkey users)
-   image_upload_id bigint (null)
-   outbound_message_id varchar(0) (null)

### topics

-   id serial (primary key)
-   title varchar(0)
-   last_posted_at timestamp (null, denormal posts)
-   created_at timestamp
-   updated_at timestamp
-   views integer (default 0, denormal topic_views)
-   posts_count integer (default 0, denormal posts)
-   user_id integer (null, fkey users)
-   last_post_user_id integer (fkey users)
-   reply_count integer (default 0, denormal posts)
-   featured_user1_id integer (null, fkey users)
-   featured_user2_id integer (null, fkey users)
-   featured_user3_id integer (null, fkey users)
-   deleted_at timestamp (null)
-   highest_post_number integer (default 0, denormal posts)
-   like_count integer (default 0, denormal post_actions)
-   incoming_link_count integer (default 0, denormal topic_links)
-   category_id integer (null, fkey categories)
-   visible boolean (default true)
-   moderator_posts_count integer (default 0, denormal posts)
-   closed boolean (default false)
-   archived boolean (default false)
### badge_types

-   id serial (primary key)
-   name varchar(0)
-   created_at timestamp
-   updated_at timestamp

### bookmarks

-   id serial (primary key)
-   user_id bigint (fkey users)
-   name varchar(100) (null)
-   reminder_at timestamp (null)
-   created_at timestamp
-   updated_at timestamp
-   reminder_last_sent_at timestamp (null)
-   reminder_set_at timestamp (null)
-   auto_delete_preference integer (default 0)
-   pinned boolean (null, default false)
-   bookmarkable_id integer (null)
-   bookmarkable_type varchar(0) (null)

### calendar_events

-   id serial (primary key)
-   topic_id integer (fkey topics)
-   post_id integer (null, fkey posts)
-   post_number integer (null)
-   user_id integer (null, fkey users)
-   username varchar(0) (null)
-   description varchar(0) (null)
-   start_date timestamp
-   end_date timestamp (null)
-   recurrence varchar(0) (null)
-   region varchar(0) (null)
-   created_at timestamp
-   updated_at timestamp
-   timezone varchar(0) (null)

### categories_web_hooks

-   web_hook_id integer
-   category_id integer (fkey categories)

### category_custom_fields

-   id serial (primary key)
-   category_id integer (fkey categories)
-   name varchar(256)
-   value text (null)
-   created_at timestamp
-   updated_at timestamp

### category_featured_topics

-   category_id integer (fkey categories)
-   topic_id integer (fkey topics)
-   created_at timestamp
-   updated_at timestamp
-   rank integer (default 0)
-   id serial (primary key)

### category_groups

-   id serial (primary key)
-   category_id integer (fkey categories)
-   group_id integer (fkey groups)
-   created_at timestamp
-   updated_at timestamp
-   permission_type integer (null, default 1)

### category_required_tag_groups

-   id serial (primary key)
-   category_id bigint (fkey categories)
-   tag_group_id bigint
-   min_count integer (default 1)
-   order integer (default 1)
-   created_at timestamp
-   updated_at timestamp

### category_search_data

-   category_id integer (fkey categories)
-   search_data tsvector
-   raw_data text (null)
-   locale text (null)
-   version integer (null, default 0)

### category_tag_groups

-   id serial (primary key)
-   category_id integer (fkey categories)
-   tag_group_id integer
-   created_at timestamp
-   updated_at timestamp

### category_tag_stats

-   id serial (primary key)
-   category_id bigint (fkey categories)
-   tag_id bigint
-   topic_count integer (default 0)

### category_tags

-   id serial (primary key)
-   category_id integer (fkey categories)
-   tag_id integer
-   created_at timestamp
-   updated_at timestamp

### category_users

-   id serial (primary key)
-   category_id integer (fkey categories)
-   user_id integer (fkey users)
-   notification_level integer
-   last_seen_at timestamp (null)

### gamification_scores

-   id serial (primary key)
-   user_id integer (fkey users)
-   date date
-   score integer

### given_daily_likes

-   user_id integer
-   likes_given integer
-   given_date date
-   limit_reached boolean (default false)

### group_archived_messages

-   id serial (primary key)
-   group_id integer (fkey groups)
-   topic_id integer (fkey topics)
-   created_at timestamp
-   updated_at timestamp

### group_associated_groups

-   id serial (primary key)
-   group_id bigint (fkey groups)
-   associated_group_id bigint
-   created_at timestamp
-   updated_at timestamp

### group_category_notification_defaults

-   id serial (primary key)
-   group_id integer (fkey groups)
-   category_id integer (fkey categories)
-   notification_level integer

### group_custom_fields

-   id serial (primary key)
-   group_id integer (fkey groups)
-   name varchar(256)
-   value text (null)
-   created_at timestamp
-   updated_at timestamp

### group_histories

-   id serial (primary key)
-   group_id integer (fkey groups)
-   acting_user_id integer (fkey users)
-   target_user_id integer (null, fkey users)
-   action integer
-   subject varchar(0) (null)
-   prev_value text (null)
-   new_value text (null)
-   created_at timestamp
-   updated_at timestamp

### group_mentions

-   id serial (primary key)
-   post_id integer (null, fkey posts)
-   group_id integer (null, fkey groups)
-   created_at timestamp
-   updated_at timestamp

### group_requests

-   id serial (primary key)
-   group_id integer (null, fkey groups)
-   user_id integer (null, fkey users)
-   reason text (null)
-   created_at timestamp
-   updated_at timestamp

### group_tag_notification_defaults

-   id serial (primary key)
-   group_id integer (fkey groups)
-   tag_id integer
-   notification_level integer

### group_users

-   id serial (primary key)
-   group_id integer (fkey groups)
-   user_id integer (fkey users)
-   created_at timestamp
-   updated_at timestamp
-   owner boolean (default false)
-   notification_level integer (default 2)
-   first_unread_pm_at timestamp (default CURRENT_TIMESTAMP)

### groups_web_hooks

-   web_hook_id integer
-   group_id integer (fkey groups)

### ignored_users

-   id serial (primary key)
-   user_id integer (fkey users)
-   ignored_user_id integer (fkey users)
-   created_at timestamp
-   updated_at timestamp
-   summarized_at timestamp (null)
-   expiring_at timestamp

### imap_sync_logs

-   id serial (primary key)
-   level integer
-   message varchar(0)
-   group_id bigint (null, fkey groups)
-   created_at timestamp
-   updated_at timestamp

### incoming_chat_webhooks

-   id serial (primary key)
-   name varchar(0)
-   key varchar(0)
-   chat_channel_id integer
-   username varchar(0) (null)
-   description varchar(0) (null)
-   emoji varchar(0) (null)
-   created_at timestamp
-   updated_at timestamp

### incoming_domains

-   id serial (primary key)
-   name varchar(100)
-   https boolean (default false)
-   port integer

### incoming_emails

-   id serial (primary key)
-   user_id integer (null, fkey users)
-   topic_id integer (null, fkey topics)
-   post_id integer (null, fkey posts)
-   raw text (null)

### minimum_discourse_version

-   minimum_discourse_version varchar(0) (null)
-   maximum_discourse_version varchar(0) (null)

### reviewable_claimed_topics

-   id serial (primary key)
-   user_id integer (fkey users)
-   topic_id integer (fkey topics)
-   created_at timestamp
-   updated_at timestamp

### reviewable_histories

-   id serial (primary key)
-   reviewable_id integer
-   reviewable_history_type integer
-   status integer
-   created_by_id integer (fkey users)
-   edited json (null)
-   created_at timestamp
-   updated_at timestamp

### reviewable_scores

-   id serial (primary key)
-   reviewable_id integer
-   user_id integer (fkey users)
-   reviewable_score_type integer
-   status integer
-   score double (default 0.0)
-   take_action_bonus double (default 0.0)
-   reviewed_by_id integer (null, fkey users)
-   reviewed_at timestamp (null)
-   meta_topic_id integer (null)
-   created_at timestamp
-   updated_at timestamp
-   reason varchar(0) (null)
-   user_accuracy_bonus double (default 0.0)

### reviewables

-   id serial (primary key)
-   type varchar(0)
-   status integer (default 0)
-   created_by_id integer (fkey users)
-   reviewable_by_moderator boolean (default false)
-   reviewable_by_group_id integer (null)
-   category_id integer (null, fkey categories)
-   topic_id integer (null, fkey topics)
-   score double (default 0.0)
-   potential_spam boolean (default false)
-   target_id integer (null)
-   target_type varchar(0) (null)
-   target_created_by_id integer (null, fkey users)
-   payload json (null)
-   version integer (default 0)
-   latest_score timestamp (null)
-   created_at timestamp
-   updated_at timestamp
-   force_review boolean (default false)
-   reject_reason text (null)

### saved_search_results

-   id serial (primary key)
-   saved_search_id integer
-   post_id integer (fkey posts)
-   notification_id integer (null)
-   created_at timestamp
-   updated_at timestamp

### saved_searches

-   id serial (primary key)
-   user_id integer (fkey users)
-   query varchar(0)
-   compiled_query varchar(0) (null)
-   frequency integer
-   last_post_id integer
-   last_searched_at timestamp
-   created_at timestamp
-   updated_at timestamp

### scheduler_stats

-   id serial (primary key)
-   name varchar(0)
-   hostname varchar(0)
-   pid integer
-   duration_ms integer (null)
-   live_slots_start integer (null)
-   live_slots_finish integer (null)
-   started_at timestamp
-   success boolean (null)
-   error text (null)

### schema_migration_details

-   id serial (primary key)
-   version varchar(0)
-   name varchar(0)
-   hostname varchar(0) (null)
-   git_version varchar(0) (null)
-   rails_version varchar(0) (null)
-   duration integer (null)
-   direction varchar(0) (null)
-   created_at timestamp
-   updated_at timestamp

### schema_migrations

-   version varchar(0)

### screened_emails

-   id serial (primary key)
-   email varchar(0)
-   action_type integer
-   match_count integer (default 0)
-   last_match_at timestamp (null)
-   created_at timestamp
-   updated_at timestamp
-   ip_address inet (null)

### screened_ip_addresses

-   id serial
### user_api_key_scopes

-   id serial (primary key)
-   user_api_key_id integer
-   name varchar(0)
-   created_at timestamp
-   updated_at timestamp
-   allowed_parameters jsonb (null)

### user_api_keys

-   id serial (primary key)
-   user_id integer (fkey users)
-   client_id varchar(0)
-   application_name varchar(0)
-   push_url varchar(0) (null)
-   created_at timestamp
-   updated_at timestamp
-   revoked_at timestamp (null)
-   scopes ARRAY (null)
-   last_used_at timestamp (default CURRENT_TIMESTAMP)
-   key_hash varchar(0)

### user_archived_messages

-   id serial (primary key)
-   user_id integer (fkey users)
-   topic_id integer (fkey topics)
-   created_at timestamp
-   updated_at timestamp

### user_associated_accounts

-   id serial (primary key)
-   provider_name varchar(0)
-   provider_uid varchar(0)
-   user_id integer (null, fkey users)
-   last_used timestamp (default CURRENT_TIMESTAMP)
-   info jsonb (default '{}'::jsonb)
-   credentials jsonb (default '{}'::jsonb)
-   extra jsonb (default '{}'::jsonb)
-   created_at timestamp
-   updated_at timestamp

### user_associated_groups

-   id serial (primary key)
-   user_id bigint (fkey users)
-   associated_group_id bigint
-   created_at timestamp
-   updated_at timestamp

### user_auth_token_logs

-   id serial (primary key)
-   action varchar(0)
-   user_auth_token_id integer (null)
-   user_id integer (null, fkey users)
-   client_ip inet (null)
-   user_agent varchar(0) (null)
-   auth_token varchar(0) (null)
-   created_at timestamp (null)
-   path varchar(0) (null)

### user_auth_tokens

-   id serial (primary key)
-   user_id integer (fkey users)
-   auth_token varchar(0)
-   prev_auth_token varchar(0)
-   user_agent varchar(0) (null)
-   auth_token_seen boolean (default false)
-   client_ip inet (null)
-   rotated_at timestamp
-   created_at timestamp
-   updated_at timestamp
-   seen_at timestamp (null)

### user_avatars

-   id serial (primary key)
-   user_id integer (fkey users)
-   custom_upload_id integer (null, fkey uploads)
-   gravatar_upload_id integer (null, fkey uploads)
-   last_gravatar_download_attempt timestamp (null)
-   created_at timestamp
-   updated_at timestamp

### user_badges

-   id serial (primary key)
-   badge_id integer
-   user_id integer
-   fkey users
-   granted_at timestamp
-   granted_by_id integer
-   fkey users
-   post_id integer (null, fkey posts)
-   notification_id integer (null, fkey notifications)
-   seq integer (default 0)
-   featured_rank integer (null)
-   created_at timestamp
-   is_favorite boolean (null)

### user_chat_channel_memberships

-   id serial (primary key)
-   user_id integer
-   fkey users
-   chat_channel_id integer
-   last_read_message_id integer (null)
-   following boolean (default false)
-   muted boolean (default false)
-   desktop_notification_level integer (default 1)
-   mobile_notification_level integer (default 1)
-   created_at timestamp
-   updated_at timestamp
-   last_unread_mention_when_emailed_id integer (null)
-   join_mode integer (default 0)

### user_custom_fields

-   id serial (primary key)
-   user_id integer
