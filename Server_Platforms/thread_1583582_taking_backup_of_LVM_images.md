---
title: "taking backup of LVM images"
date: 2010-09-28
forum: Server Platforms
---

### Post by tapas_mishra on 2010-09-28
Hi,
I am using Lucid 10.04 64 bit.
I had created some lvms in some locations on my server.
Which I am not able to recall.
pvdsiplay
lvdisplay
```

  --- Physical volume ---
  PV Name               /dev/sda6
  VG Name               nintendo
  PV Size               441.55 GiB / not usable 3.00 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              113035
  Free PE               10635
  Allocated PE          102400
  PV UUID               UMmBxP-upFM-H3S4-neHF-XYyo-gs3Q-rZsWMx


 --- Logical volume ---
  LV Name                /dev/nintendo/lvm1
  VG Name                nintendo
  LV UUID                pM9IVB-UorL-9CtJ-qRp5-wRsX-KEKm-ws5nvc
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0

  --- Logical volume ---
  LV Name                /dev/nintendo/lvm2
  VG Name                nintendo
  LV UUID                cVyyOe-QbdC-R2Ys-xGdv-I3GB-m6Da-fFjFFd
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                150.00 GiB

  Current LE             38400
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1

  --- Logical volume ---
  LV Name                /dev/nintendo/lvm3
  VG Name                nintendo
  LV UUID                fppbX8-bJTZ-is2U-qMjk-VpBT-3h7n-yCF4qv
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                50.00 GiB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2

--- Logical volume ---
  LV Name                /dev/nintendo/lvm4
  VG Name                nintendo
  LV UUID                y3I7sC-S2vn-huo0-CaGu-W7cF-duIR-B8fKWP
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:3

```


but when I go to directory
/dev/nintendo I see the files
```
total 0
lrwxrwxrwx 1 root root 28 2010-08-27 10:58 lvm4 -> ../mapper/nintendo-lvm4
lrwxrwxrwx 1 root root 33 2010-09-14 14:51 lvm3 -> ../mapper/nintendo-lvm3
lrwxrwxrwx 1 root root 31 2010-08-27 10:58 lvm2 -> ../mapper/nintendo-lvm2
lrwxrwxrwx 1 root root 33 2010-08-27 10:58 lvm1 -> ../mapper/nintendo-lvm1

```
 of only zero bytes.

So how do I take backup of these and how do I find out what will be
the size of hard disk required to take backups.
If an LVM image is 100Gb so do I need 100Gb space in my hard disk to
take backup.
Or how is the process of backup done when I have LVM based images?

---

