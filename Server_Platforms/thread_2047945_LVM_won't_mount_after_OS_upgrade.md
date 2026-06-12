---
title: "LVM won't mount after OS upgrade"
date: 2012-08-25
forum: Server Platforms
---

### Post by andymurn on 2012-08-25
I installed 12.04 on a new hard drive in my media center to update from 9.10 that is on an old drive. The problem lies when I run the following command and it spits out the following error:

```
vgchange -ay Storage
  device-mapper: resume ioctl failed: Invalid argument
  Unable to resume Storage-files (252:0)
  1 logical volume(s) in volume group "Storage" now active
```So I checked the logs and saw this.
```
 device-mapper: table: 252:0: sdf too small for target: start=384, len=**3907026944**, dev_size=**3907027055**
```The numbers don't make sense. I have seen lots of other posts online where the length is more than the dev_size but I don't understand why this won't fit.

```
sudo pvs -o +dev_size
  PV         VG      Fmt  Attr PSize   PFree   DevSize
  /dev/sda   Storage lvm2 a-     1.82t      0    1.82t
  /dev/sdb   Storage lvm2 a-     1.82t      0    1.82t
  /dev/sdd   Storage lvm2 a-     1.82t      0    1.82t
  /dev/sde   Storage lvm2 a-     2.73t      0    2.73t
  /dev/sdf   Storage lvm2 a-     1.82t      0    1.82t

```I ran parted and noticed that only sdf, the problem disk, has a disk label and it's zfs. The drives are all lvm and ext4.
```
sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Error: /dev/sdb: unrecognised disk label                                  

Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sdc: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  55.7GB  55.7GB  primary   ext4            boot
 2      55.7GB  60.0GB  4292MB  extended
 5      55.7GB  60.0GB  4292MB  logical   linux-swap(v1)


Error: /dev/sdd: unrecognised disk label                                  

Error: /dev/sde: unrecognised disk label                                  

Model: ATA WDC WD20EADS-14R (scsi)
Disk /dev/sdf: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  2000GB  2000GB  zfs

```

Any suggestions on how to proceed would be appreciated.

Thanks,
Andy

---

