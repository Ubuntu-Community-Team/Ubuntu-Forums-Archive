---
title: "Problem with maildomain"
date: 2011-03-10
forum: Server Platforms
---

### Post by Kozley on 2011-03-10
I do not understand what happens to the domain name when I try to send a test e-mail outside. It should be [EMAIL="webmaster@mydomain.com"]webmaster@mydomain.com[/EMAIL] but I see webmaster@kozley-desktop.

I submit mail.log here:

```
Mar  9 17:37:25 kozley-desktop postfix/pickup[32156]: 40D993C1FF8: uid=0 from=<webmaster@kozley-desktop>
Mar  9 17:37:25 kozley-desktop postfix/cleanup[32299]: 40D993C1FF8: message-id=<1299688645.32295@kozley-desktop>
Mar  9 17:37:25 kozley-desktop postfix/qmgr[32157]: 40D993C1FF8: from=<webmaster@kozley-desktop>, size=605, nrcpt=1 (queue active)
Mar  9 17:37:25 kozley-desktop postfix/smtp[32305]: 40D993C1FF8: to=<jessehijet@gmail.com>, relay=mail2.bahnhof.se[213.136.33.9]:25, delay=0.41, delays=0.15/0.16/0.03/0.06, dsn=5.0.0, status=bounced (host mail2.bahnhof.se[213.136.33.9] said: 504 <webmaster@kozley-desktop>: Sender address rejected: need fully-qualified address (in reply to RCPT TO command))
Mar  9 17:37:25 kozley-desktop postfix/cleanup[32299]: 9503A3C1FF9: message-id=<20110309163725.9503A3C1FF9@mail.kozleybloodchaser.com>
Mar  9 17:37:25 kozley-desktop postfix/qmgr[32157]: 9503A3C1FF9: from=<>, size=2697, nrcpt=1 (queue active)
Mar  9 17:37:25 kozley-desktop postfix/bounce[32307]: 40D993C1FF8: sender non-delivery notification: 9503A3C1FF9
Mar  9 17:37:25 kozley-desktop postfix/qmgr[32157]: 40D993C1FF8: removed
Mar  9 17:37:25 kozley-desktop postfix/smtp[32305]: 9503A3C1FF9: to=<webmaster@kozley-desktop>, relay=mail2.bahnhof.se[213.136.33.9]:25, delay=0.16, delays=0.07/0/0.03/0.06, dsn=5.0.0, status=bounced (host mail2.bahnhof.se[213.136.33.9] said: 504 <webmaster@kozley-desktop>: Recipient address rejected: need fully-qualified address (in reply to RCPT TO command))
Mar  9 17:37:25 kozley-desktop postfix/qmgr[32157]: 9503A3C1FF9: removed
```Im using Postfix and Dovecot. Anyone know why?

---

### Post by mciverza on 2011-03-10
The issue is with your Postfix config (postfix handles the SMTP connections, Dovecot just offers the IMAP/POP3 mailbox function)

If you set your computer's hostname to mydomain.com, then it will work. I do recommend that you read up about "how" mail works. Originally email was sent between users at hosts. ie. [email]bob@server2.com[/email] and [email]joe@server3.net[/email]

Postfix's config indicates that your hostname is kozley-desktop, thus email it handles is for "user"@kozley-desktop

---

### Post by Kozley on 2011-03-10
Thanks you for reply.

Okay, how I could replace computer's hostname to mydomain.com?

EDIT: Nvm, that was stupid question. Just edit on hostname in terminal then restart computer. Now I can send a test e-mail without problem. Thanks you!

---

### Post by jmacgowan on 2011-03-10
Be sure to make the changes in /etc/hostname AND /etc/hosts or SUDO will no longer work.

---

### Post by Kozley on 2011-03-10
> **jmacgowan said:**
> Be sure to make the changes in /etc/hostname AND /etc/hosts or SUDO will no longer work.

It's already done.

---

