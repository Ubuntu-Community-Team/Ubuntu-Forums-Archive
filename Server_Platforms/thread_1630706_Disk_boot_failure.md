---
title: "Disk boot failure"
date: 2010-11-25
forum: Server Platforms
---

### Post by Stan* on 2010-11-25
Hi there,

I've installed a fresh system on my old computer. In my computer are 2 hard drives combined as 1 in a RAID 0. I configured a software raid while installing Ubuntu Server.
I made a partition of 256 MB on the first hard disk, mounted as /boot, but I couldn't set the bootable flag. I read on the forums that it was a bug and I could ignore it. So I did. Then I made another two partitions on that disk: 1 swap and 1 for the raid. On the other hard drive I made another two partitions: 1 swap and 1 for the raid.
Then I've configured the software raid to use those 2 big partitions. Everything's fine and the system gets installed.

But, when the installation has finished, the system gifs a "Disk boot failure" error while booting. When I insert the CD and choose "Boot from hard disk" the system works fine.

This is the partition table:
[img]http://img823.imageshack.us/img823/9397/schermafbeelding20101120.png[/img]
As you can see the bootable flag is set.

And here you can see the raid works fine:
[img]http://img683.imageshack.us/img683/3783/schermafbeelding2010112p.png[/img]

How come I can't boot without the CD? Please help me out.

---

### Post by Vegan on 2010-11-25
First off, never use software RAID.

So use the primary disk for the system, them mount the other disk somewhere and use that for a backup or for general storage.

---

### Post by Stan* on 2010-11-26
Hm, oke. So I'm better off reinstalling the system?

---

### Post by Stan* on 2010-11-26
I've reinstalled the system. Mounted the smallest (second) hard disk as root (/) and the largest as /srv, but still I get a disk boot failure. Could it be caused by the hardware?

---

