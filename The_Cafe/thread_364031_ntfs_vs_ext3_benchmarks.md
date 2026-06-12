---
title: "ntfs vs ext3 benchmarks"
date: 2007-02-17
forum: The Cafe
---

### Post by ankara on 2007-02-17
just finished moving data from an NTFS (sda5 partition to a spare drive and then formatting the partition to EXT3 with gparted and then moved the data back across from the spare drive to the newly formatted partition (sda5). 
but before i did i (non scientifically) benchmarked the partition before and after the format with the same data copied back across after the format.

the purpose of the excersise is that now ive moved away from M$ for my everyday computer activities i had no use for maintaining NTFS partitions with their weak permissions and ownership options etc. Plus the fact that when doing heavy data transfer with EXT3 partitions there was little to no increase in CPU load, with ntfs-3g, there was between 9% and 45% load averaging around 20% extra cpu load.

just in case anyone wanted data for curiositys sake.

before as NTFS:
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
Desktop          2G 10018  26 32232   7 11824   3 19638  45 30244   3  93.3   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16  2652   5 12663   5  4661   5  3237   5 14359  10  4434   6
Desktop,2G,10018,26,32232,7,11824,3,19638,45,30244,3,93.3,0,16,2652,5,12663,5,4661,5,3237,5,14359,10,4434,6

```
and after as EXT3
```
Version  1.03       ------Sequential Output------ --Sequential Input- --Random-
                    -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
Desktop          2G 17625  48 31046   8 12952   3 23815  52 32382   3 111.2   0
                    ------Sequential Create------ --------Random Create--------
                    -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 25847  46 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Desktop,2G,17625,48,31046,8,12952,3,23815,52,32382,3,111.2,0,16,25847,46,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++

```

the hardware is:
Gigabyte GA-M55plus-SG3
AM2 semptron 3000
1GB corsair ddr2 667
sata maxtor 6g1060e0

software was ntfs-g3 ver 20060920-0
one noteworth piece of info, while i was running the benchmark with ntfs-3g i was away cooking dinner with no other applications running in X. when i ran the benchmark after converting to EXT3 and moving the data back i was sat browsing and had system monitor open aswell,, tsk, tsk, im a poor scientific experimentor but im lazy. but hey, the results are still favourable :)

---

### Post by pezmanlou on 2008-11-16
I am surprised that there was no response to this post.  I think that this is very interesting.  It makes me glad that I use ext3.

---

### Post by SunnyRabbiera on 2008-11-16
ext3 is a great filesystem indeed, its fast, it doesnt fragment nearly as much as NTFS and it seems more solid.

---

### Post by ad_267 on 2008-11-16
I wonder what the difference would be between using Ext3 with Linux and NTFS on Windows, as the Linux drivers for NTFS are probably not as fast and efficient as the Windows ones. The NTFS specification is a Microsoft secret. That would probably be quite difficult to benchmark though.

---

### Post by SunnyRabbiera on 2008-11-16
> **ad_267 said:**
> I wonder what the difference would be between using Ext3 with Linux and NTFS on Windows, as the Linux drivers for NTFS are probably not as fast and efficient as the Windows ones. The NTFS specification is a Microsoft secret. That would probably be quite difficult to benchmark though.

Well ntfs-3g and stuff like it come close to the surface of NTFS, heck the way ntfs-3g does some stuff makes booting into windows for benchmarking useless.
Anything they can do we can do better :D

---

### Post by FuturePilot on 2008-11-16
Read/write to NTFS on Linux is actually slower because ntfs-3g is a user-space driver and therefore inherently slower than say an in kernel driver.

---

### Post by Martje_001 on 2008-11-16
Very interesting, thank you for sharing!

---

### Post by szaka on 2008-11-16
> **FuturePilot said:**
> Read/write to NTFS on Linux is actually slower because ntfs-3g is a user-space driver and therefore inherently slower than say an in kernel driver.

This is absolutely untrue. The main factors for file systems performance are design and the quality of the implementation.

The above test used a TWO years old, BETA NTFS-3G driver. Today NTFS-3G is often much faster than ext3, especially when transferring very huge files. Ext3 fragments very badly compared to NTFS. Ext4 will solve this problem.

Below are some more recent performance numbers though these are also old, since the NTFS-3G write speed performance record today is 902 MB/sec. All below numbers are in MB/sec. 

```

                      
 block         tmpfs   blkdev blkdev
  size tmpfs  ntfs-3g  ntfs-3g  ext3

   4k    898     88      98     545
   8k    949    185     174     579
  16k    973    255     289     593
  32k    964    388     395     603
  64k    971    556     515     613
 128k    977    687     665     621

```

---

### Post by Sef on 2008-11-16
> The above test used a TWO years old, BETA NTFS-3G driver.

Locked - Necromancing.

---

