---
title: "Logical volumes on Raid5 won't work."
date: 2009-10-12
forum: Server Platforms
---

### Post by u-slayer on 2009-10-12
```
mdadm --assemble /dev/md3 sdb sdc sda
mdadm: /dev/md3 has been started with 3 drives.
root@ubuntu:/dev# 
root@ubuntu:/dev# pvcreate -f -M2 --metadatasize 960K --setphysicalvolumesize 950T md3
  WARNING: md3: Overriding real size. You could lose data.
  Physical volume "md3" successfully created
root@ubuntu:/dev# vgcreate -s 256M raid md3
  Volume group "raid" successfully created
root@ubuntu:/dev# 
root@ubuntu:/dev# lvcreate --extents 100%FREE raid
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume raid-lvol0 (252:2)
  /dev/raid/lvol0: write failed after 0 of 4096 at 0: No space left on device
  Logical volume "lvol0" created
```

I can create logical volumes. But I can't use them. 

lvdisplay shows this:

```
lvdisplay
  --- Logical volume ---
  LV Name                /dev/raid/lvol0
  VG Name                raid
  LV UUID                ******
  LV Write Access        read/write
  LV Status              suspended
  # open                 0
  LV Size                950.00 TB
  Current LE             3891199
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

```

---

### Post by u-slayer on 2009-10-12
echo echo echo

---

### Post by u-slayer on 2009-10-12
I tried installing ubuntu 9.04 i386. I upgraded both mdadm and lvm2. Same result:

```
lvcreate --extents 100%FREE raid5
  device-mapper: reload ioctl failed: Invalid argument
  Aborting. Failed to activate new LV to wipe the start of it.
```


Pls Help.

---

### Post by u-slayer on 2009-10-12
Thanks for all of you helpful suggestions and comments guys, but after hours of googling I solved this myself. Apparently the error causing my logical volume not to mount wasn't being displayed. It was buried in the dmseg log:

```
[ 1955.272254] device-mapper: table: device 9:127 too small for target
[ 1955.272265] device-mapper: table: 252:2: linear: dm-linear: Device lookup failed

```

Turns out when I created the physical volume for LVM I said 950T instead of 950G. oops. So device mapper was trying to create a mapping bigger than the  physical disk under it. Would have been nice if lvcreate would have told me that.

---

