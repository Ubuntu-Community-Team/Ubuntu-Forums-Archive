---
title: "Mail to the outside world."
date: 2008-08-20
forum: Server Platforms
---

### Post by yield999 on 2008-08-20
Hi Everyone,

I have a box with Ubuntu 8.04 Server and I would like that box to send e-mail to the outside world.

The reason is that I have a application that can send me notice if a service goes down, and I would like to use that feature.

Please help.

Thanks !

---

### Post by de0xyrib0se on 2008-08-20
If you plan to have this act like a mail server, sending mail to the outside world is quite complicated now a days as most outside world servers have protections such as reverse DNS lookups and many more which i'm not about to list since the list grows every day.

What I would suggest is have your server send e-mails through a third party, such as your ISP, most ISPs have SMTP servers exposed for their customers to act as relays.

As for making your own mail server, read up on sendmail or postfix and good luck.

---

### Post by Ximbiot on 2008-08-20
If you are only forwarding local mail, consider installing the nullmailer package:

```
sudo apt-get install nullmailer
```

Nullmailer queues and delivers local mail and can be configured to forward via your ISP's mail server.

---

