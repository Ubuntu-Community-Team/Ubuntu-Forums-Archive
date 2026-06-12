---
title: "Broken raid 5 (11 drives in mdadm) -- data recovery/raid reconstruction needed -- ple"
date: 2010-07-21
forum: Server Platforms
---

### Post by jay48197 on 2010-07-21
Hi there:

Thanks for reading this thread and I thank you in advance for any help you can provide.

So this is what happened... I noticed that my MDADM RAID 5 array with drives ordered: /dev/sd[EFGHIABCDKJ]1 reported a failed drive -- /dev/sdb1. I stopped the array and ran smartctl -t long /dev/sdb1 and received a pass. 

So I added /dev/sdb1 back to /dev/md0 with mdadm --add. In the process of rebuilding, /dev/sdh1 went offline (the data cable must have been knocked loose while I was moving from FL to MI) and now the array state is degraded. I checked both drives using smartctl again and received 2 passes.

I read advice on some forum about using mdadm -C /dev/md0 /dev/sd[efghiabcdkj]1 but the array resynced with the drive order messed up (sd[abcdefghijk]1 as opposed to sd[efghiabcdkj]1). I tried to mdadm -Af /dev/md0 but got a missing superblock error message.

Came across another post stating that I should do mdadm -C --assume-clean /dev/md0 /dev/sd[efghia MISSING cdkj]1 and then add /dev/sdb1 and then mdadm --assemble /dev/md0 --resync=update but I had a flashdrive plugged in my server which got assigned /dev/sdi1 (OPPS)... Anyways, I pulled the plug quickly, halted the system, removed the flash drive and repeated the steps.

================================================================================
fdisk -l reports:
Disk /dev/hda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/hda2            3188       60801   462784455    5  Extended
/dev/hda5            3188        9561    51199123+   7  HPFS/NTFS
/dev/hda6            9562       28045   148472698+  83  Linux
/dev/hda7           28046       28835     6345643+  82  Linux swap / Solaris
/dev/hda8           28836       60801   256766863+  83  Linux

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      182402  1465138552+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      182402  1465138552+  fd  Linux raid autodetect

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      182402  1465138552+  83  Linux

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      182402  1465138552+  83  Linux

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1      182401  1465136001   83  Linux

Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1      182401  1465136001   83  Linux

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1      182401  1465136001   83  Linux

Disk /dev/sdh: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1      182401  1465136001   83  Linux

Disk /dev/sdi: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1     2907021  1465138552+  83  Linux

Disk /dev/sdj: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1   *           1      182402  1465138552+  83  Linux

Disk /dev/sdk: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1      182402  1465138552+  83  Linux

Disk /dev/md0: 0 MB, 0 bytes
2 heads, 4 sectors/track, 0 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table


================================================================================

So I am guessing that me inserting the flashdrive messed up the # of heads on all the other drives except the drive that did not get assigned the first mdadm -C because its assignment was taken by the flashdrive.

So.... bottom line is... now the resync is completed (diskstats shows reads but no writes to disk) and I am unable to mount the array. I get a "VFS: Can't find ext3 filesystem on dev md0" message. 

Current status: R-Studio reports some data, testdisk is still analyzing my partition, I aborted Raid Reconstructor cause it reports taking like 20 days to complete...

Any hints on how I can recover my data? Any suggestions you can offer will be greatly appreciated cause I am starting a new job and cannot afford to look disorganized despite the bad run of events this past week. Thanks... J

---

