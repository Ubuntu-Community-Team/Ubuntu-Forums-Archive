---
title: "ERROR: Connection dropped by IMAP server"
date: 2008-02-13
forum: Server Platforms
---

### Post by satimis on 2008-02-13
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8
SquirrelMail version 1.4.11


The Mail Server has been running for sometimes.  Previously whenever a new account is created the Maildir including its subdirectories will be automatically created upon receipt of the 1st mail.


Just created a new account and sent a new mail to it.  But no Maildir was created automatically.  On starting SM and login the new account a warning "ERROR: Connection dropped by IMAP server" popup, unable to login.  Other users login w/o problem.


Please advise where shall I check and how to fix the problem.  TIA


B.R.
satimis

---

### Post by ikonia on 2008-02-13
postfix isn't an Imap server, 

what are you using as an imap server, 

the creation of the maildir is done by postfix - so won't have anything to do with the imap or pop3 service not running.

what does your mail logs say about the mail it recived eg: "could not create maildir - no permissions" or anything like that.

---

### Post by satimis on 2008-02-13
> **ikonia said:**
> postfix isn't an Imap server, 

what are you using as an imap server, 

the creation of the maildir is done by postfix - so won't have anything to do with the imap or pop3 service not running.
Thanks for your advice.


> 
what does your mail logs say about the mail it recived eg: "could not create maildir - no permissions" or anything like that.
$ tail /var/log/mail.log```

Feb 14 10:40:26 mail postfix/anvil[5439]: statistics: max connection count 1 for
 (smtp:220.229.215.159) at Feb 14 10:35:11
Feb 14 10:40:26 mail postfix/anvil[5439]: statistics: max cache size 2 at Feb 14
 10:35:27
Feb 14 10:44:36 mail postfix/smtpd[5463]: connect from cwb.pacific.net.hk[202.14
.67.92]
Feb 14 10:44:37 mail postfix/smtpd[5463]: warning: support for restriction "reje
ct_maps_rbl" will be removed from Postfix; use "reject_rbl_client domain-name" i
nstead
Feb 14 10:44:37 mail postfix/smtpd[5463]: 246D0DF00ED: client=cwb.pacific.net.hk
[202.14.67.92]
Feb 14 10:44:37 mail postfix/cleanup[5467]: 246D0DF00ED: message-id=<20080214023
6.m1E2aF8F005377@cwb.pacific.net.hk>
Feb 14 10:44:37 mail postfix/qmgr[4950]: 246D0DF00ED: from=<satimis@pacific.net.
hk>, size=809, nrcpt=1 (queue active)
Feb 14 10:44:37 mail postfix/smtpd[5463]: disconnect from cwb.pacific.net.hk[202
.14.67.92]
Feb 14 10:44:37 mail postfix/local[5468]: 246D0DF00ED: to=<reynold@satimis.com>,
 relay=local, delay=0.3, delays=0.25/0.01/0/0.04, dsn=2.0.0, status=sent (delive
red to command: procmail -a "$EXTENSION")
Feb 14 10:44:37 mail postfix/qmgr[4950]: 246D0DF00ED: removed

```


Edit-1:

I manually created Maildir, Maildir/cur, Maildir/new and Maildir/tmp.  But still the user (NOT only the new user, including all users) can't receive the mail.


$ tail /var/log/mail.log```

Feb 14 15:39:48 mail imapd: LOGOUT, user=rey, ip=[::ffff:127.0.0.1], headers=0, body=0, rcvd=87, sent=391, time=0
Feb 14 15:39:48 mail imapd: Connection, ip=[::ffff:127.0.0.1]
Feb 14 15:39:48 mail imapd: LOGIN, user=rey, ip=[::ffff:127.0.0.1], protocol=IMAP
Feb 14 15:39:48 mail imapd: LOGOUT, user=rey, ip=[::ffff:127.0.0.1], headers=165, body=0, rcvd=340, sent=1420, time=0
Feb 14 15:40:13 mail imapd: Connection, ip=[::ffff:127.0.0.1]
Feb 14 15:40:13 mail imapd: LOGIN, user=rey, ip=[::ffff:127.0.0.1], protocol=IMAP
Feb 14 15:40:13 mail imapd: LOGOUT, user=rey, ip=[::ffff:127.0.0.1], headers=165, body=0, rcvd=340, sent=1420, time=0
Feb 14 15:40:14 mail imapd: Connection, ip=[::ffff:127.0.0.1]
Feb 14 15:40:14 mail imapd: LOGIN, user=rey, ip=[::ffff:127.0.0.1], protocol=IMAP
Feb 14 15:40:14 mail imapd: LOGOUT, user=rey, ip=[::ffff:127.0.0.1], headers=165, body=0, rcvd=340, sent=1420, time=0

```


$ tail /var/log/mail.err ```

Jan 25 18:58:27 mail postfix/smtp[5806]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 18:59:28 mail postfix/smtp[5807]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:00:29 mail postfix/smtp[5810]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:01:30 mail postfix/smtp[5823]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:02:31 mail postfix/smtp[5824]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:03:32 mail postfix/smtp[5825]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:04:33 mail postfix/smtp[5826]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 19:05:34 mail postfix/smtp[5827]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter
Jan 25 23:35:28 mail postfix[5559]: error: to submit mail, use the Postfix sendmail command
Jan 25 23:35:28 mail postfix[5559]: fatal: the postfix command is reserved for the superuser

```


On commenting out following line on /etc/postfix/main.cf```

#mailbox_command = procmail -a "$EXTENSION"

```


$ sudo /etc/init.d/postfix restart```

 * Stopping Postfix Mail Transport Agent postfix                         [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                         [ OK ] 

```

Then all users can receive mails.


Edit-2

(with the abovementioned line uncommented)

$ postconf | grep smtp_sasl_```

smtp_sasl_auth_enable = no
smtp_sasl_mechanism_filter = 
smtp_sasl_password_maps = 
smtp_sasl_path = 
smtp_sasl_security_options = noplaintext, noanonymous
smtp_sasl_tls_security_options = $smtp_sasl_security_options
smtp_sasl_tls_verified_security_options = $smtp_sasl_tls_security_options
smtp_sasl_type = cyrus

```


$ postconf | grep enforce_tls```

lmtp_enforce_tls = no
smtp_enforce_tls = no
smtpd_enforce_tls = no

```


B.R.
satimis

---

