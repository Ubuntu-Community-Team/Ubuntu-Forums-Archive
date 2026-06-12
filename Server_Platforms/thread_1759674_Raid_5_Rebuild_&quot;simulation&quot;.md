---
title: "Raid 5 Rebuild &quot;simulation&quot;"
date: 2011-05-16
forum: Server Platforms
---

### Post by Zeggi on 2011-05-16
Hi,

as the topic says... I have 6x WD20EARS and i have given up on my FakeRaid setup so i went with a software raid in hope of understanding how exactly mdadm works.

I followed alot of guides and managed to figure out how to creat a Raid5 array containing 5hdds (1 for simulation of a hdd failure) and check status of rebuild/sync.

so a few questions.

1. i want to simulate a broken hdd, does the array have to build to 100% before i can simulate a broken hdd swap to a fresh and do a rebuild?

- i gave this a try but i didn't let the array build to 100% i think i stoped everything at 2% what i did was that i simply shutdown the server and swapped one of the 5x raid5 setup, but what i didn't know was that i apparently have to remove the "broken" hdd from the array before actually swapping hdd, is this correct?

2. disk utility states that 1 of my discs has misallignment of 3078b, how can this be fixed?

So what i want to understand is more of how mdadm works with software raid in case i in the future have to swap a broken hdd, would be nice to figure out how mdadm actually works before a total hdd failure. 

oh and a also, is there a GUI for total n00bs? :)

---

### Post by rubylaser on 2011-05-16
I've been using mdadm for years, and have been very happy with it.  I'll answer your questions in the same order you asked them.

1. If you want to give a real failure a test, you'll want to wait until your array syncs.  If it's going really slow there are options you can pass to allow it to sync faster.  What's the output of this command when it's syncing?
```
cat /proc/mdstat
```
You'll either want to physically remove the hard drive from the SATA cable to test, or mdadm fail and then remove the drive.  Something like this.
```
mdadm --manage /dev/md0 --fail /dev/sdb1
mdadm --manage /dev/md0 --remove /dev/sdb1
```
Then, you'd add the new drive in...
```
mdadm --manage /dev/md0 --add /dev/sdb1
```
You can view the rsync process like this...
```
watch cat /proc/mdstat
```

2. Sounds like your partition is not aligned correctly, you can view it like this...
```
fdisk -luc
```

Learning how to use a tool, especially one that will hold important data is a great idea.  I would probably suggest just setting up a virutal machine (in virtualbox) with 1GB disks (or smaller) to simulate your setup, so that you can test quickly (and with snapshots) without having to wait for resyncs each time.

You could also test adding more disks to the array, and growing the filesystem so that you can see how that works if you ever run out of storage space.

Finally, if you really want to understand how something works, I'd avoid the GUI.  Learning to use the CLI will really help you to see and understand your commands.  I hope that helps.

---

### Post by Zeggi on 2011-05-19
Thanks alot for your reply.
I gave up with fakeraid since a rebuild doesn't work unless you use less than 4hdds or use intel rst application that only works with windows.

So I'm up and runing with mdadm, 6x WD20EARS sadly 4different generations.
2 new bought just recently, both give away misalignment with 512bytes, according to other ears users it's normal and can be ignored. All hdds are starting at sector 63 and end the same.

I checked at the rebuild speed and it says finish at 2400h @ 22mb/s
Is that a normal speed?

Again thanks alot for your post, helped me alot, cheers

---

### Post by rubylaser on 2011-05-19
I believe your newer WD20EARS drives are [advanced format]("http://www.storagereview.com/western_digital_caviar_green_2tb_review_wd20ears") drives based on what you just said.  If that's the case, you'll definitely want to align the partitions properly, or you will be taking a serious [performance hit]("http://www.osnews.com/story/22872/Linux_Not_Fully_Prepared_for_4096-Byte_Sector_Hard_Drives"). Here's another [thread]("http://ubuntuforums.org/showthread.php?t=1496239") to look at.

22MB/s sync is pretty slow (I've seen users with much lower values though).  I normally see between 65MB/s-85MB/s on my various servers.  There was a forum thread a few days ago that a user was syncing well over 100MB/s.

---

### Post by Zeggi on 2011-05-19
These are my hdds,
WD20EARS -07MVWB0 (misaligned by 512byte)
WD20EARS -07MVWB0 (misaligned by 512byte)
WD20EARS -00MVWB0
WD20EARS -00J2GB0
WD20EARS -00S8B1
WD20EARS -00S8B1

So my 2 new hdds are misaligned

```
fdisk -luc
```Gives me this output,
Its a Raid5 setup starting from /dev/sdb and on to sdg

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000224e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   455025059   227512498+  83  Linux
/dev/sda2       455025060   488392064    16683502+   5  Extended
/dev/sda5       455025123   488392064    16683471   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x5bcf183a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907024064  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeeae86e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd5aae662

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18a46680

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3de2ace

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc9f66604

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  3907024064  1953512001   fd  Linux raid autodetect

Disk /dev/md0: 10002.0 GB, 10001973248000 bytes
2 heads, 4 sectors/track, -1853079296 cylinders, total 19535104000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 1048576 bytes / 5242880 bytes
Alignment offset: 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

``````
sudo mdadm --detail /dev/md0
```Gives me this output,

```
 
Version : 1.2
  Creation Time : Thu May 19 00:55:40 2011
     Raid Level : raid5
     Array Size : 9767552000 (9315.06 GiB 10001.97 GB)
  Used Dev Size : 1953510400 (1863.01 GiB 2000.39 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent

    Update Time : Thu May 19 20:00:37 2011
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 1024K

 Rebuild Status : 72% complete

           Name : BunMaster-NAS:0  (local to host BunMaster-NAS)
           UUID : 6d385df8:46289b14:663f0791:9a8f3b2a
         Events : 18

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
       6       8       97        5      spare rebuilding   /dev/sdg1

```this is the rebuild speed,

```
 cat /proc/mdstat 
``````

Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdg1[6] sdf1[4] sde1[3] sdd1[2] sdc1[1] sdb1[0]
      9767552000 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [6/5] [UUUUU_]
      [==============>......]  recovery = 72.2% (1411554688/1953510400) finish=494.0min speed=18282K/sec

```

---

### Post by Zeggi on 2011-05-19
YAY! nice result!

I just got my rebuild up to 60-65mb/s
How, well by starting a new partition, according to this tip.
[http://www.johannes-bauer.com/linux/wdc/?menuid=3](http://www.johannes-bauer.com/linux/wdc/?menuid=3)

Start sector 2048
Last sector 2847

then i simply created raid partitions for the rest of the volume, worked like a charm :)
I also found some info about, NCQ, stripe cache size, will give it a go :)

[https://raid.wiki.kernel.org/index.php/Performance](https://raid.wiki.kernel.org/index.php/Performance)

---

### Post by YesWeCan on 2011-05-19
M = mega, m = milli
B = byte, b = bit
:)

---

### Post by Zeggi on 2011-05-19
Oh sorry,

Its megabyte per second:) 
" speed=65282K/s "

Hmm im not sure if i should do the same to all discs, i only did the start-last sector on the 2 discs that complained about being misaligned..
they are the ones i bought recently.
Whats your thought?
are all WD20EARS 4k block hdds?

---

### Post by Zeggi on 2011-05-20
I did the same "fix" on all hdds, just to be safe.
Speeds are the same 65-68MB/s, i haven't given NCQ a go, not sure if i should stop now that speeds are alot better, atleast faster than windows runing with Intel RST application.

Other than that, im not sure what chunk size to use, i have tried 2048 earlier and now im runing at 128 or was it 512, will have a look once im at home.

anyone know how to change chunksize with a complete array, is it possible or do i have to remove it and create a new one?

---

### Post by rubylaser on 2011-05-20
Sorry for my tardiness.  I'm glad that the alignment made your speed increase so dramatically.  I always tweak my array for speed.  This script works great...
[http://ubuntuforums.org/showthread.php?t=1494846]("http://ubuntuforums.org/showthread.php?t=1494846")

You cannot change the chunk size on an existing array without recreating it and wiping out your data in the process.  I run a 512K chunk on mine. And, I've aligned my stripe and stride width for my ext4 filesystem to this chunk size.  This [site]("http://uclibc.org/~aldot/mkfs_stride.html") will provide you the parameters to create your filesystem.  Based on 6 disks and a 1024K chunk, your ext4 filesystem should look like this.
```
mkfs.ext4 -b 4096 -E stride=256,stripe-width=1280 /dev/md0
```
**[COLOR="Red"]^Don't do this if you have important info on your array, you will lose it![/COLOR]**

---

