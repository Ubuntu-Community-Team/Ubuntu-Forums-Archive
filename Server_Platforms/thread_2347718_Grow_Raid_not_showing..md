---
title: "Grow Raid not showing."
date: 2016-12-28
forum: Server Platforms
---

### Post by lars17 on 2016-12-28
Hi. 
I just grown my raid With 1 Harddrive. But its not showing that my Raid has increased. 

Showing that my raid has 3,64TB (4TB) space
[IMG]https://s27.postimg.org/6hk02spwz/image.png[/IMG]

Stil Showing old Space
[IMG]https://s27.postimg.org/4k0kykbj7/image.png[/IMG]
[IMG]https://s28.postimg.org/6hnq15m5p/image.png[/IMG]

anyone who has an idea of why the raid isnt showing the New Storage Space?

---

### Post by darkod on 2016-12-28
Usable size is not always equivalent to actual size. The usable size is the max size but your array can be smaller and needed to be grown. From terminal pls post the output of:
```
sudo mdadm -D /dev/md1
```

That will show you (among other info) the size of each raid member, the array size and the max available size. If you need to grow it you can do that with mdadm (sorry, I don't use webmin because it's not supported and recommended).

After you grow it you still have to extend the filesystem. Maybe only this step is missing for you. The mdadm -D will show you that. You extend the filesystem to max available with:
```
sudo resize2fs /dev/md1
```

---

### Post by lars17 on 2016-12-28
Output from mdadm
```
sudo mdadm -D /dev/md1
```

```
        Version : 1.2
  Creation Time : Fri Sep 30 21:16:50 2016
     Raid Level : raid5
     Array Size : 3906043904 (3725.09 GiB 3999.79 GB)
  Used Dev Size : 488255488 (465.64 GiB 499.97 GB)
   Raid Devices : 9
  Total Devices : 9
    Persistence : Superblock is persistent
  Intent Bitmap : Internal
    Update Time : Wed Dec 28 16:45:12 2016
          State : clean
 Active Devices : 9
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-asymmetric
     Chunk Size : 1024K
           Name : DAVID:1  (local to host DAVID)
           UUID : e6bac54f:96358ee6:f7234534:9c04635e
         Events : 304576
    Number   Major   Minor   RaidDevice State
       0       8       96        0      active sync   /dev/sdg
       1       8       32        1      active sync   /dev/sdc
       9       8       16        2      active sync   /dev/sdb
       3       8      128        3      active sync   /dev/sdi
       4       8      176        4      active sync   /dev/sdl
       5       8      144        5      active sync   /dev/sdj
       7       8      160        6      active sync   /dev/sdk
       8       8       64        7      active sync   /dev/sde
      10       8       48        8      active sync   /dev/sdd


```

it says Array Size : 3906043904 (3725.09 GiB 3999.79 GB)

will i lose data if i resize my array?



i use Webmin because its easy for showing status of Devices and services. all other server maintenance i do in the Terminal.

---

### Post by lars17 on 2016-12-28
I found this link on WIKI. 
[https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)

Saying i have to unmount the Array and then run the command, but the rest is unclear. this is the first time im doing this

---

### Post by darkod on 2016-12-28
I don't think you need to grow the array, it is already done. See, the Array Size is 4TB and the device size (Used Dev Size) is 500GB. A 9 member raid5 has one member for parity and 8 for data, which means total array size 8x500GB=4TB. So, it is already grown after adding the 9th disk.

You probably need only to resize the filesystem like I said earlier because that is not done automatically. And you don't need to unmount for that, you can do it online.

You resize the filesystem size to the maximum with:
```
sudo resize2fs /dev/md1
```

You are aware you are running a risky configuration, right? raid5 offers protection only against single member failure and running 9 members in raid5 is too much. More or less if using 6 members or more you need to start thinking about 2-member redundancy, like raid6.

---

### Post by lars17 on 2016-12-29
Reasson i use Raid 5 is that i need the Space not the Redundancy.. All items have been backuped. but so that i dont loos all when a drive fail i use raid 5

i had to unmount the array and reboot. then it worked or else i got this 

```
halfe@DAVID:~$ sudo resize2fs /dev/md1
resize2fs 1.42.13 (17-May-2015)
resize2fs: Enheten eller ressursen opptatt while trying to open /dev/md1
Couldn't find valid filesystem superblock.
```


So this is the result

```
resize2fs 1.42.13 (17-May-2015)
Please run 'e2fsck -f /dev/md1' first.
halfe@DAVID:~$ sudo e2fsck -f /dev/md1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/md1: 3040/213614592 files (3.2% non-contiguous), 600159122/854447104 blocks
halfe@DAVID:~$ sudo resize2fs /dev/md1
resize2fs 1.42.13 (17-May-2015)
Resizing the filesystem on /dev/md1 to 976510976 (4k) blocks.
The filesystem on /dev/md1 is now 976510976 (4k) blocks long.


```

---

### Post by darkod on 2016-12-29
OK, great. Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

