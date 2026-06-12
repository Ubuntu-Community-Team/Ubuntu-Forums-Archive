---
title: "LVM - Disk doesn't contain a valid partition table"
date: 2013-01-29
forum: Server Platforms
---

### Post by JohnnyDisco on 2013-01-29
Hi all,

I've just added a hard drive to my HP MicroServer running Ubuntu 12.04 so I have 1 x 250Gb as the OS and then 2 x 1Tb HDD which I want to set up as an LVM so I can add further drives as and when necessary and keep just the one volume/mount point. 

I set up as an LVM following this guide [http://www.howtoforge.com/linux_lvm_p3](http://www.howtoforge.com/linux_lvm_p3) .  Essentially I created a PV across sdb and sdc, created a LG across sdb and sdc, then created a VG called data, followed by a LV called drive1 which I then formatted to ext4.  In summary:

```
pvcreate /dev/sdb1 /dev/sdc1
vgcreate data /dev/sdb1 /dev/sdc1
lvcreate --name drive1 --size 100%FREE data
mkfs.ext4 /dev/data/drive1
```Everything appears to work fine when I mount it and I can copy data to and from it but when I look at ```
fdisk -l
``` I get the following message about no valid partition table on the /dev/mapper/data-drive1 so I have 2 newbie questions:

1) Is this normal, fine and dandy as it's not actually a physical drive or have I done something wrong?

and

2) Why is the device called /dev/mapper/data-drive when I mount using /dev/data/drive1 ?


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a6a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   478175231   239086592   83  Linux
/dev/sda2       478177278   488396799     5109761    5  Extended
/dev/sda5       478177280   488396799     5109760   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
78 heads, 63 sectors/track, 397542 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc337ca7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953525167   976761560   8e  Linux LVM

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00545f9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953525167   976761560   8e  Linux LVM

Disk /dev/mapper/data-drive1: 2000.4 GB, 2000406183936 bytes
255 heads, 63 sectors/track, 243202 cylinders, total 3907043328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/data-drive1 doesn't contain a valid partition table

```

---

### Post by darkod on 2013-01-29
Both are normal. fdisk can't look into the LVM partition table (and I don't think there is a classic partition table in LVM anyway), so it returns that message.

Also, fdisk will see the LVM as /dev/mapper/VGname-LVname but you would usually use /dev/VGname/LVname. I think the /dev/mapper/... is usable too.

---

