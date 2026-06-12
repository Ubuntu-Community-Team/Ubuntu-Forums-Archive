---
title: "lvm logical volume size not the same as disk free"
date: 2007-08-10
forum: Server Platforms
---

### Post by skela on 2007-08-10
I have two terrabyte disks, and the plan was to have em both show as one large hard drive without using raid. lvm2 seemed the logical choice, anyway...

I've read around a bit so I know the basics of logical volumes, but this problem has me puzzled.
I first set up a physical volume for the first hard drive, then I created a volume group and created a logical volume. I made sure my physical extent was large enough to handle at least 2 TB (Went for 64M , meaning I could in theory expand later to a total of 4 TB).

Anyway, when I tried to incorporate the second hard drive into the logical volume, something weird happened.

In essence, the right information shows up with the various logical volume commands. But when I do a simple "df" the available space is only half that of what the logical volume says... (in other words only one hard drive is showing up with the df command, but both with the logical volume commands).
Here are some of my printouts:

root@newton3:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/vg/fs
  VG Name                vg
  LV UUID                uecdJU-Lxha-ryKr-lod6-0k5P-ukJV-4WCJCp
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.82 TB
  Current LE             29808
  Segments               2
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0

root@newton3:~# vgdisplay
  --- Volume group ---
  VG Name               vg
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  4
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1.82 TB
  PE Size               64.00 MB
  Total PE              29808
  Alloc PE / Size       29808 / 1.82 TB
  Free  PE / Size       0 / 0
  VG UUID               OXfIDc-F1Tf-3484-aMNY-rfei-cMeL-mS2T90

root@newton3:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdc
  VG Name               vg
  PV Size               931.50 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       65536
  Total PE              14904
  Free PE               0
  Allocated PE          14904
  PV UUID               TdFXF5-6A5D-Am0U-7uoa-G2tT-QHxM-2DRnks

  --- Physical volume ---
  PV Name               /dev/sda
  VG Name               vg
  PV Size               931.50 GB / not usable 0
  Allocatable           yes (but full)
  PE Size (KByte)       65536
  Total PE              14904
  Free PE               0
  Allocated PE          14904
  PV UUID               SzdVnL-aZoD-lEa7-0xA3-lNrz-BGmw-E0gBVS

root@newton3:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              52G   12G   38G  24% /
varrun                1.5G  212K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
procbususb            1.5G   84K  1.5G   1% /proc/bus/usb
udev                  1.5G   84K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.20-16-generic/volatile
**/dev/mapper/vg-fs     932G  853G   79G  92% /fs**

root@newton3:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5e793774-622e-4d6b-b444-9960bc342d4d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a8f7b975-4465-4a87-9654-5b7bb576b483 none            swap    sw              0       0
/dev/hdc                /media/cdrom0   udf,iso9660     user,noauto     0 0
**/dev/vg/fs      /fs             reiserfs        defaults        0 2**

---

### Post by jlintz on 2007-08-11
Did you extend the filesystem after extending the volume group?

It looks like you are using reiser so you would use resize_reiserfs

---

### Post by conjur3r on 2007-08-13
Yup, exactly what jlintz said.

After expanding your LVM with new disks, you need to take your logical volume offline and expand it using whichever filesystem tool your partition uses.  It is also recommended to scan the disk for any errors and fix accordingly before expansion.

For reference, see [http://tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html#AEN1209](http://tldp.org/HOWTO/LVM-HOWTO/recipeadddisk.html#AEN1209)

---

