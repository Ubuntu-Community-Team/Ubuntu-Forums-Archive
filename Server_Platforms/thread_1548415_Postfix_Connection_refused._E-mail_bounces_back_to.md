---
title: "Postfix: Connection refused. E-mail bounces back to sender."
date: 2010-08-08
forum: Server Platforms
---

### Post by Fidelix on 2010-08-08
I'm testing my mail server, and sending email works fine.

However, when i tried to send emails to my server from gmail, i get this log:

```
Aug  8 14:18:17 anbient postfix/smtpd[14228]: warning: database /etc/postfix/virtual.db is older than source file /etc/postfix/virtual
Aug  8 14:18:17 anbient postfix/smtpd[14228]: connect from mail-qy0-f169.google.com[209.85.216.169]
Aug  8 14:18:17 anbient postfix/smtpd[14228]: F3D4B1DD02C0: client=mail-qy0-f169.google.com[209.85.216.169]
Aug  8 14:18:18 anbient postfix/cleanup[9988]: F3D4B1DD02C0: message-id=<4C5EBC96.2030800@gmail.com>
Aug  8 14:18:18 anbient postfix/qmgr[9993]: F3D4B1DD02C0: from=<felipefidelix@gmail.com>, size=1982, nrcpt=1 (queue active)
Aug  8 14:18:18 anbient postfix/smtp[9995]: connect to net[174.132.240.146]:25: Connection refused
Aug  8 14:18:18 anbient postfix/smtp[9995]: F3D4B1DD02C0: to=<fidelix@net>, orig_to=<eu@felipefidelix.com>, relay=none, delay=0.15, delays=0.09/0/0.05/0, dsn=4.4.1, status=deferred (connect to net[174.132.240.146]:25: Connection refused)
```


And this is strange. 174.132.240.146 seems to be the web address 'net.net'.

I am sure this has to be some setting in postfix, cuz its trying to deliver the email to 'fidelix@net', and that cant be right.

I appreciate any help at all.

Here is my postconf -n output:

```
root@anbient:/var/mail# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
html_directory = /usr/share/doc/postfix/html
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
mydestination = localhost, 127.0.0.1
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = $mydomain
readme_directory = /usr/share/doc/postfix
recipient_delimiter = +
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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_received_header = yes
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
virtual_alias_maps = hash:/etc/postfix/virtual
virtual_mailbox_base = /var/mail/vhosts
virtual_mailbox_domains = anbient.net, felipefidelix.com
virtual_mailbox_maps = hash:/etc/postfix/vmailbox
virtual_minimum_uid = 100
virtual_uid_maps = static:5000
```

```
root@anbient:/var/mail# cat /etc/aliases
# See man 5 aliases for format
postmaster:    root
```

```
root@anbient:/var/mail# cat /etc/postfix/vmailbox
eu@felipefidelix.com felipefidelix.com/eu
@felipefidelix.com felipefidelix.com/eu
```

```
root@anbient:/var/mail# cat /etc/postfix/virtual
# Anbient CATCH-ALL
anbient.net     root
# Postmaster
postmaster@anbient.net  postmaster
# Postmaster FF
postmaster@felipefidelix.com    postmaster
```

```

root@anbient:/var/mail# cat /var/mail/vhosts 
root@anbient:/var/mail#

```

---

### Post by Bachstelze on 2010-08-08
```
# Anbient CATCH-ALL
anbient.net     root

```

Should be

```
# Anbient CATCH-ALL
@anbient.net     root

```

---

### Post by Fidelix on 2010-08-08
Fixed that. But problem still remains.

I restarted dovecot / postfix and retried:

```

Aug  8 16:45:30 anbient dovecot: dovecot: Killed with signal 15 (by pid=15558 uid=0 code=kill)
Aug  8 16:45:31 anbient dovecot: Dovecot v1.2.9 starting up (core dumps disabled)
Aug  8 16:46:12 anbient postfix/smtpd[21571]: connect from mail-qy0-f176.google.com[209.85.216.176]
Aug  8 16:46:13 anbient postfix/smtpd[21571]: 2FEDE1DD0327: client=mail-qy0-f176.google.com[209.85.216.176]
Aug  8 16:46:13 anbient postfix/cleanup[21619]: 2FEDE1DD0327: message-id=<4C5EDF3E.6050008@gmail.com>
Aug  8 16:46:13 anbient postfix/qmgr[13962]: 2FEDE1DD0327: from=<felipefidelix@gmail.com>, size=1986, nrcpt=1 (queue active)
Aug  8 16:46:13 anbient postfix/error[21620]: 2FEDE1DD0327: to=<fidelix@net>, orig_to=<eu@felipefidelix.com>, relay=none, delay=0.16, delays=0.15/0/0/0, dsn=4.4.1, status=deferred (delivery temporarily suspended: connect to net[174.132.240.146]:25: Connection refused)

```

Email is still bouncing back.

---

### Post by Bachstelze on 2010-08-08
```
to=<fidelix@net>
```

Why are you trying to send mail to fidelix@net? Actually, you say you try to "send mail to your server". What are you doing, exactly? You don't send mail to a machine, you send mail to a user.

---

### Post by Fidelix on 2010-08-08
Thats right.

I'm on my gmail account, and i'm trying to send an email to [email]eu@felipefidelix.com[/email], which is my e-mail on the postfix/dovecot.

The email bounces back immediately after gmail sends it.

It seems my postfix server is trying to deliver the e-mail at fidelix@net, for some reason. And thats what i want to fix, but dont know how.

---

### Post by karesmakro on 2010-08-08
```
warning: database /etc/postfix/virtual.db is older than source file
```
you have to postmap, if you use hash files in your main.cf!

```
sudo postmap /etc/postfix/virtual
``` 
and reload service

also some logfiles would be nice

regards

---

### Post by Fidelix on 2010-08-08
Did it karesmakro. Still bouncing.
What you said seems to be the right way.

Its now clear that i have a bad config, look at the new logs:

mail.log
```

Aug  8 18:57:45 anbient postfix/qmgr[5332]: 272A1CCA008B: from=<www-data@lingonberry.canonical.com>, size=1993, nrcpt=1 (queue active)
Aug  8 18:57:45 anbient postfix/smtp[29848]: connect to net[174.132.240.146]:25: Connection refused
Aug  8 18:57:45 anbient postfix/smtp[29848]: 272A1CCA008B: to=<fidelix@net>, orig_to=<eu@felipefidelix.com>, relay=none, delay=1375, delays=1375/0.01/0.06/0, dsn=4.4.1, status=deferred (connect to net[174.132.240.146]:25: Connection refused)
Aug  8 18:57:46 anbient dovecot: imap-login: Login: user=<eu>, method=PLAIN, rip=187.112.218.249, lip=184.82.3.65, TLS
Aug  8 18:57:48 anbient postfix/smtpd[29874]: connect from mail-qw0-f41.google.com[209.85.216.41]
Aug  8 18:57:48 anbient postfix/smtpd[29874]: C8D0C1DD0335: client=mail-qw0-f41.google.com[209.85.216.41]
Aug  8 18:57:48 anbient postfix/cleanup[29880]: C8D0C1DD0335: message-id=<4C5EFE19.7020904@gmail.com>
Aug  8 18:57:48 anbient postfix/qmgr[5332]: C8D0C1DD0335: from=<felipefidelix@gmail.com>, size=3635, nrcpt=1 (queue active)
Aug  8 18:57:48 anbient postfix/virtual[29882]: warning: recipient eu@felipefidelix.com: not found in virtual_gid_maps
Aug  8 18:57:48 anbient postfix/virtual[29882]: C8D0C1DD0335: to=<eu@felipefidelix.com>, relay=virtual, delay=0.11, delays=0.1/0/0/0.01, dsn=4.3.5, status=deferred (mail system configuration error)

```

mail.warn
```

Aug  8 18:52:45 anbient postfix/virtual[5337]: warning: recipient eu@felipefidelix.com: not found in virtual_gid_maps
Aug  8 18:57:48 anbient postfix/virtual[29882]: warning: recipient eu@felipefidelix.com: not found in virtual_gid_maps

```

Any tips on how should i proceed for solving this?

---

### Post by karesmakro on 2010-08-08
Where do you have declared the virtual_gid_maps in your main.cf?

[http://www.akadia.com/services/postfix_separate_mailboxes.html]("http://www.akadia.com/services/postfix_separate_mailboxes.html")
[http://www.postfix.org/postconf.5.html#virtual_gid_maps]("http://www.postfix.org/postconf.5.html#virtual_gid_maps")

How is working your authentication part, because I saw in a logpart from you, that you are using short names ```
dovecot: imap-login: Login: user=<eu>, method=PLAIN,
```
This is no good idea for an internet server!
Perhaps this is your issue, you should use complete mail address.

Hope this helps

---

### Post by Fidelix on 2010-08-08
OK, i fixed virtual_gid_maps. Set both UID and GID to postfix.

Now i have this, which looks an unrelated problem:
```

Aug  8 22:09:19 anbient postfix/anvil[18391]: statistics: max connection rate 2/60s for (smtp:209.85.216.41) at Aug  8 22:05:50
Aug  8 22:09:19 anbient postfix/anvil[18391]: statistics: max connection count 1 for (smtp:209.85.216.169) at Aug  8 21:59:19
Aug  8 22:09:19 anbient postfix/anvil[18391]: statistics: max cache size 2 at Aug  8 22:00:13
Aug  8 22:09:57 anbient postfix/smtpd[15940]: connect from mail-qy0-f176.google.com[209.85.216.176]
Aug  8 22:09:58 anbient postfix/smtpd[15940]: 1DDEE1DD01CC: client=mail-qy0-f176.google.com[209.85.216.176]
Aug  8 22:09:58 anbient postfix/cleanup[15958]: 1DDEE1DD01CC: message-id=<4C5F2B22.80902@gmail.com>
Aug  8 22:09:58 anbient postfix/qmgr[16053]: 1DDEE1DD01CC: from=<felipefidelix@gmail.com>, size=1981, nrcpt=1 (queue active)
Aug  8 22:09:58 anbient postfix/virtual[11496]: 1DDEE1DD01CC: to=<eu@felipefidelix.com>, relay=virtual, delay=0.39, delays=0.39/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Aug  8 22:09:58 anbient postfix/qmgr[16053]: 1DDEE1DD01CC: removed

```

The emails are still bouncing for some reason.

Plus...
How do i change postfix not to use short names?

---

### Post by Fidelix on 2010-08-09
OK. I fixed all that.
Purged and reinstalled postfix and dovecot and abandoned virtual accounts.

My emails are coming perfectly, HOWEVER, it stills bounces back to gmail.

Yes. The emails are inbox but still get bounced back.

I'll open a new thread for that.
Thanks for the help.

---

