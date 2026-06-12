---
title: "Stopping Postfix from sending bounce email for non-existent emails"
date: 2013-11-04
forum: Server Platforms
---

### Post by dheianevans on 2013-11-04
I'm migrating to a new server soon and decided to migrate my mail setup first, switching from qmail to postfix.

In qmail, I used the validrcptto script to drop email for non-existent users completely so the server isn't bogged down with bounce emails and backscatter. I've read tutorials here and Googled elsewhere, but I'm missing something obvious I'm assuming and my system is still sending out "Recipient address rejected" emails instead of ignoring them. The users are virtual users and everyhting appears to be working fine except for this one aspect.

I'd appreciate new sets of eyes looking at my config. Many thanks.

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
local_recipient_maps = hash:/etc/postfix/validrcpt
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot.conf -m "${EXTENSION}"
mailbox_size_limit = 0
myhostname = localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
policy-spf_time_limit = 3600s
readme_directory = no
recipient_bcc_maps = hash:/etc/postfix/recipient_bcc
recipient_delimiter = +
relay_recipient_maps = hash:/etc/postfix/relay_recipients
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination,check_policy_service unix:private/policy-spf,reject_rbl_client zen.spamhaus.org,reject_rbl_client bl.spamcop.net,reject_rbl_client cbl.abuseat.org,check_policy_service inet:127.0.0.1:10023
smtpd_relay_restrictions = permit_mynetworks,permit_sasl_authenticated,defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/dovecot/dovecot.pem
smtpd_tls_key_file = /etc/dovecot/private/dovecot.pem
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = digitalhit.com
virtual_mailbox_maps = hash:/etc/postfix/vmaps
virtual_minimum_uid = 1000
virtual_uid_maps = static:5000

```

---

### Post by houstonbofh on 2013-11-06
In most cases I have seen, a default mailbox is set up for typo-mail.  With no "Recipient address rejected" errors, there is no backscatter.  However, it does collect some spam.  For that, I love graylisting!  Cuts off a huge chunk of spam!

---

