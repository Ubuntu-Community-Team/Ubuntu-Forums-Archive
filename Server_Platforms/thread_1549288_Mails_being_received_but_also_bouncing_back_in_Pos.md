---
title: "Mails being received but also bouncing back in Postfix/dovecot"
date: 2010-08-09
forum: Server Platforms
---

### Post by Fidelix on 2010-08-09
My postfix mail server is receiving messages normally, but is also bouncing the messages back to the sender.

What could be happening?

Here is tail /var/log/mail.log

```
Aug 10 00:26:35 anbient postfix/smtpd[5638]: connect from mail-yw0-f41.google.com[209.85.213.41]
Aug 10 00:26:35 anbient postfix/smtpd[5638]: 95D3935680CE: client=mail-yw0-f41.google.com[209.85.213.41]
Aug 10 00:26:35 anbient postfix/cleanup[26288]: 95D3935680CE: message-id=<4C609CA6.1050104@gmail.com>
Aug 10 00:26:35 anbient postfix/qmgr[15798]: 95D3935680CE: from=<felipefidelix@gmail.com>, size=4438, nrcpt=1 (queue active)
Aug 10 00:26:35 anbient postfix/local[30425]: 95D3935680CE: to=<eu@anbient.net>, orig_to=<eu@felipefidelix.com>, relay=local, delay=0.11, delays=0.1/0/0/0.01, dsn=2.0.0, status=sent (delivered to maildir)
Aug 10 00:26:35 anbient postfix/qmgr[15798]: 95D3935680CE: removed
Aug 10 00:27:05 anbient postfix/smtpd[5638]: disconnect from mail-yw0-f41.google.com[209.85.213.41]
```

---

### Post by Fidelix on 2010-08-11
Please, someone help.

Its impossible to use postfix like that. Every single mail i receive goes back to the sender.

---

