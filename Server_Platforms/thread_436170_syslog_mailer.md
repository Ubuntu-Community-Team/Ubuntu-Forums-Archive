---
title: "syslog mailer"
date: 2007-05-07
forum: Server Platforms
---

### Post by sickdude on 2007-05-07
Hi all,

Well since i had so much trouble with hardware i want to prevent this in the future.

So im looking for a script that checks (or tail's) the syslog and messages log for hardware trouble (or other) on the fly.

I use logwatch and this works pretty well but it only mails me once a day. I want this script to mail me only when there are strange entrys in any of the system logs.

Do you know anything that does this? Or do you have any other tips to monitor the hardware in a server?

---

### Post by Mr. C. on 2007-06-06
Logwatch is really geared towards day-end reports.

Try logcheck instead.

MrC

---

