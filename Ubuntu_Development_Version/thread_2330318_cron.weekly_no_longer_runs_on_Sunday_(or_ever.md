---
title: "cron.weekly no longer runs on Sunday (or ever??"
date: 2016-07-10
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-07-10
Being Sunday cron.weekly should run. There is no mention of that happening in /var/log/syslog or in any /var/*log.
This is seen here in both 16.10 & recent new installs of 16.04

---

### Post by mc4man on 2016-07-12
This would, if widespread?, of concern to ssd users who may be expecting fstrim to run weekly.
[https://bugs.launchpad.net/ubuntu/+source/anacron/+bug/1600603](https://bugs.launchpad.net/ubuntu/+source/anacron/+bug/1600603)

---

