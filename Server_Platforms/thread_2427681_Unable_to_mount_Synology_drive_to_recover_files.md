---
title: "Unable to mount Synology drive to recover files"
date: 2019-09-24
forum: Server Platforms
---

### Post by asko1110 on 2019-09-24
Hello
I had a Synology single drive NAS which went down. The disk however seems has survived. Now I'm trying to access stored data but can't succeed.
So far I have found few topics which helped me a lot. 
Using below I have created array
```
mdadm --create /dev/md0 --assume-clean --verbose --level=raid1 --raid-devices=2 missing /dev/sdb5
mdadm: /dev/sdb5 appears to be part of a raid array:
       level=raid1 devices=1 ctime=Tue Apr  4 19:35:26 2017
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 971800384K
mdadm: automatically enabling write-intent bitmap on large array
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
root@Inspiron-1520:~# mdadm -Asf && vgchange -ay
root@Inspiron-1520:~# vgchange -ay -v
    No volume groups found.

```
Next I tried to mount but got failure
```
mkdir /mnt/nas
root@Inspiron-1520:~# mount /dev/md0 /mnt/nas -o ro

mount: wrong fs type, bad option, bad superblock on /dev/md0,
missing codepage or other error
```
I did few checks 
```
dmesg | tail
[ 1131.950152] md: md_import_device returned -22
[ 1131.950372] md: md3 stopped.
[ 1131.970566] md: sdb5 does not have a valid v1.2 superblock, not importing!
[ 1131.970574] md: md_import_device returned -22
[ 1131.970606] md: md3 stopped.
[ 1132.029322] md: sdb5 does not have a valid v1.2 superblock, not importing!
[ 1132.029331] md: md_import_device returned -22
[ 1132.029366] md: md3 stopped.
[ 2250.081291] md/raid1:md0: active with 1 out of 2 mirrors
[ 2250.094906] md0: detected capacity change from 0 to 995123593216

```
```
mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Tue Sep 24 23:10:00 2019
        Raid Level : raid1
        Array Size : 971800384 (926.78 GiB 995.12 GB)
     Used Dev Size : 971800384 (926.78 GiB 995.12 GB)
      Raid Devices : 2
     Total Devices : 1
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Tue Sep 24 23:10:00 2019
             State : clean, degraded 
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

              Name : Inspiron-1520:0  (local to host Inspiron-1520)
              UUID : ea50cbba:fd97f167:0894f728:834f99ae
            Events : 0

    Number   Major   Minor   RaidDevice State
       -       0        0        0      removed
       1       8       21        1      active sync   /dev/sdb5

```
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb5[1]
      971800384 blocks super 1.2 [2/1] [_U]
      bitmap: 0/8 pages [0KB], 65536KB chunk

unused devices: <none>

```

I have also been trying to mount with -t ext3 or ext4 but got the same response.
Even I thought that maybe I should try create array with just one drive so did step 1 with --force --raid-devices=1 but later had the same.

Does anyone can help me with that?

---

### Post by darkod on 2019-09-25
Did you examine the superblock BEFORE actually creating your new array? Checking it out later gives you info about the array you created, not about the array Synology had created.

I don't have much experience with synology. I guess you googled how to mount disks from broken arrays? There must be some advice.

---

