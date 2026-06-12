---
title: "RAID5 array md0 gone after reboot."
date: 2015-04-06
forum: Server Platforms
---

### Post by amerinde on 2015-04-06
Help, just finnished the weekend of creating a raid5 md0 using sd[abcd]1, took forever to format (4x 4T drives). Rebooted the system, now md0 does not exist. my 4 independent drives show as linux raid, but in /dev the is no md0. is there any way to get it back? or do i need to build it all over from scratch.

[FIXED]  i used this page. [http://superuser.com/questions/801826/new-mdadm-raid-vanish-after-reboot](http://superuser.com/questions/801826/new-mdadm-raid-vanish-after-reboot)

---

### Post by tgalati4 on 2015-04-06
Understand that RAID5 can have issues with large drives.  Make sure you have a solid backup because running a 12TB array in degraded status is risky.

---

### Post by amerinde on 2015-04-07
thanks for the info tga.. but it isnt degraded.. was new, and some reason, when i set it up, the settings werent save right... but all is ok now.

---

