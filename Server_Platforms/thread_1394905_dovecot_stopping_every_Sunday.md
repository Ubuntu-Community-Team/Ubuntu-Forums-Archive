---
title: "dovecot stopping every Sunday?"
date: 2010-01-31
forum: Server Platforms
---

### Post by akos.maroy on 2010-01-31
I have a curious case here: the dovecot instance I'm running is stopping every Sunday, early morning. I looked that the cron tasks, and I can't find anything that would make it stop. I also looked at the logs, and no indication for the reason for stopping either.

simply re-starting with the init script solves the issue. but it's rather annoying, having to do this every Sunday..

did anyone experience the same issue?

---

### Post by BkkBonanza on 2010-01-31
Which cron tasks did you check? 
It sounds like something in /etc/cron.weekly/ is causing trouble. Maybe log rotation.

---

