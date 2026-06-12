---
title: "Issuing enabling authentication on Postfix"
date: 2010-07-03
forum: Server Platforms
---

### Post by hocus on 2010-07-03
I've recently purchased an Australian based VPS plan so I can get back into playing with linux. The current issue holding me up is enabling authentication on the postfix server I've setup.

The server (sparky.atice.org) receives local mail without an issue. When I try to use Thunderbird to authenticate & send mail elsewhere (using it) the connection times out. 

When I telnet into the server directly and attempt to issue the 'AUTH' command it returns '503 5.5.1 Error: authentication not enabled'. This doesn't leave a log entry I can find.

Below are the results of 'postconf -n' - any thoughts?

> alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = ipv4
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = sparky.atice.org, localhost
myhostname = sparky.atice.org
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom


---

