---
title: "Suspicious syslog entry"
date: 2007-10-28
forum: Server Platforms
---

### Post by Runningflame570 on 2007-10-28
I've been cleaning up the menus on my 7.10 system and was checking my log reports under syslog I found an odd entry and I'm wondering if somebody could clarify if this is a risk or not..it doesn't look good to me though.

"/USR/SBIN/CRON[8086]: (root) CMD ( cd / && run-parts --report /etc/chron.hourly)"

Now I might just be crazy, but that looks like a scheduled report request over TCP/IP and it happened around twelve hours after I started the system.

EDIT: I was crazy it seems, please ignore or delete as appropriate.

---

### Post by MJN on 2007-10-28
For the sake of anyone else that might read this thread the entry is harmless - it is simply cron running its hourly scheduled jobs.

Mathew

---

