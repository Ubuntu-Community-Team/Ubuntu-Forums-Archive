---
title: "Postfix - Outgoing Rate Controls?"
date: 2008-05-26
forum: Server Platforms
---

### Post by darwin2kx on 2008-05-26
I am running Postfix to auth to an external server and use a SMTP account. Using PHP, I dump an email message to many users though this system. My SMTP provider seems to be limiting the number of messages per hour that can be sent though. Is there some way that I can configure Postfix to queue messages, and only send ~60 / hour?

---

### Post by sillygates on 2009-01-07
I founf your thread on google, when I was looking to answer this question for myself.

I read up on the queue manager:
[http://ftp.uma.es/mirror/postfix/qmgr.8.html](http://ftp.uma.es/mirror/postfix/qmgr.8.html)


  default_destination_rate_delay (0s)
              The  default  amount  of  delay  that  is  inserted
              between individual deliveries to the same  destina-
              tion;  with  per-destination recipient limit > 1, a
              destination is a domain, otherwise it is a  recipi-
              ent.

---

