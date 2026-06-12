---
title: "Help reassembling an array!!!!"
date: 2012-01-25
forum: Server Platforms
---

### Post by drpsycho on 2012-01-25
Hi, I'm having problems reassembling and array, when I try mdadm --assemble --scan I get the following:

mdadm: failed to add /dev/sdl1 to /dev/md2: Device or resource busy
mdadm: failed to add /dev/sdi1 to /dev/md2: Device or resource busy
mdadm: failed to add /dev/sdg1 to /dev/md2: Device or resource busy
mdadm: failed to add /dev/sdh1 to /dev/md2: Device or resource busy
mdadm: /dev/md2 assembled from 1 drive and 5 spares - not enough to start the array.

It was supposed to be an array with 9 devices and 3 spares, here is the section in mdadm.conf for this array:

ARRAY /dev/md2 level=raid5 num-devices=9 UUID=f4bf684d:ff6a6faf:240b9b9a:42175a7c
   spares=3


Here is the ouptut of mdstat (the array in question is md2, the others are working perfectly):

md2 : inactive sdi1[5](S) sdg1[6](S) sdh1[7](S) sdd1[3](S) sda[9](S) sdb[10](S) sdc[11](S) sde[12](S) sdk[13](S)
      6593007040 blocks

md1 : active raid0 cciss/c0d4p1[1] cciss/c0d3p1[0]
      286674816 blocks 64k chunks

md0 : active raid1 cciss/c0d2p2[2](S) cciss/c0d0p3[0] cciss/c0d5p2[3](S) cciss/c0d1p2[1]
      70578112 blocks [2/2] [UU]


If you need more info just ask.

---

### Post by rubylaser on 2012-01-25
The first step is to stop the array.

```
mdadm --stop /dev/md2
```

and if all of your disks are healthly, you should be able to force it back together like this.
```
mdadm --assemble --run --force /dev/md0 /dev/sd[abdefghijk]1
```

Then, you should be able to mount the array.
```
mount -a
```

---

### Post by drpsycho on 2012-01-26
> **rubylaser said:**
> The first step is to stop the array.

```
mdadm --stop /dev/md2
```and if all of your disks are healthly, you should be able to force it back together like this.
```
mdadm --assemble --run --force /dev/md0 /dev/sd[abdefghijk]1
```Then, you should be able to mount the array.
```
mount -a
```

The comand "mdadm --assemble --run --force /dev/md2 /dev/sd[abdefghijk]1" returned this:

```
mdadm: no recogniseable superblock on /dev/sdj1
mdadm: /dev/sdj1 has no superblock - assembly aborted
```

---

### Post by rubylaser on 2012-01-26
what's the output of this?

```
mdadm -E /dev/sd[abdefghijk]1
```

---

### Post by drpsycho on 2012-01-27
> **rubylaser said:**
> what's the output of this?

```
mdadm -E /dev/sd[abdefghijk]1
```


mdadm -E /dev/sd[abcdefghijkl]1 returns this:

```

mdadm: No md superblock detected on /dev/sdj1.
/dev/sdl1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4bf684d:ff6a6faf:240b9b9a:42175a7c
  Creation Time : Mon May 17 13:45:24 2010
     Raid Level : raid5
  Used Dev Size : 732555200 (698.62 GiB 750.14 GB)
     Array Size : 5860441600 (5588.95 GiB 6001.09 GB)
   Raid Devices : 9
  Total Devices : 11
Preferred Minor : 2

    Update Time : Tue Jan 24 18:01:02 2012
          State : active
 Active Devices : 6
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 5
       Checksum : ca5919f6 - correct
         Events : 2461117

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8      177        4      active sync   /dev/sdl1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8       81        3      active sync
   4     4       8      177        4      active sync   /dev/sdl1
   5     5       8      129        5      active sync
   6     6       8       97        6      active sync
   7     7       8      113        7      active sync
   8     8       0        0        8      faulty removed
   9     9       8      160        9      spare   /dev/sdk
  10    10       8       64       10      spare   /dev/sde
  11    11       8       48       11      spare   /dev/sdd
  12    12       8       32       12      spare   /dev/sdc
  13    13       8       16       13      spare   /dev/sdb


```

---

### Post by rubylaser on 2012-01-27
> **drpsycho said:**
> mdadm -E /dev/sd[abcdefghijkl]1 returns this:

```

mdadm: No md superblock detected on /dev/sdj1.
/dev/sdl1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4bf684d:ff6a6faf:240b9b9a:42175a7c
  Creation Time : Mon May 17 13:45:24 2010
     Raid Level : raid5
  Used Dev Size : 732555200 (698.62 GiB 750.14 GB)
     Array Size : 5860441600 (5588.95 GiB 6001.09 GB)
   Raid Devices : 9
  Total Devices : 11
Preferred Minor : 2

    Update Time : Tue Jan 24 18:01:02 2012
          State : active
 Active Devices : 6
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 5
       Checksum : ca5919f6 - correct
         Events : 2461117

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8      177        4      active sync   /dev/sdl1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8       81        3      active sync
   4     4       8      177        4      active sync   /dev/sdl1
   5     5       8      129        5      active sync
   6     6       8       97        6      active sync
   7     7       8      113        7      active sync
   8     8       0        0        8      faulty removed
   9     9       8      160        9      spare   /dev/sdk
  10    10       8       64       10      spare   /dev/sde
  11    11       8       48       11      spare   /dev/sdd
  12    12       8       32       12      spare   /dev/sdc
  13    13       8       16       13      spare   /dev/sdb


```

Where is all the other output from your other devices? abcde, etc...

---

### Post by drpsycho on 2012-01-27
> **rubylaser said:**
> Where is all the other output from your other devices? abcde, etc...

For a very stange reason there isn't sd[abcdefghik]1 anymore. The only ones that exist now are sdj1 and sdl1. Output of ls /dev/sd*:

```
/dev/sda  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sde  /dev/sdf  /dev/sdg  /dev/sdh  /dev/sdi  /dev/sdj  /dev/sdj1  /dev/sdk  /dev/sdl  /dev/sdl1
```Output of mdadm -E /dev/sdj1:

```
mdadm -E /dev/sdj1
```Output of  mdadm -E /dev/sdl1:

```
/dev/sdl1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f4bf684d:ff6a6faf:240b9b9a:42175a7c
  Creation Time : Mon May 17 13:45:24 2010
     Raid Level : raid5
  Used Dev Size : 732555200 (698.62 GiB 750.14 GB)
     Array Size : 5860441600 (5588.95 GiB 6001.09 GB)
   Raid Devices : 9
  Total Devices : 11
Preferred Minor : 2

    Update Time : Tue Jan 24 18:01:02 2012
          State : active
 Active Devices : 6
Working Devices : 11
 Failed Devices : 0
  Spare Devices : 5
       Checksum : ca5919f6 - correct
         Events : 2461117

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8      177        4      active sync   /dev/sdl1

   0     0       0        0        0      removed
   1     1       0        0        1      faulty removed
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8       81        3      active sync
   4     4       8      177        4      active sync   /dev/sdl1
   5     5       8      129        5      active sync
   6     6       8       97        6      active sync
   7     7       8      113        7      active sync
   8     8       0        0        8      faulty removed
   9     9       8      160        9      spare   /dev/sdk
  10    10       8       64       10      spare   /dev/sde
  11    11       8       48       11      spare   /dev/sdd
  12    12       8       32       12      spare   /dev/sdc
  13    13       8       16       13      spare   /dev/sdb

```

---

### Post by drpsycho on 2012-02-06
Any clues??

---

### Post by rubylaser on 2012-02-06
Did you have a mix of devices using partitions and raw devices for your array?  It looks like it based off or you mdadm -E on some of the disks.  What do these say?

[CODE]mdadm -E /dev/sd[bcdek]/CODE]

I'm hoping you have a backup, or a good understanding of how your array was originally structured to have a chance to put this back together.  Also, have you verified all of your disks with smartmontools to figure out what disk(s) are bad?

---

### Post by drpsycho on 2012-02-06
> **rubylaser said:**
> Did you have a mix of devices using partitions and raw devices for your array?  It looks like it based off or you mdadm -E on some of the disks.  What do these say?

[CODE]mdadm -E /dev/sd[bcdek]/CODE]

I'm hoping you have a backup, or a good understanding of how your array was originally structured to have a chance to put this back together.  Also, have you verified all of your disks with smartmontools to figure out what disk(s) are bad?


It was supposed to be made only with devices, no partitions. All this stuff started to occur when i tried to configure multipath. When I added another hba controller to the server the array started do go crazy and the names of the devices changed. For example: sda changed to sdaa and sdab, and sdb changed to sdac and sdad and this made the array degraded. So I decided to not use multipath but the names didn't change to normal and some errors started to occur like "sd[x] has the same superblock as sd[y]" and following some advice in other forums i did this:[FONT=Verdana] [/FONT]mdadm --zero-superblock /dev/[FONT=Verdana]sd[abcdefghijkl]. This error disappeared but yet I couldnt reassemble the array so i followed this http://kevin.deldycke.com/2007/03/how-to-recover-a-raid-array-after-having-zero-ized-superblocks/ and I think this erased all my data because the array reassembled normally but didn't find my filesystem[/FONT]

---

