---
title: "Raid 5 missing"
date: 2017-11-10
forum: Server Platforms
---

### Post by daniele29 on 2017-11-10
Hello everyone
First of all: I'm sorry for my English, but I do not talk him badly, and I have to use the google translator.
"born and raised" with a windows background, I recently decided to build a NAS with Ubuntu 14.04 server os in a machine such as: 
Asus P8P67EVO m/b, Intel i7 2600k CPU, Corsair 16Gb 1.600Mhz RAM, Enermax Infiniti 720W PSU, 14 Western Digital WD30EFRX HDD, 8 managed by two Startech SATA controllers, while the remaining 6 from native controllers, 1 SSD Corsair ForceGT 120Gb (Windows), 1 SSD Samsung 850 EVO 256Gb (Ubuntu).
The need for the dual system disk is due to the fact that I have not been able to find the system to permanently delete the Ubuntu login window and consequently the decision to use WIndows 8.1 Pro for NAS management.
Recently, during the final data transfer on Windows drives, Ubuntu RAID 5 has disappeared ...
Since I'm a bad Ubunter, I'm no longer able to make him back.
All drives seem ok.
I've done so many tests, but nothing.
Inside him there are still 2Tb of data, and I've finished the house walls where I slammed my head.
Unfortunately, the Italian community has not been able to help me.
Any good soul can give me a hand telling him to me to make such tests in order to understand where is the problem?
Thanks in advance.
Daniele

---

### Post by darkod on 2017-11-10
Log into the ubuntu server and post us the output of this command:
```
sudo blkid
cat /etc/mdadm/mdadm.conf
```

That is to start with.

---

### Post by daniele29 on 2017-11-10
Hello darkod
Thank you for your answer.
Output command sudo blkid:

```
/ dev / sda1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "e875c057-078c-39eb-145d-a265f5b6f49e" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sdb1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "bd0327c4-84d7-52c3-c01f-1f22801f0b58" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sdc1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "61db0909-21b7-dd78-38f5-4e2a4a41dd73" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sdd1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "609b425c-8b4c-fa37-76a2-f7dbb54e7c6d" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sde1: UUID = "6B6E-3547" TYPE = "vfat"
/ dev / sde2: UUID = "3298b510-4501-47a2-acbd-9fef095e0227" TYPE = "ext4"
/ dev / sde3: UUID = "2f54a1de-4aa9-4303-815b-52ce5395c8d7" TYPE = "swap"
/ dev / sdf1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "ee63ac40-5f64-3a7b-545b-2360f7b9584d" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sdg1: UUID = "04bfdfa2-36fd-9f17-2095-a8748fd6bde6" UUID_SUB =  "306b21c7-c074-eb9f-b3b4-3e2dae17c68e" LABEL = "NAS3200: 1" TYPE =  "linux_raid_member"
/ dev / sdh1: LABEL = "DATA_3" UUID = "F88A0C788A0C35A2" TYPE = "ntfs"
```

Output command cat /etc/mdadm/mdadm.conf:

```
# mdadm.conf
#
# Please refer to mdadm.conf (5) for information about this file.
#

# by default (built-in), scan all partitions (/ proc / partitions) and all
# containers for MD superblocks. Alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner = root group = disk mode = 0660 auto = yes

# automatically tags new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY / dev / md / 1 metadata = 1.2 UUID = 04bfdfa2: 36fd9f17: 2095a874: 8fd6bde6 name = NAS3200: 1

# This file was auto-generated on Fri, 01 Aug 2017 18:11:07 +0200
# by mkconf $ Id $
sudo mkdir -p / mnt / md0
```

Small specification:
SDE is the system disk, SDH is a 1Tb Wetern Digital disc I use for Windows and Ubuntu interchange files

---

### Post by darkod on 2017-11-10
When posting output you can use CODE tags for better readability.

What if you try to autoassemble the array with:
```
sudo mdadm --verbose --assemble --scan
```

If that fails please post the whole output or at least the lines with the errors that it shows you.

Also if it fails, give us the output of:
```
sudo mdadm --examine /dev/sd[abcdfg]1
```

But I see only 6 disks members of the raid. Is that correct or you had more? Because you say you have 14 disks and many are missing in blkid. Looks like the Startech controllers might not be working???

---

### Post by daniele29 on 2017-11-10
I finally understood how to use the code tag ...
You are right, I forgot to specify that 8 disks are managed by a Windows raid 5 and they are not currently connected.
The remaining 6, the ones you can see listed by the Ubuntu raid 5.
Tomorrow I give you the outputs of the two commands you told me to use
Greetings.
Daniele

Good morning
Output command sudo mdadm --verbose --assemble --scan```
mdadm: looking for devices for /dev/md/1
mdadm: no RAID superblock on /dev/sdh1
mdadm: no RAID superblock on /dev/sdh
mdadm: /dev/sdg1 is busy - skipping
mdadm: no RAID superblock on /dev/sdg
mdadm: /dev/sdf1 is busy - skipping
mdadm: no RAID superblock on /dev/sdf
mdadm: no RAID superblock on /dev/sde3
mdadm: no RAID superblock on /dev/sde2
mdadm: no RAID superblock on /dev/sde1
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 is busy - skipping
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc1 is busy - skipping
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 is busy - skipping
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sda1 is busy - skipping
mdadm: no RAID superblock on /dev/sda
mdadm: no RAID superblock on /dev/ram15
mdadm: no RAID superblock on /dev/ram14
mdadm: no RAID superblock on /dev/ram13
mdadm: no RAID superblock on /dev/ram12
mdadm: no RAID superblock on /dev/ram11
mdadm: no RAID superblock on /dev/ram10
mdadm: no RAID superblock on /dev/ram9
mdadm: no RAID superblock on /dev/ram8
mdadm: no RAID superblock on /dev/ram7
mdadm: no RAID superblock on /dev/ram6
mdadm: no RAID superblock on /dev/ram5
mdadm: no RAID superblock on /dev/ram4
mdadm: no RAID superblock on /dev/ram3
mdadm: no RAID superblock on /dev/ram2
mdadm: no RAID superblock on /dev/ram1
mdadm: no RAID superblock on /dev/ram0

```

For completeness, even though the first command gave an output, I also ran 
sudo mdadm --examine /dev/sd[abcdfg]1

```
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e875c057:078c39eb:145da265:f5b6f49e

    Update Time : Fri Sep 22 23:18:49 2017
       Checksum : b22f2a82 - correct
         Events : 17171

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA.. ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : bd0327c4:84d752c3:c01f1f22:801f0b58

    Update Time : Fri Sep 22 23:18:49 2017
       Checksum : 6c422f0a - correct
         Events : 17171

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA.. ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 61db0909:21b7dd78:38f54e2a:4a41dd73

    Update Time : Fri Sep 22 22:27:50 2017
       Checksum : 8ab6d1a0 - correct
         Events : 17166

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 609b425c:8b4cfa37:76a2f7db:b54e7c6d

    Update Time : Fri Sep 22 22:27:50 2017
       Checksum : 4853e1b2 - correct
         Events : 17166

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AAAAAA ('A' == active, '.' == missing)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : ee63ac40:5f643a7b:545b2360:f7b9584d

    Update Time : Fri Sep 22 23:18:49 2017
       Checksum : d400f224 - correct
         Events : 17171

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA.. ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 04bfdfa2:36fd9f17:2095a874:8fd6bde6
           Name : NAS3200:1
  Creation Time : Sun Jul  3 21:59:13 2016
     Raid Level : raid5
   Raid Devices : 6

 Avail Dev Size : 5860265887 (2794.39 GiB 3000.46 GB)
     Array Size : 14650662400 (13971.96 GiB 15002.28 GB)
  Used Dev Size : 5860264960 (2794.39 GiB 3000.46 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 306b21c7:c074eb9f:b3b43e2d:ae17c68e

    Update Time : Fri Sep 22 23:18:49 2017
       Checksum : 8dafc0dc - correct
         Events : 17171

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA.. ('A' == active, '.' == missing)
```
Greetings
Daniele

---

### Post by darkod on 2017-11-11
Hmmm, the volumes are busy, looks like it is assembled (or trying to).

Also the --examine shows that 4x disks have a number of events 17171 but 2x of them have 17166. That makes them little out of date but you should be able to force them to assemble.

Check if there is any array active first:
```
cat /proc/mdstat
```

If there is you have to stop it with (using the correct devic name /dev/mdX):
```
sudo mdadm --stop /dev/mdX
```

Then you can try forcing the assemble with using correct disk order that --examine gives you:
```
sudo mdadm --verbose --assemble --force /dev/md1 /dev/sd[bagfdc]1
```

See if that helps...

---

### Post by daniele29 on 2017-11-11
Hi darkod
cat /proc/mdstat output 
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sdg1[2](S) sdd1[5](S) sdf1[4](S) sda1[1](S) sdb1[0](S) sdc1[6](S)
      17580797661 blocks super 1.2

```

sudo mdadm --stop /dev/mdX output
```
mdadm: stopped /dev/md1
```

sudo mdadm --verbose --assemble --force /dev/md1 /dev/sd[bagfdc]1 output
```
sudo mdadm --verbose --assemble --force /dev/md1 /dev/sdb1 /dev/sda1 /dev/sdg1 /dev/sdf1 /dev/sdd1 /dev/sdc1
mdadm: Unknown keyword sudo
mdadm: looking for devices for /dev/md1
mdadm: /dev/sdb1 is identified as a member of /dev/md1, slot 0.
mdadm: /dev/sda1 is identified as a member of /dev/md1, slot 1.
mdadm: /dev/sdg1 is identified as a member of /dev/md1, slot 2.
mdadm: /dev/sdf1 is identified as a member of /dev/md1, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md1, slot 4.
mdadm: /dev/sdc1 is identified as a member of /dev/md1, slot 5.
mdadm: forcing event count in /dev/sdd1(4) from 17166 upto 17171
mdadm: forcing event count in /dev/sdc1(5) from 17166 upto 17171
mdadm: clearing FAULTY flag for device 4 in /dev/md1 for /dev/sdd1
mdadm: clearing FAULTY flag for device 5 in /dev/md1 for /dev/sdc1
mdadm: Marking array /dev/md1 as 'clean'
mdadm: added /dev/sda1 to /dev/md1 as 1
mdadm: added /dev/sdg1 to /dev/md1 as 2
mdadm: added /dev/sdf1 to /dev/md1 as 3
mdadm: added /dev/sdd1 to /dev/md1 as 4
mdadm: added /dev/sdc1 to /dev/md1 as 5
mdadm: added /dev/sdb1 to /dev/md1 as 0
mdadm: /dev/md1 has been started with 6 drives.

```

Yeah!!!!!
Great darkod, the raid is on the road again!!!!
But what happened?
Is it possible that the raid has disappeared due to a series of power losses in my area ??
Thanks so much darkod !!!!
Now I do a restart test to make sure that the raid re-runs regularly.
Greetings.
Daniele

Ok, the raid reappears regularly.
How do I do to write [solved]?
Thank you very much darkod !!

Found  ;)

---

