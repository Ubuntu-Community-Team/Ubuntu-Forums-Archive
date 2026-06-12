---
title: "Spambot Email Server"
date: 2009-02-26
forum: Server Platforms
---

### Post by kooseefoo on 2009-02-26
Hey all,


My server seems to have been broken into somehow. A review of the mail.log file shows a bunch of strange email that it's trying to send. I'm not sure how to go about finding the source of these emails. As far as I could tell, my configuration doesn't allow it to be an open relay.

So, basically, I'm confused. For starters, I'm going to post the mail.log file and my postfix configuration.

The email seems to be linked to the user www-data: the only thing that's running on my web server is drupal 6.9.

Thanks for any help!

mail.log:
```
Feb 22 07:14:34 macfly postfix/qmgr[5036]: AC98C1FB655: removed
Feb 22 07:14:34 macfly postfix/local[21039]: 3D2B91FB656: to=<www-data@kooseefoo.com>, relay=local, delay=0.1, delays=0.05/0.03/0/0.03, dsn=2.0.0, status=sen
Feb 22 07:14:34 macfly postfix/qmgr[5036]: 3D2B91FB656: removed
Feb 22 08:02:03 macfly postfix/smtpd[23573]: connect from 114-45-59-20.dynamic.hinet.net[114.45.59.20]
Feb 22 08:02:04 macfly postfix/smtpd[23573]: NOQUEUE: reject: RCPT from 114-45-59-20.dynamic.hinet.net[114.45.59.20]: 554 5.7.1 <vjei3b9x@yahoo.com.tw>: Rela
Feb 22 08:02:04 macfly postfix/smtpd[23573]: lost connection after RCPT from 114-45-59-20.dynamic.hinet.net[114.45.59.20]
Feb 22 08:02:04 macfly postfix/smtpd[23573]: disconnect from 114-45-59-20.dynamic.hinet.net[114.45.59.20]
Feb 22 08:05:24 macfly postfix/anvil[23575]: statistics: max connection rate 1/60s for (smtp:114.45.59.20) at Feb 22 08:02:03
Feb 22 08:05:24 macfly postfix/anvil[23575]: statistics: max connection count 1 for (smtp:114.45.59.20) at Feb 22 08:02:03
Feb 22 08:05:24 macfly postfix/anvil[23575]: statistics: max cache size 1 at Feb 22 08:02:03
Feb 22 08:14:06 macfly postfix/qmgr[5036]: E77201FB641: from=<www-data@kooseefoo.com>, size=1097, nrcpt=1 (queue active)
Feb 22 08:14:28 macfly postfix/smtp[23591]: connect to mailin-03.mx.aol.com[64.12.138.153]:25: Connection refused
Feb 22 08:14:28 macfly postfix/smtp[23591]: E77201FB641: host mailin-02.mx.aol.com[64.12.138.120] refused to talk to me: 554- (RTR:DU)  http://postmaster.inf
Feb 22 08:14:28 macfly postfix/smtp[23591]: E77201FB641: host mailin-04.mx.aol.com[64.12.138.57] refused to talk to me: 554- (RTR:DU)  http://postmaster.info
Feb 22 08:14:29 macfly postfix/smtp[23591]: E77201FB641: host mailin-02.mx.aol.com[205.188.249.91] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 08:14:29 macfly postfix/smtp[23591]: E77201FB641: to=<Gunnerdude4@aol.com>, relay=mailin-04.mx.aol.com[205.188.159.216]:25, delay=126568, delays=12654
Feb 22 08:24:06 macfly postfix/qmgr[5036]: BDBA71FB642: from=<www-data@kooseefoo.com>, size=1152, nrcpt=1 (queue active)
Feb 22 08:24:07 macfly postfix/smtp[23605]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.52] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 08:24:07 macfly postfix/smtp[23605]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.50] refused to talk to me: 554 bosimpinc02.eigbox.net
Feb 22 08:24:07 macfly postfix/smtp[23605]: BDBA71FB642: to=<nvrnopnl@onlineovernightpharmacy.com>, relay=mx.onlineovernightpharmacy.com[66.96.140.51]:25, de
Feb 22 09:24:06 macfly postfix/qmgr[5036]: E77201FB641: from=<www-data@kooseefoo.com>, size=1097, nrcpt=1 (queue active)
Feb 22 09:24:08 macfly postfix/smtp[23772]: E77201FB641: host mailin-04.mx.aol.com[205.188.159.216] refused to talk to me: 554- (RTR:DU)  http://postmaster.i
Feb 22 09:24:08 macfly postfix/smtp[23772]: E77201FB641: host mailin-04.mx.aol.com[64.12.138.88] refused to talk to me: 554- (RTR:DU)  http://postmaster.info
Feb 22 09:24:08 macfly postfix/smtp[23772]: E77201FB641: host mailin-01.mx.aol.com[205.188.159.57] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 09:24:08 macfly postfix/smtp[23772]: E77201FB641: host mailin-03.mx.aol.com[205.188.109.56] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 09:24:09 macfly postfix/smtp[23772]: E77201FB641: to=<Gunnerdude4@aol.com>, relay=mailin-01.mx.aol.com[205.188.156.248]:25, delay=130747, delays=13074
Feb 22 09:34:06 macfly postfix/qmgr[5036]: BDBA71FB642: from=<www-data@kooseefoo.com>, size=1152, nrcpt=1 (queue active)
Feb 22 09:34:07 macfly postfix/smtp[23777]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.52] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 09:34:07 macfly postfix/smtp[23777]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.50] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 09:34:07 macfly postfix/smtp[23777]: BDBA71FB642: to=<nvrnopnl@onlineovernightpharmacy.com>, relay=mx.onlineovernightpharmacy.com[66.96.140.51]:25, de
Feb 22 10:34:06 macfly postfix/qmgr[5036]: E77201FB641: from=<www-data@kooseefoo.com>, size=1097, nrcpt=1 (queue active)
Feb 22 10:34:07 macfly postfix/smtp[24256]: E77201FB641: host mailin-04.mx.aol.com[205.188.159.216] refused to talk to me: 554- (RTR:DU)  http://postmaster.i
Feb 22 10:34:08 macfly postfix/smtp[24256]: E77201FB641: host mailin-02.mx.aol.com[64.12.137.89] refused to talk to me: 554- (RTR:DU)  http://postmaster.info
Feb 22 10:34:08 macfly postfix/smtp[24256]: E77201FB641: host mailin-02.mx.aol.com[205.188.249.91] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 10:34:09 macfly postfix/smtp[24256]: E77201FB641: host mailin-04.mx.aol.com[64.12.138.57] refused to talk to me: 554- (RTR:DU)  http://postmaster.info
Feb 22 10:34:09 macfly postfix/smtp[24256]: E77201FB641: to=<Gunnerdude4@aol.com>, relay=mailin-02.mx.aol.com[64.12.138.120]:25, delay=134947, delays=134945/
Feb 22 10:44:06 macfly postfix/qmgr[5036]: BDBA71FB642: from=<www-data@kooseefoo.com>, size=1152, nrcpt=1 (queue active)
Feb 22 10:44:07 macfly postfix/smtp[24272]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.52] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 10:44:07 macfly postfix/smtp[24272]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.51] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 10:44:07 macfly postfix/smtp[24272]: BDBA71FB642: to=<nvrnopnl@onlineovernightpharmacy.com>, relay=mx.onlineovernightpharmacy.com[66.96.140.50]:25, de
Feb 22 11:44:06 macfly postfix/qmgr[5036]: E77201FB641: from=<www-data@kooseefoo.com>, size=1097, nrcpt=1 (queue active)
Feb 22 11:44:37 macfly postfix/smtp[24430]: connect to mailin-03.mx.aol.com[64.12.138.153]:25: Connection timed out
Feb 22 11:44:37 macfly postfix/smtp[24430]: E77201FB641: host mailin-02.mx.aol.com[205.188.249.91] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 11:44:38 macfly postfix/smtp[24430]: E77201FB641: host mailin-01.mx.aol.com[205.188.159.57] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 11:44:38 macfly postfix/smtp[24430]: E77201FB641: host mailin-02.mx.aol.com[205.188.155.72] refused to talk to me: 554- (RTR:DU)  http://postmaster.in
Feb 22 11:44:38 macfly postfix/smtp[24430]: E77201FB641: to=<Gunnerdude4@aol.com>, relay=mailin-01.mx.aol.com[64.12.139.249]:25, delay=139177, delays=139145/
Feb 22 11:54:06 macfly postfix/qmgr[5036]: BDBA71FB642: from=<www-data@kooseefoo.com>, size=1152, nrcpt=1 (queue active)
Feb 22 11:54:07 macfly postfix/smtp[24435]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.52] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 11:54:07 macfly postfix/smtp[24435]: BDBA71FB642: host mx.onlineovernightpharmacy.com[66.96.140.51] refused to talk to me: 554 bosimpinc01.eigbox.net
Feb 22 11:54:08 macfly postfix/smtp[24435]: BDBA71FB642: to=<nvrnopnl@onlineovernightpharmacy.com>, relay=mx.onlineovernightpharmacy.com[66.96.140.50]:25, de
Feb 22 12:54:06 macfly postfix/qmgr[5036]: E77201FB641: from=<www-data@kooseefoo.com>, size=1097, nrcpt=1 (queue active)

```


main.cf:
```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = kooseefoo.com

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = kooseefoo.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = kooseefoo.com, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

#smtpd_enforce_tls = yes
smtpd_tls_auth_only = no

smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/

```

---

### Post by kooseefoo on 2009-02-26
Problem solved. I'm an idiot.


A spambot was trying to create user names on my drupal setup. Those were user confirmation emails attempting to be sent out.


Thanks anyways. Hah.

---

