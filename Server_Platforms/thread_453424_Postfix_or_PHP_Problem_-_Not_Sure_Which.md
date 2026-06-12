---
title: "Postfix or PHP Problem - Not Sure Which"
date: 2007-05-24
forum: Server Platforms
---

### Post by nomb on 2007-05-24
Hey guys I have a quick question for you about postfix (I think).  I can send mail from my server the folling way:

telnet localhost 25
helo nomb
MAIL FROM: [email]nomb@xxxxxx.com[/email]
RCPT TO: [email]nomb85@xxxxxx.net[/email]
DATA
This is a test...
.
quit

The above sends fine w/o any problems.  However when I try to send a mail in php, I get somehting like:

```

May 23 15:16:49 localhost postfix/pickup[12021]: B1C8243C15: uid=33 from=<www-data>
May 23 15:16:49 localhost postfix/cleanup[12028]: B1C8243C15: message-id=<20070523191649.B1C8243C15@localhost>
May 23 15:16:49 localhost postfix/qmgr[12022]: B1C8243C15: from=<www-data@localhost>, size=305, nrcpt=1 (queue active)
May 23 15:16:50 localhost postfix/smtp[12030]: B1C8243C15: to=<nomb@xxxxxxxxx.com>, relay=smtp.secureserver.net[64.202.166.12]:25, delay=0.68, delays=0.06/0.0$
May 23 15:16:50 localhost postfix/cleanup[12028]: 6F4F943C18: message-id=<20070523191650.6F4F943C18@localhost>
May 23 15:16:50 localhost postfix/qmgr[12022]: 6F4F943C18: from=<>, size=2100, nrcpt=1 (queue active)
May 23 15:16:50 localhost postfix/bounce[12031]: B1C8243C15: sender non-delivery notification: 6F4F943C18
May 23 15:16:50 localhost postfix/qmgr[12022]: B1C8243C15: removed
May 23 15:16:50 localhost postfix/local[12032]: 6F4F943C18: to=<www-data@localhost>, relay=local, delay=0.06, delays=0.02/0.02/0/0.03, dsn=2.0.0, status=sen$
May 23 15:16:50 localhost postfix/qmgr[12022]: 6F4F943C18: removed

```

Whenever it has the 'www-data@localhost' it never really gets anywhere.  I don't know where this is or what is causing this.  Any advice would be really helpfu.  

PHP is not in safe mode.

Thank You In Advanced

nomb

---

### Post by nomb on 2007-05-24
Does anyone have a suggestion of whether it is a php or an apache problem even?

---

