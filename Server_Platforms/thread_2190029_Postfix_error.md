---
title: "Postfix error"
date: 2013-11-25
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-11-25
Hy.. I try to send email from yahoo to my server but not work. In postfix main.cf i have this:

```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
debug_peer_level = 2
disable_vrfy_command = yes
dovecot_destination_recipient_limit = 1
inet_interfaces = all
mailbox_size_limit = 0
mailbox_transport = dovecot
milter_default_action = accept
milter_protocol = 2
mydestination = mail.andortipo.ro, andortipo, localhost.localdomain, localhost
myhostname = mail.andortipo.ro
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
non_smtpd_milters = inet:localhost:8892, inet:localhost:12345
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_sasl_mechanism_filter = plain
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_delay_reject = yes
smtpd_helo_required = yes
smtpd_milters = inet:localhost:8892, inet:localhost:12345
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_non_fqdn_sender, reject_non_fqdn_recipient, reject_unknown_sender_domain, reject_unauth_pipeling, permit_mynetworks, reject_unauth_destination, permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_path = private/auth
smtpd_sasl_type = dovecot
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unknown_address, permit
smtpd_tls_CAfile = /etc/postfix/cert/mail_andortipo_ro.ca-bundle
smtpd_tls_cert_file = /etc/postfix/cert/mail_andortipo_ro.crt
smtpd_tls_key_file = /etc/postfix/cert/andortipo.key
smtpd_tls_loglevel = 1
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, proxy:mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_uid_maps = static:5000

```

In postmaster mailbox i have this:
```
 Out: 220 mail.andortipo.ro ESMTP Postfix (Ubuntu)
 In:  EHLO nm37.bullet.mail.ne1.yahoo.com
 Out: 250-mail.andortipo.ro
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-AUTH PLAIN LOGIN
 Out: 250-AUTH=PLAIN LOGIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  STARTTLS
 Out: 220 2.0.0 Ready to start TLS
 In:  EHLO nm37.bullet.mail.ne1.yahoo.com
 Out: 250-mail.andortipo.ro
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-ETRN
 Out: 250-AUTH PLAIN LOGIN
 Out: 250-AUTH=PLAIN LOGIN
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  MAIL FROM:<[EMAIL="andortipo@yahoo.com"]andortipo@yahoo.com[/EMAIL]>
 Out: 250 2.1.0 Ok
 In:  RCPT TO:<[EMAIL="comezni@andortipo.ro"]comezni@andortipo.ro[/EMAIL]>
 Out: 451 4.3.5 Server configuration error
 In:  RSET
 Out: 250 2.0.0 Ok
 In:  QUIT
 Out: 221 2.0.0 Bye
```

What is wrong in my postfix config?

---

