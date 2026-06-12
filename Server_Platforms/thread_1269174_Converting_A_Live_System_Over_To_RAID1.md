---
title: "Converting A Live System Over To RAID1"
date: 2009-09-17
forum: Server Platforms
---

### Post by KiLaHuRtZ on 2009-09-17
Has anyone every done this before?  I'm looking to convert a system over to a RAID 1.  I found this document ([https://help.ubuntu.com/community/Installation/UpgradeToSoftwareRaid](https://help.ubuntu.com/community/Installation/UpgradeToSoftwareRaid)), however the format part scares me a bit.  I have tape backups, but would prefer a smooth transition from a single disk system over to a RAID 1.  If anyone can shed some light on this or share their experience with me, I would be extremely grateful!  Thanks.

---

### Post by Dublee on 2009-09-21
I've had success on performing a live migration from one drive to a two drive RAID1 using this HOW-TO:  [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch).

In the link you provided, the method in which it detects a degraded array and fails over during bootup seems a little more elegant than the method from the link I provided.

---

### Post by KiLaHuRtZ on 2009-09-23
Thanks for that.  I may end up using that method instead.  Either way, I'm going to fire up a test box a see which method is easier.

---

### Post by star3am on 2009-09-23
check out mdadm ... a tutorial I used on gentoo, but will work an anything :D 

[http://forums.gentoo.org/viewtopic-t-96109-highlight-mdadm+hotadd.html]("http://forums.gentoo.org/viewtopic-t-96109-highlight-mdadm+hotadd.html")

works like a charm on any hardware, 

ciao/Riaan

---

