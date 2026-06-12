---
title: "Postfix 553 Error"
date: 2010-04-13
forum: Server Platforms
---

### Post by Norami on 2010-04-13
Ok. I've been having issues left and right with this mail server situation, and I've figured most of them out. This particular issue, however, has been lingering for months. It's not a huge hindrance, but at the same time it takes away a little bit of convenience for my clients.

Specs:
Ubuntu 9.10 Server
Postfix/Dovecot
UNIX Users (as opposed to virtual users)
Postfix is using Dovecot SASL

The server works perfectly all the way up to one point. I can receive e-mails just fine, and same with sending, as long as it's directly from the server. I have roundcube setup on it for webmail, and my clients are happy with it, but they want the ability to use their mail programs (outlook, evolution, thunderbird, etc.). Here's my problem! Anyone know how the heck I'm supposed to fix this? I've been searching for days.... This isn't the first post about my mail server, either. I seem to attract quite a few issues.

```
Apr 13 09:23:10 mail postfix/smtpd[13901]: NOQUEUE: reject: RCPT from unknown[216.203.6.11]: 553 5.7.1 <adam@weebot.net>: Sender address rejected: not owned by user adam; from=<adam@weebot.net> to=<adam@adamwgay.com> proto=ESMTP helo=<[172.16.146.118]>
```

postconf -n:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
inet_interfaces = all
mailbox_size_limit = 0
mydestination = weebot.net, mail.weebot.net, localhost.weebot.net, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = reject_sender_login_mismatch permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = weebot.net
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous, noplaintext
smtpd_sasl_tls_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

---

### Post by KB1JWQ on 2010-04-13
It's caused by the presence of reject_sender_login_mismatch before your permit statements.

---

### Post by Norami on 2010-04-13
Wow. Something so simple! Thank you so much! Works like a charm now.

---

### Post by KB1JWQ on 2010-04-13
Glad it worked!

Thanks for providing the postconf -n and log message up front in your initial post; makes it a LOT easier to troubleshoot that way!

---

