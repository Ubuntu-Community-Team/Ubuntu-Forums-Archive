---
title: "smtp gateway"
date: 2010-05-13
forum: Server Platforms
---

### Post by amber1 on 2010-05-13
I have to configure SMTP gateway for multifunction printer HP 4100 MFP. Scanned document can be send to mailbox via SMTP mail server, but problem is that printer can't use SMTP authentication.

I think solution is to setup local SMTP server whith resend incoming mails from printer via ISP SMTP server (now with authentication) or by itself.

I foud POSTFIX SMTP server for ubuntu, but for first look is universal and difficult, probably need additional like COURIER. I don't need fully futured SMTP server for only this task.

Please direct me howto setup local SMTP server only for accept local unauthenticated mails from printer and forward via ISP SMTP server (with authentication).

---

