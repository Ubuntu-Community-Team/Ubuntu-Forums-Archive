---
title: "Raid 0 Mdadm Superblocks Problem"
date: 2016-10-07
forum: Server Platforms
---

### Post by mark120 on 2016-10-07
Hi, I wonder if anybody could please help me try and repair my array, the 2 disk are both tested and are fine, nor sure why my array failed, but it has, any help would be highly appreciated.

**fdisk -l | grep "Disk "**

```

GPT PMBR size mismatch (1953525167 != 1565586943) will be corrected by w(rite).
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: A36F5CFC-A3BB-4DD2-9BCE-84198569BD05
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Disk identifier: 0xd0de3d61
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Disk /dev/md0: 2.7 TiB, 3000603770880 bytes, 5860554240 sectors
Disk identifier: A36F5CFC-A3BB-4DD2-9BCE-84198569BD05
```


**sudo mdadm --misc --examine /dev/sdb**

```
/dev/sdb:
Magic : a92b4efc
Version : 1.2
Feature Map : 0x0
Array UUID : 56736c28:5fa9c36e:0779b651:b442ba26
Name : nas:Storage (local to host nas)
Creation Time : Fri Sep 16 13:21:09 2016
Raid Level : linear
Raid Devices : 2

Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
Used Dev Size : 0
Data Offset : 262144 sectors
Super Offset : 8 sectors
Unused Space : before=262056 sectors, after=0 sectors
State : clean
Device UUID : b15e50ba:d330ae24:caad267d:f7d0be80


Update Time : Fri Sep 16 13:21:09 2016
Bad Block Log : 512 entries available at offset 72 sectors
Checksum : 302a1c2a - correct
Events : 0


Rounding : 0K


Device Role : Active device 1
Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```


[B] sudo mdadm --misc --examine /dev/sdc
[/B]

```
/dev/sdc:
MBR Magic : aa55
Partition[0] : 1953525167 sectors at 1 (type ee)
```




cat /proc/mdstat


```

Personalities : [linear] [raid0]
md0 : active raid0 sdb[1] sdc[0]
      2930277120 blocks super non-persistent 64k chunks


unused devices: <none>


```

sudo mdadm --detail /dev/md*

```

mdadm: /dev/md does not appear to be an md device
/dev/md0:
        Version :
  Creation Time : Fri Oct  7 18:59:39 2016
     Raid Level : raid0
     Array Size : 2930277120 (2794.53 GiB 3000.60 GB)
   Raid Devices : 2
  Total Devices : 2


          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 64K


    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       16        1      active sync   /dev/sdb
/dev/md0p1:
        Version :
  Creation Time : Fri Oct  7 18:59:39 2016
     Raid Level : raid0
     Array Size : 976761543 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2


          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 64K


    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       16        1      active sync   /dev/sdb

```

sudo blkid

```

/dev/sda1: UUID="8d1d3996-2cfc-4fa1-9331-cf36e9eb1062" TYPE="ext4" PARTUUID="d0de3d61-01"
/dev/sda5: UUID="b5124a8b-4207-4e8c-88e0-b3040fc803e7" TYPE="swap" PARTUUID="d0de3d61-05"
/dev/sdb: UUID="56736c28-5fa9-c36e-0779-b651b442ba26" UUID_SUB="b15e50ba-d330-ae24-caad-267df7d0be80" LABEL="nas:Storage" TYPE="linux_raid_member"
/dev/sdc1: PARTUUID="ff63aded-5d0a-4755-9cdf-2e29535ce547"
/dev/md0: PTUUID="a36f5cfc-a3bb-4dd2-9bce-84198569bd05" PTTYPE="gpt"
/dev/md0p1: PARTUUID="ff63aded-5d0a-4755-9cdf-2e29535ce547"

```

From my google research I have tried:
[FONT=&amp][B]
mdadm --assemble --verbose --force /dev/md127 /dev/sd[bc][/B][COLOR=#666666]
[/COLOR][/FONT][B][COLOR=#666666][FONT=Consolas]
[/FONT][/COLOR][/B]```
mdadm: looking for devices for /dev/md127
mdadm: /dev/sdb is busy - skipping
mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted
root@nas:~# mdadm --assemble --verbose --force /dev/md127 /dev/sd[bc] 

```

Anyone any other ideas how I can repair this please?

Cheers
[B][COLOR=#666666][FONT=Consolas]



[/FONT][/COLOR][/B]

---

### Post by mark120 on 2016-10-07
double post

---

### Post by darkod on 2016-10-07
Are you looking to repair the array or build a new one? By definition a failed raid0 array can't be recovered because it has no redundancy.
Also, advice for the future: use partitions when creating mdadm arrays, not the disk designator.

---

### Post by mark120 on 2016-10-07
I was hoping to recover one file off the array as the drives have not failed. My backup system stopped about a week ago and I never got around to repairing it :(
I was surprised the array failed so easily.
Do I have any chance of recovering it?

---

### Post by darkod on 2016-10-08
There are only two more things you can try:
- forced assemble using --run
- re-create using --assume-clean (that tells mdadm to use existing data on the disks instead of creating new blank array)

Also, the order of the drives in the array seems to be sdc first, and sdb second. And you need to stop any wrong assembled array because it would keep the partition busy.

So, that would be:
Option 1
```
sudo mdadm --stop /dev/md0
sudo mdadm --stop /dev/md127 (depending how any started array is called)
sudo mdadm --assemble --verbose --force --run /dev/md0 /dev/sdc /dev/sdb
```

Option 2
```
sudo mdadm --stop /dev/md0
sudo mdadm --stop /dev/md127
sudo mdadm --create --verbose --assume-clean --level=raid0 --raid-devices=2 /dev/md0 /dev/sdc /dev/sdb
```

This is exactly the problem with raid0 and having no redundancy. Even if the disks a good in general, if one of them drops out of the array temporarily for any reason, the array fails and it might not be recoverable because it has no redundancy like real raid.

---

### Post by mark120 on 2016-10-08
Thanks very much Darkod for your suggestions,
Option 1 never worked, but option 2 has

```


sudo mdadm --create --verbose --assume-clean --level=raid0 --raid-devices=2 /dev/md0 /dev/sdc /dev/sdb
mdadm: chunk size defaults to 512K
mdadm: /dev/sdc appears to be part of a raid array:
       level=raid0 devices=0 ctime=Thu Jan  1 01:00:00 1970
mdadm: partition table exists on /dev/sdc but will be lost or
       meaningless after creating array
mdadm: /dev/sdb appears to be part of a raid array:
       level=linear devices=2 ctime=Fri Sep 16 13:21:09 2016
Continue creating array? y
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.


```

sudo mdadm --detail /dev/md0

```




/dev/md0:
        Version : 1.2
  Creation Time : Sat Oct  8 10:56:08 2016
     Raid Level : raid0
     Array Size : 2930014720 (2794.28 GiB 3000.34 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Sat Oct  8 10:56:08 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 512K


           Name : nas:0  (local to host nas)
           UUID : 31f15675:a2b188d6:087e1202:3c0a5b7a
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       16        1      active sync   /dev/sdb
root@nas:~#  sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Sat Oct  8 10:56:08 2016
     Raid Level : raid0
     Array Size : 2930014720 (2794.28 GiB 3000.34 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Sat Oct  8 10:56:08 2016
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


     Chunk Size : 512K


           Name : nas:0  (local to host nas)
           UUID : 31f15675:a2b188d6:087e1202:3c0a5b7a
         Events : 0


    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       16        1      active sync   /dev/sdb


```



What I don't understand now that according to the system the array is clean, is there anyway to read the old data off it?
Yes what I certainly have realised is that Raid 0 Mdadm arrays are very temperamental indeed.

---

### Post by darkod on 2016-10-08
OK, but this still doesn't mean it worked. Also the chunk size it used by default is 512K and in your first --detail output it said 64K. So you might need to recreate it again adding a parameter to use 64K.

But as it is now, try mounting it temporarily. If it says it can't read the filesystem, it might be because of wrong chunk size or because the data is gone completely...
```
sudo mount /dev/md0 /mnt
```

If that doesn't work and you want to try the recreate again, use the above command and add one more parameter (not at the end, the command has to finish with the array members, add it between all the other parameters in the middle):
```
--chunk=64K
```

After that try mounting it.

---

### Post by mark120 on 2016-10-08
I tried it both ways 512k and 64k and both gave me:

```

sudo mount /dev/md0 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

dmesg | tail

```

[ 2599.948184] md: zone0=[sdc/sdb]
[ 2599.948189]       zone-offset=         0KB, device-offset=         0KB, size=1953262976KB
[ 2599.948191] md: zone1=[sdb]
[ 2599.948195]       zone-offset=1953262976KB, device-offset= 976631488KB, size= 976752000KB


[ 2599.948214] md0: detected capacity change from 0 to 3000335335424
[ 2599.949173]  md0: unknown partition table
[ 2623.064716] EXT4-fs (md0): bad geometry: block count 976661504 exceeds size of device (732503744 blocks)
[ 2647.844442] EXT4-fs (md0): bad geometry: block count 976661504 exceeds size of device (732503744 blocks)
[ 3115.078679] EXT4-fs (md0): bad geometry: block count 976661504 exceeds size of device (732503744 blocks)

```

I am guessing I have lost the data then :(

---

### Post by mark120 on 2016-10-08
I fear I may be at the end of the road now trying to remount my array and recover the data, if there is anything else you feel I could try in the command terminal please let me know
One other option I could try if there is nothing else from the command prompt is but this raid reconstruction software for windows, maybe there is a chance it would work. [http://www.runtime.org/raid.htm](http://www.runtime.org/raid.htm)
I have downloaded the demo, but just need to confirm something if you don't mind:
Would I set it up with the following settings:
Start Sectors to probe - 0,72
Block Size to probe - 512k, 64k
number of sectors to probe - [COLOR=#000000][FONT=&amp]2930277120[/FONT][/COLOR]
Thanks very much for all your help it has been most appreciated.

---

### Post by frostschutz on 2016-10-08
--chunk=64K should be correct, so stick with that. Also, --data-offset=128M.

 Something created a partition table on sdc and killed your data with it? You could try photorec on your md device, if you had unencrypted, 2-3MB sized files of known type on it, if photorec finds those you have the correct RAID setting.

Not sure how to repair the filesystem... depends on what really happened with your disks there.

---

