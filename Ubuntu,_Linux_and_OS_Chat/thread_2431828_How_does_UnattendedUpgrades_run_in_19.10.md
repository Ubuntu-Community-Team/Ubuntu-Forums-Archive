---
title: "How does UnattendedUpgrades run in 19.10?"
date: 2019-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by another-birdman on 2019-11-22
I was under the impression that UnattendedUpgrades ran out of [FONT=Courier New]cron.daily[/FONT].
That would mean it started at 06:25, plus a random number of seconds between 0 and 1800.

However, I've just noticed it was run on a system at 06:14 (it clashed with a backup, which reported lots of "file missing" entries as a result). When I look at the unattended-upgrades.log it show it running several times a day, and none of those is related to cron.daily.

So how does it run?

> [nuc]: grep Starting unattended-upgrades.log | tail -12
2019-11-17 04:44:59,575 INFO Starting unattended upgrades script
2019-11-17 06:23:43,283 INFO Starting unattended upgrades script
2019-11-18 06:14:46,152 INFO Starting unattended upgrades script
2019-11-18 12:54:58,895 INFO Starting unattended upgrades script
2019-11-19 06:18:35,889 INFO Starting unattended upgrades script
2019-11-19 11:19:18,101 INFO Starting unattended upgrades script
2019-11-20 06:12:23,678 INFO Starting unattended upgrades script
2019-11-20 10:34:37,624 INFO Starting unattended upgrades script
2019-11-21 06:40:27,022 INFO Starting unattended upgrades script
2019-11-21 17:24:42,541 INFO Starting unattended upgrades script
2019-11-22 02:49:02,170 INFO Starting unattended upgrades script
2019-11-22 06:11:23,772 INFO Starting unattended upgrades script


---

### Post by another-birdman on 2019-11-22
To answer my own question - it's all in [FONT=Courier New]systemd[/FONT].

[FONT=courier new]apt-daily.timer[/FONT] has:```
OnCalendar=*-*-* 6,18:00
RandomizedDelaySec=12h
``` so will update the package list twice a day at random times, while [FONT=courier new]apt-daily-upgrade.timer [/FONT]has ```
OnCalendar=*-*-* 6:00
RandomizedDelaySec=60m
```so will run an actual update between 6 and 7a.m..

(So now I can update my backup times accordingly...).

---

