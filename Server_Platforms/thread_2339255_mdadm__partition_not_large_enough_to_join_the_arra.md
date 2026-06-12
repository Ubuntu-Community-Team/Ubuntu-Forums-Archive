---
title: "mdadm : partition not large enough to join the array"
date: 2016-10-06
forum: Server Platforms
---

### Post by MrEgg on 2016-10-06
Hello,

I'm running into a bit of a problem I cannot solve, and I do not want to mess things up and lose my data.

I have an Ubuntu 16.04 backup server, with 5 4TB drives set up in a raid5 array. One drive fell out of the array, which I have replaced with the same make and model.
```
**sudo mdadm --detail /dev/md127p2**
/dev/md127p2:
        Version : 1.2
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
     Array Size : 15624387584 (14900.58 GiB 15999.37 GB)
  Used Dev Size : unknown
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Oct  6 15:54:35 2016
          State : clean, degraded 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : RAID
           UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
         Events : 67184

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2
       4       0        0        4      removed
       4       8       66        3      active sync   /dev/sde2
       5       8       34        4      active sync   /dev/sdc2

```

I have copied the partition of sde to sdf with this command:
```
sudo sgdisk --backup=table /dev/sde
sudo sgdisk --load-backup=table /dev/sdf
sudo sgdisk -G /dev/sdf
```

I can see that both drives seem to be of identical size:
```
**sudo gdisk -l /dev/sde**
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sde: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4661B8C5-83A0-4F95-9894-4A813E93FAE1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  0700  primary
   2            4096      7814037134   3.6 TiB     FD00  RAID: RAID

**sudo gdisk -l /dev/sdf**
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdf: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): F29B6BBA-03BA-4911-8E43-D3034F76DB3A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048            4095   1024.0 KiB  0700  primary
   2            4096      7814037134   3.6 TiB     FD00  RAID: RAID

```

However, as I try to add sdf2 back to the raid5, mdadm is telling me it is not large enough to join the array:
```
**sudo mdadm --manage /dev/md127p2 --add /dev/sdf2**
mdadm: /dev/sdf2 not large enough to join array
```

Any help would be greatly appreciated. I cannot afford to lose the data on the array.
Thanks

---

### Post by darkod on 2016-10-06
The array is md127p2 or md127? Usually p# denotes partitions but a mdadm array is not partitioned further.

---

### Post by MrEgg on 2016-10-07
md127p2 is mounted -- the reason for p1 and p2 is that there used to be 2 raids on this array, the first one of which has been removed in favour of the second.

---

### Post by frostschutz on 2016-10-07
Can you show a bit more about your situation.

```

cat /proc/mdstat
sudo blockdev --getsize64 /dev/sd[abcdef]2
sudo mdadm --detail /dev/md*
sudo mdadm --examine /dev/sd*

```

---

### Post by darkod on 2016-10-07
Yes, please post the output of those commands. Plus:
```
cat /etc/mdadm/mdadm.conf
sudo blkid
```
I'm still confused about your setup. You said you had "two raids on the array" but in standard mdadm use a raid an array are synonyms. One md device is one raid array. You don't have multiple raids on the array.
But if you are talking about some kind of HW raid or fakeraid, now that's another story.

---

### Post by MrEgg on 2016-10-07
> I'm still confused about your setup. You said you had "two raids on the array" but in standard mdadm use a raid an array are synonyms. One md device is one raid array. You don't have multiple raids on the array.

I'm sorry I sounded confusing. Originally, I had partitioned all 5 drives with 2 partitions (hence having sd[abcef]1 and sd[abcef]2) and then created two differents raid5 (hence having md127p1 and md127p2). So what I meant to say a bit awkwardly with "two raids on the array" was : two raid5 on my array of 5 drives.

```
**cat /etc/mdadm/mdadm.conf**
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/RAID  metadata=1.2 UUID=9c4bd22c:7c7adaee:8f89ea36:789dea5c name=RAID
ARRAY /dev/md/0  metadata=1.2 UUID=f2f74d4b:6de8dbba:d245ea72:811ccc5a name=nt-backup:0

# This file was auto-generated on Wed, 05 Oct 2016 17:13:29 +0200
# by mkconf $Id$
ARRAY /dev/md/RAID metadata=1.2 name=RAID UUID=9c4bd22c:7c7adaee:8f89ea36:789dea5c


**sudo blkid**  <--- Please note sdd is not part of the array
/dev/sda1: PARTLABEL="primary" PARTUUID="ec7c9ac2-7320-4192-a1ed-5dfc5459e912"
/dev/sda2: UUID="9c4bd22c-7c7a-daee-8f89-ea36789dea5c" UUID_SUB="69094822-e2f6-5448-df92-a579ef0c0696" LABEL="RAID" TYPE="linux_raid_member" PARTLABEL="RAID: RAID" PARTUUID="52d6aa13-9133-448f-a7dc-4e486f7873e6"
/dev/md127: PTUUID="4113a005-45df-4061-a513-282e5c3b36a4" PTTYPE="gpt"
/dev/md127p1: PARTLABEL="primary" PARTUUID="dcfa5d74-5850-4d99-af12-067d6b2ce16d"
/dev/md127p2: LABEL="BACKUP" UUID="6a48d644-91cf-4707-a7f2-777df034f3c9" TYPE="ext4" PARTLABEL="primary" PARTUUID="78a51d7f-5177-462f-9342-043eb2bc1c41"
/dev/sdb1: PARTLABEL="primary" PARTUUID="285f3a76-ef75-4dba-95f9-8a88a7c56abc"
/dev/sdb2: UUID="9c4bd22c-7c7a-daee-8f89-ea36789dea5c" UUID_SUB="f3599869-9de6-8c77-9d46-ba908971cc08" LABEL="RAID" TYPE="linux_raid_member" PARTLABEL="RAID: RAID" PARTUUID="e4124305-8cdd-41d0-85b5-e54538915bac"
/dev/sdc1: PARTLABEL="primary" PARTUUID="e3c5de36-bc68-4cac-bb6b-3955b5ac7e3e"
/dev/sdc2: UUID="9c4bd22c-7c7a-daee-8f89-ea36789dea5c" UUID_SUB="fcf053e9-08df-8aee-5c76-85141a8df032" LABEL="RAID" TYPE="linux_raid_member" PARTLABEL="RAID: RAID" PARTUUID="be52cce0-086a-4cec-910e-e356f02c9fa2"
[I]/dev/sdd1: UUID="cc9d9e25-7393-4c50-afbd-908be2aea351" TYPE="ext4" PARTUUID="0533a25a-01"
/dev/sdd2: UUID="54a66288-7d04-4eb8-b2bd-23613575f9aa" TYPE="ext4" PARTUUID="0533a25a-02"
/dev/sdd5: UUID="7ecfacf0-41b4-491f-9857-94ced864ca54" TYPE="swap" PARTUUID="0533a25a-05"[/I]
/dev/sde1: PARTLABEL="primary" PARTUUID="669f54be-ad3e-4c74-ae8c-6de9fff9480b"
/dev/sde2: UUID="9c4bd22c-7c7a-daee-8f89-ea36789dea5c" UUID_SUB="1a842961-08fa-1e80-7df4-7c35e9394550" LABEL="RAID" TYPE="linux_raid_member" PARTLABEL="RAID: RAID" PARTUUID="0e1b0dd4-5492-41af-8691-5f6227595ef2"
/dev/sdf1: PARTLABEL="primary" PARTUUID="10a354e2-ee84-4a40-a142-fa85c830f8ba"
/dev/sdf2: PARTLABEL="RAID: RAID" PARTUUID="e283d5b2-7139-4eee-8596-d93ccd9c5beb"


**cat /proc/mdstat**
Personalities : [raid6] [raid5] [raid4] [linear] [multipath] [raid0] [raid1] [raid10] 
md127 : active raid5 sde2[4] sdc2[5] sdb2[0] sda2[1]
      15627540480 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/4] [UU_UU]
      bitmap: 14/30 pages [56KB], 65536KB chunk

unused devices: <none>

**sudo blockdev --getsize64 /dev/sd[abcef]2** <--- Please note I am leaving sdd out, as it is not a member of the array
4000784915968
4000784915968
4000784915968
4000784915968
4000784915968
[B]
sudo mdadm --detail /dev/md*[/B]
mdadm: /dev/md does not appear to be an md device
/dev/md127:
        Version : 1.2
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
     Array Size : 15627540480 (14903.58 GiB 16002.60 GB)
  Used Dev Size : 3906885120 (3725.90 GiB 4000.65 GB)
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Oct  6 22:23:14 2016
          State : clean, degraded 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : RAID
           UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
         Events : 67492

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2
       4       0        0        4      removed
       4       8       66        3      active sync   /dev/sde2
       5       8       34        4      active sync   /dev/sdc2
/dev/md127p1:
        Version : 1.2
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
     Array Size : 1536
  Used Dev Size : -1
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Oct  6 22:23:14 2016
          State : clean, degraded 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : RAID
           UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
         Events : 67492

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2
       4       0        0        4      removed
       4       8       66        3      active sync   /dev/sde2
       5       8       34        4      active sync   /dev/sdc2
/dev/md127p2:
        Version : 1.2
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
     Array Size : 15624387584 (14900.58 GiB 15999.37 GB)
  Used Dev Size : unknown
   Raid Devices : 5
  Total Devices : 4
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Thu Oct  6 22:23:14 2016
          State : clean, degraded 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : RAID
           UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
         Events : 67492

    Number   Major   Minor   RaidDevice State
       0       8       18        0      active sync   /dev/sdb2
       1       8        2        1      active sync   /dev/sda2
       4       0        0        4      removed
       4       8       66        3      active sync   /dev/sde2
       5       8       34        4      active sync   /dev/sdc2

[B]
sudo mdadm --examine /dev/sd*[/B]
/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
           Name : RAID
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 15627540480 (14903.58 GiB 16002.60 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 258048 sectors
   Super Offset : 8 sectors
   Unused Space : before=257968 sectors, after=4751 sectors
          State : clean
    Device UUID : 69094822:e2f65448:df92a579:ef0c0696

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Oct  6 22:23:14 2016
       Checksum : ac398aad - correct
         Events : 67492

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdb1.
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
           Name : RAID
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 15627540480 (14903.58 GiB 16002.60 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 258048 sectors
   Super Offset : 8 sectors
   Unused Space : before=257968 sectors, after=4751 sectors
          State : clean
    Device UUID : f3599869:9de68c77:9d46ba90:8971cc08

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Oct  6 22:23:14 2016
       Checksum : ac9ce349 - correct
         Events : 67492

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA.AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdc1.
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
           Name : RAID
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 15627540480 (14903.58 GiB 16002.60 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 258048 sectors
   Super Offset : 8 sectors
   Unused Space : before=257960 sectors, after=4751 sectors
          State : clean
    Device UUID : fcf053e9:08df8aee:5c768514:1a8df032

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Oct  6 22:23:14 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 514dbe5b - correct
         Events : 67492

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : AA.AA ('A' == active, '.' == missing, 'R' == replacing)
[I]/dev/sdd:  <--- not part of the array
   MBR Magic : aa55
Partition[0] :    119998047 sectors at         2048 (type 83)
Partition[1] :     60000256 sectors at    120000512 (type 83)
Partition[2] :     54437890 sectors at    180002814 (type 05)
mdadm: No md superblock detected on /dev/sdd1.
mdadm: No md superblock detected on /dev/sdd2.
/dev/sdd3:
   MBR Magic : aa55
Partition[0] :     54437888 sectors at            2 (type 82)[/I]
mdadm: No md superblock detected on /dev/sdd5.
/dev/sde:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sde1.
/dev/sde2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 9c4bd22c:7c7adaee:8f89ea36:789dea5c
           Name : RAID
  Creation Time : Thu Jan  9 11:53:58 2014
     Raid Level : raid5
   Raid Devices : 5

 Avail Dev Size : 7813770895 (3725.90 GiB 4000.65 GB)
     Array Size : 15627540480 (14903.58 GiB 16002.60 GB)
  Used Dev Size : 7813770240 (3725.90 GiB 4000.65 GB)
    Data Offset : 258048 sectors
   Super Offset : 8 sectors
   Unused Space : before=257968 sectors, after=4751 sectors
          State : clean
    Device UUID : 1a842961:08fa1e80:7df47c35:e9394550

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu Oct  6 22:23:14 2016
       Checksum : 98fb971f - correct
         Events : 67492

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AA.AA ('A' == active, '.' == missing, 'R' == replacing)
/dev/sdf:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : f2f74d4b:6de8dbba:d245ea72:811ccc5a
           Name : nt-backup:0  (local to host nt-backup)
  Creation Time : Fri Sep 23 13:17:13 2016
     Raid Level : raid6
   Raid Devices : 5

 Avail Dev Size : 7813772943 (3725.90 GiB 4000.65 GB)
     Array Size : 11720658432 (11177.69 GiB 12001.95 GB)
  Used Dev Size : 7813772288 (3725.90 GiB 4000.65 GB)
    Data Offset : 259072 sectors
   Super Offset : 8 sectors
   Unused Space : before=258984 sectors, after=18446744065895522304 sectors
          State : active
    Device UUID : e56df87e:6c456373:8a47adfc:70240603

Internal Bitmap : 8 sectors from superblock
    Update Time : Tue Sep 27 06:54:45 2016
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f266367 - correct
         Events : 23051

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAA.. ('A' == active, '.' == missing, 'R' == replacing)
mdadm: No md superblock detected on /dev/sdf2.




```

---

### Post by darkod on 2016-10-07
Like I thought. The array seems to be /dev/md127 and I don't know how you got the p1 and p2 parts. If you see the --detail output for md127 it list both array size and device size ( member size) while for p2 only array size. And the md127 uuid is identical to the partitions uuid.
You also seem to have weird definitions in mdadm.conf which might contribute to the p# confusion.
You can try:
1. Accepting that md127 is your array simply add sdf2 to it. That should work. And use md127 as your array, not md127p2 (test if it will mount).
2. Try stopping this array and assemble it as md0 for example, to see if it will assemble and mount. If it does and if all data is accessible, modify the array definition in mdadm.conf and use md0.

---

### Post by frostschutz on 2016-10-07
Yup, this looks like you should work with -add /dev/md127 and not /dev/md127p2 since your md device is for some reason partitioned.

Not sure why --detail works on md127p{1,2} at all, but it's showing the same RAID UUID as md127 itself, and wrong values for used dev size etc. so that's just nonsense.

EDIT:

Oh also there seems to be a RAID 6 header on your sdf disk, ... where did it come from, is that RAID 6 okay, from the metadata it looks like sdf was one of the disks needed to make it work (two others failed)?

If that RAID 6 no longer exists (for sdf, on this box, anyway) you might want to get rid of that old header with mdadm --zero-superblock.

---

