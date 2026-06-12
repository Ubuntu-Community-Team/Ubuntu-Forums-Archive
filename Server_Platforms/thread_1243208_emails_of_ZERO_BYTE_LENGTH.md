---
title: "emails of ZERO BYTE LENGTH"
date: 2009-08-18
forum: Server Platforms
---

### Post by uyuy on 2009-08-18
I am user of Ubuntu Server 9.04 (kernel uname -a 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 x86_64 GNU/Linux) as an email server.

It works great with SMTP & IMAP and I love it. :P:guitar:

Recently, there has been annoyance that too many ZERO BYTE LENGTH mails showed up in INBOXes. :(

Checking the /var/log/mail.log I suspect that SPAMMERS  are using some Email address Scanning Robots to scan for valid mail addresses, their bots engaged the SMTP as if they were here to send emails, and they tried all sorts of mail addresses, if the SMTPD responded OK with the address tried by the scan-bots they just disconnect away and note that scanned address as Valid, and they will use them for future SPAM. :(

Some how, Ubuntu server 9.04's postfix and procmail still did not throw away these ZERO BYTE LENGTH mails, and sent it to users' INBOXes. I checked the MAILDIR and the size of these mail files are indeed zero byte lengths.:KS The mail logs also showed that these IPs are from SPAM-like origins and very unlikely to be geneuine senders to this server. They disconnected away and never re-send anything afterwards.

I hope to get a solution from high skill mail server users here, that e.g. a simple procmailrc receipe to discard these annoying ZERO BYTE LENGTH messages that don't even have a Header.

Thanks

---

### Post by uyuy on 2009-08-18
I have discovered in /var/mail.log that these mail are associated with :

```
 Aug 18 12:12:03 myServer postfix/local[16144]: B688434277A:
 to=<sales@myServer.com>, relay=local, delay=0.62,delays=0.57/0.02/0/0.03,
 dsn=5.2.0, status=bounced (can't create user output file) 
```I am now puzzled how these postfix/local errors had arise, unless OS can at only those times lock the file system? :confused:

Had any person ever encountered these?

Thanks

---

