---
title: "Postfix-Squirrelmail Local Mail Problems"
date: 2008-08-29
forum: Server Platforms
---

### Post by kooseefoo on 2008-08-29
I have Postfix, Dovecot, and Squirrelmail working on my server. It is a pretty basic setup.

Whenever I log into squirrelmail and try to send an email to "root", the message gets bounced. Postfix logs show that it was addressed to root@foobarcom instead of [email]root@foobar.com[/email]. I'm not sure if this error is happening on the squirrelmail side of things or with postfix. Does anybody have any idea what could be causing this?

Here is an excerpt of the postfix log:

```
Aug 29 17:26:44 macfly postfix/smtpd[12828]: C36CB1FB271: client=localhost[127.0.0.1]
Aug 29 17:26:44 macfly postfix/cleanup[12831]: C36CB1FB271: message-id=<43781.192.168.1.1.1220056004.squirrel@foobar.com>
Aug 29 17:26:44 macfly postfix/qmgr[21035]: C36CB1FB271: from=<address@foobar.com>, size=755, nrcpt=1 (queue active)
Aug 29 17:26:44 macfly postfix/smtpd[12828]: disconnect from localhost[127.0.0.1]
Aug 29 17:26:44 macfly postfix/smtp[12832]: C36CB1FB271: to=<root@foobarcom>, relay=none, delay=0.16, delays=0.06/0.05/0.05/0, dsn=5.4.4, status=bounced (Host or domain name not found. Name service error for name=foobarcom type=AAAA: Host not found)
Aug 29 17:26:44 macfly postfix/cleanup[12831]: EFC421FB640: message-id=<20080830002644.EFC421FB640@foobar.com>
Aug 29 17:26:45 macfly postfix/qmgr[21035]: EFC421FB640: from=<>, size=2697, nrcpt=1 (queue active)
Aug 29 17:26:45 macfly postfix/bounce[12835]: C36CB1FB271: sender non-delivery notification: EFC421FB640

```

Does anybody know how to go about diagnosing this? Postfix is a pretty serious enigma to me.

---

