---
title: "Cannot mount cryptswap using systemd"
date: 2015-07-29
forum: Ubuntu Development Version
---

### Post by NCLI on 2015-07-29
I find myself asked for the password to unlock cryptswap, which of course doesn't exist, whenever I try to use the new systemd boot method. When using Upstart, this doesn't happen. Anyone else encounter this?

---

### Post by dino99 on 2015-07-29
Looks like that bug report

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1453738](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/1453738)

---

### Post by NCLI on 2015-07-29
Huh, looks like it was just fixed. I'll update and reboot, thanks!

---

### Post by sudodus on 2015-07-29
It works / should be fixed in Wily. I just tested it in Lubuntu according to [this testcase for Lubuntu alternate](http://iso.qa.ubuntu.com/qatracker/milestones/343/builds/98863/testcases/1439/results). Encrypted home and cryptswap should work in all Ubuntu flavours (it is independent of the differences between Lubuntu and the other Ubuntu flavours).

---

