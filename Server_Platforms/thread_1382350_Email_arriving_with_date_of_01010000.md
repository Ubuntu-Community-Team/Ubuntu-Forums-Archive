---
title: "Email arriving with date of 01/01/0000"
date: 2010-01-15
forum: Server Platforms
---

### Post by mrgordonz on 2010-01-15
Hi All,

This may not be the correct forum to post this in - if there is a better (or more appropriate) forum, please let me know.  The reason I have posted on this forum is that the server I am running is Ubuntu 8.04 LTS.

On the server I have a PHP help desk application which sends me emails when a customer submits or updates a case/request.  I use Postfix as my MTA.  When I receive the email in my Outlook Inbox, the date and time of the email are correct.  But when the same email arrives on my mobile phone (Nokia E71), the date and time is 01/01/0000 00:00.  Emails generally arrive on my PC and on my phone at about the same time.  I have checked the Postfix log and I can't see anything there which would indicate an issue.  Below are the log entries for the two most recent emails:

```
Jan 15 16:17:04 hgsupport postfix/smtpd[12030]: connect from localhost[127.0.0.1]
Jan 15 16:17:04 hgsupport postfix/smtpd[12030]: 3CCAC2EA3EF: client=localhost[127.0.0.1]
Jan 15 16:17:04 hgsupport postfix/cleanup[12033]: 3CCAC2EA3EF: message-id=<a006b8ecb8d56618bcee218a4756c207@support.mydomain.com>
Jan 15 16:17:04 hgsupport postfix/qmgr[16319]: 3CCAC2EA3EF: from=<support@mydomain.com>, size=3188, nrcpt=1 (queue active)
Jan 15 16:17:04 hgsupport postfix/smtpd[12030]: disconnect from localhost[127.0.0.1]
Jan 15 16:17:06 hgsupport postfix/smtp[12034]: 3CCAC2EA3EF: to=<my.name@mydomain.com>, relay=aspmx.l.google.com[209.85.216.80]:25, delay=2.2, delays=0$
Jan 15 16:17:06 hgsupport postfix/qmgr[16319]: 3CCAC2EA3EF: removed
Jan 15 16:18:34 hgsupport postfix/smtpd[12030]: connect from localhost[127.0.0.1]
Jan 15 16:18:34 hgsupport postfix/smtpd[12030]: 6C0322EA3EF: client=localhost[127.0.0.1]
Jan 15 16:18:34 hgsupport postfix/cleanup[12033]: 6C0322EA3EF: message-id=<e60eb191f12e8c3931160096c40dbf07@support.mydomain.com>
Jan 15 16:18:34 hgsupport postfix/qmgr[16319]: 6C0322EA3EF: from=<support@mydomain.com>, size=3096, nrcpt=1 (queue active)
Jan 15 16:18:34 hgsupport postfix/smtpd[12030]: disconnect from localhost[127.0.0.1]
Jan 15 16:18:36 hgsupport postfix/smtp[12034]: 6C0322EA3EF: to=<my.name@mydomain.com>, relay=aspmx.l.google.com[209.85.216.80]:25, delay=2, delays=0.0$
Jan 15 16:18:36 hgsupport postfix/qmgr[16319]: 6C0322EA3EF: removed

```

When I execute the "date" command on the server, it returns the correct date and time:

```
Sat Jan 16 11:59:46 EST 2010
```

I don't know what is causing the problem, but I believe it is most likely an issue with either Postfix or Linux (probably I have got some config wrong).  My reasons for reaching this conclusion are as follows:

1.  On my mobile phone the only emails which suffer from this issue are ones from this server - all other emails on my phone are correct.
2.  Until recently the PHP application was hosted at Host Gator, and emails arriving on my mobile phone had the correct date and time.  I recently migrated the application from Host Gator to my own server - that was when the problem started.

Can anyone suggest what might be causing the problem, and/or how I can solve it?

Cheers,

Paul

---

