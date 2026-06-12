---
title: "need to run FIXMBR without a recovery consol"
date: 2006-10-22
forum: Windows
---

### Post by dbaray on 2006-10-22
Made a really big mistake. I have 2 hard drives -win XP sp2 on one and ubuntu on the other. Made a mistake and deleted the ubuntu hard drive partition. Now I get the Error 17 when I start up. so I cant boot to windows. I need to run FIXMBR but have no recovery consol.  Any suggestions?

Thank you

---

### Post by Kateikyoushi on 2006-10-22
Try the super grub disc. [LINK]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows")

---

### Post by mahy on 2006-10-22
> **dbaray said:**
> Made a really big mistake. I have 2 hard drives -win XP sp2 on one and ubuntu on the other. Made a mistake and deleted the ubuntu hard drive partition. Now I get the Error 17 when I start up. so I cant boot to windows. I need to run FIXMBR but have no recovery consol.  Any suggestions?

Thank you

How come you don't have a recovery console? Do you have an installation CD? Then you have recovery console (unless it's a special disk-image-like laptop recovery CD -- Benq laptop use such installation CDs).

In any case, try to install Ubuntu again, that's the best solution. ;)

---

### Post by ibanez on 2006-10-22
if grub is still on the MBR you can just remove it by booting from a 98 cd or floppy and type   FDISK /MBR   ( I've had to do this many times before when I've deleted different Linux's while I was learning.
Alternatively try one of the multi purpose boot disks like "Hirens"

---

