---
title: "[SOLVED] 2 Failed disk in a Raid 5 array, what are my best options?"
date: 2013-08-17
forum: Server Platforms
---

### Post by nico4 on 2013-08-17
Hi

I had 2 disks failing a raid5 array due to a powerloss.

It seemed to work fine at boot but on first write atempt it failed (10 minutes or so later). 

2 disks hade strange status (don't remember exactly, couldn't get SMART status from it) so I powered off, reseated cables, on boot again the seemed fine and now I was able to read smart checks from them.

Ubuntu 12.04

sda1,   Array State : ..AAAAAA,   Active device 4, Events : 53219
sdb1,   Array State : ..AAAAAA,   Active device 5, Events : 53219
sdc1,   Array State : ..AAAAAA,   Active device 6, Events : 53219
sdd1,   Array State : ..AAAAAA,   Active device 7, Events : 53219
sdg1,   Array State : AAAAAAAA,   Active device 0, Events: 53211
sdh1,   Array State : AAAAAAAA,   Active device 1, Events: 53211
sdi1,   Array State : ..AAAAAA,   Active device 2, Events : 53219
sdj1,   Array State : ..AAAAAA,   Active device 3, Events : 53219



Status of superblocks before trying anything:

```

mdadm --examine /dev/sd[abcdefghij]1

/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 992ab4f1:73c2d3a1:5e6aa300:3a113d1e

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : 63d0bdc4 - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 4
   Array State : ..AAAAAA ('A' == active, '.' == missing)
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 8b49b9c1:759ac413:487ef0bd:016653f6

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : 3b2a1b1b - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 5
   Array State : ..AAAAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 52d82e71:5b7f2a30:1678969c:fb575016

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : 5a87a90 - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 6
   Array State : ..AAAAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a197c14b:63277562:6d34e182:48718d0a

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : ed0db78c - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 7
   Array State : ..AAAAAA ('A' == active, '.' == missing)
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : f63b00a2:40fba765:f17ca8b9:d1007424

    Update Time : Thu Aug 15 22:35:17 2013
       Checksum : 972f0541 - correct
         Events : 53211

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : feaf3de7:8d210aa4:a2180f69:05aca92c

    Update Time : Thu Aug 15 22:35:17 2013
       Checksum : d26ae684 - correct
         Events : 53211

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAAAAAA ('A' == active, '.' == missing)
/dev/sdi1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : b49ba7d3:c93c23dd:f9350cda:da07051a

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : 5644691f - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : ..AAAAAA ('A' == active, '.' == missing)
/dev/sdj1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b775e5b6:8be367c5:77f0d3ac:b1196bd0
           Name : stacker:0  (local to host stacker)
  Creation Time : Sat May  7 23:54:03 2011
     Raid Level : raid5
   Raid Devices : 8

 Avail Dev Size : 3907024896 (1863.01 GiB 2000.40 GB)
     Array Size : 13674583552 (13041.10 GiB 14002.77 GB)
  Used Dev Size : 3907023872 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : a6709b2e:384f6543:13839fda:0d130053

    Update Time : Thu Aug 15 22:45:53 2013
       Checksum : 5108a97d - correct
         Events : 53219

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : ..AAAAAA ('A' == active, '.' == missing)


```

So I figured trying to put one disk back and then rebuild the last one if that worked. After a lot of research it seemed like it would be possible to get it up and running with the following:

```

mdadm --create --assume-clean --level=5 --raid-devices=8 /dev/md0 /dev/sdg1 missing /dev/sdi1 /dev/sdj1 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

```

When doing this it doesn't recognize the partition so I though I would ask for help here before trying anything else myself.

I'm not very experienced in Linux so I'm not sure i have provided all relevant information here.

BR
Nico

---

### Post by Cheesemill on 2013-08-17
Your quickest and easiest option is to re-create the array from scratch with 8 drives that have been tested as working and then restore all the data from your last backup.

---

### Post by nico4 on 2013-08-17
Thanks for your reply, but this does not need to be fixed in a hurry. I also hope to get a better understanding of raid recovery in the same go :) 

I'm prepared to put several days into this before restoring.

---

### Post by SaturnusDJ on 2013-08-17
So what are the S.M.A.R.T. values for the drives?

Why didn't you run an assemble first?
```

mdadm --assemble --force --run /dev/md0 /dev/sd[a,b,c,d,g,h,i,j]1

```
However chances are very small, you might still give the assemble a try.

If you've read careful, you would have read also that a re-create is a last resort.

Think about this: You are leaving one disk out of the re-create, while there is a problem with two disks. So the logic here is: Use all of the disks, or don't use the two problem giving disks. This last option is not possible, so then you would go with the first...if doing a re-create at all.
It looks like your re-create order is fine. If there was a reboot between the examine's and the re-create and you didn't look up the order it still might be the wrong, because sometimes devices names change. Therefor basing the order at UUID is better.

The state of the 2 problem disks is 'active.' You need to find out why.
```
cat /proc/mdstat
```

---

### Post by nico4 on 2013-08-17
Hi SaturnusDJ

I forgot to mention but I tried with --assemble first of all but not with the --force parameter. I don't remember the error message.

I tested --assemble as you posted here now but it says superblock on /dev/sdh1 doesn't match others, and that of course is probably because I tried to re-create. So I guess this would have worked if I tried that option first thing.

SMART reports no errors on any disk.

My logic for only using one of the failed disks was that if they failed at different times (maybe even only a few ms apart) was that I at least had a 50% chance of selecting the one failing last, even though from the superblocks it looks like they failed at the same time. The events counter was not that high, so I can't imagine it will increase for every write to the raid set.

Any suggestions for my next move? My plan is to try and recreate again but with the other disk first, and if that not works with both.

If none of that works I will try to look at it at a lower level, so if anyone have good suggestions for sources of knowledge where I can enlighten myself, it will be appreciated.

/Nico

---

### Post by SaturnusDJ on 2013-08-17
I can't think of anything else here. So the data is probably corrupted or the order is still wrong.

---

### Post by nico4 on 2013-08-17
Hi

I think I got this working now :)

The problem was that the RAID was created with an older version of MDADM (3.2.3 or older) where the offset is 2048 sectors. There is no way to set the offset in current version of MDADM 3.2.5. In MDADM 3.3 rc2 you should be able to set this but I ran into dificulties installing it. So I just downgraded to 3.2.3 and then it worked.

apt-get install mdadm=3.2.3-2ubuntu1

I set as much parameters as possible from the old superblock information.

mdadm --create --assume-clean --level=5 --chunk=512 --parity=left-symmetric --raid-devices=8 /dev/md0 /dev/sdg1 /dev/sdh1 /dev/sdi1 /dev/sdj1 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1

Even though this problem took a while to fix I wonder if it was not faster than restore anyway (14TB).

Now I only have one little problem and that is that the superblocks from the newer mdadm might have overvritten some data when I did the firs create. On version 3.2.3 the data offset is 1MiB (2048 sectors), on 3.2.5 it's 128 MiB (262144 sectors). Is there any smart way to check this? Fortunately i have MD5 files for most of the data on this raidset so I will check it this way if I don't comeup with anything better.

---

### Post by SaturnusDJ on 2013-08-18
Ahh, the more parameters, the better...ofcourse. Good work.

I know superblock version differ, but I don't know about the offset. Maybe you can see by checking a file bigger than 128MiB.

---

