---
title: "about raid"
date: 2011-11-05
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-11-05
Hello There

I have a machine which has 2 sata disks that are the same size.
I installed ubuntu server 11.10 64 bit with raid1 on it.
During the installation, I set it if a disk fails ubuntu will boot using other disk.
if one of these disks fails, What should I do for replacing with a new disk without any problem?

I have 2 raid arrays, one of them is for swap sda1, sdb1
and the other (md1) is for data (ext4) sda2, sdb2.

is there a document about that for ubuntu 11.10 ? 

Thanks

---

### Post by darkod on 2011-11-05
If it is software RAID1 (created with the OS, not in motherboard BIOS), looks like this is the procedure:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

---

### Post by yavuz.maslak on 2011-11-10
Thanks it is useful. but  isn't it suppose to run grup-install for the new disk ?  

Now I have raid1. ubuntu11.10 server64bit works on it.

As a test, after shutdown, I unpluged one of disks,

When I boot the system, the system booted as degraded. everything works.
And then I unplugged the second disk ( certainly I attached the first disk before ), when I boot the system, I get an error,
no such disk 
rescue grub> 

I could recovered the test machine using install CD.

I think that whichever one of both disks I detache, the system should run .
Whats wrong with it ? 
is there any better way ? 
Thanks

---

### Post by darkod on 2011-11-10
You can always install grub to both disks if you want to. Boot your ubuntu and just do:

sudo grub-install /dev/sda
sudo grub-install /dev/sdb

---

### Post by yavuz.maslak on 2011-11-11
I can run these commands without any problem.
But if I detach sdb, it comes out no such disk grub rescue>
if I detach sda, the system boots as degrade. 
when I run fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   fd  Linux raid autodetect
  
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1    *       2048  1919975423   959986688   fd  Linux raid autodetect

Although I ran grub-install /dev/sda and sdb, Why am I not be able to see the both Boot is active above ?
as you know only /dev/sda1 is active as Boot

Thanks

---

### Post by darkod on 2011-11-11
Write down the UUID it looks for when it says no such disk. Then you can find out the UUID of your disks with:
sudo blkid

You can easily set the boot flag on /dev/sdb1 too, but I have not much experience with this to know if it will boot. Missing boot flag is a problem for some motherboards but the error is showing up when the disk without the flag is disconnected, not the other way around.

---

### Post by yavuz.maslak on 2011-11-11
I did as following but there has been no useful.
I set bootflag on the both ones.
update-grub
grub-install /dev/sda
grub-install /dev/sdb

When I detach one of the 2 disks, it comes out grubrescue> during the boot. if i detach other one, it boots as degrade.  

fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     4818943     2408448   82  Linux swap / Solaris
/dev/sda2   *     4818944   234438655   114809856   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000ae0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     3905535     1951744   fd  Linux raid autodetect
/dev/sdb2   *     3905536   156301311    76197888   fd  Linux raid autodetect


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[2] sdb1[0]
      1950708 blocks super 1.2 [2/2] [UU]
      
md1 : active raid1 sdb2[3] sda2[2]
      76194744 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

---

### Post by darkod on 2011-11-11
But now sda1 and sda2 are not shown as linux raid type. In the previous fdisk -l they were.

Right now the results has some logic. sda is not shown as raid type, only sdb. That's why removing sda boots sdb degraded, but removing sdb can't boot sda degraded because they are not even raid type.

On the other hand mdstat says they are members of the array. The partitions on sda I mean.

---

### Post by yavuz.maslak on 2011-11-14
I am reinstalling the test server.

I 'll share the case.

---

### Post by yavuz.maslak on 2011-11-14
I reinstalled the server as raid1
When I detach one of them, the system degraded. after that I attached it and then I detached second of them. 
I get the screen no such disk grub rescue>

root@ubunturaid:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee7ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3905535     1951744   fd  Linux raid autodetect
/dev/sda2   *     3905536   156297215    76195840   fd  Linux raid autodetect

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002798b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     3905535     1951744   fd  Linux raid autodetect
/dev/sdb2   *     3905536   156301311    76197888   fd  Linux raid autodetect

Disk /dev/md1: 78.0 GB, 78023417856 bytes
2 heads, 4 sectors/track, 19048686 cylinders, total 152389488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 1997 MB, 1997524992 bytes
2 heads, 4 sectors/track, 487677 cylinders, total 3901416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

---

### Post by yavuz.maslak on 2011-11-17
is there a solve about that ?

---

### Post by darkod on 2011-11-17
What exactly is the problem, that it doesn't boot with one disk disconnected?

After reinstalling the server did you install grub again to both disks? Usually grub rescue would mean it can't locate the grub files to continue booting.

And do you have fakeraid or software raid? You never said.

---

### Post by yavuz.maslak on 2011-11-18
Yes it doesn't boot with one disk disconnected.
it comes out no such disk grub rescue>

I reinstalled the machine freshly.
the installation asks me whether grub-install will install during the install.
I press yes button. it installed grub-install

I installed software raid1.

I followed at [https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.10/serverguide/C/advanced-installation.html)

---

### Post by yavuz.maslak on 2011-11-18
I have to correct a thing that I said "it doesn't boot with one disk disconnected." before 

I have to explain that. There is a raid1 insfructure with software raid. 
if I disconnect one of them the ubuntu server boots as degrade.
that's to say it is well. But if I disconnect other disk, it says "no such disk grub-rescue> "

---

### Post by darkod on 2011-11-18
Have you tried also the option to install grub on the array itself (not separately the HDDs) at it is mentioned in that link? It goes like:

sudo grub-install /dev/md0

depending if your raid device is /dev/md0. Chage it accordingly if it isn't.

Also I tried to test this yesterday in VirtualBox and using 11.10 server the same happened. If you remove /dev/sda it boots fine in degraded state, but if you remove /dev/sdb it doesn't boot at all.

However, when I tested it with 10.04 server it worked fine without difference which disk is removed. This might be a bug in 11.10. I guess always more attention is paid to LTS releases and 10.04 is LTS.

---

