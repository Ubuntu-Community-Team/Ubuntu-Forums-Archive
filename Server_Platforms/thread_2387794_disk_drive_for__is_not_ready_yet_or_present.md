---
title: "disk drive for / is not ready yet or present"
date: 2018-03-23
forum: Server Platforms
---

### Post by carbon13 on 2018-03-23
Hi,

I'm running a really old version of ubuntu 14.01 on an old pc with a 4tb raid array serving as a nas for my home use. Power just went out and upon reboot I'm getting this error (fstab attached). Something wrong with /home (wrong drive or read only). I would appreciate if anyone can help me fix this. Thanks!

---

### Post by kerry_s on 2018-03-23
fsck /dev/sda

---

### Post by carbon13 on 2018-03-23
/dev/sda is in use

---

### Post by kerry_s on 2018-03-23
are you still at that root shell?
unmount /dev/sda

---

### Post by carbon13 on 2018-03-23
I get an option to skip and boot to guest login (but can't log in) or m to a manual shell. Tried command from there.

Thx for helping

---

### Post by oldfred on 2018-03-23
Power failure often causes file corruption, so fsck is the first thing to try.

But you cannot run fsck on a drive, but on partitions.

And since RAID, you need to run the fsck on the RAID partition(s).

---

### Post by carbon13 on 2018-03-24
I can't seem to unmount or run fsck on the partition.

---

### Post by carbon13 on 2018-03-24
Progress. I was able to boot Ubuntu from CD. I can open gparted. See disks but can't access the files on raid partition.

---

### Post by carbon13 on 2018-03-24
Ok. Here's my situation. Ubuntu is located on a separate 80gb drive. I then have a separate raid 5 array of 4x1tb disks. 

Upon bootup, it can't find /home. In gparted I see the 80gb drive no problem and all the raid devices separately but not the combined raid partition. 

Not sure what to do next. Really need to recover my data on here. Some backed up but some is not. Please help!

---

### Post by oldfred on 2018-03-24
Moved to the server sub-forum where those who know RAID and possible solutions may be able to help.

I know horse is out of barn and late to close barn door, but you must have missed this. RAID is not backup, so you still need a good backup procedure.
 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by darkod on 2018-03-24
First, try to calm down little otherwise running a wrong command can destroy the data.
From live mode open terminal and post the output of:
```
sudo blkid
```

That should show us the raid partitions so that we know what to work with.

---

### Post by carbon13 on 2018-03-24
Thanks for your help!

---

### Post by darkod on 2018-03-25
OK. So, your OS is on sda1 and then you have two raid arrays:
sdb1-sdc1-sdd1-sde1
sdb2-sdc2-sdd2-sde2

To use any mdadm commands in live mode, you need to add the package first. You always need to do this after rebooting in live mode. After that we can check the superblock info for each array members:
```
sudo apt-get install mdadm
sudo mdadm -E /dev/sd[bcde]1
sudo mdadm -E /dev/sd[bcde]2
```

To use apt-get you will have to connect the machine to internet in live mode. I suggest you do that anyway because it's better to post the text output of the commands here, inside CODE tags, instead of pictures. The mdadm output will span mutiple screens, you won't be able to capture it on a photo.

Copy-paste the output here and it will show us more details of the array members.

---

### Post by carbon13 on 2018-03-25
Ok thanks. I'm fairly certain that there should be only 1 raid array. I know physically there is only one. Is it possible  the second is a partition on the raid?

---

### Post by carbon13 on 2018-03-25
Here's the results:

```
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sd[bcde]1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 546e13bc:38e80be6:3a7a41f3:7f0087f1
           Name : vault:0
  Creation Time : Wed Aug  5 01:05:02 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 2144256 (1047.18 MiB 1097.86 MB)
     Array Size : 3214848 (3.07 GiB 3.29 GB)
  Used Dev Size : 2143232 (1046.68 MiB 1097.33 MB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 871a2dc7:40891fed:b523fc56:596d45ed

    Update Time : Sun Mar  4 05:57:39 2018
       Checksum : 45ab55d3 - correct
         Events : 98

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 546e13bc:38e80be6:3a7a41f3:7f0087f1
           Name : vault:0
  Creation Time : Wed Aug  5 01:05:02 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 2144256 (1047.18 MiB 1097.86 MB)
     Array Size : 3214848 (3.07 GiB 3.29 GB)
  Used Dev Size : 2143232 (1046.68 MiB 1097.33 MB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 2e201845:eb24c39a:55dc7e9b:917c6aff

    Update Time : Sun Mar  4 05:57:39 2018
       Checksum : c7e1befd - correct
         Events : 98

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 546e13bc:38e80be6:3a7a41f3:7f0087f1
           Name : vault:0
  Creation Time : Wed Aug  5 01:05:02 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 2144256 (1047.18 MiB 1097.86 MB)
     Array Size : 3214848 (3.07 GiB 3.29 GB)
  Used Dev Size : 2143232 (1046.68 MiB 1097.33 MB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 34a34254:44b97806:d99ddccd:ecbce365

    Update Time : Sun Mar  4 05:57:39 2018
       Checksum : db98d83b - correct
         Events : 98

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 546e13bc:38e80be6:3a7a41f3:7f0087f1
           Name : vault:0
  Creation Time : Wed Aug  5 01:05:02 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 2144256 (1047.18 MiB 1097.86 MB)
     Array Size : 3214848 (3.07 GiB 3.29 GB)
  Used Dev Size : 2143232 (1046.68 MiB 1097.33 MB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : f3e319fc:6517cf0a:22675f40:2cce17c1

    Update Time : Sun Mar  4 05:57:39 2018
       Checksum : 557d51a6 - correct
         Events : 98

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
ubuntu@ubuntu:~$ 

```

and second...

```
ubuntu@ubuntu:~$ sudo mdadm -E /dev/sd[bcde]2
/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecf60edb:32ea67bd:4165f05a:f03db118
           Name : vault:1
  Creation Time : Wed Aug  5 01:06:22 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1951113216 (930.36 GiB 998.97 GB)
     Array Size : 2926668288 (2791.09 GiB 2996.91 GB)
  Used Dev Size : 1951112192 (930.36 GiB 998.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6cea51bb:4061baea:3a440bc3:5b69d450

    Update Time : Mon Aug  5 18:02:11 2002
       Checksum : 5742e88a - correct
         Events : 8323

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA. ('A' == active, '.' == missing)
/dev/sdc2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecf60edb:32ea67bd:4165f05a:f03db118
           Name : vault:1
  Creation Time : Wed Aug  5 01:06:22 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1951113216 (930.36 GiB 998.97 GB)
     Array Size : 2926668288 (2791.09 GiB 2996.91 GB)
  Used Dev Size : 1951112192 (930.36 GiB 998.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e1e80185:48bf0f3c:4980689e:06e850eb

    Update Time : Mon Aug  5 18:02:16 2002
       Checksum : e822ffc8 - correct
         Events : 8327

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sdd2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecf60edb:32ea67bd:4165f05a:f03db118
           Name : vault:1
  Creation Time : Wed Aug  5 01:06:22 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1951113216 (930.36 GiB 998.97 GB)
     Array Size : 2926668288 (2791.09 GiB 2996.91 GB)
  Used Dev Size : 1951112192 (930.36 GiB 998.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 589fbff6:b3559d13:efe308d0:fda9b61d

    Update Time : Mon Aug  5 18:02:16 2002
       Checksum : 95747268 - correct
         Events : 8327

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : .AA. ('A' == active, '.' == missing)
/dev/sde2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : ecf60edb:32ea67bd:4165f05a:f03db118
           Name : vault:1
  Creation Time : Wed Aug  5 01:06:22 2015
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 1951113216 (930.36 GiB 998.97 GB)
     Array Size : 2926668288 (2791.09 GiB 2996.91 GB)
  Used Dev Size : 1951112192 (930.36 GiB 998.97 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 57ada937:f68cb600:4044e933:e65612ac

    Update Time : Mon Mar  5 22:58:17 2018
       Checksum : d306b402 - correct
         Events : 483

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
ubuntu@ubuntu:~$ 

```

---

### Post by darkod on 2018-03-25
Well, not sure what to tell you, but you obviously have 2 arrays. One very small one (maybe just some remains) of only 4x 1GB partitions. Maybe earlier /boot partition?

Then you have another 4x 1TB array. If you notice the Events counters of the second array, they are:
sdb2 - 8323
sdc2 - 8327
sdd2 - 8327
sde2 - 483

For an array in sync all counters have to show the same. In your case it looks like sde2 is way out of sync (maybe you lost it a while ago without even noticing it) and also sdb2 has slight difference compared with sdc2 and sdd2. With two members "out of sync" a raid5 will not assemble. Since sdb2 is very close to sdc2 and sdd2 events, it should be fairly easy to reassemble this. I would first try using only three members which have close Events counters (sdb2,sdc2,sdd2).

Try something like:
```
sudo mdadm --assemble --verbose --force /dev/md1 /dev/sd[bcd]2
```

The verbose mode will show you messages as it tries to assemble. If that goes well, we can discuss how to re-add sde2.

---

### Post by carbon13 on 2018-03-25
Darko, that did the trick! THANK YOU SO MUCH!!

I'm going to backup my files now and then decide what to do with this array.

---

### Post by darkod on 2018-03-25
Perfect. After you backup the data, you will probably want to add sde2 back to the array. You can try that with:
```
sudo mdadm /dev/md1 --add /dev/sde2
```

If that doesn't work because sde2 is so out of sync, you can always remove the superblock from sde2 and add it as if it was new member:
```
sudo mdadm --zero-superblock /dev/sde2
sudo mdadm /dev/md1 --add /dev/sde2
```

---

