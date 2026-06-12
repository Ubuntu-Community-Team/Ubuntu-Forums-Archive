---
title: "Split array"
date: 2011-08-28
forum: Server Platforms
---

### Post by jimmydorry on 2011-08-28
Hi, I am a complete linux noob, so please excuse any lack of information provided (but definitely tell me what info you need) or general ignorance. I desperately am in need of help.

My array seems to have degraded and split. I have 1 dieing HDD, and 1 HDD that has formed its own array for what ever reason. If I recall correctly, the array was 7 devices including 1 spare (6active and 1 spare).

The dieing HDD is still in the array, so this HDD that is by itself in its own split off array can't just be formatted and added back in.

Please advise what I should do.

```

root@XXXX:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : inactive sdd1[0](S) sdf1[6](S) sdh1[9](S) sdb1[7](S) sda1[3](S) sde1[8](S)
      8790821700 blocks super 1.2
       
md127 : inactive sdg1[10]
      1465135896 blocks super 1.2
       
unused devices: <none>

``````

root@XXXX:~# cat /etc/mdadm/mdadm.conf
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 28 Aug 2011 18:52:43 +1000
# by mkconf $Id$
ARRAY /dev/md/storage metadata=1.2 UUID=8f635958:2e61d990:6341a97a:8f2680bd name=:storage

``````

root@XXXX:~# mdadm --detail /dev/md126
mdadm: md device /dev/md126 does not appear to be active.

``````

root@XXXX:~# mdadm --manage --run --force /dev/md126
mdadm: failed to run array /dev/md126: Input/output error

``````

root@XXXX:~# mdadm --detail /dev/md126
/dev/md126:
        Version : 1.2
  Creation Time : Sun Mar  7 20:16:38 2010
     Raid Level : raid5
  Used Dev Size : 1465135808 (1397.26 GiB 1500.30 GB)
   Raid Devices : 7
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Sun May 29 13:12:59 2011
          State : active, FAILED, Not Started
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           Name : :storage
           UUID : 8f635958:2e61d990:6341a97a:8f2680bd
         Events : 252461

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       8       8       65        1      active sync   /dev/sde1
       3       8        1        2      active sync   /dev/sda1
       7       8       17        3      active sync   /dev/sdb1
       9       8      113        4      spare rebuilding   /dev/sdh1
       6       8       81        5      active sync   /dev/sdf1
       6       0        0        6      removed

``````

root@XXXX:~# mdadm --detail /dev/md127
/dev/md127:
        Version : 1.2
  Creation Time : Sun Mar  7 20:16:38 2010
     Raid Level : raid5
  Used Dev Size : 1465135808 (1397.26 GiB 1500.30 GB)
   Raid Devices : 7
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Sun May 29 13:12:10 2011
          State : active, FAILED, Not Started
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : :storage
           UUID : 8f635958:2e61d990:6341a97a:8f2680bd
         Events : 252459

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       0        0        1      removed
       2       0        0        2      removed
       3       0        0        3      removed
       4       0        0        4      removed
       5       0        0        5      removed
      10       8       97        6      active sync   /dev/sdg1

```

---

### Post by jimmydorry on 2011-08-28
I'm not quite sure what is happening anymore... I can't call the array by the proper name /dev/md/storage

The only array I can see is missing 1 drive, and is apparently rebuilding.
```

root@XXXX:~# mdadm --detail /dev/md126
/dev/md126:
        Version : 1.2
  Creation Time : Sun Mar  7 20:16:38 2010
     Raid Level : raid5
  Used Dev Size : 1465135808 (1397.26 GiB 1500.30 GB)
   Raid Devices : 7
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Sun May 29 13:12:59 2011
          State : active, FAILED, Not Started
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           Name : :storage
           UUID : 8f635958:2e61d990:6341a97a:8f2680bd
         Events : 252461

    Number   Major   Minor   RaidDevice State
       0       8       49        0      active sync   /dev/sdd1
       8       8       65        1      active sync   /dev/sde1
       3       8        1        2      active sync   /dev/sda1
       7       8       17        3      active sync   /dev/sdb1
       9       8      113        4      spare rebuilding   /dev/sdh1
       6       8       81        5      active sync   /dev/sdf1
       6       0        0        6      removed

```and the 2nd split array seems to have dissapeared, and I can't see that the array shown above is actually doing anything
```

root@XXXX:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : inactive sdd1[0] sdf1[6] sdh1[9] sdb1[7] sda1[3] sde1[8]
      8790821700 blocks super 1.2
       
unused devices: <none>

```

I'm tempted to format the missing drive, and just add it back in as the spare it should be... but not too sure what will happen.

---

### Post by jimmydorry on 2011-08-28
Just found something that should have atleast force started it... but got a new error
```

root@XXXX:~# mdadm --assemble --run --force /dev/md126 /dev/sd[deabhf]1
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted

```

And I know that /dev/sda is the dieing HDD that is "imminently going to fail"

---

### Post by YesWeCan on 2011-08-28
Member rubylaser would be a good expert to contact.

How do you know sda is about to fail? I suppose what you want is to assemble the array with 5 drives sd[bcdefg]1 and one spare sdh1.
Have you tried disconnecting sda?

---

### Post by rubylaser on 2011-08-29
YesWeCan, thanks for the vote of confidence:)  @jimmydorry You've got a mess on your hands there.   Unfortunately, the array is trying to resync incorrectly, so that's not a good thing.  The first step to get this working again is to stop both of the split arrays.

```
mdadm --stop /dev/md126
mdadm --stop /dev/md127
```

Then please post the output of this...
```
mdadm -E /dev/sd[abdefgh]1
```

The above command will display the superblock info for each disk, and will show the Events count to see if the disks are at the same value.  Also, it appears that /dev/sdg is supposed to be part of your functioning array.

Have you verified that all of your disks (other than the one you mention is dying) are healthy via SMART? Please just do the above then post back.

---

