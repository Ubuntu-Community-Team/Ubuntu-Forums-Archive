---
title: "3ware 9690SA on Ubuntu Server"
date: 2009-08-04
forum: Server Platforms
---

### Post by atagar on 2009-08-04
Hi, I'm trying to install Ubuntu Server (9.04, 64-bit) on a system with three hard drives and a 3ware 9690SA-4I-SGL RAID controller (hoping to have a RAID 5 array). When booting up the controller initializes and spots the hard drives, and according to:
[http://www.3ware.com/KB/article.aspx?id=14546](http://www.3ware.com/KB/article.aspx?id=14546)

the Linux kernel should have built-in support for the card. However, during the Ubuntu Server installation it fails to find the hard disks (tried both the '3w-9xxx' and '3w-xxxx' drivers but no luck). After several hours I'm ready to throw in the towel and ask for help. This is my first time setting up a RAID array so any suggestions would be appreciated! -Damian

---

### Post by atagar on 2009-08-04
Disregard, finally figured out that you need to press Alt+3 when starting up to enter a manager where you create the array first (and no, this was not obvious - may whoever wrote the 3ware documentation die a fiery death).

---

### Post by wirelessmonkey on 2009-08-04
You may find the tw_cli software to control it too, it's hidden deep in the abyss that is 3ware's site, but the name "tw_cli" will help ;)

Best of Luck

---

