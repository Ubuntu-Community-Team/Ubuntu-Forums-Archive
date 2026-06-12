---
title: "High Memory &amp; CPU Usage"
date: 2020-06-11
forum: Server Platforms
---

### Post by markshepparduk on 2020-06-11
Hi Everyone,
I have had a recent kernel update on Ubuntu Server 18.04 and it seems to  have driven my server crazy. I am getting High CPU on MySQL and Clamav.  I have disable email scanning for Clamav within Virtualmin but when  using htop it is showing that the email is scanning with it which is  overloading my server. Even when i kill the process it keeps coming  back. The server is hitting nearly 200% i can’t even keep it on at the  moment as the disks are over active and i am getting so many MYSQL and  Clamav processes the server is locking up and sites are all down. Any  help would be appreciated.


 Thanks


 Mark

---

### Post by LHammonds on 2020-06-11
Well, the 1st thing I would do is boot the system and tell grub to use the prior kernel to see if the problem persists.

**EDIT: **Oh, press and hold SHIFT while booting up to see the grub menu.

LHammonds

---

### Post by CelticWarrior on 2020-06-11
Try booting with a previous kernel and if the problem doesn't occur keep running the kernel that works until there's a new update.

---

