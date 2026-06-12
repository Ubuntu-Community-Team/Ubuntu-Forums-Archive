---
title: "Bash script to change sshd_config"
date: 2009-07-20
forum: Server Platforms
---

### Post by dragos2 on 2009-07-20
I am in need for help regarding a bash script that will change sshd_config based on 2 other
files:

sshd_duringWeek will contain users that are allowed to log in during week days
and
sshd_allowWeekend will contain users that can log in during weekend.

After modification the sshd is restarted.

The script should modify the AllowUsers directive from /etc/ssh/sshd_config.

I did this in Java and set up a cron every Friday afternoon and Monday morning.

I am not that good in bash so I need some help to do this script.

Can you help please ?

---

