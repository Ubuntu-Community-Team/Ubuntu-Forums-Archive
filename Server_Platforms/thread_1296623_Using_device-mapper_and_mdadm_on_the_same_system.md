---
title: "Using device-mapper and mdadm on the same system?"
date: 2009-10-20
forum: Server Platforms
---

### Post by devanl on 2009-10-20
Hello,

Is it possible to configure a system such that DM and mdadm can run together on the same system?  I am using LVM2 to manage my system disks and then mdadm to create a RAID5 volume for storage.  I noticed that after rebooting I get the error:

mdadm: Cannot open /dev/sdd: Device or resource busy

From what I've read the way around this is to disable the dmraid-driver, I'm pretty sure that if I do this I will lose my system disk.  Perhaps there's a way to put the disks in the raid5 volume on a do-not-use list for dmraid?

Thanks,
Devan

---

### Post by fjgaude on 2009-10-21
Totally confused! You have a drive or partition in an **mdadm** raid array that is also part of BIOS-created array using **dm** to access while in Ubuntu?

---

### Post by devanl on 2009-10-21
Or maybe there's a way to migrate my volumes off of LVM?
I realized today that the VG is only 1 PV...

File descriptor 5 left open
  --- Logical volume ---
  LV Name                /dev/DevanLFS/swap_1
  VG Name                DevanLFS
  LV UUID                71Irc6-GdOH-NcsV-4FMm-MPMq-TviX-1F2mhH
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.80 GB
  Current LE             717
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/DevanLFS/root
  VG Name                DevanLFS
  LV UUID                a5qUF2-V8hR-0mt1-DxSN-Rxtg-RzBE-szmzjf
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                55.88 GB
  Current LE             14305
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Name                /dev/DevanLFS/home
  VG Name                DevanLFS
  LV UUID                KsULux-GiE9-uagM-LgbP-lK93-oS3v-lqdqT3
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                8.91 GB
  Current LE             2282
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
devanl@DevanLFS:~$ sudo vgdisplay
  --- Volume group ---
  VG Name               DevanLFS
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  6
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                3
  Open LV               3
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               67.59 GB
  PE Size               4.00 MB
  Total PE              17304
  Alloc PE / Size       17304 / 67.59 GB
  Free  PE / Size       0 / 0   
  VG UUID               IO2mGX-Xovc-VZTw-39C1-T1Ca-Vjvy-LkhprZ

devanl@DevanLFS:~$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda1
  VG Name               DevanLFS
  PV Size               67.60 GB / not usable 1.53 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              17304
  Free PE               0
  Allocated PE          17304
  PV UUID               Quibnz-C76N-a2zs-ipTP-AwVb-b35p-psaR8p
   
  "/dev/sdb5" is a new physical volume of "67.60 GB"
  --- NEW Physical volume ---
  PV Name               /dev/sdb5
  VG Name               
  PV Size               67.60 GB
  Allocatable           NO
  PE Size (KByte)       0
  Total PE              0
  Free PE               0
  Allocated PE          0
  PV UUID               ug3V2b-cxuo-U6kV-dZPe-tC4h-3H0o-1d0UHW


devanl@DevanLFS:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdf[3] sde[2] sdd[1] sdc[0]
      2930287488 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

---

### Post by devanl on 2009-10-31
I believe I discovered the issue here.  It seems that when I exported the array to the configuration it listed one of the disks as being a spare, even though I had created it without spares.

I don't know if this is a bug or just the way it works but my guess is that this has something to do with having exported the config before the array had finished syncronizing for the first time.

Devan

---

### Post by fjgaude on 2009-10-31
Gosh, we learn things each day as we keep our minds open, eh?

---

