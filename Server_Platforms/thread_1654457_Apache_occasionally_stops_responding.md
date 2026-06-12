---
title: "Apache occasionally stops responding"
date: 2010-12-28
forum: Server Platforms
---

### Post by GrdLock02 on 2010-12-28
I've had a VPS running Ubuntu 9.10 x64 server, hosting 3 websites of mine for a few months now. This problem has been happening for a while.

Every once in a while, probably every 2 or 3 days, I'll wake up in the morning, and apache won't be responding, no web pages will load.

/etc/init.d/apache2 status, reports that apache is functioning properly. Every time I simply have to restart the daemon and things run fine for another few days.

I thought maybe it was a memory issue, so I lowered the MaxClients in the prefork module from 50 to 30 a few days ago, but the same thing is still happening. My VPS has 512MB of ram, burstable to 1GB, and according to Virtuozzo, there was only one night of high traffic where I even came close to that soft limit.

I've checked my syslog, and there's absolutely nothing in there about apache.

I know the description of this problem is pretty vague, but whatever info may help diagnose this problem, please, ask me and I'll get the info. I'm lost here... no clue where to look.

Anyone?

---

### Post by robert_pectol on 2010-12-28
Apache2 also writes various logs.  It logs to /var/log/apache2/*.log by default but could be configured to log to another location or could even be disabled.  Did you find and check Apache2's logs?  That would be my first plan of attack if I were hunting down a problem such as that.  Keep in mind that you may need to enable logging if it's been turned off in Apache2's config.

---

### Post by GrdLock02 on 2010-12-28
> **robert_pectol said:**
> Apache2 also writes various logs.  It logs to /var/log/apache2/*.log by default but could be configured to log to another location or could even be disabled.  Did you find and check Apache2's logs?  That would be my first plan of attack if I were hunting down a problem such as that.  Keep in mind that you may need to enable logging if it's been turned off in Apache2's config.
Ahh, forgot to include that. There's nothing in my error.log file either.

```
[Tue Dec 28 11:43:58 2010] [notice] caught SIGTERM, shutting down
[Tue Dec 28 11:44:00 2010] [notice] Apache/2.2.12 (Ubuntu) PHP/5.2.10-2ubuntu6.5 with Suhosin-Patch configured -- resuming normal operations

```

That's all that's in it, which is when I restarted the process. Before that there's absolutely nothing indicating a problem.

---

