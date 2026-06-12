---
title: "Critical: mdadm --grow raid 5 failure"
date: 2008-06-18
forum: Server Platforms
---

### Post by olivero on 2008-06-18
Dear all,

I really need your help to resolve a critical situation:

Ubuntu 8.04 Server

```

root@Kaneda:~# uname -a
Linux Kaneda 2.6.24-19-server #1 SMP Wed Jun 4 17:16:58 UTC 2008 i686 GNU/Linux

```

4 SATA 320 GB disks

```
root@Kaneda:~# fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x731fc1cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         499     4008186   fd  Linux raid autodetect
/dev/sda2             500         624     1004062+  fd  Linux raid autodetect
/dev/sda3             625       38913   307556392+  fd  Linux raid autodetect

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad69db6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         498     4000153+  fd  Linux raid autodetect
/dev/sdb2             499         623     1004062+  fd  Linux raid autodetect
/dev/sdb3             624       38913   307564425   fd  Linux raid autodetect

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5adb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         499     4008186   fd  Linux raid autodetect
/dev/sdc2             500         624     1004062+  fd  Linux raid autodetect
/dev/sdc3             625       38913   307556392+  fd  Linux raid autodetect

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000469f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         499     4008186   fd  Linux raid autodetect
/dev/sdd2             500         624     1004062+  fd  Linux raid autodetect
/dev/sdd3             625       38913   307556392+  fd  Linux raid autodetect

```

MD device setup:

/dev/md0: -l 1 -n 2 -x 1 /dev/sdc1 /dev/sdd1 /dev/sda1(S) on /    - OK
/dev/md1: -l 1 -n 2 -x 1 /dev/sdc2 /dev/sdd2 /dev/sda2(S) on SWAP - OK
/dev/md2: -l 5 -n 4 -x 0 /dev/sd[abcd]3 on /mnt/raid5a - FAILURE

What happened: I had a /dev/md2 raid 5 with 3 disks up and running on /dev/sd[acd]3. In order to get more room, I added another device:

mdadm -a /dev/md2 /dev/sdb3
mdadm --grow /dev/md2 -l5 -n4

The raid went through the critical section and spent a couple of hours reshaping. This morning the system was down, with /dev/md2 unavailable.

mdadm -E /dev/sd[abcd]3 shows all partitions to be clean and reshaping:

```

root@Kaneda:~# mdadm -E /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : 95389433:4c85df37:aa11bcc6:bb47d29a (local to host Kaneda)
  Creation Time : Sat May 24 23:52:36 2008
     Raid Level : raid5
  Used Dev Size : 307556288 (293.31 GiB 314.94 GB)
     Array Size : 922668864 (879.93 GiB 944.81 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

  Reshape pos'n : 222721536 (212.40 GiB 228.07 GB)
  Delta Devices : 1 (3->4)

    Update Time : Wed Jun 18 03:12:24 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : adb99fe9 - correct
         Events : 49410

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8        3        1      active sync   /dev/sda3

   0     0       8       51        0      active sync   /dev/sdd3
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       19        3      active sync   /dev/sdb3
/dev/sdb3:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : 95389433:4c85df37:aa11bcc6:bb47d29a (local to host Kaneda)
  Creation Time : Sat May 24 23:52:36 2008
     Raid Level : raid5
  Used Dev Size : 307556288 (293.31 GiB 314.94 GB)
     Array Size : 922668864 (879.93 GiB 944.81 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

  Reshape pos'n : 222721536 (212.40 GiB 228.07 GB)
  Delta Devices : 1 (3->4)

    Update Time : Wed Jun 18 03:12:24 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : adb99ffd - correct
         Events : 49410

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       19        3      active sync   /dev/sdb3

   0     0       8       51        0      active sync   /dev/sdd3
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       19        3      active sync   /dev/sdb3
/dev/sdc3:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : 95389433:4c85df37:aa11bcc6:bb47d29a (local to host Kaneda)
  Creation Time : Sat May 24 23:52:36 2008
     Raid Level : raid5
  Used Dev Size : 307556288 (293.31 GiB 314.94 GB)
     Array Size : 922668864 (879.93 GiB 944.81 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

  Reshape pos'n : 222721536 (212.40 GiB 228.07 GB)
  Delta Devices : 1 (3->4)

    Update Time : Wed Jun 18 03:12:24 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : adb9a00b - correct
         Events : 49410

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       35        2      active sync   /dev/sdc3

   0     0       8       51        0      active sync   /dev/sdd3
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       19        3      active sync   /dev/sdb3
/dev/sdd3:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : 95389433:4c85df37:aa11bcc6:bb47d29a (local to host Kaneda)
  Creation Time : Sat May 24 23:52:36 2008
     Raid Level : raid5
  Used Dev Size : 307556288 (293.31 GiB 314.94 GB)
     Array Size : 922668864 (879.93 GiB 944.81 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2

  Reshape pos'n : 222721536 (212.40 GiB 228.07 GB)
  Delta Devices : 1 (3->4)

    Update Time : Wed Jun 18 03:12:24 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : adb9a017 - correct
         Events : 49410

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       51        0      active sync   /dev/sdd3

   0     0       8       51        0      active sync   /dev/sdd3
   1     1       8        3        1      active sync   /dev/sda3
   2     2       8       35        2      active sync   /dev/sdc3
   3     3       8       19        3      active sync   /dev/sdb3

```

Now the curious:

mdadm failed to stop the array. It said /dev/md2 stopped, but the device remained and the individual disk partitions remained busy.

mdadm failed to reassemble the array. After several attempts I got:
'Failed to restore critical section for reshape, sorry.'

I compiled and upgraded mdadm to version 2.6.7 (without applying the kernel patch to md.c - I couldn't find the right Kernel sources and config for Hardy). After rebooting the raid comes up inactive with 3 spare drives:
 
```
root@Kaneda:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive raid5 sdb3[0](S) sda3[2](S) sdc3[1](S)
      922668864 blocks

md1 : active raid1 sdd2[0] sda2[2](S) sdc2[1]
      1003968 blocks [2/2] [UU]
      
md0 : active raid1 sdd1[0] sda1[2](S) sdc1[1]
      4008064 blocks [2/2] [UU]
      
unused devices: <none>
```

I stop the raid:
mdadm -S /dev/md2

and try to reassemble it:
mdadm -As 
Segmentation fault

and again:
mdadm -A /dev/md2 /dev/sd[abcd]3
Segmentation fault

and again:
mdadm -I /dev/md2
mdadm: /dev/md2 not permitted by mdadm.conf.

Please, can anybody help me to bring the raid back to life?

Thanks,
Oliver

---

### Post by windependence on 2008-06-18
Well this is gonna sound like I'm avoiding the issue and maybe simplistic but I really mean this. There is no substitute for hardware RAID or IMHO software RAID sucks :)

I have not had good experiences with software RAID at all.

Think about this. If you are having problems now, what if you had critical data on this machine and a drive went bad, or you ran out of space? With hardware RAID, you just insert another drive and it rebuilds. Software RAID does not always work as advertised, not to mention the CPU consumption to manage it.

-Tim

---

### Post by olivero on 2008-06-18
Problem solved.

mdadm throws the segvault in function memcmp() invoked in Assemble.c at around line ~340:

```
int first = st->ss->match_home(st, homehost);
``` 

Tracing back the error, I noticed that in a previous check st was NULL and should have been initialised properly by dup_super(tst). Probably match_home() fails to implement sanity checks on the strings passed in conjunction with a weird implementation in dup_super(). I haven't checked, though. I'll point the owner of the code to this one.

Since I only wanted a working solution, I patched my version of mdadm in order to avoid the faulty code segment resulting in this:

```
root@Kaneda:~/mdadm-2.6.7# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid5 sdd3[0] sdb3[3] sdc3[2] sda3[1]
      615112576 blocks super 0.91 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [====>................]  reshape = 24.1% (74306176/307556288) finish=2226.8min speed=1744K/sec
      
md1 : active raid1 sdd2[0] sda2[2](S) sdc2[1]
      1003968 blocks [2/2] [UU]
      
md0 : active raid1 sdd1[0] sda1[2](S) sdc1[1]
      4008064 blocks [2/2] [UU]
      
unused devices: <none>
```

If anybody ever ends up in the same mess... feel free to drop me a note at oliver(dot)oldach(at)web(dot)de

P.S. This never really touched the issue why the volume failed in the first place. I just got around the re-assembly issue. Once the raid is back online I'll delve into the root cause of the failure.

---

### Post by fjgaude on 2008-06-18
Thanks, Olivero, for solving your own problem... I've never had the issue you faced using raid5 for about three years... what I've learned when what appears to be problems is to umount the array, then stop it. Then you can see what might be going on with individual drives, find their SNs and remove them or it.

I had a drive failed, I faulted it, took it offline, then put another in with the -a command. That works. You can grow array sizes. With the modern motherboards and PCI-E controllers thereon, you have to spend over $300 to get the same hardware card to have the throughput we have.

But no one ever said it was easy, or that it didn't take lots of learning, and patience, but mdadm is mature.

---

### Post by olivero on 2008-06-18
Hi Frank,

thanks for your support. It's **really** good to have a platform that you can actually fix yourself if all else fails. BTW the data on that raid was priceless... the important things in life always are. Aren't they? :-) 

Cheers,
Oliver

---

### Post by fjgaude on 2008-06-18
Well, the thing I've learned playing around, testing mdadm, is once an array is created never try to re-create it else data is lost. It seems that somehow or other we can always get ourselves out of trouble by carefully understanding what the features are.

I truly wish there was a book out... the man pages go far, but I'd like it easier to search and do all kinds of things, like how to re-use drives that have superblocks... I've learned most of it the hard way, by testing before putting an array into service.

We live and learn, daily! <smile>

---

### Post by erik_boi on 2008-09-13
Just had a power outage here while my array was undergoing a --grow. Hoping I have as much luck as you did.

Here is the relevant information
```

erik@server:~$ uname -a
Linux server 2.6.24-12-server #1 SMP Wed Mar 12 22:58:36 UTC 2008 x86_64 GNU/Linux
```

4 SATA 1TB Disks
```

erik@server:~$ sudo fdisk -l
.
.
.
Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e1451

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095beb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0cd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8ede

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      121601   976760001   fd  Linux raid autodetect

```

I have two arrays, the one I'm having issues with is md1. It was in radid5 with the drives sdg1 sdi1 and sdj1.
I added the fourth drive with 

sudo mdadm --add /dev/md1 /dev/sdh1
sudo mdadm --grow --raid-devices=4 /dev/md1

here is the output of /proc/mdstat before the outage while it was growing
```
md1 : active raid5 sdh1[3] sdg1[0] sdj1[2] sdi1[1]
      1953519872 blocks super 0.91 level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      [=>...................]  reshape =  5.2% (50799232/976759936) finish=11634.3min speed=1325K/sec
```

--examine command
```
erik@server:~$ sudo mdadm --examine /dev/sd[ghij]1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : f3c0c7e7:6d6313e4:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 22 06:00:18 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

  Reshape pos'n : 278941056 (266.02 GiB 285.64 GB)
  Delta Devices : 1 (3->4)

    Update Time : Sat Sep 13 17:51:02 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a54fca41 - correct
         Events : 0.293256

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       97        0      active sync   /dev/sdg1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8      113        3      active sync   /dev/sdh1
/dev/sdh1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : f3c0c7e7:6d6313e4:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 22 06:00:18 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

  Reshape pos'n : 278941056 (266.02 GiB 285.64 GB)
  Delta Devices : 1 (3->4)

    Update Time : Sat Sep 13 17:51:02 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a54fca57 - correct
         Events : 0.293256

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      113        3      active sync   /dev/sdh1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8      113        3      active sync   /dev/sdh1
/dev/sdi1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : f3c0c7e7:6d6313e4:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 22 06:00:18 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

  Reshape pos'n : 278941056 (266.02 GiB 285.64 GB)
  Delta Devices : 1 (3->4)

    Update Time : Sat Sep 13 17:51:02 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a54fca63 - correct
         Events : 0.293256

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      129        1      active sync   /dev/sdi1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8      113        3      active sync   /dev/sdh1
/dev/sdj1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : f3c0c7e7:6d6313e4:01f9e43d:ac30fbff (local to host server)
  Creation Time : Tue Jul 22 06:00:18 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 2930279808 (2794.53 GiB 3000.61 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1

  Reshape pos'n : 278941056 (266.02 GiB 285.64 GB)
  Delta Devices : 1 (3->4)

    Update Time : Sat Sep 13 17:51:02 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a54fca75 - correct
         Events : 0.293256

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      145        2      active sync   /dev/sdj1

   0     0       8       97        0      active sync   /dev/sdg1
   1     1       8      129        1      active sync   /dev/sdi1
   2     2       8      145        2      active sync   /dev/sdj1
   3     3       8      113        3      active sync   /dev/sdh1

```

when executing

sudo mdadm --assemble /dev/md1 /dev/sdg1 /dev/sdi1 /dev/sdj1 /dev/sdh1

I get 'Failed to restore critical section for reshape, sorry.'



I imagine I have to do what you did, applying the patches to the newest version and recompile it, thing is I have no idea how to do the patching.

A guide of what you did, the more detailed the better, would be greatly appreciated.

---

### Post by fjgaude on 2008-09-14
> If anybody ever ends up in the same mess... feel free to drop me a note at oliver(dot)oldach(at)web(dot)de

You will likely hav to go to this web site to find out what he did to get the updated mdadm patched. I've neve done it, don't know what to do.

---

### Post by erik_boi on 2008-09-14
That's an email address ;)

I sent an email yesterday when I posted asking if he could take a look at this thread again. Hopefully when he has some free time he'll pop in. Of course, this would happen on a Saturday night...

As a last resort if I can't get mdadm patched I could just boot up a distro with a newer version already installed, do the assemble, let it grow, and then go back to my original install. Right?

---

### Post by fjgaude on 2008-09-14
Good luck with another distro and mdadm. Ubuntu comes with no mdadm, you have to install it from their depository.

Let us know what distro has the latest mdadm in the liveCD. Thanks!

---

### Post by erik_boi on 2008-09-14
My internet connection is atrocious so rather than download another distro and hope it worked I installed 8.04 onto a separate drive and compiled mdadm version 2.6.4 as suggested [here](http://ph.ubuntuforums.com/showpost.php?p=5338861&postcount=6). I issued the --assemble command and everything is running again. 

It's growing and all my data is still there and intact.

Now I can go and try to enjoy the couple hours I have left in my weekend.

Thanks.

edit: Just noticed it's going to finish in about 1/10th the time it was going to take before. Good deal.

---

### Post by olivero on 2008-09-15
Hi Erik,

as I understand it, the reshaping process has two distinct phases: During phase one, the basic administrative information on the disks will be updated to the new format of the raid. In phase two, the data on the drives will be rewritten for all data blocks in order to reflect the new setup.

The primary phase is critical and any error during this phase will render the raid unrecoverable. Again, to my understanding, this is due to the fact that the administrative data on the disks is  inconsistent which in turn makes it impossible to recover the data.

Theoretically, if you had a backup of the administrative blocks, you could restore them and try to recover the data. Also, theoretically, if you had a set of empty disks, you could try to build an exact copy of your raid on them in 3 disk configuration and copy the admin data, hoping that the raid will come back to life in 3 disk mode. The issues are, though, you'd have to know the exact position and structure of the admin data block, which I don't.

My raid was through the critical section and was in data recovery mode. Your Raid seems to have died within the critical section. I'm sorry. It really sounds, like your raid is beyond 'simple' repair. Depending on the value of the data stored, you may want to find some professional data recovery guys, who access the data in raw mode and try to reassemble it.

One word of caution: If you try anything else but reassemble on the raid, your data will be gone for good.

Oliver

---

### Post by erik_boi on 2008-09-15
Thank you for your reply, luckily I've gotten it running again. If anyone finds this thread like I did my solution was to downgrade to a previous version (2.6.4) that didn't have this bug.

It's still finishing up growing but I can see my data so all is well.

Thanks for responding.

---

### Post by fjgaude on 2008-09-15
Okay, it seems mdadm v2.6.4 will solve the only known issue with the program. I trust it will be in Ubuntu 8.10 repository. Of course you can get it from:

```
wget http://freshmeat.net/redir/mdadm/294...dadm-2.6.4.tgz
```

Glad you folks got your arrays up and running after much hassle.

---

### Post by HwyXingFrog on 2008-09-30
Hey Erik, here's my info, I had the same issue as you.  Was adding another 1TB to my raid5, and "poof" power outage.  OOPS!!!

Please, Please, Please help me out.

This is the recently added drive:
```
sudo mdadm --add /dev/md0 /dev/sde1
```

I know it was at least 70% done when the computer got powered off.

And here's some info on my system:

```
:~$ uname -a
Linux raidserver 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

```
:~$ mdadm --version
mdadm - v2.6.3 - 20th August 2007
```


```
:~$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : dd475f4e:4a38cf3a:0ac83c7a:b2cbefd1
  Creation Time : Mon Jul  7 08:10:45 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

  Reshape pos'n : 2812147200 (2681.87 GiB 2879.64 GB)
  Delta Devices : 1 (4->5)

    Update Time : Tue Sep 30 19:16:53 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a92ccbc3 - correct
         Events : 0.1116600

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       17        2      active sync   /dev/sdb1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3     254        0        3      active sync   /dev/vg0/lvm0
   4     4       8       65        4      active sync   /dev/sde1
:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : dd475f4e:4a38cf3a:0ac83c7a:b2cbefd1
  Creation Time : Mon Jul  7 08:10:45 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

  Reshape pos'n : 2812147200 (2681.87 GiB 2879.64 GB)
  Delta Devices : 1 (4->5)

    Update Time : Tue Sep 30 19:16:53 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a92ccbcf - correct
         Events : 0.1116600

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8       33        0      active sync   /dev/sdc1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3     254        0        3      active sync   /dev/vg0/lvm0
   4     4       8       65        4      active sync   /dev/sde1
:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : dd475f4e:4a38cf3a:0ac83c7a:b2cbefd1
  Creation Time : Mon Jul  7 08:10:45 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

  Reshape pos'n : 2812147200 (2681.87 GiB 2879.64 GB)
  Delta Devices : 1 (4->5)

    Update Time : Tue Sep 30 19:16:53 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a92ccbe1 - correct
         Events : 0.1116600

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       49        1      active sync   /dev/sdd1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3     254        0        3      active sync   /dev/vg0/lvm0
   4     4       8       65        4      active sync   /dev/sde1
:~$ sudo mdadm --examine /dev/vg0/lvm0
/dev/vg0/lvm0:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : dd475f4e:4a38cf3a:0ac83c7a:b2cbefd1
  Creation Time : Mon Jul  7 08:10:45 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

  Reshape pos'n : 2812147200 (2681.87 GiB 2879.64 GB)
  Delta Devices : 1 (4->5)

    Update Time : Tue Sep 30 19:16:53 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a92cccaa - correct
         Events : 0.1116600

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3     254        0        3      active sync   /dev/vg0/lvm0

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3     254        0        3      active sync   /dev/vg0/lvm0
   4     4       8       65        4      active sync   /dev/sde1

:~$ sudo mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 00.91.00
           UUID : dd475f4e:4a38cf3a:0ac83c7a:b2cbefd1
  Creation Time : Mon Jul  7 08:10:45 2008
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0

  Reshape pos'n : 2812147200 (2681.87 GiB 2879.64 GB)
  Delta Devices : 1 (4->5)

    Update Time : Tue Sep 30 19:16:53 2008
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a92ccbf7 - correct
         Events : 0.1116600

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8       65        4      active sync   /dev/sde1

   0     0       8       33        0      active sync   /dev/sdc1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       8       17        2      active sync   /dev/sdb1
   3     3     254        0        3      active sync   /dev/vg0/lvm0
   4     4       8       65        4      active sync   /dev/sde1

```

And then here's the issue....

```
:~$ sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sdb1 /dev/vg0/lvm0 /dev/sde1
mdadm: Failed to restore critical section for reshape, sorry.
```

Darn,Darn,Darn..........Double Darn (Not my exact words, but I'm sure you can figure it out)

Thanks
Highway Crossing Frog

---

### Post by HwyXingFrog on 2008-10-01
Still Broken, I think it may be unrecoverable now though, I upgraded mdadm, and now I get a segfault.

```
:~$ mdadm --version
mdadm - v2.6.7 - 6th June 2008
```

```
:~$ sudo mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sdb1 /dev/vg0/lvm0 /dev/sde1
Segmentation fault
```

```
Oct  1 09:42:51 raidserver kernel: [ 1102.761620] mdadm[7794]: segfault at 00000038 eip 08062d78 esp bfeed7f0 error 4
```

Any Ideas Anyone??

---

### Post by HwyXingFrog on 2008-10-03
WHOOHOO Got it fixed, just installed mdadm 2.6.4 found here:

[https://launchpad.net/ubuntu/intrepid/i386/mdadm/2.6.4-2ubuntu1](https://launchpad.net/ubuntu/intrepid/i386/mdadm/2.6.4-2ubuntu1)

Here's the actual link to the file:

[http://launchpadlibrarian.net/14938100/mdadm_2.6.4-2ubuntu1_i386.deb](http://launchpadlibrarian.net/14938100/mdadm_2.6.4-2ubuntu1_i386.deb)

You may need to install some dependencies described in the first link.

WHEW!

---

### Post by santhony on 2008-11-02
I'm coming from a similiar situation..  I just reshaped my array, added a new drive to increase my Raid5 Size.  I just got the drive back.. wheew.. thought I lost it for good..

My questions is this.. I never got to the last commands of completing the grow, expanding the directory structure.

fsck.ext3 /dev/md1
resize2fs /dev/md1

From what I see right now, it doesn't look like I have the new space available yet....  

Where do I continue at??

---

### Post by Lutefisk on 2008-12-20
Here we go, my first cup of Ubuntu :-)

This thread really saved my day. After a reboot while growing a RAID5 on 8.04, I had the same "Failed to restore critical section for reshape". Installing mdadm 2.6.4 fixed the problem.

One question that is not addressed in the above posts is what would be the "clean" way to install mdadm 2.6.4; having already wasted enough time with this first seemingly failed experiment to grow my RAID I was hesitant to do an "aptitude purge" on the mdadm package, because dpkg -L shows it contains a lot more files than those installed when running make install on the original mdadm-2.6.4 tarball.

In the end what I did was "sudo aptitude hold mdadm" before installing mdadm from the original source, which I believe should prevent the updater from later overwriting the manually installed 2.6.4 mdadm binary.

---

### Post by Lutefisk on 2008-12-20
While I am at it, in case there are others who read this who have the same issue - after the relief that the RAID came back online came the surprise how horribly slow the reshaping process was running, which had ETA 6-7 days to complete ("cat /proc/mdadm").

That is until I came across [this thread]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/1056831.html") which explains how you can tune some parameters driving performance. What I did was:

```

echo 20000000 > /proc/sys/dev/raid/speed_limit_max
echo 25000 > /proc/sys/dev/raid/speed_limit_min

```

This brought the ETA down to ~20 hours

---

### Post by obscure_detour on 2009-03-19
Um just an FYI, this thread is like gold.  Thanks for all the knowledge.

Cheers.

---

### Post by jeyno on 2009-04-04
I've just spent the past 2 weeks of spare time (!) muddling through this issue and agree - it's a golden thread.  A true lifesaver!

My Ubuntu 8.04 64-bit server failed to restart after a grow operation was unexpectedly stopped mid-way.  The ONLY version of mdadm I could recover the grow operation with was mdadm 2.6.4 - using 2.6.7 just segfaulted, as did a number of other versions.  I was unable to locate a 2.6.4 deb package (for amd64) from either Ubuntu or Debian repositories.  So my approach has been to:

- boot from the Ubuntu 8.04 Workstation LiveCD
- download the mdadm 2.6.4 source from

[http://www.kernel.org/pub/linux/utils/raid/mdadm/mdadm-2.6.4.tar.gz](http://www.kernel.org/pub/linux/utils/raid/mdadm/mdadm-2.6.4.tar.gz)

extract the archive 

$ tar xvzf mdadm-2.6.4.tar.gz

then from the directory

$ sudo make
$ sudo make install

after which I was able to 

$ sudo mdadm --assemble /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3

and see the reshape operation in flight once again.

So a few things emerge from this:

BEWARE Ubuntu 8.04 Server Users using mdadm for software RAID !
  
- the mdadm grow operation takes a long time to complete - in my case, a 4 disk RAID5 array with 4x1TB drives the resulting reshape was a multi-day process.
- during this time your system is in a highly vulnerable state - if the system stops you too will enjoy the total system failure experience that I and others have mused about in this thread
- there is no mdadm package currently available to Ubuntu 8.04 (IA 64-bit) server users which can be used to recover this situation
- the newest version of mdadm (i.e. that provided under Ubuntu long term support) does not fix this.  More long term support required please!!
- the only version found to recover this is (2.6.4) which must be downloaded as source and compiled

The real issue highlighted here is the fragility of the software RAID environment provided by mdadm.  mdadm - and RAID in general - is supposed to enable failover and redundancy and improve overall resilience of disk storage.  Issues like this one defeat its entire purpose.

---

### Post by jeyno on 2009-04-05
To supplement my last posting it occurs to me that others may find the next step a problem too.

So here's the issue: having completed the reshape, the Ubuntu 8.04 server still fails to boot - because at boot the mdadm configuration file buried within the initrd image file did not match reality any more.

Now I dare say there are a number of ways to fix this, but here's the way I used...

- boot using the LiveCD as before;
- install mdadm from the standard package repository (because it's not on the LiveCD) ... note that this time, it's not necessary to go download 2.6.4 and compile / install, because we don't need to restart the reshape;
- assemble my set of arrays using

$ sudo bash

because we need to be root for pretty much everything here, then

$ mdadm --assemble /dev/md0 /dev/sd[abc]1
$ mdadm --assemble /dev/md1 /dev/sd[abcd]3
$ mdadm --assemble /dev/md2 /dev/sd[abcde]2

- my boot time partition was on the /dev/md0 RAID1 array so I gained access to it by

$ mkdir /tmp/boot
$ mount -t ext3 /dev/md0 /tmp/boot

- now to get access to the mdadm.conf file causing the trouble, we extract the image from the initrd which will not boot

$ mkdir /tmp/extract
$ cd /tmp/extract
$ gzip -dc /tmp/boot/initrd-2.6.24-23-generic | cpio -id

which will extract the image to the current directory.  once here, we can edit the configuration file

$ gedit ./etc/mdadm/mdadm.conf

Once here, I must recommend that you verify the num-devices and UUID values listed for the ARRAY declarations.  Check these against the values you see from the display command e.g.

$ mdadm -D /dev/md1

When you are confident that the UUID and num-devices entries match correctly, save this file (and close gedit if you used this).

Create a new initrd from the updated directory contents.

$ find ./ | cpio -H newc -o > /tmp/boot/new-initrd.cpio
{whatever} blocks
$ cd /tmp/boot
$ gzip new-initrd.cpio
$ mv new-initrd.cpio.gz new-initrd.img

Now you can try the reboot ... when you do, you should hit ESC when the grub bootloader offers this option, so that you can ask grub to use your new initrd image.  I had to select the initrd= line, press e to edit it, then after changing the filename I pressed b to boot from it.

Then ... wahey!  Finally booted into the regular environment!

Now before all the spanners get polished and put back in the toolbox there is one last job to do....

$ sudo bash

again.

Edit the "real" /etc/mdadm/mdadm.conf and repeat the updates made earlier. 

Now generate an initrd from the currently booted environment so that the standard grub boot will work.

$ dpkg-reconfigure mdadm

and at the prompts, select the mdadm behaviour that suits you.  If you don't know what to choose, just take what it gives you because it will still work.

Now reboot and watch your system come up without the need for intensive care.

I hope someone else finds this helpful one day and gets to spend their day doing what they wanted to do, instead of having to scour the Web for threads of hope....

---

### Post by fjgaude on 2009-04-05
Thanks, jeyno, for your reports... many will find them useful.

I do believe, as time moves along, mdadm will be as rebust as a hardware raid card, but it has taken time to get to where it presently is. The real issue these days is the size of the hard drives and the time taken to resync. This goes for both hardware and software. I think the latest version of mdadm being shipped with 8.10 and 9.04 doesn't have the issue you and others have faced with failure in mid-stream. <smile>

It wasn't that long ago when 32GB was a huge drive, and raid recovery was quick. Not anymore, because of our access to really huge drives.

So be it! Have backups of everything important. I use three, as said so many times and places.

---

### Post by gilforsyth on 2009-04-05
This thread has been a huge help and gotten me closer to recovery that I've been in the last somewhat nerve-wracking 72 hours.  On Intrepid 8.10 64-bit I compiled and installed 2.6.4 and finally avoided segfaults only to have this happen:
```

mythbox@mythbox-desktop:~$ sudo mdadm --assemble --verbose /dev/md0 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda3 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb3 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdc3 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdd3 is identified as a member of /dev/md0, slot 3.
mdadm: added /dev/sdb3 to /dev/md0 as 1
mdadm: added /dev/sdc3 to /dev/md0 as 2
mdadm: added /dev/sdd3 to /dev/md0 as 3
mdadm: added /dev/sda3 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
mythbox@mythbox-desktop:~$ cat /proc/mdstat
Personalities : 
md0 : inactive sda3[0](S) sdd3[3](S) sdc3[2](S) sdb3[1](S)
      3870090240 blocks
       
unused devices: <none>
mythbox@mythbox-desktop:~$ 

```
It seems like it's adding all 4 drives but then it can only start 2?  The UUID's all check out, they all claim to be clean and actively synced.  

Help?

---

### Post by fjgaude on 2009-04-05
> It seems like it's adding all 4 drives but then it can only start 2? The UUID's all check out, they all claim to be clean and actively synced.

Well, gilforsyth, the only thing I can think of is to try a force assemble:

```
sudo mdadm --assemble --force /dev/md0 /dev/sd[abcd]3
```

then do this:

```
sudo mdadm -D /dev/md0
```

Let us know how you do. There are more things to try, maybe. <smile>

---

### Post by gilforsyth on 2009-04-05
Why I hadn't thought of that I'm not quite sure, but thank you so very very much.

---

### Post by fjgaude on 2009-04-05
> **gilforsyth said:**
> Why I hadn't thought of that I'm not quite sure, but thank you so very very much.

You mean that's all it took to get the array healthy?

---

### Post by su1c1de on 2009-04-05
Hey guys

just a little tip...

today i started growing my raid from 3 to 5 tb and then all the sudden my system hdd failed and after the reinstall of a new system i could not resume the grow on hardy.

but in between i was using systemrescuecd for some data recovery and i noticed that it automatically resumed the grow in background. systemrescuecd 1.1.4 comes with mdadm 2.6.4 and it just works out of the box :)

it also has the higher speed values from the other thread so it is like 10 times faster than before

so if you have any trouble and dont need your machine for like 24hs then just use systemrescuecd :)

hope that is some usefull info

---

### Post by fjgaude on 2009-04-05
> but in between i was using systemrescuecd for some data recovery and i noticed that it automatically resumed the grow in background. systemrescuecd 1.1.4 comes with mdadm 2.6.4 and it just works out of the box

I never knew that systemrescue CD came with 2.6.4, out of the box, what box?

Pray tell, from where did you get such?

---

### Post by obscure_detour on 2009-04-09
Thanks for any help and sorry to bombard this thread. I just want some more info on growing mdadm arrays as my new drive is going to be here soon.  I just rebuilt my server using Ubuntu Server 8.04.2 x64 and taking this thread into consideration it seems like not necessarily a good idea.  I´m about to add a 4th drive to the array and try to grow it.  Will I run into the same issues as posted?  Should I just reinstall 32bit Ubuntu desktop for better compatibility and less issues?  Is it also recommended to just go for 8.10 and/or 9.04?

After installation, I was able to --assemble my old raid array after searching threads of hope including this one.  The first issue I encountered was that the ¨md¨ service wasn´t starting at boot.

Added *modprobe md* to /etc/rc.local.  After every reboot the array still wasn´t accessible.  

Added *mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1* to /etc/rc.local.

I had already added */dev/md0 /raid auto defaults 0 3* to fstab, but the array wasn´t being mounted at start up. (I think, correct me if I´m wrong, it wasn´t being mounted because rc.local loads too late, so the array wasn´t being assembled before fstab was loaded.)  

Of course *mount -a* was a simple fix in that case.  So that was added to /etc/rc.local as well.

This all seems very silly IMO, I´ve never used /etc/rc.local before.  When I originally built my server with different hardware, the same array and using Ubuntu 8.04 Desktop I never had any of these issues.  What is the better way of going about what I did above?  I also did a *mdadm --version* and found out I´m using mdadm 2.6.3 for some reason.  I´m sure that isn´t recommended, right?

---

### Post by windependence on 2009-04-10
I know Frank won't agree with me on this but just go out and buy a cheap hardware RAID controller. It's so much easier. They are really starting to get cheap. Just make sure you don't get a "software RAID on a chip" card, you want a real hardware RAID solution. (Sorry Frank).

-Tim

---

### Post by obscure_detour on 2009-04-10
> **windependence said:**
> I know Frank won't agree with me on this but just go out and buy a cheap hardware RAID controller. It's so much easier. They are really starting to get cheap. Just make sure you don't get a "software RAID on a chip" card, you want a real hardware RAID solution. (Sorry Frank).

-Tim

I don´t agree with you either :rolleyes:

I´ve had nothing but good experience with Linux Software RAID.  I just upgraded my server´s RAM/CPU. Doubled my cached read speeds.  I´d love to see you upgrade performance on a hardware solution.  :)

Bottom line, they both have their needs, advantages and disadvantages.  Depending on needs, either solution (software/hardware) can work very well.

*-obscure detour*

---

### Post by fjgaude on 2009-04-12
For growing arrays this is a good link:

[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

Let us know how you are doing with your new drive.

---

### Post by windependence on 2009-04-15
> **obscure_detour said:**
> I don´t agree with you either :rolleyes:

I´ve had nothing but good experience with Linux Software RAID.  I just upgraded my server´s RAM/CPU. Doubled my cached read speeds.  I´d love to see you upgrade performance on a hardware solution.  :)

Bottom line, they both have their needs, advantages and disadvantages.  Depending on needs, either solution (software/hardware) can work very well.

*-obscure detour*

I can, and do get better performance from true hardware RAID than software RAID. In real life, RAID is used many times for hardware failure protection as well as pure performance. I run (real) production servers with hardware as well as software RAID and both are good in the correct application. Neither is the "ultimate" solution. 

With hardware RAID, I can boot from the RAID array if I want to, and I can change drives with little or no interruption on my server. I can also expand my array MUCH easier than with software RAID no matter what method you use. This is what the OP was asking about and I offered a suggestion.

-Tim

---

### Post by u-slayer on 2009-10-10
I was growing my raid 5 array and like an Idiot knocked the power strip, killing the computer. I rebooted and mdadm gave me a segmentation fault when I tried to assemble it.

I just downloaded version 3 of mdadm from [http://www.kernel.org/pub/linux/utils/raid/mdadm/](http://www.kernel.org/pub/linux/utils/raid/mdadm/) and ran make install. Work like a charm. Even on 64-bit.

It is a bit slow tho.

---

### Post by windependence on 2009-10-10
Frank is the absolute expert on software RAID. I'm wondering if he has any ideas about whether increasing block size in the array would make expansion or rebuild time any quicker.

-Tim

---

### Post by fjgaude on 2009-10-11
Block size increae... can't say. It's the huge drives that are the issue now days. I trust mdadm will somehow take them into consideration. I have tried 3.0 yet, as I've had no need.

Tim, I don't have anything against hardware raid, except cost. For the same throughput software is a good way to go, if you know what you are doing. If not, get the expensive hardware card.

Also remember, failure rate increases as you add hardware. If CPU goes so does the card. For those interested there's analyses you can find to help you determine which way to go.

---

### Post by windependence on 2009-10-11
I have changed my thinking a bit on software RAID since I wrote those posts, primarily from reading your posts. There ARE cheap hardware RAID cards these days and they aren't really that bad. Unfortunately for me, I have to use the more expensive ones because I use ESXi on almost all my installs now. Version 4 has added some cheaper controllers, but you must use 64 bit hardware with ESXi 4. Not all my hardware is that new.

I do have some software RAID running on a SAN I have set up with FreeBSD. Totally different software RAID, but it seems to be stable as everything else *BSD. :-)

Thanks for voicing your opinion.

-Tim

---

### Post by Fcon_Vpro on 2010-01-19
This thread helped a lot. Just thought Id add to it in case anyone else gets stuck.

I had to use the --force command and had to use version 2.6.4. 
2.6.7 or whatever the latest 8.10 version is wouldnt work for me.
Also couldnt get 2.6.4 to compile on 8.04 so I also upgraded to 8.10

---

### Post by u-slayer on 2010-12-05
If anyone is reading this I had my power go out while expanding an array from 4 to 5 drives. Everytime, I tried to assemble the array, I got a seg fault error.

Well I downloaded mdadm 3.1 from the natty repos:

[http://packages.ubuntu.com/search?searchon=names&keywords=mdadm](http://packages.ubuntu.com/search?searchon=names&keywords=mdadm)

and everything seems to be working now.

(I tried 2.6.7 and it seg faulted on me. 3.1 worked great)

---

