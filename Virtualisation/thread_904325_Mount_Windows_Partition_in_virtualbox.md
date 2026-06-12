---
title: "Mount Windows Partition in virtualbox"
date: 2008-08-29
forum: Virtualisation
---

### Post by Amaroq on 2008-08-29
Hey guys, following the directions in the virtualbox instruction manual (section 9.9), I was able to create a .vmdk file that pointed to my windows partition. However, upon attempting to boot up this windows XP installation in virtualbox, I get error 17 from GRUB.

My partitioning scheme is as follows.

/dev/sda1 boot partition
/dev/sda2 extended partition
/dev/sda3 swap
/dev/sda4 ntfs (windows partition, somehow has bootable flag)
/dev/sda5 ubuntu
/dev/sda6 gentoo (not installed yet. I plan on using this one for gentoo.)

Considering the fact that I am only trying to boot from the windows partition, there are two things that worry me.

First of all, my windows partition has the bootable flag when I view the partitions in fdisk. Second of all, there must be a grub install on my windows partition, otherwise I would get no grub errors when trying to boot the windows partition in virtualbox.

I originally did have a gentoo install, hence the boot partition. /dev/sda3 was originally the gentoo partition, but I deleted it and made it an extended one so I could have both ubuntu and gentoo.

Anyway, I've been wondering if I'm supposed to have a grub install trying to boot up on my windows partition. When I installed gentoo the first time around, I made sure I installed anything grub to the boot partition. Unless the mbr has anything to do with it. I also had set the boot partition with the bootable flag, not the windows one.

So I guess there are two issues I've got here. Grub error 17 is apparently due to not being able to identify the type of the filesystem it's trying to boot. But I'm also wondering if I have a rootkit or something, because I'm pretty sure I didn't put anything grub or any bootable flags on the windows partition.

---

### Post by Amaroq on 2008-08-29
Upon booting up today in Ubuntu, the computer took an uncomfortably long time to connect to the network. I could also not navigate to any pages. Out of suspicion and a gut feeling, I turned off the bootable flag on the windows partition, turned the bootable flag on for my boot partition, and restarted. Network connected instantly and have had no connection issues.

However, now when I try to launch my windows partition in virtualbox, it tells me "FATAL: Could not read from boot medium! System halted."

---

### Post by overdrank on 2008-08-30
Moved to Virtualization :)

---

