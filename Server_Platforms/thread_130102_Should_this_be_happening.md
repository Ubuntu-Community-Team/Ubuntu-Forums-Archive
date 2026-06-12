---
title: "Should this be happening?"
date: 2006-02-15
forum: Server Platforms
---

### Post by carlosqueso on 2006-02-15
Just for kicks, I checked my auth.log and found a bunch of lines like this: ```
Feb 10 18:17:01 localhost CRON[6862]: (pam_unix) session opened for user root b$
Feb 10 18:17:02 localhost CRON[6862]: (pam_unix) session closed for user root
Feb 10 19:17:01 localhost CRON[6864]: (pam_unix) session opened for user root b$
Feb 10 19:17:01 localhost CRON[6864]: (pam_unix) session closed for user root

```  I don't know that this is a threat, as each session lasts less than a second, but it seems kind of weird.....

---

### Post by LordHunter317 on 2006-02-15
It's just some cron job running.  That's why cron is logging the occurance.

---

### Post by carlosqueso on 2006-02-15
okay....thanks....I wasn't terribly worried...but thought I'd ask.  By the way...were are the chron instructions, so I can see what job is running as root every hour?

---

### Post by carlosqueso on 2006-02-15
never mind...I found it myself in /etc/crontab.   Apparantly, it's just a self-test making sure cron is working.

---

