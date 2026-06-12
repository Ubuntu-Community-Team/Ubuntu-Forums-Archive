---
title: "ClamTK functionality question"
date: 2013-08-17
forum: Security
---

### Post by r_avital on 2013-08-17
Hoping this is the right forum, hi all,

I've used clamav for years, with klamav as its front-end, which is no longer maintained, so I fall back on the alternative, clamtk.

I've configured clamtk with a schedule, for both updating the virus db and a scan of my /home directory.

DB update is scheduled for 1:00am, scan for 3:00am, and clamtk confirms that the schedules are set.

The reason for this question is, that clamtk, when I run it, never shows me a history of last night's update and scan.  It only shows me the last time I did a manual scan.  So here's the first really silly question: Does clamtk need to be running at 1:00am~3:00am for the scheduled tasks to execute, or does it simply schedule the jobs with some system-level tool like cron or something similar?  

I've checked the following:
```
~$ ps ax | grep [c]lamd
 2463 ?        Ssl    0:08 /usr/sbin/clamd
``` So we know clamd is running, and my system-monitor reports it's run by user clamav.

Apologies, but this is not the silliest question I've ever asked :)
TIA

**Update:** Solved my own problem looking at /var/log/clamav/ checking both clamav.log and freshclam.log.  Duh.

Since I've yet not found a way to delete a post, I'll just mark it solved, hope it will save someone else my embarrassment.

---

