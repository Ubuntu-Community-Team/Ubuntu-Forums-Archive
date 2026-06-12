---
title: "Postfix: Bad Sender Address Syntax"
date: 2012-01-23
forum: Server Platforms
---

### Post by dr1134 on 2012-01-23
I am running Ubuntu Server 11.10 with Postfix

I am using Postfix for internal mail only. Email will not be accessed from the web.

When I try to send email to root@192.168.2.1 the SMTP server gives my a bad sender address syntax. However I can send email to root@localhost.

I do not know which config option to change. I have set Postfix up to accept outside connections.

---

### Post by SeijiSensei on 2012-01-23
Try root@[192.168.2.1] instead.

---

### Post by dr1134 on 2012-01-24
Thanks for that

---

