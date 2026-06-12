---
title: "First help required: Software Raid"
date: 2006-02-28
forum: Server Platforms
---

### Post by trentend on 2006-02-28
I'm running Breezy on a dual opteron 1U server box, booting from a dual scsi raid 1 array.  I'm hoping to setup virtualised Xen server domains using a second software raid for just storing the vitualised server data.

I have a highpoint 1542, with two 400GB drives.  These are showing as two seperate devices /dev/hdk and /dev/hdg (as expected as the controller is fakeRAID).

I would like to setup the two drives as a software RAID, but am not interested in booting from the drives.

I would appreciate any tips, or even better a walkthrough, that you could point me to.

I'm a complete newbie, but aiming to setup virtualised servers to run as mail server (groupware, probably using Kolab), file server, webserver, and ofbiz server.  I'm hoping the virtualisation will allow me to spread the load over multiple machines as the load increases, and the use of data on the second (non-SCSI, non-boot) RAID array will allow me to achieve a large cheap mirrored (RAID 1) storage.

My apologies if this is covered elsewhere, but I have been unable to find help with software RAID that excludes the boot option.

Thanks in advance for your assistance.
Paul aka trentend

---

### Post by trentend on 2006-03-01
Okay.  Here's where I've got to.  Hopefully someone can help me out.

I partitioned the two drives as fd:
[INDENT]
Disk /dev/hdg: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/hdk: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdk1               1       48641   390708801   fd  Linux raid autodetect[/INDENT]


and used mdadm to create /dev/md0.

[INDENT]/$ sudo mdadm -Q /dev/md0
/dev/md0: 372.61GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: No md super block found, not an md component.
paulcham@glenweb1:/$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Wed Mar  1 11:50:12 2006
     Raid Level : raid1
     Array Size : 390708736 (372.61 GiB 400.09 GB)
    Device Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Mar  1 11:50:12 2006
          State : clean, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 2% complete

           UUID : 32a971bd:82fc6b9e:ed86898c:2579e888
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0      34        1        0      active sync   /dev/.static/dev/hdg1
       1      57        1        1      active sync   /dev/hdk1
[/INDENT]

If I query again I get:
[INDENT]
$ sudo mdadm -Q /dev/md0
/dev/md0: 372.61GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: No md super block found, not an md component.
[/INDENT]

I can't partition md0, and can't seem to be able to get access to the array.  If anyone could lead me through what I need to do to get the array setup (non-bootable) and mounted as /vserver I would be massively gratefull.  This has become a huge sticking point for me.

Thanks in advance
Paul aka trentend.

---

### Post by LordHunter317 on 2006-03-01
[QUOTE=trentend]I can't partition md0, and can't seem to be able to get access to the array.[/quote]You can't.  RAID devices are unpartitionable.  You have to partition the disks first, then create a RAID device for each partition group.  Alternatively (and probably smarter) use LVM.


>  If anyone could lead me through what I need to do to get the array setup (non-bootable) and mounted as /vserver I would be massively gratefull. This has become a huge sticking point for me.What did you run to actually create the array?  mdadm -Q won't do it.

---

### Post by trentend on 2006-03-01
I used:
[INDENT]
$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/hdg1 /dev/hdk1[/INDENT]

to create the array.  After I had partitioned it as two big drives (type fd).  Unfortunately from there I couldn't seem to mount it.

Should I mount one partition as /vserve, and then add the other disk to it as an array?  What should the partition settings for the drives should be?  How do I best do this.

Additionally I seem to be able to stop the array, but I don't know how to delete it, and start again!

Thanks for taking the time to try to help.
Paul aka trentend.

---

### Post by LordHunter317 on 2006-03-01
Did you create an fs via mkfs on the RAID array first?  You have to create a filesystem before you can mount it.

---

### Post by trentend on 2006-03-01
No I didn't.

I had problems understanding the process, from the variety of guides that are available, as none of them match the circumstances applicable in my case.  So I've tried to have a go at it myself by looking at the mdadm documentation.  Not an ideal process for a newbie.

I've tried stopping the array, and re-partitioning the disks, but it won't let me.  Currently I get this:

[INDENT]$ sudo fdisk -l
Password:

Disk /dev/sda: 73.5 GB, 73545023488 bytes
255 heads, 63 sectors/track, 8941 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32        8941    71569575    5  Extended
/dev/sda5              32        8941    71569543+  8e  Linux LVM

Disk /dev/hdg: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/hdk: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdk1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/md0: 400.0 GB, 400085745664 bytes
2 heads, 4 sectors/track, 97677184 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table
[/INDENT]

Using mdadm shows:
[INDENT]
$ sudo mdadm --detail -Q /dev/md0
/dev/md0: 372.61GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.
/dev/md0: No md super block found, not an md component.
[/INDENT]

---

### Post by trentend on 2006-03-01
I feel like I'm on the right track, but I haven't quite cracked it.

I have re-created the array, used mkfs to format the md0 array to ext3, and now just need to mount the array as /vserver[INDENT]

$ sudo cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 hdk1[1] hdg1[0]
      390708736 blocks [2/2] [UU]
      [==>..................]  resync = 11.2% (43916608/390708736) finish=350.8min speed=16473K/sec
unused devices: <none>


$ sudo mdadm -Q --detail /dev/md0
/dev/md0:
        Version : 00.90.01
  Creation Time : Wed Mar  1 17:37:10 2006
     Raid Level : raid1
     Array Size : 390708736 (372.61 GiB 400.09 GB)
    Device Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Mar  1 17:52:30 2006
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

 Rebuild Status : 11% complete

           UUID : 9531cd55:92b9c0f0:783bf13c:cdd04536
         Events : 0.3

    Number   Major   Minor   RaidDevice State
       0      34        1        0      active sync   /dev/.static/dev/hdg1
       1      57        1        1      active sync   /dev/hdk1
[/INDENT]


I tried:
[INDENT]
$ sudo mount -t auto /dev/md0 /vserver[/INDENT]

but all I got was:
[INDENT]
mount: mount point /vserver does not exist
[/INDENT]

Any ideas what I should do?  Remember I'm a real newbie.....

---

### Post by trentend on 2006-03-01
Struck by the newbie curse!

I hadn't released that I needed to

[INDENT]$ sudo mkdir /vserver[/INDENT]

before I:

[INDENT]$ sudo mount /dev/md0 /vserver
[/INDENT]

Subsequently looking at mount points shows /vserver mounted on md0 as required.

[INDENT]$ sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Ubuntu-root
                      67554920    547120  63576172   1% /
tmpfs                  1038240         0   1038240   0% /dev/shm
tmpfs                  1038240     12588   1025652   2% /lib/modules/2.6.12-9-386/volatile
/dev/sda1               233335     11565    209322   6% /boot
/dev/md0             384578100    131228 364911436   1% /vserver[/INDENT]

If I look at my softRAID array (md0), it is still "resyncing".  Presumably this is because of the large disk size and is part of the initial initialisation stage.

[INDENT]$ sudo cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 hdk1[1] hdg1[0]
      390708736 blocks [2/2] [UU]
      [=======>.............]  resync = 36.8% (143959296/390708736) finish=251.4min speed=16352K/sec
[/INDENT]

Assuming that I come across no further problems, I think I have achieved what I was aiming for.  I would appreciate your observations.

Thanks very much for your comments and help.
Paul aka trentend

---

### Post by LordHunter317 on 2006-03-01
Yes, the procedure is:[list=1][*]Partition the RAID array members[*]Create the arrays[*]Format the arrays via mkfs[*]Create the mount points via mkdir[*]Mount the arrays[/list]

---

### Post by trentend on 2006-03-01
Thanks for pointing me the right way.  I got there in the end.

---

