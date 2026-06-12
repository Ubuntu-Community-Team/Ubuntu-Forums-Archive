---
title: "mdadm: Raid 5 failure"
date: 2011-08-22
forum: Server Platforms
---

### Post by Sanados on 2011-08-22
Hi,

I have a mdadm raid 5 setup with originally 4 disks.
One disk died and a second one has I/O error.

I can still manage to start array with those 3 drives and read some chunks from it.
Though every once in a while the arrays drops dead when i read from a damages sector from the disk with I/O error.

My question now is if i can somehow extract the data which is still available.

I already tried to dd the damaged disk to a new disk, aswell as i tried dd_rescue. None of those methods lets me add the new disk to the array

/dev/sdb1 raid
/dev/sdc1 raid
/dev/sde1 raid / with I/O errors
/dev/sdd new harddisk

mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sde1 --force 
(works and starts the array and lets me access the files until i hit den third disk on I/O error)


my first try was to add the new disk to array and let mdadm to a resync:
mdadm --add /dev/md0 /dev/sdd1 works and starts resync ... but at 100% resync dies and says I/O error on /dev/sde1


Then i tried first dd then dd_rescue:
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 --force 
does not work (do i need to reset superblocks or else? And how?)

(outut:)
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 --force
mdadm: /dev/md0 assembled from 2 drives and 1 spare - not enough to start the array.



Any chance to rescue at least some of the data?
(Without trying each single file and restart array after I/O error)


Thanks in advance
 Jürgen

---

### Post by rubylaser on 2011-08-22
I'm confused, did you do dd_rescue on the disk with I/O errors?  If so, it should have made a block level copy of the disk. So, you'd remove your disk with I/O errors, and put the new disk in it's place.  If you're luckily and dd_rescue has made a good image of your faulty disk, your array should be able to start degraded (3 disks out of the 4).

Then you could backup your data, and then add another working hard drive, and implement a backup strategy.

---

### Post by Sanados on 2011-08-22
actually dd_rescue complained about cpl of I/O errors and badblocks and ran over 2 weeks.
I wonder if it really finished or just died.
However it did not recognize the disk as part of the raid.

(right now rerunning dd_rescue over dd_rhelp, and this time i do dd_rescue on the disk itself and not only the partition)

I wonder if i have to clear the superblock though before trying.



Isn't there a way to put the array into faulty (just created that word) mode to read all the data that is actually readable without the array going down on error?



EDIT: backup solution already in place ... just need to get the last bits of data out of my array.

---

### Post by Sanados on 2011-08-22
root@unkalo:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 4c7608b6:4941cc66:28d33e85:0a6b59d4
  Creation Time : Mon Mar 29 18:02:34 2010
     Raid Level : raid5
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
     Array Size : 5860535808 (5589.04 GiB 6001.19 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Aug 18 08:46:58 2011
          State : clean
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 809e8304 - correct
         Events : 459584

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       65        2      active sync   /dev/sde1
   3     3       8       17        3      active sync   /dev/sdb1
   4     4       8       49        4      spare   /dev/sdd1


it seems that sdd1 is in as spare, although it should have 4 working devices without hot-spare.

---

