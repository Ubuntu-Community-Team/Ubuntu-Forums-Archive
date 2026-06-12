---
title: "Disk quota notifications"
date: 2010-09-17
forum: Server Platforms
---

### Post by xx77aBs on 2010-09-17
Hello ! I've set up disk quotas (per user) on my server ... Everything is working as it should :)

Now I'm wandering is there any way to notify user when soft limit is reached ?

I've only thought of script that will check at regular intervals (using cron) if someone has reached soft limit ...

Is there any other way, maybe something built in ?

Thanks :)

---

### Post by gzarkadas on 2010-09-17
Set `run_warnquota=true' to your /etc/default/quota to enable the built-in daily cron.job (/etc/cron.daily/quota).

---

