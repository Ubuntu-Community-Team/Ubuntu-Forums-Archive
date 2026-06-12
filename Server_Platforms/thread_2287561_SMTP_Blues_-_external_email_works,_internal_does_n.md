---
title: "SMTP Blues - external email works, internal does not"
date: 2015-07-20
forum: Server Platforms
---

### Post by darius7 on 2015-07-20
Hi all,


I desperately need some help with Postfix. I have 3 domains hosted on a remote server, but I am using this postfix server for SMTP only.


External email appears to be good, but internal e-mail is not working (e.g. [EMAIL="user@domain1.com"]user@domain1.com[/EMAIL] to [EMAIL="user@domain2.com"]user@domain2.com[/EMAIL]). I have an excerpt of my logs and my main.cnf. ANY help or advice would be greatly appreciated.


IP/domains redacted for obvious reasons, but can be provided if necessary...


mail.domain1.com - remote mail server, storing mailboxes. used for imap smtp.domain1.com - local postfix server, used only for smtp

Working example of external email:
```
Jul 20 17:16:35 smtp postfix/smtpd[12808]: warning: hostname mail.domain1.com does not resolve to address REMOTE IP (NO IDEA why this appears, yet the email sends fine)
Jul 20 17:16:35 smtp postfix/smtpd[12808]: connect from unknown[REMOTE IP]
Jul 20 17:16:35 smtp postfix/smtpd[12808]: A42EDD4323: client=unknown[REMOTE IP]
Jul 20 17:16:35 smtp postfix/cleanup[12811]: A42EDD4323: message-id=<55AD2CEC.5090601@domain1.com>
Jul 20 17:16:35 smtp postfix/qmgr[12792]: A42EDD4323: from=<user@domain1.com>, size=579, nrcpt=1 (queue active)
Jul 20 17:16:35 smtp postfix/smtpd[12808]: disconnect from unknown[REMOTE IP]
Jul 20 17:16:36 smtp postfix/smtp[12812]: A42EDD4323: to=<user@yahoo.com>, relay=mta7.am0.yahoodns.net[63.250.192.46]:25, delay=1.2, delays=0.04/0/0.21/0.98, dsn=2.0.0, status=sent (250 ok dirdel)
Jul 20 17:16:36 smtp postfix/qmgr[12792]: A42EDD4323: removed

```

What doesn't work, internal email:
```
Jul 20 17:15:32 smtp postfix/master[12787]: daemon started -- version 2.9.6, configuration /etc/postfix
Jul 20 17:15:55 smtp postfix/smtpd[12808]: connect from mail.domain1.com[REMOTE IP]
Jul 20 17:15:55 smtp postfix/smtpd[12808]: A61FAD4323: client=mail.domain1.com[REMOTE IP]
Jul 20 17:15:55 smtp postfix/cleanup[12811]: A61FAD4323: message-id=<d21879c0d64402672666e684b991551d@domain3.com>
Jul 20 17:15:55 smtp postfix/qmgr[12792]: A61FAD4323: from=<user@domain2.com>, size=1232, nrcpt=1 (queue active)
Jul 20 17:15:55 smtp postfix/smtpd[12808]: disconnect from mail.domain1.com[REMOTE IP]
Jul 20 17:15:55 smtp postfix/smtp[12812]: A61FAD4323: to=<user@domain1.com>, relay=mail.domain1.com[REMOTE IP]:25, delay=0.08, delays=0.05/0/0.01/0.02, dsn=5.0.0, status=bounced (host mail.provocativ.com[173.203.181.124] said: 530 SMTP authentication is required. (in reply to RCPT TO command))
Jul 20 17:15:55 smtp postfix/cleanup[12811]: B8757D4327: message-id=<20150720171555.B8757D4327@smtp.domain1.com>
Jul 20 17:15:55 smtp postfix/qmgr[12792]: B8757D4327: from=<>, size=3274, nrcpt=1 (queue active)
Jul 20 17:15:55 smtp postfix/bounce[12813]: A61FAD4323: sender non-delivery notification: B8757D4327
Jul 20 17:15:55 smtp postfix/qmgr[12792]: A61FAD4323: removed
Jul 20 17:15:55 smtp postfix/local[12814]: B8757D4327: to=<user@domain2.com>, relay=local, delay=0.01, delays=0/0/0/0, dsn=5.1.1, status=bounced (unknown user: "ez-proposal")
Jul 20 17:15:55 smtp postfix/qmgr[12792]: B8757D4327: removed

```

My main.cf
```

myhostname = smtp.domain1.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = smtp.domain1.com, localhost.domain1.com, domain2.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [REMOTE IP]/32 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtp_host_lookup = native

```

Again, any advice would be greatly appreciated...

---

