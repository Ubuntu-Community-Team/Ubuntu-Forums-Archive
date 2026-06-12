---
title: "Postfix relay problem"
date: 2008-04-06
forum: Server Platforms
---

### Post by Dr Small on 2008-04-06
I just installed courier-pop and can connect on port 110 with Evolution, so sending and receiving (locally) works fine. But when I tried to send an email to hackermail, I got:
```
Error while performing operation.

RCPT TO <drsmall@hackermail.com> failed: <drsmall@hackermail.com>: Relay access denied
```

How do I fix this so I can send with SMTP to other domains??

Dr Small

---

### Post by Metro_Dan on 2008-04-06
Are you authenticating?

---

### Post by Dr Small on 2008-04-06
Yes, and no. I have trying practically everything. Whether it be authenticating or not. But to answer your question, no. In the above post, I am not authenticating.

For the record, here is the output of "postconf -d"
```

2bounce_notice_recipient = postmaster
access_map_reject_code = 554
address_verify_default_transport = $default_transport
address_verify_local_transport = $local_transport
address_verify_map = 
address_verify_negative_cache = yes
address_verify_negative_expire_time = 3d
address_verify_negative_refresh_time = 3h
address_verify_poll_count = 3
address_verify_poll_delay = 3s
address_verify_positive_expire_time = 31d
address_verify_positive_refresh_time = 7d
address_verify_relay_transport = $relay_transport
address_verify_relayhost = $relayhost
address_verify_sender = postmaster
address_verify_sender_dependent_relayhost_maps = $sender_dependent_relayhost_maps
address_verify_service_name = verify
address_verify_transport_maps = $transport_maps
address_verify_virtual_transport = $virtual_transport
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases, nis:mail.aliases
allow_mail_to_commands = alias, forward
allow_mail_to_files = alias, forward
allow_min_user = no
allow_percent_hack = yes
allow_untrusted_routing = no
alternate_config_directories = 
always_bcc = 
anvil_rate_time_unit = 60s
anvil_status_update_time = 600s
append_at_myorigin = yes
append_dot_mydomain = yes
application_event_drain_time = 100s
authorized_flush_users = static:anyone
authorized_mailq_users = static:anyone
authorized_submit_users = static:anyone
backwards_bounce_logfile_compatibility = yes
berkeley_db_create_buffer_size = 16777216
berkeley_db_read_buffer_size = 131072
best_mx_transport = 
biff = yes
body_checks = 
body_checks_size_limit = 51200
bounce_notice_recipient = postmaster
bounce_queue_lifetime = 5d
bounce_service_name = bounce
bounce_size_limit = 50000
bounce_template_file = 
broken_sasl_auth_clients = no
canonical_classes = envelope_sender, envelope_recipient, header_sender, header_recipient
canonical_maps = 
cleanup_service_name = cleanup
command_directory = /usr/sbin
command_execution_directory = 
command_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
command_time_limit = 1000s
config_directory = /etc/postfix
connection_cache_protocol_timeout = 5s
connection_cache_service_name = scache
connection_cache_status_update_time = 600s
connection_cache_ttl_limit = 2s
content_filter = 
daemon_directory = /usr/lib/postfix
daemon_timeout = 18000s
debug_peer_level = 2
debug_peer_list = 
default_database_type = hash
default_delivery_slot_cost = 5
default_delivery_slot_discount = 50
default_delivery_slot_loan = 3
default_destination_concurrency_limit = 20
default_destination_recipient_limit = 50
default_extra_recipient_limit = 1000
default_minimum_delivery_slots = 3
default_privs = nobody
default_process_limit = 100
default_rbl_reply = $rbl_code Service unavailable; $rbl_class [$rbl_what] blocked using $rbl_domain${rbl_reason?; $rbl_reason}
default_recipient_limit = 10000
default_transport = smtp
default_verp_delimiters = +=
defer_code = 450
defer_service_name = defer
defer_transports = 
delay_logging_resolution_limit = 2
delay_notice_recipient = postmaster
delay_warning_time = 0h
deliver_lock_attempts = 20
deliver_lock_delay = 1s
disable_dns_lookups = no
disable_mime_input_processing = no
disable_mime_output_conversion = no
disable_verp_bounces = no
disable_vrfy_command = no
dont_remove = 0
double_bounce_sender = double-bounce
duplicate_filter_limit = 1000
empty_address_recipient = MAILER-DAEMON
enable_original_recipient = yes
error_notice_recipient = postmaster
error_service_name = error
execution_directory_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
expand_owner_alias = no
export_environment = TZ MAIL_CONFIG LANG
fallback_transport = 
fallback_transport_maps = 
fast_flush_domains = $relay_domains
fast_flush_purge_time = 7d
fast_flush_refresh_time = 12h
fault_injection_code = 0
flush_service_name = flush
fork_attempts = 5
fork_delay = 1s
forward_expansion_filter = 1234567890!@%-_=+:,./abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
forward_path = $home/.forward${recipient_delimiter}${extension}, $home/.forward
frozen_delivered_to = yes
hash_queue_depth = 1
hash_queue_names = deferred, defer
header_address_token_limit = 10240
header_checks = 
header_size_limit = 102400
helpful_warnings = yes
home_mailbox = 
hopcount_limit = 50
html_directory = no
ignore_mx_lookup_error = no
import_environment = MAIL_CONFIG MAIL_DEBUG MAIL_LOGTAG TZ XAUTHORITY DISPLAY LANG=C
in_flow_delay = 1s
inet_interfaces = all
inet_protocols = ipv4
initial_destination_concurrency = 5
internal_mail_filter_classes = 
invalid_hostname_reject_code = 501
ipc_idle = 100s
ipc_timeout = 3600s
ipc_ttl = 1000s
line_length_limit = 2048
lmtp_bind_address = 
lmtp_bind_address6 = 
lmtp_cname_overrides_servername = no
lmtp_connect_timeout = 0s
lmtp_connection_cache_destinations = 
lmtp_connection_cache_on_demand = yes
lmtp_connection_cache_time_limit = 2s
lmtp_connection_reuse_time_limit = 300s
lmtp_data_done_timeout = 600s
lmtp_data_init_timeout = 120s
lmtp_data_xfer_timeout = 180s
lmtp_defer_if_no_mx_address_found = no
lmtp_destination_concurrency_limit = $default_destination_concurrency_limit
lmtp_destination_recipient_limit = $default_destination_recipient_limit
lmtp_discard_lhlo_keyword_address_maps = 
lmtp_discard_lhlo_keywords = 
lmtp_enforce_tls = no
lmtp_generic_maps = 
lmtp_host_lookup = dns
lmtp_lhlo_name = $myhostname
lmtp_lhlo_timeout = 300s
lmtp_line_length_limit = 0
lmtp_mail_timeout = 300s
lmtp_mx_address_limit = 5
lmtp_mx_session_limit = 2
lmtp_pix_workaround_delay_time = 10s
lmtp_pix_workaround_threshold_time = 500s
lmtp_quit_timeout = 300s
lmtp_quote_rfc821_envelope = yes
lmtp_randomize_addresses = yes
lmtp_rcpt_timeout = 300s
lmtp_rset_timeout = 20s
lmtp_sasl_auth_enable = no
lmtp_sasl_mechanism_filter = 
lmtp_sasl_password_maps = 
lmtp_sasl_path = 
lmtp_sasl_security_options = noplaintext, noanonymous
lmtp_sasl_tls_security_options = $lmtp_sasl_security_options
lmtp_sasl_tls_verified_security_options = $lmtp_sasl_tls_security_options
lmtp_sasl_type = cyrus
lmtp_send_xforward_command = no
lmtp_sender_dependent_authentication = no
lmtp_skip_5xx_greeting = yes
lmtp_starttls_timeout = 300s
lmtp_tcp_port = 24
lmtp_tls_CAfile = 
lmtp_tls_CApath = 
lmtp_tls_cert_file = 
lmtp_tls_dcert_file = 
lmtp_tls_dkey_file = $lmtp_tls_dcert_file
lmtp_tls_enforce_peername = yes
lmtp_tls_exclude_ciphers = 
lmtp_tls_key_file = $lmtp_tls_cert_file
lmtp_tls_loglevel = 0
lmtp_tls_mandatory_ciphers = medium
lmtp_tls_mandatory_exclude_ciphers = 
lmtp_tls_mandatory_protocols = SSLv3, TLSv1
lmtp_tls_note_starttls_offer = no
lmtp_tls_per_site = 
lmtp_tls_policy_maps = 
lmtp_tls_scert_verifydepth = 5
lmtp_tls_secure_cert_match = nexthop
lmtp_tls_security_level = 
lmtp_tls_session_cache_database = 
lmtp_tls_session_cache_timeout = 3600s
lmtp_tls_verify_cert_match = hostname
lmtp_use_tls = no
lmtp_xforward_timeout = 300s
local_command_shell = 
local_destination_concurrency_limit = 2
local_destination_recipient_limit = 1
local_header_rewrite_clients = permit_inet_interfaces
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
local_transport = local:$myhostname
luser_relay = 
mail_name = Postfix
mail_owner = postfix
mail_release_date = 20070301
mail_spool_directory = /var/mail
mail_version = 2.3.8
mailbox_command = 
mailbox_command_maps = 
mailbox_delivery_lock = fcntl, dotlock
mailbox_size_limit = 51200000
mailbox_transport = 
mailbox_transport_maps = 
mailq_path = /usr/bin/mailq
manpage_directory = /usr/share/man
maps_rbl_domains = 
maps_rbl_reject_code = 554
masquerade_classes = envelope_sender, header_sender, header_recipient
masquerade_domains = 
masquerade_exceptions = 
max_idle = 100s
max_use = 100
maximal_backoff_time = 4000s
maximal_queue_lifetime = 5d
message_reject_characters = 
message_size_limit = 10240000
message_strip_characters = 
milter_command_timeout = 30s
milter_connect_macros = j {daemon_name} v
milter_connect_timeout = 30s
milter_content_timeout = 300s
milter_data_macros = i
milter_default_action = tempfail
milter_end_of_data_macros = i
milter_helo_macros = {tls_version} {cipher} {cipher_bits} {cert_subject} {cert_issuer}
milter_macro_daemon_name = $myhostname
milter_macro_v = $mail_name $mail_version
milter_mail_macros = i {auth_type} {auth_authen} {auth_author} {mail_addr}
milter_protocol = 2
milter_rcpt_macros = i {rcpt_addr}
milter_unknown_command_macros = 
mime_boundary_length_limit = 2048
mime_header_checks = $header_checks
mime_nesting_limit = 100
minimal_backoff_time = 1000s
multi_recipient_bounce_reject_code = 550
mydestination = $myhostname, localhost.$mydomain, localhost
mydomain = localdomain
myhostname = mycroft.localdomain
mynetworks = 127.0.0.0/8 192.168.0.0/24 
mynetworks_style = subnet
myorigin = $myhostname
nested_header_checks = $header_checks
newaliases_path = /usr/bin/newaliases
non_fqdn_reject_code = 504
non_smtpd_milters = 
notify_classes = resource, software
owner_request_special = yes
parent_domain_matches_subdomains = debug_peer_list,fast_flush_domains,mynetworks,permit_mx_backup_networks,qmqpd_authorized_clients,relay_domains,smtpd_access_maps
permit_mx_backup_networks = 
pickup_service_name = pickup
plaintext_reject_code = 450
prepend_delivered_header = command, file, forward
process_id_directory = pid
propagate_unmatched_extensions = canonical, virtual
proxy_interfaces = 
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks
qmgr_clog_warn_time = 300s
qmgr_fudge_factor = 100
qmgr_message_active_limit = 20000
qmgr_message_recipient_limit = 20000
qmgr_message_recipient_minimum = 10
qmqpd_authorized_clients = 
qmqpd_error_delay = 1s
qmqpd_timeout = 300s
queue_directory = /var/spool/postfix
queue_file_attribute_count_limit = 100
queue_minfree = 0
queue_run_delay = 1000s
queue_service_name = qmgr
rbl_reply_maps = 
readme_directory = /usr/share/doc/postfix
receive_override_options = 
recipient_bcc_maps = 
recipient_canonical_classes = envelope_recipient, header_recipient
recipient_canonical_maps = 
recipient_delimiter = 
reject_code = 554
relay_clientcerts = 
relay_destination_concurrency_limit = $default_destination_concurrency_limit
relay_destination_recipient_limit = $default_destination_recipient_limit
relay_domains = $mydestination
relay_domains_reject_code = 554
relay_recipient_maps = 
relay_transport = relay
relayhost = 
relocated_maps = 
remote_header_rewrite_domain = 
require_home_directory = no
resolve_dequoted_address = yes
resolve_null_domain = no
resolve_numeric_domain = no
rewrite_service_name = rewrite
sample_directory = /usr/share/doc/postfix/examples
sender_bcc_maps = 
sender_canonical_classes = envelope_sender, header_sender
sender_canonical_maps = 
sender_dependent_relayhost_maps = 
sendmail_path = /usr/sbin/sendmail
service_throttle_time = 60s
setgid_group = postdrop
show_user_unknown_table_name = yes
showq_service_name = showq
smtp_always_send_ehlo = yes
smtp_bind_address = 
smtp_bind_address6 = 
smtp_cname_overrides_servername = no
smtp_connect_timeout = 30s
smtp_connection_cache_destinations = 
smtp_connection_cache_on_demand = yes
smtp_connection_cache_time_limit = 2s
smtp_connection_reuse_time_limit = 300s
smtp_data_done_timeout = 600s
smtp_data_init_timeout = 120s
smtp_data_xfer_timeout = 180s
smtp_defer_if_no_mx_address_found = no
smtp_destination_concurrency_limit = $default_destination_concurrency_limit
smtp_destination_recipient_limit = $default_destination_recipient_limit
smtp_discard_ehlo_keyword_address_maps = 
smtp_discard_ehlo_keywords = 
smtp_enforce_tls = no
smtp_fallback_relay = $fallback_relay
smtp_generic_maps = 
smtp_helo_name = $myhostname
smtp_helo_timeout = 300s
smtp_host_lookup = dns
smtp_line_length_limit = 0
smtp_mail_timeout = 300s
smtp_mx_address_limit = 5
smtp_mx_session_limit = 2
smtp_never_send_ehlo = no
smtp_pix_workaround_delay_time = 10s
smtp_pix_workaround_threshold_time = 500s
smtp_quit_timeout = 300s
smtp_quote_rfc821_envelope = yes
smtp_randomize_addresses = yes
smtp_rcpt_timeout = 300s
smtp_rset_timeout = 20s
smtp_sasl_auth_enable = no
smtp_sasl_mechanism_filter = 
smtp_sasl_password_maps = 
smtp_sasl_path = 
smtp_sasl_security_options = noplaintext, noanonymous
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_tls_security_options
smtp_sasl_type = cyrus
smtp_send_xforward_command = no
smtp_sender_dependent_authentication = no
smtp_skip_5xx_greeting = yes
smtp_skip_quit_response = yes
smtp_starttls_timeout = 300s
smtp_tls_CAfile = 
smtp_tls_CApath = 
smtp_tls_cert_file = 
smtp_tls_dcert_file = 
smtp_tls_dkey_file = $smtp_tls_dcert_file
smtp_tls_enforce_peername = yes
smtp_tls_exclude_ciphers = 
smtp_tls_key_file = $smtp_tls_cert_file
smtp_tls_loglevel = 0
smtp_tls_mandatory_ciphers = medium
smtp_tls_mandatory_exclude_ciphers = 
smtp_tls_mandatory_protocols = SSLv3, TLSv1
smtp_tls_note_starttls_offer = no
smtp_tls_per_site = 
smtp_tls_policy_maps = 
smtp_tls_scert_verifydepth = 5
smtp_tls_secure_cert_match = nexthop, dot-nexthop
smtp_tls_security_level = 
smtp_tls_session_cache_database = 
smtp_tls_session_cache_timeout = 3600s
smtp_tls_verify_cert_match = hostname
smtp_use_tls = no
smtp_xforward_timeout = 300s
smtpd_authorized_verp_clients = $authorized_verp_clients
smtpd_authorized_xclient_hosts = 
smtpd_authorized_xforward_hosts = 
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_connection_count_limit = 50
smtpd_client_connection_rate_limit = 0
smtpd_client_event_limit_exceptions = ${smtpd_client_connection_limit_exceptions:$mynetworks}
smtpd_client_message_rate_limit = 0
smtpd_client_new_tls_session_rate_limit = 0
smtpd_client_recipient_rate_limit = 0
smtpd_client_restrictions = 
smtpd_data_restrictions = 
smtpd_delay_open_until_valid_rcpt = yes
smtpd_delay_reject = yes
smtpd_discard_ehlo_keyword_address_maps = 
smtpd_discard_ehlo_keywords = 
smtpd_end_of_data_restrictions = 
smtpd_enforce_tls = no
smtpd_error_sleep_time = 1s
smtpd_etrn_restrictions = 
smtpd_expansion_filter = \t\40!"#$%&'()*+,-./0123456789:;<=>?@ABCDEFGHIJKLMNOPQRSTUVWXYZ[\\]^_`abcdefghijklmnopqrstuvwxyz{|}~
smtpd_forbidden_commands = CONNECT GET POST
smtpd_hard_error_limit = 20
smtpd_helo_required = no
smtpd_helo_restrictions = 
smtpd_history_flush_threshold = 100
smtpd_junk_command_limit = 100
smtpd_milters = 
smtpd_noop_commands = 
smtpd_null_access_lookup_key = <>
smtpd_peername_lookup = yes
smtpd_policy_service_max_idle = 300s
smtpd_policy_service_max_ttl = 1000s
smtpd_policy_service_timeout = 100s
smtpd_proxy_ehlo = $myhostname
smtpd_proxy_filter = 
smtpd_proxy_timeout = 100s
smtpd_recipient_limit = 1000
smtpd_recipient_overshoot_limit = 1000
smtpd_recipient_restrictions = permit_mynetworks, reject_unauth_destination
smtpd_reject_unlisted_recipient = yes
smtpd_reject_unlisted_sender = no
smtpd_restriction_classes = 
smtpd_sasl_auth_enable = no
smtpd_sasl_authenticated_header = no
smtpd_sasl_exceptions_networks = 
smtpd_sasl_local_domain = 
smtpd_sasl_path = smtpd
smtpd_sasl_security_options = noanonymous
smtpd_sasl_tls_security_options = $smtpd_sasl_security_options
smtpd_sasl_type = cyrus
smtpd_sender_login_maps = 
smtpd_sender_restrictions = 
smtpd_soft_error_limit = 10
smtpd_starttls_timeout = 300s
smtpd_timeout = 300s
smtpd_tls_CAfile = 
smtpd_tls_CApath = 
smtpd_tls_always_issue_session_ids = yes
smtpd_tls_ask_ccert = no
smtpd_tls_auth_only = no
smtpd_tls_ccert_verifydepth = 5
smtpd_tls_cert_file = 
smtpd_tls_dcert_file = 
smtpd_tls_dh1024_param_file = 
smtpd_tls_dh512_param_file = 
smtpd_tls_dkey_file = $smtpd_tls_dcert_file
smtpd_tls_exclude_ciphers = 
smtpd_tls_key_file = $smtpd_tls_cert_file
smtpd_tls_loglevel = 0
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_exclude_ciphers = 
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = no
smtpd_tls_req_ccert = no
smtpd_tls_security_level = 
smtpd_tls_session_cache_database = 
smtpd_tls_session_cache_timeout = 3600s
smtpd_tls_wrappermode = no
smtpd_use_tls = no
soft_bounce = no
stale_lock_time = 500s
strict_7bit_headers = no
strict_8bitmime = no
strict_8bitmime_body = no
strict_mime_encoding_domain = no
strict_rfc821_envelopes = no
sun_mailtool_compatibility = no
swap_bangpath = yes
syslog_facility = mail
syslog_name = postfix
tls_daemon_random_bytes = 32
tls_export_cipherlist = ALL:+RC4:@STRENGTH
tls_high_cipherlist = ALL:!EXPORT:!LOW:!MEDIUM:+RC4:@STRENGTH
tls_low_cipherlist = ALL:!EXPORT:+RC4:@STRENGTH
tls_medium_cipherlist = ALL:!EXPORT:!LOW:+RC4:@STRENGTH
tls_null_cipherlist = !aNULL:eNULL+kRSA
tls_random_bytes = 32
tls_random_exchange_name = ${queue_directory}/prng_exch
tls_random_prng_update_period = 3600s
tls_random_reseed_period = 3600s
tls_random_source = dev:/dev/urandom
trace_service_name = trace
transport_maps = 
transport_retry_time = 60s
trigger_timeout = 10s
undisclosed_recipients_header = To: undisclosed-recipients:;
unknown_address_reject_code = 450
unknown_client_reject_code = 450
unknown_hostname_reject_code = 450
unknown_local_recipient_reject_code = 550
unknown_relay_recipient_reject_code = 550
unknown_virtual_alias_reject_code = 550
unknown_virtual_mailbox_reject_code = 550
unverified_recipient_reject_code = 450
unverified_sender_reject_code = 450
verp_delimiter_filter = -=+
virtual_alias_domains = $virtual_alias_maps
virtual_alias_expansion_limit = 1000
virtual_alias_maps = $virtual_maps
virtual_alias_recursion_limit = 1000
virtual_destination_concurrency_limit = $default_destination_concurrency_limit
virtual_destination_recipient_limit = $default_destination_recipient_limit
virtual_gid_maps = 
virtual_mailbox_base = 
virtual_mailbox_domains = $virtual_mailbox_maps
virtual_mailbox_limit = 51200000
virtual_mailbox_lock = fcntl
virtual_mailbox_maps = 
virtual_minimum_uid = 100
virtual_transport = virtual
virtual_uid_maps = 
```

That may be, or may not be very helpful, I don't know. Thanks for asking, and hopefully I can supply you with whatever information you need, so we can solve this issue :)

Dr Small

---

### Post by Metro_Dan on 2008-04-06
Have you tried using a external mail client?

---

### Post by MJN on 2008-04-06
> **Dr Small said:**
> For the record, here is the output of "postconf -d"

Postconf -d gives the default settings, what we need to see is [B]postconf -n

[/B]The key thing here is that Postfix is not letting you send mail to domains outside of that which is responsible for - this boils down to it not considering you 'trusted'. Gaining that trust can take one of many forms including coming from an IP address which it trusts (i.e. local addresses, explicitly set external addresses) or authenticating with a username/password.

Mathew

P.S. Are you the Dr Small that contacted me about IPv6...?

---

### Post by Dr Small on 2008-04-06
Ok, here is postconf -n:
```
drsmall@mycroft:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
mailbox_command = 
mailbox_size_limit = 0
mydestination = mycroftserver.homelinux.org, selftech.homelinux.org, mycroft, localhost.localdomain, localhost, mycroft.org
mydomain = mycroftserver.homelinux.org
myhostname = mycroftserver.homelinux.org
myorigin = /etc/mailname
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_use_tls = yes

```

Yes, I am the same Dr Small :D

So.... is there any way I can trust all domains? Because I would like to use my POP account to send to other addresses. I am still reading on Postfix documentation, but any fresh pointers would be most generous :)

Dr Small

---

### Post by Dr Small on 2008-04-06
After receiving a few hints from #postfix @ freenode, I was able to somewhat solve the problem. My "mynetworks" was set to:
```
mynetworks = 127.0.0.0/8 192.168.0.0/24
```

Well, I added my IP address to the end of it (the WAN IP) and then the email sent. Ok. So let's say my WAN IP changes, or I want to check my mail from a friends house or laptop on the go. How would I enable ANY IP address to relay mail through my SMTP server?

Dr Small

---

### Post by MJN on 2008-04-07
You need to configure either POP-before-SMTP authentication or, preferably, SMTP AUTH. There must be a HowTo guide around these parts somewhere.
 
The key step here is that IP address authentication is only really any use for fixed known networks, e.g. your LAN, and falls down when it comes to authenticating users out on the Internet and hence why you need 'proper' authentication. 
 
Mathew

---

### Post by Dr Small on 2008-04-07
Ok. Thanks for that hint. I found a guide and am reading through and trying it, but am having absolutely no success yet.
[http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html](http://postfix.state-of-mind.de/patrick.koetter/smtpauth/smtp_auth_mailclients.html)

Here is my /etc/postfix/main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# SASL SUPPORT FOR CLIENTS
# The following options set parameters needed by Postfix to enable 
# Cyrus-SASL support for authentication of mail clients. 
# 
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mynetworks = 127.0.0.0/8 192.168.0.0/24
myhostname = mycroftserver.homelinux.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mycroftserver.homelinux.org, selftech.homelinux.org, mycroft, localhost.localdomain, localhost, mycroft.org
mailbox_size_limit = 0
recipient_delimiter = +
mydomain = mycroftserver.homelinux.org
home_mailbox = Maildir/
mailbox_command = 

smtpd_recipient_restrictions = 
   permit_sasl_authenticated, 
   permit_mynetworks, 
   check_relay_domains

broken_sasl_auth_clients = yes

```

And in Sylpheed (the mail client) I setup SMTP Authentication, type CRAM-MD5, entered my username and password that I login with to the system, attempt to send an email, and Authentification Fails.

Also, when I telnet to it, on port 25 and say "elho host" it says:
```
250-mycroftserver.homelinux.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
[B]250-AUTH PLAIN CRAM-MD5 LOGIN NTLM DIGEST-MD5
250-AUTH=PLAIN CRAM-MD5 LOGIN NTLM DIGEST-MD5[/B]
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

Thanks for all the help so far.
Dr Small

---

### Post by Dr Small on 2008-04-07
Ok, so I have just tried a different guide:
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I did absolutely everything for the SMTP AUTH using SASL in that guide.
I got down to testing, and I have the same results as the guide, yet I still can not Authenticate in Sylpheed.

Here is my new configuration file:
```

#ee /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = mycroftserver.homelinux.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mycroftserver.homelinux.org, selftech.homelinux.org, mycroft.org,localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom

```

And here is the output when I telnet:
```

root@mycroft:/home/drsmall# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 mycroftserver.homelinux.org ESMTP Postfix (Ubuntu)
ehlo localhost
250-mycroftserver.homelinux.org
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
[B]250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN[/B]
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

Here is my settings in Sylpheed:
```
Authentication:
[x] SMTP Authentication (SMTP AUTH)
     Authenticaion Method: [PLAIN]
      USER ID: drsmall
      Password: (my password here)
```

And the error I receive is:
```
Authentication failed:
535 5.7.0 Error: authentication failed: generic failure
```

Boy, I am getting close, as it seems, yet I still can not authenticate.... I am really desperate!

Dr Small

---

