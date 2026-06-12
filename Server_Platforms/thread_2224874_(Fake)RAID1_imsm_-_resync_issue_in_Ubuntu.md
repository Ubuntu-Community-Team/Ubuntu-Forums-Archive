---
title: "(Fake)RAID1 imsm - resync issue in Ubuntu"
date: 2014-05-18
forum: Server Platforms
---

### Post by dam-brouard on 2014-05-18
Hi,

First, I hope I'm in the right section to ask the question ! I'm using Ubuntu 14.04 LTS x86_64, kernel 3.13.0-24-generic., 

I installed 2x 3TB hard-drive (sdb and sdc) in my desktop that I want to use as storage in RAID1 array. My OS's (Ubuntu and Windows7) are running on independent SSD drive (sda), hence I am not trying to boot or install anything on the RAID1 array. 
Ideally, the RAID1 would be accessible in Read/Write from both Ubuntu and Windows. (hence the use of imsm instead of a Linux software-RAID...)

I set-up FakeRAID using Intel Rapide Storage Technology on my motherboard (AsRock Z77). Everything went smoothly, HDD were setup as GPT drives in Windows as they are > 2TB and I created NTFS partition in Windows.
Then, I just assembled the array in Ubuntu using mdadm package - *mdadm --assemble --scan* -. Again, it went pretty smoothly and I can now access the RAID array from both Windows and Ubuntu.

BUT (there's always a but...), I'm still facing 1 issue ! RESYNC !
So, I did a few experiments, and here are the outcomes:

When RAID1 array is in Normal state and nothing is written in the partition, you can boot and reboot as many times as you want in Ubuntu and Windows. RAID1 array will stay in Normal mode and no resync will be triggered: that's cool, exactly how it should behave
(hence, this post is NOT another thread post about resync issue after each reboot :D )

A. File/Directory is created/deleted/modified under Ubuntu, and RAID1 array...:[INDENT]A.1 IS NOT unmounted BEFORE shutdown => Ubuntu start resync after reboot : That is not an expected behavior!
[/INDENT]
[INDENT]A.1 IS unmounted manually before shutdown => Ubuntu will not start resync after reboot: that's cool, exactly how it should behave
[/INDENT]
[INDENT]A.2 IS unmounted manually and mounted again => Ubuntu will not start resync after boot: that's good too. means A.1 case something goes wrong at system unmount/reboot, RAID is not correctly unmounted at reboot phase after writing to it.
[/INDENT]
[INDENT]A.3 ERROR : ANY CASE, Windows triggers a verification on the RAID1 array - setting the array in Verify mode, Ubuntu will continue the verification state where Windows left it at reboot. The verification process can be cancelled in Windows, reverting the     RAID1 array to Normal state. In that case, you can boot on either Ubuntu or Windows just fine (without the RAID1 array going into Verify)[/INDENT]
 
B. File/Directory created/deleted/modified under Windows and followed by reboot, everything is GOOD (wether you reboot to Ubuntu or Windows): that's cool, exactly how it should behave

C. Cancelling Verification in Windows revert the array to Normal state and then becomes fine on both Windows and Ubuntu.

_** It seems there are 2 bugs:**_
1. Ubuntu is not able to unmount the RAID1 properly during shutdown after writing to it.
2. Windows triggers a verification everytime Ubuntu created/deleted/modified a file.






*More information regarding my setup:*

** Version:**
```
damien@damien-desktop:~$ sudo mdadm --version
mdadm - v3.2.5 - 18th May 2012
```

**Plateform:**
```
damien@damien-desktop:~$ sudo mdadm --detail-platform
       Platform : Intel(R) Matrix Storage Manager
        Version : 11.2.0.1527
    RAID Levels : raid0 raid1 raid10 raid5
    Chunk Sizes : 4k 8k 16k 32k 64k 128k
    2TB volumes : supported
      2TB disks : supported
      Max Disks : 6
    Max Volumes : 2 per array, 4 per controller
 I/O Controller : /sys/devices/pci0000:00/0000:00:1f.2 (SATA)
```

**Detail Scan:**
```
damien@damien-desktop:~$ sudo mdadm --detail --scan
ARRAY /dev/md/imsm0 metadata=imsm UUID=366ec5d5:8a1ef347:e8744f26:8f20550e
ARRAY /dev/md/STORAGE container=/dev/md/imsm0 member=0 UUID=43c24e0b:41d2fff1:6a9ceace:54691c3d
```
[B]
mdadm.conf:[/B]
```
damien@damien-desktop:~$ cat /etc/mdadm/mdadm.conf | grep ARRAY
ARRAY metadata=imsm UUID=366ec5d5:8a1ef347:e8744f26:8f20550e
ARRAY /dev/md/STORAGE container=366ec5d5:8a1ef347:e8744f26:8f20550e member=0 UUID=43c24e0b:41d2fff1:6a9ceace:54691c3d
```

**fstab:**
```
damien@damien-desktop:~$ cat /etc/fstab
# /media RAID array
/dev/md126p2    /media/damien/RAID1        ntfs-3g      rw,user 0    0 
```

**mtab:**
```
damien@damien-desktop:~$ cat /etc/mtab | grep md
/dev/md126p2 /media/damien/RAID1 fuseblk rw,noexec,nosuid,nodev,allow_other,blksize=4096 0 0
```

_**NORMAL BOOT (NO RESYNC):**_

**mdstat:**
```
damien@damien-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid1 sdb[1] sdc[0]
      2930264064 blocks super external:/md127/0 [2/2] [UU]
      
md127 : inactive sdc[1](S) sdb[0](S)
      4776 blocks super external:imsm
       
unused devices: <none>
```

**dmesg:**
```
damien@damien-desktop:~$ dmesg | grep md

[    0.827739] systemd-udevd[114]: starting version 204
[    0.837550] md: linear personality registered for level -1
[    0.844652] md: multipath personality registered for level -4
[    0.846739] md: raid0 personality registered for level 0
[    0.849942] md: raid1 personality registered for level 1
[    1.098814] md: raid6 personality registered for level 6
[    1.098815] md: raid5 personality registered for level 5
[    1.098816] md: raid4 personality registered for level 4
[    1.102807] md: raid10 personality registered for level 10

[    2.919773] systemd-udevd[412]: starting version 204
[    3.068454] md: bind<sdb>
[    3.270228] md: bind<sdc>
[    3.272916] md: bind<sdc>
[    3.272970] md: bind<sdb>
[    3.274027] md/raid1:md126: active with 2 out of 2 mirrors
[    3.274039] md126: detected capacity change from 0 to 3000590401536
[    3.278435]  md126: p1 p2
[    3.280622] md: md126 switched to read-write mode.
```


**Details**:

```
damien@damien-desktop:~$ sudo mdadm --detail /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 2

Working Devices : 2


           UUID : 366ec5d5:8a1ef347:e8744f26:8f20550e
  Member Arrays : /dev/md/STORAGE

    Number   Major   Minor   RaidDevice

       0       8       16        -        /dev/sdb
       1       8       32        -        /dev/sdc

damien@damien-desktop:~$ sudo mdadm --detail /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid1
     Array Size : 2930264064 (2794.52 GiB 3000.59 GB)
  Used Dev Size : -1
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           UUID : 43c24e0b:41d2fff1:6a9ceace:54691c3d
    Number   Major   Minor   RaidDevice State
       1       8       16        0      active sync   /dev/sdb
       0       8       32        1      active sync   /dev/sdc


damien@damien-desktop:~$ sudo mdadm --detail /dev/md126p1
/dev/md126p1:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid1
     Array Size : 131072 (128.02 MiB 134.22 MB)
  Used Dev Size : -1
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           UUID : 43c24e0b:41d2fff1:6a9ceace:54691c3d
    Number   Major   Minor   RaidDevice State
       1       8       16        0      active sync   /dev/sdb
       0       8       32        1      active sync   /dev/sdc

damien@damien-desktop:~$ sudo mdadm --detail /dev/md126p2
/dev/md126p2:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid1
     Array Size : 2930130944 (2794.39 GiB 3000.45 GB)
  Used Dev Size : -1
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           UUID : 43c24e0b:41d2fff1:6a9ceace:54691c3d
    Number   Major   Minor   RaidDevice State
       1       8       16        0      active sync   /dev/sdb
       0       8       32        1      active sync   /dev/sdc
```


[U][B]BUG BOOT: STARTING RESYNC
[/B][/U]
**dmesg:**
```
damien@damien-desktop:~$ dmesg | grep md
[    0.827108] systemd-udevd[114]: starting version 204
[    0.844456] md: linear personality registered for level -1
[    0.847866] md: multipath personality registered for level -4
[    0.849476] md: raid0 personality registered for level 0
[    0.852284] md: raid1 personality registered for level 1
[    1.102517] md: raid6 personality registered for level 6
[    1.102518] md: raid5 personality registered for level 5
[    1.102519] md: raid4 personality registered for level 4
[    1.106568] md: raid10 personality registered for level 10
...
[    2.910352] systemd-udevd[410]: starting version 204
[    3.047692] md: bind<sdb>
[    3.251824] md: bind<sdc>
[    3.267043] md: bind<sdc>
[    3.267103] md: bind<sdb>
**[    3.268331] md/raid1:md126: not clean -- starting background reconstruction**
[    3.268332] md/raid1:md126: active with 2 out of 2 mirrors
[    3.268345] md126: detected capacity change from 0 to 3000590401536
[    3.270596]  md126: p1 p2
[    3.304574] md: md126 switched to read-write mode.
[B][    3.304627] md: resync of RAID array md126
[    3.304628] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[    3.304629] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[    3.304630] md: using 128k window, over a total of 2930264196k.[/B]
```

**Details:**
```
damien@damien-desktop:~$ sudo mdadm --detail /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid1
     Array Size : 2930264064 (2794.52 GiB 3000.59 GB)
  Used Dev Size : -1
   Raid Devices : 2
  Total Devices : 2

          State : clean**, resyncing **
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

  Resync Status : 0% complete


           UUID : 43c24e0b:41d2fff1:6a9ceace:54691c3d
    Number   Major   Minor   RaidDevice State
       1       8       16        0      active sync   /dev/sdb
       0       8       32        1      active sync   /dev/sdc
```

**mdstat:**
```
damien@damien-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid1 sdb[1] sdc[0]
      2930264064 blocks super external:/md127/0 [2/2] [UU]
      **[>....................]  resync =  0.1% (3813440/2930264196) finish=409.2min speed=119170K/sec**
      
md127 : inactive sdc[1](S) sdb[0](S)
      4776 blocks super external:imsm
       
unused devices: <none>
```

Please, let me know if you need any extra information ! 

Thanks for your help,
The Setlaz

---

### Post by ilia-3 on 2014-12-02
my problem is 100% like yours, how you decide, please help, already three days I try :)

---

### Post by dam-brouard on 2014-12-02
Hi,

Actually, I haven't solved the problem myself, but I've been following up on Launchpad and it seems someone eventually came up with a fix in the last few weeks!
Check it out: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1320402](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/1320402)
Hopefully, that should get you running !

---

