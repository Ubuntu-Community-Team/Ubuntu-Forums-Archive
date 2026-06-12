---
title: "Grub hanging booting Proliant DL120 G5"
date: 2008-10-09
forum: Server Platforms
---

### Post by jezndi on 2008-10-09
I've just spent the best part of a day installing 8.04-1 amd64 server on an Proliant DL120 G5, using software RAID.

The problem, which I have solved, was this: 

Following a successful RAID configuration with the installer, grub hung up or stalled with:

GRUB Loading stage 1.5.

This message lasted approx 94 seconds and was then replaced with 

GRUB loading please wait..

which lasted another 94 seconds and was then follwed by the usual grub boot menu. Thereafter things behaved normally.

The machine in question has two SATA disks configured to use a 10GB root, 10GB swap, 10GB /tmp 40GB /var and 190GB /data ext3 file systems, all of which are RAID1, so that either disk can run the server if the other one dies.

After a lot of mucking about, trying small ext3 linux partitions for /boot installing the 386 not amd64 version, no improvement was noted.

I figured there must be a hardware issue somewhere, but what? I've been through everyting in the BIOS.

I tried removing the second drive after marking its RAID components as failed, but no joy. Then I tried attaching the first drive to the *second* disk connector - and the grub response was immediate. Reattaching the second disk to the *third* connector and I have the RAID up and running and no grub delay.

I've no idea why this should work, but it does.

---

### Post by lima25 on 2009-01-21
Yesterday I had this problem, and I finally fixed it by unpluging the blue cdrom sata cable.
It seems that if anything is connected to the blue sata connectors on board, the grub problem arises.
If I plug the cdrom cable to the normal sata connector, everything is ok.

---

