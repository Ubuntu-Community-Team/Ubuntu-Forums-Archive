---
title: "My RAID 5 failed! Please help."
date: 2010-05-14
forum: Server Platforms
---

### Post by gecka on 2010-05-14
Hello,

After a reboot, my raid5 array fails. I cannot boot the system at all
and only have the initramfs command line.

Here is what cat proc/mdstat gives me about my raid5 partition:

md0: inactive sdc[3](S) sdb5[1](S) sda5[0](S)

When I do

mdadm --assemble --scan --force

I get mdadm: /dev/md0 has been started with 2 drives (out of 3) and 1 spare.

Here is what cat proc/mdstat gives me
md0 : active raid5 sda5[0] sdc5[3] sdb5[1]
... 2[3/2] [UU_]

And it shows me the recovery progress bar.

After a while, I get:
raid5 : Disk failure on sdb5, disabling device.
raid5: Operation continuing on 1 devices.

Here is what cat proc/mdstat gives me:
md0 : active raid5 sda5[0] sdc[3](S) sdb5[4](F)

I am stuck there. How can I reassemble the raid5 array with sda and sdc ?

---

### Post by gecka on 2010-05-14
Anyone? Here is some more information:

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri May 14 10:22:49 2010
     Raid Level : raid5
     Array Size : 951079936 (907.02 GiB 973.91 GB)
  Used Dev Size : 475539968 (453.51 GiB 486.95 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat May 15 01:07:40 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : a34c4986:f07a41a9:3d186b3c:53958f34
         Events : 0.27

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       0        0        1      removed
       2       0        0        2      removed

       3       8       37        -      spare   /dev/sdc5
       4       8       21        -      faulty spare   /dev/sdb5

---

### Post by tgalati4 on 2010-05-14
How long has this RAID5 been running?  What type of motherboard and SATA controller?  It's possible that your SATA controller is not up the task of running RAID5.  There's a lot of interdisk communication that takes place between the striping and rolling checksums.  Are these consumer-grade hard drives or enterprise-class hard drives?

---

### Post by gecka on 2010-05-15
Hi,

 The raid has been running since august 2008. 

I will reinstall the system anyway. For now I reached the point where I am trying to restore my crutial data.

Why I assemble my array, I can access some of my data by mounting /dev/md0 and I backed those up (using nautilus) until I get the:

raid5 : Disk failure on sdb5, disabling device.
raid5: Operation continuing on 1 devices.

But some data is just not accessible. When that error occurs, here is what I get: 

```
sudo mdadm --detail /dev/md0
/dev/md0:
       Version : 00.90
 Creation Time : Fri May 14 10:22:49 2010
    Raid Level : raid5
    Array Size : 951079936 (907.02 GiB 973.91 GB)
 Used Dev Size : 475539968 (453.51 GiB 486.95 GB)
  Raid Devices : 3
 Total Devices : 3
Preferred Minor : 0
   Persistence : Superblock is persistent

   Update Time : Sat May 15 01:07:40 2010
         State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
 Spare Devices : 1

        Layout : left-symmetric
    Chunk Size : 64K

          UUID : a34c4986:f07a41a9:3d186b3c:53958f34
        Events : 0.27

   Number   Major   Minor   RaidDevice State
      0       8        5        0      active sync   /dev/sda5
      1       0        0        1      removed
      2       0        0        2      removed

      3       8       37        -      spare   /dev/sdc5
      4       8       21        -      faulty spare   /dev/sdb5
```

I am pretty sure the data I miss is either on sdb5 or at least on sdc5 witch keeps being marked as spare.... I tried mounting individual raid partitions with 'mount -t ext3', but it failed.

Do you know any command for running a degraded raid5 array with sda5 and sdc5 only ? 


Oh, and I also tried GNU ddrescue on individual raid partitions, but the resulting image doesn't mount.....

---

### Post by tgalati4 on 2010-05-15
dmesg | grep error
dmesg | more            (spacebar to move forward, q to quit)

Look for read errors or other errors related to your RAID.

Install smartmontools and see what is actually wrong with the drive.

sudo apt-get install smartmontools

sudo smartctl -a /dev/sdb
sudo smartctl -a /dev/sdc

---

### Post by Cracauer on 2010-05-16
You get hard errors when re-syncing to the missing disk.

What's S.M.A.R.T. saying about the drive?

Does it work fine for `cat /dev/hd. | wc` outside the RAID?

---

### Post by laluz on 2010-05-16
why not just remove the faulty drive and start the array with --force with the other two?

---

