---
title: "mdadm RAID5 problems after power down"
date: 2008-12-30
forum: Server Platforms
---

### Post by MaximB on 2008-12-30
Hello
A few days ago we had a power down in our company and since then one of the raids on one server stopped working.
I didn't made that raid in the first place so I'm not sure how it supposed to work.

Some info about it...

/dev/md2        /dev/sda1 /dev/sdb1 /dev/sdc1 750GB RAID5

/dev/sda1
```
mdadm: No md superblock detected on /dev/sda.
[root@openfiler /]# mdadm -E /dev/sda1
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: No md superblock detected on /dev/sda1.

```

/dev/sdb1
```

[root@openfiler /]# mdadm -E /dev/sdb1
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0f24b3df:9bfd7f61:3ab0909e:3f0b96ed
  Creation Time : Tue Dec 11 00:55:32 2007
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2

    Update Time : Wed Dec 24 04:14:28 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8a94083e - correct
         Events : 0.3134863

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed

```

/dev/sdc1
```
[root@openfiler /]# mdadm -E /dev/sdc1
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 0f24b3df:9bfd7f61:3ab0909e:3f0b96ed
  Creation Time : Tue Dec 11 00:55:32 2007
     Raid Level : raid5
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2

    Update Time : Wed Dec 24 04:14:28 2008
          State : active
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : 8a940857 - correct
         Events : 0.3134863

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8        1        0      active sync
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed

```

/dev/md2
```
[root@openfiler /]# mdadm -D /dev/md2
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: md device /dev/md2 does not appear to be active.

```

I suspect that /dev/sda1 was damaged but I cannot know that for sure, I can still get info about it but it doesn't tell me if there is anything wrong with that device.
I only use the built-in commands as I cannot add more programs to that specific server.

```
[root@openfiler /]# mdadm -As /dev/md2 /dev/sdb1 /dev/sdc1
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
mdadm: /dev/md2 assembled from 1 drive and 1 spare - not enough to start the array.
mdadm: /dev/sdb1 not identified in config file.
mdadm: /dev/sdc1 not identified in config file.

```

The other raids seems to work fine.

How can I repair that RAID without losing any information ?

---

### Post by MaximB on 2008-12-30
After I did :

mdadm --verbose --assemble --force /dev/md2 /dev/sdc1 /dev/sdb1 /dev/sda

I've managed to recover all the data and save the RAID !

---

### Post by fjgaude on 2008-12-30
Bravo, you did it! Great to have things work out correctly, eh? We learn something new everyday.

---

### Post by joeinbend on 2008-12-30
Sounds like you made it through! My question is, if you reboot, does the RAID come back online automatically? Also i notice in one of your outputs it says you have a failed disk (probably due to a disk failure, and the hot-spare resync'ed on it's own). If you want some help with some preventitve measures, post your mdadm.conf file here, and also the output of "sudo mdadm --detail /dev/md2

---

### Post by MaximB on 2008-12-31
Well, the RAID does come back automatically on reboot - at least until now ;)

mdadm.conf - I've edited this file (added the DEVICE section and md2 ARRAY - originally it was without /dev/sdx and worked fine - just messed it up a little bit when I tried to find what's wrong.

```
[root@openfiler images]# cat /etc/mdadm.conf

#
# PLEASE DO NOT MODIFY THIS CONFIGURATION FILE!
#   This configuration file was auto-generated
#   by Openfiler. Please do not modify it.
#
# Generated at: Tue Dec 11 3:16:56 IST 2007
#

DEVICE partitions
DEVICE          /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sdd2 /dev/sdd3 /dev/sde1 /dev/sde2 /dev/sde3
ARRAY /dev/md2  devices=/dev/sdb1,/dev/sdc1
ARRAY /dev/md1
ARRAY /dev/md0
PROGRAM /opt/openfiler/bin/mdalert

```

/dev/md2
```

[root@openfiler images]# mdadm --detail /dev/md2
mdadm: ARRAY line /dev/md1 has no identity information.
mdadm: ARRAY line /dev/md0 has no identity information.
/dev/md2:
        Version : 00.90.03
  Creation Time : Tue Dec 11 00:55:32 2007
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Wed Dec 31 08:22:09 2008
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 0f24b3df:9bfd7f61:3ab0909e:3f0b96ed
         Events : 0.3146276

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed

       3       8       33        3      active sync   /dev/sdc1

```

I still cannot understand what and where is the "identify information" and if it's absent - why it's still works fine ?

The same command that "saved" my RAID without the "force" option - didn't work.
I feared that "force" might delete all data and mess up the RAID completely - but it didn't happen.

---

### Post by fjgaude on 2008-12-31
The --froce commands worked likely because it used only the array UUID to assemble, ignoring the somewhat bad mdadm.conf file. This file is not the usual believe me.

I would suggest deleting it, removing mdadm, re-booting, re-installing mdadm and then running this command:

```
sudo --assemble --scan
```

That way a new mdadm.conf file will be auto created by mdadm and you will have a correct file.

---

### Post by joeinbend on 2008-12-31
I agree with fjgaude -- However if you are not comfortable with removing and re-adding mdadm (I dont blame you if this is a production server), What I would do is, for your arrays in mdadm.conf, get rid of the /dev/sd** definitions, and replace it with just the UUID=. So for example, for your md2 array, i would delete that line, and put this in its' place:

ARRAY /dev/md0 UUID=0f24b3df:9bfd7f61:3ab0909e:3f0b96ed

That will tell mdadm when it starts up, to look for any device/partition defined in your DEVICE line, containing the UUID superblock, to assemble.

My personal preference, others may disagree, is if you ever rebuld that RAID entirely, to not use partitions, use whole disks. That would allow you to delete the line "DEVICE partitions", and also you can replace the long line defining each partition (your DEVICE  /dev/sd.... line), with simply: DEVICE /dev/sd*. In a RAID5, there's no reason for using partitions, when the whole structure is based off block-level data anyway. Again, others may disagree, and I await your response :)

---

