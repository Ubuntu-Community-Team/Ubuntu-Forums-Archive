---
title: "Postfix 'lost' some message"
date: 2011-06-10
forum: Server Platforms
---

### Post by LeXav on 2011-06-10
Hi !

I'm using postfix in relay mode with my provider's smtp server.
I'm sending nightly some emails by batch (logs, commercial stats ....) and some emails never arrive. It's not always the 'same' emails, this is not everyday, but it's happen and I don't understand why.

Here is the result of postconf -n


```
postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = loopback-only
mailbox_size_limit = 0
mydestination = xav-serveur, localhost.localdomain, localhost
myhostname = xav-serveur
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin =xxx.com
readme_directory = no
recipient_delimiter = +
relayhost = smtp.hosts.co.uk:25
smtp_enforce_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_password_maps = hash:/etc/postfix/sasl/sasl_passwd
smtp_sasl_security_options = noanonymous
smtp_tls_CAfile = /etc/ssl/certs/ca-certificates.crt
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```
Here is the log of a 'lost' email

```
Jun 10 03:30:12 xav-serveur postfix/pickup[23052]: 81A24604ED: uid=1000 from=<xav>
Jun 10 03:30:12 xav-serveur postfix/cleanup[23267]: 81A24604ED: message-id=<20110610013012.81A24604ED@xav-serveur>
Jun 10 03:30:12 xav-serveur postfix/qmgr[1488]: 81A24604ED: from=<xav@xxxx.com>, size=9151000, nrcpt=1 (queue active)
Jun 10 03:32:04 xav-serveur postfix/smtp[23269]: 81A24604ED: to=<geek@xxxx.com>, relay=smtp.hosts.co.uk[85.233.160.19]:25, delay=112, delays=0.55/0.02/0.85/110, dsn=2.0.0, status=sent (250 OK id=1QUqY9-0007jp-M0)
Jun 10 03:32:04 xav-serveur postfix/qmgr[1488]: 81A24604ED: removed
```The email seems to be sent ( " status=sent ") but it was never arrived...

Another mail, 10 minutes later was arrived.

```
Jun 10 03:40:01 xav-serveur postfix/pickup[23052]: A614D604ED: uid=1000 from=<xav>
Jun 10 03:40:01 xav-serveur postfix/cleanup[23314]: A614D604ED: message-id=<20110610014001.A614D604ED@xav-serveur>
Jun 10 03:40:01 xav-serveur postfix/qmgr[1488]: A614D604ED: from=<xav@xxxx.com>, size=150474, nrcpt=1 (queue active)
Jun 10 03:40:04 xav-serveur postfix/smtp[23319]: A614D604ED: to=<geek@xxxx.com>, relay=smtp.hosts.co.uk[85.233.160.19]:25, delay=3, delays=0.11/0/0.84/2.1, dsn=2.0.0, status=sent (250 OK id=1QUqhe-0008Nx-Jf)
Jun 10 03:40:04 xav-serveur postfix/qmgr[1488]: A614D604ED: removed
```
I've found these 3 lignes witch seems to mean that's there is something wrong, but I don't understand what....

```
un 10 09:03:53 xav-serveur postfix/scache[25134]: statistics: start interval Jun 10 09:00:03
Jun 10 09:03:53 xav-serveur postfix/scache[25134]: statistics: domain lookup hits=0 miss=3 success=0%
```Could someone help me ?
Thanks a lot

---

