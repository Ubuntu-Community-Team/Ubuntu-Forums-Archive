---
title: "Raid 5 failure on Debian system."
date: 2013-04-11
forum: Server Platforms
---

### Post by jonlisty on 2013-04-11
Hello!


I have a 4-disc Raid 5 server running Open Media Vault (Debian).  The other day, it disappeared from OMV, which was reporting 3 drives failed.  Panic Stations.  However, using MDADM I can get info from 3 of the drives which suggests they are functioning ok (info below).  The remaining 4th drive doesn't give anything back via mdadm --examine.  Any ideas how I can rebuild the drive without destroying the data?  According to what I have read, as the three apparently working drives all have the same events number (103), it is fairly likely the data is intact on them - but how to I rebuild?


Thanks my lovelies!


Jon

```

/dev/sdf:
Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dc344271:82f55bd0:fcfd0e16:a2a60bc8
           Name : TTVServer:TTV2  (local to host TTVServer)
  Creation Time : Mon Jan  7 11:03:39 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 17581590528 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : c792c6b2:78fd4e78:e4f008ea:826e25e8


    Update Time : Sat Apr  6 13:17:10 2013
       Checksum : 30386dbe - correct
         Events : 103


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)




/dev/sdg:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dc344271:82f55bd0:fcfd0e16:a2a60bc8
           Name : TTVServer:TTV2  (local to host TTVServer)
  Creation Time : Mon Jan  7 11:03:39 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 17581590528 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : c0426118:614cb315:15c9a0ee:2ad88e26


    Update Time : Sat Apr  6 13:17:10 2013
       Checksum : 7638ae70 - correct
         Events : 103


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)






/dev/sdi:
  Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : dc344271:82f55bd0:fcfd0e16:a2a60bc8
           Name : TTVServer:TTV2  (local to host TTVServer)
  Creation Time : Mon Jan  7 11:03:39 2013
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 5860531120 (2794.52 GiB 3000.59 GB)
     Array Size : 17581590528 (8383.56 GiB 9001.77 GB)
  Used Dev Size : 5860530176 (2794.52 GiB 3000.59 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 8a96d5fe:594418b6:c63dafd0:c459e498


    Update Time : Sat Apr  6 13:17:10 2013
       Checksum : 5175f080 - correct
         Events : 103


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)

```

---

### Post by darkod on 2013-04-11
I just saw this thread but you'll have to wait few hours so I can take a look at it. It's impossible right now. You should be able to sort this out.

---

### Post by darkod on 2013-04-11
One thing to check would also be whether the fourth disk is seen by the OS at all. parted can show you all disks and partitions:
```
sudo parted -l (small L)
```

If only the superblock is missing, no problem. If the disk is dead, you will have to replace it with a new one.

In any case a raid5 array should work with one member missing. It's strange it stopped the array.

Since you have three disks out of four, with equal event counters, first try the autoscan assembly:
```
sudo mdadm --assemble --scan
```

If that doesn't work you can force the assemble yourself but the order of the disks has to be correct, the examine command is showing you the order in Device Role. And don't forget that one member is missing. You will need to use 'misiing' at the correct place.

Is yuor device /dev/md0 or another one? If it's md0, the forced assemble would be like:
```
sudo mdadm --assemble --force /dev/md0 /dev/sdf /dev/sdg /dev/sdi missing
```

If the above doesn't work, there are more options. Lets see how it goes first.

Also, it's worth noting that you used the whole disks as members of the array. It's better practice to use partitions, not the whole disk devices. Like /dev/sdf1, /dev/sdg1, /dev/sdi1, etc.

---

### Post by jonlisty on 2013-04-14
Thanks for your help!  I tried > [COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm --assemble --scan[/FONT][/COLOR] but nothing happened.  Before I try your second suggestion, a quick question; my three 'working' drives are showing as Active Device 0, 1 and 2.  But they are actually discs 1, 2 and 4 in the enclosure and are listed as such when I did mdadm --examine for each disc (so sda = Active Device 0, sdb = AD 1, sdc = dead, sdd = AD2).  This seems strange to me!  Or is the failed drive actually the fourth disc in the array (Active Device 3)?  That would affect the order in which I reassemble the raid I assume...

Thanks for your help, Darko,  tis hugely appreciated.

---

### Post by darkod on 2013-04-15
The Device Role in --examine should be correct, that's the content of the superblock that mdadm will use. So, stick to it.

Why do you say the disks are sda, sdb and sdd and in the first post it shows them as sdf, sdh and sdi?

---

### Post by jonlisty on 2013-04-15
Thanks.  I reconnected the drives and they are now abcd.  I am going to back up every drive to identical drives before I have a go at this, I'll hopefully be able to give it a go this week.  Cheers dude. Jon

---

### Post by jonlisty on 2013-04-21
Hey Darko,

I tried 


sudo mdadm --assemble --force /dev/md0 /dev/sdf /dev/sdg /dev/sdi missing

and I got

> mdadm: missing has no superblock - assembly aborted

any ideas?

Thanks!

Jon

---

### Post by jonlisty on 2013-04-21
Ok after some more reading, I tried this:

> mdadm --create /dev/md8 --verbose --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc missing

and got this:

> mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: super1.x cannot open /dev/sda: Device or resource busy
mdadm: failed container membership check
mdadm: device /dev/sda not suitable for any style of array



aaagghhh!!

---

### Post by jonlisty on 2013-04-21
also...


> $ sudo cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
md8 : inactive sda[0] sdc[2] sdb[1]
      8790796680 blocks super 1.2

---

### Post by jonlisty on 2013-04-21
also:


> $ sudo mdadm --detail /dev/md8
/dev/md8:
        Version : 1.2
  Creation Time : Mon Jan  7 11:03:39 2013
     Raid Level : raid5
  Used Dev Size : -1
   Raid Devices : 4
  Total Devices : 3
    Persistence : Superblock is persistent


    Update Time : Sat Apr  6 13:17:10 2013
          State : active, degraded, Not Started
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : TTVServer:TTV2  (local to host TTVServer)
           UUID : dc344271:82f55bd0:fcfd0e16:a2a60bc8
         Events : 103


    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       0        0        3      removed

---

### Post by darkod on 2013-04-22
First of all, DO NOT run --create since that is used to create new md devices deleting the existing data.

Can you post again:
```
sudo mdadm --examine /dev/sd[abcd]
```

I was wrong about using missing, it seems to be used only when creating new md devices. That was the only error in the --assemble command. But lets see first the output of --examine and we can continue.

---

### Post by jonlisty on 2013-04-22
SOLVED!


This is what did it:


> sudo mdadm --create /dev/md0 --verbose --level=5 --raid-devices=4 /dev/sda /dev/sdb /dev/sdc missing

---

### Post by darkod on 2013-04-22
But that doesn't keep the data man. Or does it? That is for creating a new raid5 array with foure devices out of which one is missing right now. That was easy to do if you wanted a new array. I thought you wanted to keep the data.

---

### Post by SaturnusDJ on 2013-04-24
I've seen more cases where using --create without --assume-clean didn't end up in data loss. Maybe mdadm recognizes previous setups sometimes. It's still stupid to try of course. As you said --assemble absolutely was the way to go here.

Using missing in assemble isn't needed indeed. From what I know, the order in --assemble doesn't matter either because that information comes from the metadata/superblock. But sometimes, due to corruption or something else, the event count is way out of sync. In that case you would be using the --force (and --run) flag(s) in a way nicely described here: [https://raid.wiki.kernel.org/index.php/RAID_Recovery#Trying_to_assemble_using_--force](https://raid.wiki.kernel.org/index.php/RAID_Recovery#Trying_to_assemble_using_--force)

---

