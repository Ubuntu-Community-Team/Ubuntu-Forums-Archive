---
title: "Spam from 127.0.1.50"
date: 2012-03-09
forum: Server Platforms
---

### Post by OwlaPowla on 2012-03-09
Hi, 

I'm using postfix and my logs were showing some spam records, the server is not an open relay as I have tested for that, and only allow local networks and sasl authenticated users to send mail. So this must be coming from a script or even a virus on the server right?

```

Mar  9 20:45:34 postfix/smtpd[5427]: connect from unknown[127.0.1.50]
Mar  9 20:45:36 postfix/smtpd[5427]: xxxx: client=unknown[127.0.1.50]
Mar  9 20:45:36 postfix/smtp[5431]: warning: host 127.0.1.50[127.0.1.50]:25 greeted me with my own hostname xxxxxxxx
Mar  9 20:45:36 postfix/smtp[5431]: warning: host 127.0.1.50[127.0.1.50]:25 replied to HELO/EHLO with my own hostname xxxxxxxx

```

I have scanned with clamscan and it didn't find any infected files.
How can I trace the source from this mail?

---

