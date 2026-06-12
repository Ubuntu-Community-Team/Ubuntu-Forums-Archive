---
title: "warning: connect to transport private/myemail@example.com: No such file or directory"
date: 2016-11-10
forum: Server Platforms
---

### Post by fixps on 2016-11-10
Hi guys,

I tried to enable SASL authentication and now I cannot receive mail, but sending mail works just fine. (The inbox actually does exist, I sent from it and responded to the message to test receiving).
When I research this error, most others have something like warning: connect to transport private/smtpd - so I think I've made a mistake in the config somewhere, but I'm not sure where.

When I send myself an email, it gets stuck in the Postfix queue, this error appears in the logs:
```
Nov 10 09:04:15 mail postfix/qmgr[3264]: warning: connect to transport private/test@mail.example.com: No such file or directory
Nov 10 09:04:15 mail postfix/error[14276]: 39273120A4A: to=<test@mail.example.com>, relay=none, delay=75075, delays=75075/0.03/0/0, dsn=4.3.0, status=deferred (mail transport unavailable)
```

main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

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
readme_directory = /usr/share/doc/postfix
# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = mail.example.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
myorigin = /etc/mailname
mydestination = localhost.membership-avenue.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
html_directory = /usr/share/doc/postfix/html
virtual_alias_domains = 
virtual_alias_maps = hash:/var/lib/mailman/data/virtual-mailman, proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /var/vmail
virtual_uid_maps = mysql:/etc/postfix/mysql-virtual_uids.cf
virtual_gid_maps = mysql:/etc/postfix/mysql-virtual_gids.cf
sender_bcc_maps = proxy:mysql:/etc/postfix/mysql-virtual_outgoing_bcc.cf
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
queue_directory = /var/spool/postfix
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_local_domain = mail.example.com
## SASL default policy ##
smtpd_sasl_security_options = noanonymous
smtpd_restriction_classes = greylisting
greylisting = check_policy_service inet:127.0.0.1:10023
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination, check_recipient_access mysql:/etc/postfix/mysql-virtual_recipient.cf, reject_rbl_client zen.spamhaus.org, check_recipient_access mysql:/etc/postfix/mysql-virtual_policy_greylist.cf
smtpd_tls_security_level = may
smtpd_tls_received_header = yes 
smtpd_tls_auth_only = no 
## loglevel 3 or 4 can be used during troubleshooting ##
smtpd_tls_loglevel = 1
## server will announce STARTTLS ##
smtp_tls_note_starttls_offer = yes
smtpd_tls_session_cache_timeout = 3600s
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
relay_domains = mysql:/etc/postfix/mysql-virtual_relaydomains.cf
relay_recipient_maps = mysql:/etc/postfix/mysql-virtual_relayrecipientmaps.cf
smtpd_sender_login_maps = proxy:mysql:/etc/postfix/mysql-virtual_sender_login_maps.cf
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $sender_bcc_maps $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $smtpd_sender_login_maps
smtpd_helo_required = yes
smtpd_helo_restrictions = permit_sasl_authenticated, permit_mynetworks, check_helo_access regexp:/etc/postfix/helo_access, reject_invalid_hostname, reject_non_fqdn_hostname, check_helo_access regexp:/etc/postfix/blacklist_helo
smtpd_sender_restrictions = check_sender_access regexp:/etc/postfix/tag_as_originating.re , permit_mynetworks, permit_sasl_authenticated, check_sender_access mysql:/etc/postfix/mysql-virtual_sender.cf, check_sender_access regexp:/etc/postfix/tag_as_foreign.re
smtpd_client_restrictions = check_client_access mysql:/etc/postfix/mysql-virtual_client.cf
smtpd_client_message_rate_limit = 100
maildrop_destination_concurrency_limit = 1
maildrop_destination_recipient_limit = 1
virtual_transport = dovecot
header_checks = regexp:/etc/postfix/header_checks
mime_header_checks = regexp:/etc/postfix/mime_header_checks
nested_header_checks = regexp:/etc/postfix/nested_header_checks
body_checks = regexp:/etc/postfix/body_checks
owner_request_special = no
smtp_tls_security_level = may
smtpd_tls_mandatory_protocols = !SSLv2, !SSLv3
smtpd_tls_protocols = !SSLv2,!SSLv3
smtp_tls_protocols = !SSLv2,!SSLv3
smtpd_tls_exclude_ciphers = RC4, aNULL
smtp_tls_exclude_ciphers = RC4, aNULL
dovecot_destination_recipient_limit = 1
content_filter = amavis:[127.0.0.1]:10024
receive_override_options = no_address_mappings
# DKIM
milter_default_action = accept
milter_protocol = 2
smtpd_milters = inet:localhost:8891
non_smtpd_milters = inet:localhost:8891

```

I purged Postfix and started a new installation; the same error occurs.

---

### Post by Kirk Schnable on 2016-11-12
This looks like a transport issue, so I would call your attention to the transport maps.

```
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
```

A good next step might be to post the content of those files as well.

---

### Post by fixps on 2016-11-13
Hi Kirk,

/var/lib/mailman/data/transport-mailman:
[blank] -- however, there is also a: /var/lib/mailman/data/transport-mailman**.db**

/etc/postfix/mysql-virtual_transports.cf:
```
user = ispconfig
password = [password here]
dbname = dbispconfig
table = mail_transport
select_field = transport
where_field = domain
additional_conditions = and active = 'y' and server_id = 1
hosts = 127.0.0.1
```

(none of the database stuff has been updated since this problem started)

---

### Post by fixps on 2016-11-13
> **Kirk Schnable said:**
> This looks like a transport issue, so I would call your attention to the transport maps.

```
transport_maps = hash:/var/lib/mailman/data/transport-mailman, proxy:mysql:/etc/postfix/mysql-virtual_transports.cf
```

A good next step might be to post the content of those files as well.

Your post gave me a clue of where to look - I've been spending so much time thinking this was postfix related (because it's the postfix daemon, according to the logs), I never thought to double-check the database.

I opened the mail_transport field in the database to double-check it wasn't blank.. noticed my email address in both domain & transport tables (not sure how/why it got there. I don't recall messing with the database for this SASL config).  
Anyway, I changed the "transport" field to dovecot (because I use dovecot to receive mail - and similar errors around the web report private/**auth** (or whatever method)) .. and finally, the deferred message went into my inbox once i re-queued.

Thanks Kirk, I would have NEVER thought to look there without your comment. You saved me from reloading the server.  I've been at battle with this for a few days.  Thanks so much!!!

---

