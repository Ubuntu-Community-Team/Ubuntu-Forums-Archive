---
title: "/home/user/.gvfs unreadable"
date: 2013-03-06
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-03-06
Wonder if you also get that issue on your system ?

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1148823](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1148823)

---

### Post by dino99 on 2013-03-06
hm, dont know whats happened: i've rebooted after having installed the latest 3.8.0.11 kernel, and the .gvfs file is gone now  :confused:

---

### Post by The Cog on 2013-03-06
Sebastien probably really wants to see the output from ```
ls -ld ~/.gvfs
```

On my PC here (for reference), I get:```
dr-x------ 2 steve steve 1 Dec 22  2009 /home/steve/.gvfs
```
Which suggests to me that .gvfs hasn't been used here since 2011. In recent releases, Ubuntu has been using /run/user/*username*/gvfs instead.

---

### Post by dino99 on 2013-03-06
That .gvfs file have catched my attention because nautilus is set to sort the most recent changes first, and recent boot have tried to update/read it but failed. As its now gone, its likely a "leftover" file as says Sebastien into the bug report.

---

