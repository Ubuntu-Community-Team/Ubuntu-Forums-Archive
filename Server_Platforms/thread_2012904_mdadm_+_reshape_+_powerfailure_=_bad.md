---
title: "mdadm + reshape + powerfailure = bad"
date: 2012-06-30
forum: Server Platforms
---

### Post by bnut on 2012-06-30
I was doing this on Oneiric

mdadm --grow /dev/md0 --level=6 --raid-devices=6 --backup-file /md0.backup

to this  
ARRAY /dev/md0 metadata=1.2 spares=1 name=server:0 UUID=c64d8bc1:fe26faa5:c9f6538f:8cb82480


I got to something like 6 and a half days in (it was at 96% when I checked a few hours earlier) and then had a power failure.


When power was restored, the array did not come back up.

me@server:[~]cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[1] sdf1[2] sdg1[3] sdh1[4] sdd1[5] sdb1[0]
      11603871747 blocks super 1.2

unused devices: <none>

```me@server:[~]mdadm --detail --scan
```
ARRAY /dev/md0 metadata=1.2 spares=1 name=server:0 UUID=c64d8bc1:fe26faa5:c9f6538f:8cb82480

me@server:[/etc/mdadm]cat mdadm.conf
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR me@mydomain.net
ARRAY /dev/md0 metadata=1.2 UUID=c64d8bc1:fe26faa5:c9f6538f:8cb82480 name=server:0

```me@server:[~]mdadm --detail /dev/md0
```
/dev/md0:
        Version : 1.2
  Creation Time : Thu May 24 12:06:26 2012
     Raid Level : raid6
  Used Dev Size : 1933978112 (1844.39 GiB 1980.39 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Fri Jun 29 20:38:02 2012
          State : active, degraded, Not Started
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric-6
     Chunk Size : 512K

     New Layout : left-symmetric

           Name : server:0  (local to host server)
           UUID : c64d8bc1:fe26faa5:c9f6538f:8cb82480
         Events : 1904783

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       65        1      active sync   /dev/sde1
       2       8       81        2      active sync   /dev/sdf1
       3       8       97        3      active sync   /dev/sdg1
       4       8      113        4      active sync   /dev/sdh1
       5       8       49        5      spare rebuilding   /dev/sdd1


```me@server:[/etc/mdadm]mdadm --misc --examine /dev/sd[bdefgh]1 | egrep 'dev|Update|Role|State|Chunk Size'
```
/dev/sdb1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 0
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdd1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sde1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 1
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdf1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 2
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdg1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 3
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdh1:
          State : clean
    Update Time : Fri Jun 29 20:38:02 2012
     Chunk Size : 512K
   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing)
```After several hours of troublshooting I did a 

mdadm --stop /dev/md0

and then tried to reassemble the array using 

me@server:[/etc/mdadm]mdadm --create --assume-clean --verbose /dev/md0 --chunk=512 --level=6 --raid-devices=6 /dev/sd[befghd]1
```
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Thu May 24 12:06:26 2012
mdadm: size set to 1933978112K
Continue creating array?
```

Now the array is coming up, but the UUID has changed and it is coming up md127


me@server:[~]mdadm --detail /dev/md127
```
/dev/md127:
        Version : 1.2
  Creation Time : Fri Jun 29 22:51:25 2012
     Raid Level : raid6
     Array Size : 7735912448 (7377.54 GiB 7921.57 GB)
  Used Dev Size : 1933978112 (1844.39 GiB 1980.39 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Fri Jun 29 23:07:42 2012
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : server:0  (local to host server)
           UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1
       2       8       65        2      active sync   /dev/sde1
       3       8       81        3      active sync   /dev/sdf1
       4       8       97        4      active sync   /dev/sdg1
       5       8      113        5      active sync   /dev/sdh1
```
UUID on the partitions has changed as well

me@server:[~]mdadm --misc --examine /dev/sd[bdefgh]1 | grep Array\ UUID
```
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
     Array UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
```
There is no backup.

Is the array recoverable?

---

### Post by ian dobson on 2012-06-30
Hi,

As the array is degraded ubuntu won't start it. So maybe try to manually start the array mdadm -As /dev/mdXXX

Try recreating your mdadm.conf file then updating your inital ram fs (Used by linux during the boot process, before the full root file system is available) with update-initramfs -u -k all

I know this may not sound too nice but having a 8Tb array and no backup is crazy.

Regards
Ian Dobson

---

### Post by bnut on 2012-06-30
same.  unable to mount the drive.


me@server:[~]cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdh1[5] sde1[2] sdg1[4] sdd1[1] sdf1[3] sdb1[0]
      7735912448 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/6] [UUUUUU]

unused devices: <none>
```me@server:[~]mount /RAID
```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```from dmesg
```

[  152.735443] EXT4-fs (md0): Couldn't mount because of unsupported optional features (7fd00001)

```

---

### Post by bnut on 2012-06-30
It looks like it's being assembled in the wrong order [bhcdef] instead of [befghd] as specified.

me@server:[~]mdadm --detail /dev/md0
```

/dev/md0:
        Version : 1.2
  Creation Time : Fri Jun 29 22:51:25 2012
     Raid Level : raid6
     Array Size : 7735912448 (7377.54 GiB 7921.57 GB)
  Used Dev Size : 1933978112 (1844.39 GiB 1980.39 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Sat Jun 30 00:26:14 2012
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : server:0  (local to host server)
           UUID : d74f392c:f69a96d4:927668fd:91bc3f4a
         Events : 2

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8      113        1      active sync   /dev/sdh1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
```

---

### Post by bnut on 2012-07-01
Based on my last finding (and a good night's sleep) I was able to restore the array.

It seems that using regex brackets in the create does not actually define the correct order.  By issuing an mdadm --stop /dev/md0 and then the following command the raid came back with the data intact (as well as the original UUID).

me@server:[~]mdadm --create --verbose /dev/md0 --uuid=c64d8bc1:fe26faa5:c9f6538f:8cb82480 --chunk=512 --level=6 --raid-devices=6 /dev/sdb1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdd1
```
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: size set to 1933978112K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```

You can see based on my previous paste that the order here is different.  Additionally, I removed the assume-clean flag, so it's doing a quick resync, but the speed is high.

me@server:[~]cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdd1[5] sdh1[4] sdg1[3] sdf1[2] sde1[1] sdb1[0]
      7735912448 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      [>....................]  resync =  1.0% (20297232/1933978112) finish=1899.1min speed=16793K/sec

unused devices: <none>
```

---

### Post by rubylaser on 2012-07-01
> **bnut said:**
> Based on my last finding (and a good night's sleep) I was able to restore the array.

It seems that using regex brackets in the create does not actually define the correct order.  By issuing an mdadm --stop /dev/md0 and then the following command the raid came back with the data intact (as well as the original UUID).

me@server:[~]mdadm --create --verbose /dev/md0 --uuid=c64d8bc1:fe26faa5:c9f6538f:8cb82480 --chunk=512 --level=6 --raid-devices=6 /dev/sdb1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdd1
```
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid6 devices=6 ctime=Fri Jun 29 22:51:25 2012
mdadm: size set to 1933978112K
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
```

You can see based on my previous paste that the order here is different.  Additionally, **I removed the assume-clean flag**, so it's doing a quick resync, but the speed is high.

me@server:[~]cat /proc/mdstat
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdd1[5] sdh1[4] sdg1[3] sdf1[2] sde1[1] sdb1[0]
      7735912448 blocks super 1.2 level 6, 512k chunk, algorithm 2 [6/6] [UUUUUU]
      [>....................]  resync =  1.0% (20297232/1933978112) finish=1899.1min speed=16793K/sec

unused devices: <none>
```

I hope your order is correct, or removing the assume-clean flag just hosed any chance of data recovery.  If you use the assume-clean flag you can try to assemble the array in all possible orders without risking you data.  As soon as you remove it, if the order isn't exactly the same as before, you will break your filesystem and as result, your data.  I hope this works out well for you.

---

### Post by bnut on 2012-07-01
> **rubylaser said:**
> I hope your order is correct, or removing the assume-clean flag just hosed any chance of data recovery.  If you use the assume-clean flag you can try to assemble the array in all possible orders without risking you data.  As soon as you remove it, if the order isn't exactly the same as before, you will break your filesystem and as result, your data.  I hope this works out well for you.


good to know. 

As you can see from one of my original commands, I was very careful to get the order correct but I was not aware of the risk you identified.

---

### Post by ziggo0 on 2012-07-01
> **bnut said:**
> good to know. 

As you can see from one of my original commands, I was very careful to get the order correct but I was not aware of the risk you identified.

It's beyond important - I recently lost a 12TB raid6 array due to conflicting mdadm superblock versions, zeroing the superblocks and re-creating the array in the wrong order. Needless to say everything is well documented now.

You should consider investing in a UPS. When I went from a 6 to 8 disk raid6 array I was very worried about power loss. I couldn't bare to lose what was on the array so I went to Staples and bought a 60 ~ 70$ 350w APC unit. It's worked flawlessly since then and has provided more than enough power to keep my machine running for 20 minutes before it needs to shut it down (i5 750, 16gb, 10x 3.5hdd and 4x 2.5hdd). Long story short at the end of the first re-shaping - probably 93% or so the power did go out due to someone plugging in one too many high powered appliances into that circuit...needless to say my heart sank heating that APC beep from across the house. Machine shut down...came back when power was restored and the reshaping picked up from where it left off.

---

