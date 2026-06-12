---
title: "Deleting Win Recovery Partitions to add more Linux"
date: 2015-10-14
forum: Ubuntu/Debian BASED
---

### Post by MagisterDixit on 2015-10-14
I have a Compaq Presario that currently has Windows 10 (upgraded Win7) and Elementary OS. I want to add other Linux distros to my computer, but Windows takes up 3 of the 4 partitions. I already have recovery disks for Windows and don't need the two recovery partitions that MS put on there. My question is... What is the simplest way to eliminate those unwanted recovery partitions so that I can have room for more OS? Should I use Windows disk management to simply delete them? I believe that option will render the partitions as unallocated. OR do I need to do something more complicated in Linux so that I can install a couple new OS? 

I'm sorry if this is not an appropriate question for this forum because Elementary isn't an officially supported spin of Ubuntu, but it's based on Ubuntu 14.04 LTS and the Elementary forums are not nearly as developed as this one. Thanks for any help!

---

### Post by oldfred on 2015-10-14
Moved to Other OS sub forum.

If BIOS with MBR, you can have an unlimited number of logical partitions whether / (root) or data partitions. If installing mulitple Linux best to have at least once share data partition and a shared NTFS data partition if also dual booting Windows. But Windows 10 must have its fast startup or always on hibernation turned off. (Like Windows 8).

If you have good backups and Windows 10 repair flash drive, then you can use any tool you want to remove partitions, either Windows or gparted. But may not be necessary, if you already have an extended partition to hold your logical partitions. The recovery partitions are not usually large.

---

