---
title: "Postfix delay of 5 mins"
date: 2017-03-11
forum: Server Platforms
---

### Post by Jeffrey_Becker on 2017-03-11
I searched every file in my entire linux server for 300s and found it in my main.cf file of postfix.. I changed it to 10s and restarted and the same issue is happening.
Now i'm searching every file in my linux server for 5m

As a side note this is a mailcow install and they said it isn't them. The messages are also not being signed by DKIM

[http://www.roundcubeforum.net/index.php/topic,24104.0.html](http://www.roundcubeforum.net/index.php/topic,24104.0.html)

---

### Post by cariboo on 2017-03-11
Moved here for quicker help.

---

### Post by TheFu on 2017-03-13
**postconf -n** please. Use **code tags** so it is readable.
None of my stock postfix installs have any delays in sending unless the server is very busy. If it is over 90% utilized, sending email is disabled. That is a normal feature.

---

### Post by Jeffrey_Becker on 2017-03-21
```
alias_database = hash:/etc/aliasesalias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
bounce_queue_lifetime = 1d
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
disable_vrfy_command = yes
greylist = permit_dnswl_client list.dnswl.org, check_policy_service inet:127.0.0.1:10023
html_directory = /usr/share/doc/postfix/html
inet_protocols = all
mailbox_size_limit = 0
maximal_backoff_time = 1800s
maximal_queue_lifetime = 1d
message_size_limit = 104857600
milter_default_action = accept
milter_protocol = 6
minimal_backoff_time = 5s
mydestination = mail.jnjinca.com, localhost.jnjinca.com, localhost
mydomain = jnjinca.com
myhostname = mail.jnjinca.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = $mydomain
plaintext_reject_code = 550
postscreen_access_list = permit_mynetworks, cidr:/etc/postfix/postscreen_access.cidr
postscreen_bare_newline_enable = no
postscreen_blacklist_action = drop
postscreen_cache_cleanup_interval = 24h
postscreen_cache_map = proxy:btree:$data_directory/postscreen_cache
postscreen_dnsbl_action = enforce
postscreen_dnsbl_sites = b.barracudacentral.org=127.0.0.2*7 dnsbl.inps.de=127.0.0.2*7 bl.mailspike.net=127.0.0.2*5 bl.mailspike.net=127.0.0.[10;11;12]*4 dnsbl.sorbs.net=127.0.0.10*8 dnsbl.sorbs.net=127.0.0.5*6 dnsbl.sorbs.net=127.0.0.7*3 dnsbl.sorbs.net=127.0.0.8*2 dnsbl.sorbs.net=127.0.0.6*2 dnsbl.sorbs.net=127.0.0.9*2 zen.spamhaus.org=127.0.0.[10;11]*8 zen.spamhaus.org=127.0.0.[4..7]*6 zen.spamhaus.org=127.0.0.3*4 zen.spamhaus.org=127.0.0.2*3 hostkarma.junkemailfilter.com=127.0.0.2*3 hostkarma.junkemailfilter.com=127.0.0.4*1 hostkarma.junkemailfilter.com=127.0.1.2*1 wl.mailspike.net=127.0.0.[18;19;20]*-2 hostkarma.junkemailfilter.com=127.0.0.1*-2
postscreen_dnsbl_threshold = 8
postscreen_dnsbl_ttl = 5m
postscreen_greet_action = enforce
postscreen_greet_banner = $smtpd_banner
postscreen_greet_ttl = 2d
postscreen_greet_wait = 3s
postscreen_non_smtp_command_enable = no
postscreen_pipelining_enable = no
proxy_read_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_sender_acl.cf, proxy:mysql:/etc/postfix/sql/mysql_tls_enforce_out_policy.cf, proxy:mysql:/etc/postfix/sql/mysql_tls_enforce_in_policy.cf, $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $smtpd_sender_login_maps
queue_run_delay = 5s
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
relay_domains = proxy:mysql:/etc/postfix/sql/mysql_virtual_mxdomain_maps.cf
relay_recipient_maps = proxy:mysql:/etc/postfix/sql/mysql_relay_recipient_maps.cf
relayhost = mail.twc.com
sender_dependent_default_transport_maps = proxy:mysql:/etc/postfix/sql/mysql_tls_enforce_out_policy.cf
smtp_header_checks = pcre:/etc/postfix/mailcow_anonymize_headers.pcre
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_cert_file = /etc/ssl/mail/mail.crt
smtp_tls_key_file = /etc/ssl/mail/mail.key
smtp_tls_loglevel = 1
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname
smtpd_data_restrictions = reject_unauth_pipelining, permit
smtpd_delay_reject = yes
smtpd_error_sleep_time = 10s
smtpd_hard_error_limit = ${stress?1}${stress:5}
smtpd_helo_required = yes
smtpd_proxy_timeout = 600s
smtpd_recipient_restrictions = check_recipient_access proxy:mysql:/etc/postfix/sql/mysql_tls_enforce_in_policy.cf, permit_sasl_authenticated, permit_mynetworks, reject_invalid_helo_hostname, reject_unknown_reverse_client_hostname, reject_unauth_destination
smtpd_restriction_classes = greylist
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_path = private/auth_dovecot
smtpd_sasl_type = dovecot
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_sender_acl.cf
smtpd_sender_restrictions = reject_authenticated_sender_login_mismatch, permit_mynetworks, reject_sender_login_mismatch, permit_sasl_authenticated, reject_unlisted_sender, reject_unknown_sender_domain
smtpd_soft_error_limit = 3
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/mail/mail.crt
smtpd_tls_dh1024_param_file = /etc/ssl/mail/dhparams.pem
smtpd_tls_eecdh_grade = strong
smtpd_tls_exclude_ciphers = ECDHE-RSA-RC4-SHA
smtpd_tls_key_file = /etc/ssl/mail/mail.key
smtpd_tls_loglevel = 1
smtpd_tls_mandatory_ciphers = high
smtpd_tls_mandatory_exclude_ciphers = ECDHE-RSA-RC4-SHA
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
tls_high_cipherlist = EDH+CAMELLIA:EDH+aRSA:EECDH+aRSA+AESGCM:EECDH+aRSA+SHA384:EECDH+aRSA+SHA256:EECDH:+CAMELLIA256:+AES256:+CAMELLIA128:+AES128:+SSLv3:!aNULL:!eNULL:!LOW:!3DES:!MD5:!EXP:!PSK:!DSS:!RC4:!SEED:!ECDSA:CAMELLIA256-SHA:AES256-SHA:CAMELLIA128-SHA:AES128-SHA
virtual_alias_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_alias_maps.cf, proxy:mysql:/etc/postfix/sql/mysql_virtual_spamalias_maps.cf, proxy:mysql:/etc/postfix/sql/mysql_virtual_alias_domain_maps.cf, proxy:mysql:/etc/postfix/sql/mysql_virtual_alias_domain_catchall_maps.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/vmail/
virtual_mailbox_domains = proxy:mysql:/etc/postfix/sql/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/sql/mysql_virtual_mailbox_maps.cf, proxy:mysql:/etc/postfix/sql/mysql_virtual_alias_domain_mailbox_maps.cf
virtual_minimum_uid = 104
virtual_transport = lmtp:unix:private/dovecot-lmtp
virtual_uid_maps = static:5000
postconf: warning: /etc/postfix/master.cf: unused parameter: smtp_delivery_status_filter=pcre:/etc/postfix/smtp_dsn_filter.pcre

```

---

### Post by gtozzi on 2017-03-23
Could it be a DNS issue? Is your DNS subsystem ok?

---

### Post by Jeffrey_Becker on 2017-03-31
not really sure what you mean here.  
[COLOR=#000000][FONT=&quot]Do you mean this?
```
postscreen_dnsbl_ttl = 5m

```
[/FONT][/COLOR]
> **gtozzi said:**
> Could it be a DNS issue? Is your DNS subsystem ok?

---

### Post by gtozzi on 2017-04-01
No, I mean: can the system correctly resolve DNS names into IPs and the inverse?

---

