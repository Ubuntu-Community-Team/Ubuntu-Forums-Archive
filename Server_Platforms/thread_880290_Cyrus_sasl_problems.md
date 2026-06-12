---
title: "Cyrus sasl problems"
date: 2008-08-04
forum: Server Platforms
---

### Post by scrooge on 2008-08-04
Hi
I'm running a Postfix mail server on Ubuntu 7.10 using Cyrus as an imap server. I would like to authenticate user logins from a database so I've got a MySQL DB with one table for that with two columns, userid and password. Now, storing the passwords in plain text is not something I like to do so I would like to use the MD5 sums of them.
My /etc/imapd.conf file is as follows (without comments):
```
configdirectory: /var/lib/cyrus
defaultpartition: default
partition-default: /var/spool/cyrus/mail
partition-news: /var/spool/cyrus/news
newsspool: /var/spool/news
altnamespace: no
unixhierarchysep: no
lmtp_downcase_rcpt: yes
admins: cyrus
allowanonymouslogin: no
popminpoll: 1
autocreatequota: 0
umask: 077
sieveusehomedir: false
sievedir: /var/spool/sieve
hashimapspool: true
allowplaintext: yes
sasl_minimum_layer: 0
tls_ca_path: /etc/ssl/certs
tls_session_timeout: 1440
tls_cipher_list: TLSv1+HIGH:!aNULL:@STRENGTH
lmtpsocket: /var/run/cyrus/socket/lmtp
idlemethod: poll
idlesocket: /var/run/cyrus/socket/idle
notifysocket: /var/run/cyrus/socket/notify
syslog_prefix: cyrus

sasl_pwcheck_method: auxprop
sasl_mech_list: CRAM-MD5
sasl_auxprop_plugin: sql
sasl_sql_engine: mysql
sasl_sql_hostnames: localhost
sasl_sql_user: mysql_user
sasl_sql_passwd: ****
sasl_sql_database: mail
sasl_sql_verbose: yes
sasl_sql_select: SELECT password FROM accounts WHERE userid = '%u'
```

From what I've read the CRAM-MD5 setting should work for sasl_mech_list, but it doesn't :( When I try to log in from Thunderbird I can't succeed unless I type in the MD5 sum of the password, so I'm really just logging in in plaintext.

If anyone has a clue what I might be doing wrong I would be very glad to hear what it is, all help is really appreciated, and if anything is unclear I'd be glad to offer some more detail.

---

