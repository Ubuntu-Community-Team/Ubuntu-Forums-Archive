---
title: "Grub failure after upgrading in Ubuntu Server 10.10"
date: 2011-06-27
forum: Server Platforms
---

### Post by Actuary on 2011-06-27
I have done an insane amount of Googling before posting this and it's probably the most difficult thing I've faced so far.

The basic problem is very simple, I upgraded the boot loader using **apt-get upgrade**. So Grub upgraded and I believe it automatically ran the **upgrade-grub-from-legacy** executable. I was confused on what to do so I selected all drives. When I did that, I received a bunch of messages, I will write only non-redundant ones:

**mdadm group disk not found**                      (many times, over 20 or so)
**installation finished, no errors reported**     (4 times, I guess for my 4 hard drives)
[B]Found linux image vmlinux ...
Found initrd image ...[/B]

Next, I reboot, and absolutely nothing, not even a grub prompt!! So I tried the following:

1) grub-install /dev/sda1
2) Super grub disk
3) Ubuntu Server Installation CD in rescue mode trying, I get the infamous red error screen when trying to install grub

Nothing worked! My partitions are all there and I can see them and mount them from rescue CD, but I cannot boot to the system, HELP!

My partitions layout:
One **LVM** sitting on two RAID-1 Drives Sitting on all four hard drives sda, sdb, sdc, sdd
One **Root** partition /dev/md2 in RAID-1 Drive sitting on two of the four drives (sda2 and sdb2)
Four **bios_grub** partitions sda1, sdb1, sdc1 and sdd1 each ~1MB
Two **Swap** partitions on two raid drives

I would give more detail but I think the problem is probably in the bootloader configuration because I can access all partitions including LVM and RAIDs from the rescue CD.

Thank you for any help you can provide!!

---

### Post by Actuary on 2011-06-28
bump!

---

### Post by Actuary on 2011-06-28
Ok, it's solved after pain and tears, but it was much, much easier than I expected.

Simply put, the main offender was my BIOS. The damn thing wouldn't install GRUB properly nor would it boot properly simply because I have attached my external USB drives!!

The error messages explained earlier are a red herring. It's just crap and warning that GRUB throws at you while installing against a RAIDed system.

---

