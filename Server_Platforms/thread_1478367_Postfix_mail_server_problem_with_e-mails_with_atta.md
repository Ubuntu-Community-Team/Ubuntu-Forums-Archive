---
title: "Postfix mail server: problem with e-mails with attachments"
date: 2010-05-09
forum: Server Platforms
---

### Post by jmidgley on 2010-05-09
Hi

I run Postfix on an Ubuntu server which I access either from Evolution on an Ubuntu desktop or a client on an HTC mobile phone.

Some messages with attachments seemingly don't make it through intact. The header appears in evolution, showing an attachment (on the mobile phone it even quotes an attachment size), but then hangs on 'Retrieving message'. Strangely, others work - I sent myself an equivalent size message attachment from googlemail and that worked fine.

I'm a bit stuck. There's nothing apparent (to me) in the log, the max message size is 10240000 (plenty big enough). Anything obvious I should check?

Alternatively, can I try to extract the attachment directly off the server?

Cheers
John

---

### Post by jjcv on 2010-05-12
> **jmidgley said:**
> 
I'm a bit stuck. There's nothing apparent (to me) in the log, the max message size is 10240000 (plenty big enough). Anything obvious I should check?


Are you running any virus/spam software with the server.   This can often be a problem.

Have a good look through /var/log/mail.log and see if you can see what is happening with the messages with attachments.   Is it timing out?

Could be so many different things sadly,

---

