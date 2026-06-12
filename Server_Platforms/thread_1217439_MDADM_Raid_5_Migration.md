---
title: "MDADM Raid 5 Migration"
date: 2009-07-19
forum: Server Platforms
---

### Post by santhony on 2009-07-19
I've been trying to move a MDADM Raid 5 configuration to a brand new Ubuntu AMD64 Build, coming from a Ubuntu I386 Build.  Both are Ubuntu Jaunty.

When moving the raid set to the new OS, there are three Partitions that the New Ubuntu AMD64 will not recognize.  Thus, I cannot assemble or create the build.

My Raid set consists of 7 Drives, sd[abdefgh]1.

ARRAY /dev/md0 level=raid5 num-devices=7 UUID=67350c39:89f0ac91:0f5b4e61:2c17f314

Partitions sd[aeg]1, are not visible by the new OS.

What is happening is when I boot with the new OS drive, mdadm does not see partitions, SDA1, SDG1, SDE1.

I've tried deleting and reformatting SDA1 from both the OLD OS and the New OS.. Once the drive is inserted back and synced into the RAID, the NEW OS mdadm doesn't even see SDA1.  It says it does not exist if I try to even force the assemble or create.

mdadm: cannot open /dev/sda1: No such file or directory

The hard drive order stays the same between both builds.

My Raid set on the original OS is clean and fully assembles.  If I examine each drive, via mdadm -E /dev/sd[abdefgh]1, they all come up perfect, correct UUID's and all the stuff matche's exactly as it should be.

Running examine from the NEW build, I can only do this too mdadm -E /dev/sd[bdfh]1.
For sda1,sde1, and sdg1, mdadm says those partitions do not exist.

GParted does see all Seven Partitions, identical and as expected, unknown file type, raid on the NEW OS.

All seven partitions from Fdisk -l are fd raid auto detect.

I have tried forcing the build in different orders, but it doesn't work since the three disk partitions do not exist.

I can boot into the original OLD OS at any time and all assebles fine.

I have also tried the same mdadm.conf on the Original on the New OS, with no luck.

Am I missing something Obvious?

Any ideas I would be extremly greatful.

---

### Post by santhony on 2009-07-19
ADDITIONAL INFO:

fdisk -l Output and mdadm create, this is from the new OS, Ubuntu Jaunty AMD64 Build.


santhony@Ubuntu:~$ sudo mdadm -E /dev/sda1
[sudo] password for santhony:
mdadm: cannot open /dev/sda1: No such file or directory
santhony@Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010749

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15bef5d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00084ae9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e387c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095888

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bab3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bab3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abcd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 250.0 GB, 250059349504 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd69d8188

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1       29659   238235886   83  Linux
/dev/sdi2           29660       30401     5960115    5  Extended
/dev/sdi5           29660       30401     5960083+  82  Linux swap / Solaris
santhony@Ubuntu:~

santhony@Ubuntu:~$ sudo mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=7 /dev/sdf1 /dev/sde1 /dev/sdg1 /dev/sdh1 /dev/sdb1 /dev/sdd1 missing
mdadm: Cannot open /dev/sdf1: Device or resource busy
mdadm: Cannot open /dev/sde1: No such file or directory
mdadm: Cannot open /dev/sdg1: No such file or directory
mdadm: Cannot open /dev/sdh1: Device or resource busy
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: Cannot open /dev/sdd1: Device or resource busy
mdadm: create aborted
santhony@Ubuntu:~$

---

### Post by fjgaude on 2009-07-19
It's not good to do a "create" on an array that's already created. Use only assemble. The four drives that show as busy are part of the old array. Before they can be used in a new array each have to have their superblocks zeroed.

Show us what your **/etc/mdadm/mdadm.conf** file and your **/etc/fstab** files are, please.

---

