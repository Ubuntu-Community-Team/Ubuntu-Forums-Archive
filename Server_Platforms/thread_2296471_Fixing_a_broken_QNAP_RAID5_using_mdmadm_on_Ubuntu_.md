---
title: "Fixing a broken QNAP RAID5 using mdmadm on Ubuntu 12.04"
date: 2015-09-26
forum: Server Platforms
---

### Post by asker-styile on 2015-09-26
Hi There,

One of our QNAP NAS had gone down while alerting on disk thus they  were all working/accessible on the array. And I'm trying to recover the  DATA as the QNAP NAS neither boots nor responds with/without the disks.


  I've booted all the HDD's using an Ubuntu live disk with **mdadm** command. I'm not sure what happened to disk one as it shows **HPFS/NTFS/exFAT** on partition 3 of one disk. Further, the **UUID* which suppose to some unique numbers are now shown as **0000:0000....** along with **Raid level: unknown**.

I do know that keeping a backup is very critical and important but this not maintained by me. It was the whole responsibility of another user but I'm just here to help recover the DATA.

  
However, below are some outputs that I have collected.

```


root@ubuntu:/home/ubuntu# fdisk -l | more

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00009a4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              40     1060289      530125   83  Linux
/dev/sda2         1060296     2120579      530142   83  Linux
/dev/sda3         2120584  1952507969   975193693    7  HPFS/NTFS/exFAT
/dev/sda4      1952507976  1953503999      498012   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000ac6cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              40     1060289      530125   83  Linux
/dev/sdb2         1060296     2120579      530142   83  Linux
/dev/sdb3         2120584  1952507969   975193693   83  Linux
/dev/sdb4      1952507976  1953503999      498012   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b7ac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              40     1060289      530125   83  Linux
/dev/sdc2         1060296     2120579      530142   83  Linux
/dev/sdc3         2120584  1952507969   975193693   83  Linux
/dev/sdc4      1952507976  1953503999      498012   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000b7ac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              40     1060289      530125   83  Linux
/dev/sdc2         1060296     2120579      530142   83  Linux
/dev/sdc3         2120584  1952507969   975193693   83  Linux
/dev/sdc4      1952507976  1953503999      498012   83  Linux

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d2a20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              40     1060289      530125   83  Linux
/dev/sdd2         1060296     2120579      530142   83  Linux
/dev/sdd3         2120584  1952507969   975193693   83  Linux
/dev/sdd4      1952507976  1953503999      498012   83  Linux
```


```
root@ubuntu:/home/ubuntu# mdadm -E /dev/sd[abcd]3
/dev/sda3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Sep 25 07:04:44 2015
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Sep 25 07:19:04 2015
          State : active
 Active Devices : 0
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 3
       Checksum : 8f463afd - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     2       8        3        2      spare   /dev/sda3

   0     0       8       35        0      spare   /dev/sdc3
   1     1       8       19        1      spare   /dev/sdb3
   2     2       8        3        2      spare   /dev/sda3
/dev/sdb3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Sep 25 07:04:44 2015
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Sep 25 07:19:04 2015
          State : active
 Active Devices : 0
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 3
       Checksum : 8f463b19 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8       35        0      spare   /dev/sdc3

   0     0       8       35        0      spare   /dev/sdc3
   1     1       8       19        1      spare   /dev/sdb3
   2     2       8        3        2      spare   /dev/sda3
/dev/sdc3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Sep 25 07:04:44 2015
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 3
Preferred Minor : 0

    Update Time : Fri Sep 25 07:19:04 2015
          State : active
 Active Devices : 0
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 3
       Checksum : 8f463b0b - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     1       8       19        1      spare   /dev/sdb3

   0     0       8       35        0      spare   /dev/sdc3
   1     1       8       19        1      spare   /dev/sdb3
   2     2       8        3        2      spare   /dev/sda3
/dev/sdd3:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 00000000:00000000:00000000:00000000
  Creation Time : Fri Sep 25 09:28:22 2015
     Raid Level : -unknown-
   Raid Devices : 0
  Total Devices : 1
Preferred Minor : 0

    Update Time : Fri Sep 25 09:31:03 2015
          State : active
 Active Devices : 0
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 8f467b40 - correct
         Events : 1


      Number   Major   Minor   RaidDevice State
this     0       8        3        0      spare   /dev/sda3

   0     0       8        3        0      spare   /dev/sda3
```

```
root@ubuntu:/home/ubuntu# cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md4 UUID=a5ef83a2:3df739b9:7e77f235:9827a98f
ARRAY /dev/md0 UUID=00000000:00000000:00000000:00000000
   spares=3
ARRAY /dev/md9 UUID=c39aa918:f8de04d3:bb375993:177a40db
ARRAY /dev/md4 UUID=bb500a60:f1f7edde:07b598b5:09c70531
   spares=1
ARRAY /dev/md0 UUID=00000000:00000000:00000000:00000000
   spares=1
ARRAY /dev/md13 UUID=62a22532:1a265501:07a38901:1b2b353e

# This file was auto-generated on Sat, 26 Sep 2015 05:23:53 +0000
# by mkconf $Id$
```

```
root@ubuntu:/home/ubuntu# cat /proc/mdstat 
Personalities : 
unused devices: <none>
```

---

### Post by darkod on 2015-09-26
Wow, that doesn't look good at all... Give me a bit of time to find one article in my bookmarks and I will post the link...

---

### Post by darkod on 2015-09-26
How many arrays were there, do you have some information how it was originally set up? The mdadm.conf is confusing to me. There are two definitions for md4 with different UUIDs. Also there are md0, md9 and md13 arrays.

Also when trying to save the data it is important to know the order of the partitions (disks) in the original --create command. For example, were they sda3-sdb3-sdc3-sdd3 in that order? Because you will need to list them in the same order.

Also, according to the -E output you posted, the array of sd[abcd]3 has metadata version of 0.90. You need to keep that in mind and use the parameter when trying the --create --assume-clean. Not sure if you need it for --assemble too, but doesn't hurt to use it.

Here is a page of one forum member with great experience in mdadm. He explains saving array from multiple failures (in your case total member failure). I think this is your best bet...

First you start easy, the --assemble --force. Don't forget to list the partition in correct order and use --metadata=0.90 just in case because according to -E that's what the array had.

If that doesn't work you add --run to the options.

If it still doesn't work, your last option according to him is the --create --assemble-clean. Again don't forget to use correct order and the metadata option. Also when using --create and you want to keep the data NEVER forget the --assume-clean option. It tells mdadm to keep the data instead of creating a new blank array.

Link: [http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm](http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm)

Good luck... If any questions, ask.

---

### Post by asker-styile on 2015-09-26
Hi There,

Yes, I know. It is one messed up array and my colleague messed it up more before my visit. Now, I'm bearing the paint to fix it and thank god I know some linux at least to find out the causes...

> **darkod said:**
> How many arrays were there, do you have some information how it was originally set up? The mdadm.conf is confusing to me. There are two definitions for md4 with different UUIDs. Also there are md0, md9 and md13 arrays.

I'm not sure how many arrays were there.. but according to QNAP support each disk contains few partitions where the 3rd contains DATA. As per my experience, its is RAID5 while the rest partitions are RAID1 which is default and normal tolerate QNAP's DATA. Those md[x]'s must be that so called raid one array's as I was able to assemble them using but not the necessary partition.

```
mdadm --assemble --scan
```

it was originally set-up as RAID5 that is for sure. And according to the last screen before the NAS shutdown, disk 1 was having read/write error.

> **darkod said:**
> 
Also when trying to save the data it is important to know the order of the partitions (disks) in the original --create command. For example, were they sda3-sdb3-sdc3-sdd3 in that order? Because you will need to list them in the same order. 

yes the partition orders are correct.. I've marked the disks according to its order and the NAS bay's are noted as 1,2,3,4. Also, to make sure I've connected the disks in SATA port order too.

> **darkod said:**
> 
Also, according to the -E output you posted, the array of sd[abcd]3 has metadata version of 0.90. You need to keep that in mind and use the parameter when trying the --create --assume-clean. Not sure if you need it for --assemble too, but doesn't hurt to use it.

Here is a page of one forum member with great experience in mdadm. He explains saving array from multiple failures (in your case total member failure). I think this is your best bet...

First you start easy, the --assemble --force. Don't forget to list the partition in correct order and use --metadata=0.90 just in case because according to -E that's what the array had.

If that doesn't work you add --run to the options.


I think I've run them if I'm not mistaken. And the other thing is, these were taken out of a NAS where I'm finding difficult to search for single post which contains the RAID creation parameters of QNAP at least to recreate the array.

BTW, doing the above; will it cause any DATA loss?? and as you see on **/dev/sda3** which shows an incorrect file type. Will that be a problem too?? And can I do this without the first drive as this was on a RAID5? like below for an example;

```
mdadm --assemble --force --metadata=0.90 /dev/md0 missing /dev/sdb3 /dev/sdc3 /dev/sdd3
```


> 
If it still doesn't work, your last option according to him is the --create --assemble-clean. Again don't forget to use correct order and the metadata option. Also when using --create and you want to keep the data NEVER forget the --assume-clean option. It tells mdadm to keep the data instead of creating a new blank array.

Link: [http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm](http://zackreed.me/articles/50-recovery-from-a-multiple-disk-failure-with-mdadm)

Good luck... If any questions, ask.

I'm too afraid to play with the codes as of now due to any DATA loss.. Well, its my colleagues fault not taking backups since the DATA inside the RAID was not even 5GB in size but the rest of the DATA were not important as these. 

What do you advise on this? meanwhile, I will read the link to see if I can get a hold of anything.

Thank you so much for replying. Really appreciate it.!

---

### Post by darkod on 2015-09-26
You asked if doing the above can cause data loss but I'm not sure what you refer to. The --assemble --scan? No, it can't cause data loss, it simply tries to auto assemble what it can but in a situation with multiple disk failures it would not be able to do it automatically.

Seeing the filesystem changed on one partition is a bad sign but from mdadm perspective it shouldn't matter much. That is unless QNAP has a completely different way running the mdadm raid. You see, in default mdadm the partition do not carry the filesystem, the mdX devices carry it. So basically the /dev/sdXY stay unformatted. No linux, no windows filesystem. The mdX is what you are formatting. Again, unless QNAP does it very differently, you could hope that the filesystems on /dev/sdXY will not matter.

I don't think you need to use missing for --assemble. If one member of raid5 is too bad to use it will assemble automatically without that member because raid5 allows running without one member. However, with --create --assume-clean the situation is different and you need to use missing so that it keeps that "slot" dedicated for the disk/partition you are leaving out.

I think you could give a try to both --assemble options. There is not much damage that can do. If you have the option, it would be always good to make clones of all 4 disks before you start, for a piece of mind.

The --create --assume-clean should not do damage either, but the command itself is little bit "more risky" compared to --assemble. So you can give a try to the first two and rest and reconsider your option before trying the --create.

If someone else was manipulating the arrays before you took over that could point crucial too. The zero UUID is definitely not a good sign and might be a result of his actions. In fact I don't remember seeing zero UUID on the forum in any thread about mdadm rescue. Depending what was done with the array so far you might not have success in recovering it even by running the correct commands... That's why for mdadm recovery it's very important to get it right from the start of the recovery process.

---

### Post by tgalati4 on 2015-09-26
Welcome to the forums.  You might consider why the block ID's (UUID's) are not getting assigned.  If you can determine exactly why the UUID's are not working, then you will be in a better position to troubleshoot the array.

It might be possible to assign a [UUID]("https://help.ubuntu.com/community/UsingUUID") to each drive using *uuidgen* and then modify the mdadm.conf file to contain the correct UUID's for each drive.  You might send an email to QNAP asking how UUID's are assigned and what utilities are used.  One purpose of UUID's is to prevent a drive pulled from one server and then be popped into another server and then accidentally be overwritten.  If /dev/sda notation was used, any drive that showed up as /dev/sda could be overwritten with massive data loss.  UUID helps to prevent this situation, but it also makes recovery difficult when migrating disks to new hardware.

---

### Post by darkod on 2015-09-26
So far we have seen only one array with zero UUID, but the most important one. This could be result of the actions taken to recover the array, not necessarily a fault with linux or QNAP.

You can see all UUIDs with:
```
sudo blkid
```

That will show you more info about different UUID and UUID_SUB for the partitions.

---

### Post by asker-styile on 2015-09-26
> **darkod said:**
> You asked if doing the above can cause data loss but I'm not sure what you refer to. The --assemble --scan? No, it can't cause data loss, it simply tries to auto assemble what it can but in a situation with multiple disk failures it would not be able to do it automatically.

Yes, I have asked but not by using**--assembe --scan **as I know that it will just do a scan and assemble matching array's automatically. What I asked was when using **--assume-clean **with **--create**... and what will be the command to initiate.. is it like below?

```
mdadm --create --assume-clean --metadata=0.90 /dev/md0 missing /dev/sdb3 /dev/sdc3 /dev/sdd3
```

Do I really have to use **--metadata** at this point? or should I first try assembling with metadata before recreating the array.


> 
Seeing the filesystem changed on one partition is a bad sign but from mdadm perspective it shouldn't matter much. That is unless QNAP has a completely different way running the mdadm raid. 

the filesystem change seems like because of the user's input or any operation that carried out prior to my visit. I'm guessing at least that's the case.

> 
I don't think you need to use missing for --assemble. If one member of raid5 is too bad to use it will assemble automatically without that member because raid5 allows running without one member. However, with --create --assume-clean the situation is different and you need to use missing so that it keeps that "slot" dedicated for the disk/partition you are leaving out.

I think you could give a try to both --assemble options. There is not much damage that can do. If you have the option, it would be always good to make clones of all 4 disks before you start, for a piece of mind.

The --create --assume-clean should not do damage either, but the command itself is little bit "more risky" compared to --assemble. So you can give a try to the first two and rest and reconsider your option before trying the --create.

Do I have to image all four disks or just three working disk on the RAID is fine? and how am I suppose to re-use it if necessary?

> 
If someone else was manipulating the arrays before you took over that could point crucial too. The zero UUID is definitely not a good sign and might be a result of his actions. In fact I don't remember seeing zero UUID on the forum in any thread about mdadm rescue. Depending what was done with the array so far you might not have success in recovering it even by running the correct commands... That's why for mdadm recovery it's very important to get it right from the start of the recovery process.

QNAP support logged into my PC yesterday and said that it looks weird. He also said that he needs to get back to me on this but since its weekend I presume, I should wait until Monday.

Meanwhile its worth a shot posting here and yes I did learn something... However, I have not tried the --metadata option yet but do you think that it will work not knowing the UUID & RAID level?

---

### Post by darkod on 2015-09-26
Yes, your --create syntax looks correct, but hold on a moment.

Did you try the --assemble --force first? And then the --assemble --force --run?

Also, the instructions on that page say to zero the superblocks on the partitions before trying the --create --assume-clean. But that is the last option. You should try --assemble first (if you already hadn't).

I also think you should use the --metadata=0.90 to let it know it has old metadata and to help it understand the array you are trying to reassemble. For more info during --assemble you can also add --verbose. It doesn't do anything, just more output information of the command process.

PS. In case my reply was somewhat confusing, I think the first command you should try is:
```
mdadm --assemble --force --metadata=0.90 --verbose /dev/md0 missing /dev/sdb3 /dev/sdc3 /dev/sdd3
```

Post the output it gives...

PPS. Now thinking about it, my command above might report that you can't use missing with assemble, only with create. I'm not 100% sure about that since I have never tried it with assemble. In such case, run it without missing. You have two options. Run it only with the three members, or use /dev/sda3 instead of missing. mdadm assemble should ignore sda3 if it can't fit it into the array, there is no damage to include it into the command. I have seen such cases, it uses the partitions it can use and it leaves out the ones that can't fit. Even if you are sure the disk is bad you might include sda3 in the assemble in order to have all four members specified in the command. The choice is yours, it should be the same result using sda3 or leaving it out.

---

### Post by asker-styile on 2015-09-26
Well, I cannot recall whether I used the syntax --force but I did not use --run.. Maybe I'll give your command a shot since it just trying to force assemble the array with metadata.. BTW, do you think this will help as no UUID's and no RAID levels reported on the examine...? 

I also can see the first drive when I connected to the slot. So, I can connect it and try as well since I'm not trying to recreate the array. Let me post back tomorrow on this.

---

### Post by darkod on 2015-09-26
To be honest, I have no idea if it will work especially since no uuid and raid level is detected as you noticed. However mdadm has more info than only that and we can only hope using that info it can try to assemble the array. After all, the point of recovering array with multiple failures is that you are recovering an array that has lost too many members to function correctly. And it's still doable.

If you didn't use --force you can't expect it to assemble since there are many members that failed. Without forcing it it can only assemble if one member was missing from raid5. That's why --force is used after multiple member failures.

The second alternative, adding --run to the --force, in a way says "even if you don't think you are good to run, still run and lets see". In cases, --run allows to assemble arrays that did not assemble without it but the data was good.

Lets focus on these two options first. We can talk about the --create later.

---

### Post by asker-styile on 2015-09-26
Understood.. Let me run these and come back to you by tomorrow... Thanks for the heads up... :)

---

### Post by asker-styile on 2015-09-27
Hi There,

I've tried below command as you said with/without --run synax and the output I've got is;

```

root@ubuntu:/home/ubuntu# mdadm --assemble --force --metadata=0.90 --verbose /dev/md0 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3
mdadm: looking for devices for /dev/md0
root@ubuntu:/home/ubuntu# cat /proc/mdstat 
Personalities : 
unused devices: <none>
root@ubuntu:/home/ubuntu# mdadm --assemble --run --force --metadata=0.90 --verbose /dev/md0 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3
mdadm: looking for devices for /dev/md0
root@ubuntu:/home/ubuntu# cat /proc/mdstat 
Personalities : 
unused devices: <none>


```

---

### Post by darkod on 2015-09-27
It seems assemble can't help you. Before we go further can you post the output of:
```
sudo blkid
```

I am curious to see all UUIDs especially for the partitions that interest us. It might give us some ideas.

---

### Post by asker-styile on 2015-09-27
I'm now on a Windows machine but when I tried sudo blkid last night with grep'ing for UUID which returned 00000's for the 3rd partition on each drive.

---

### Post by darkod on 2015-09-27
Unfortunately it looks like the --create is the only thing you can try now. I don't have much hope because it looks like the damage has been done with the steps taken after the array failed. I have no other explanation. The forup partitions can't fail at the same time especially because three of the disks are still working fine. What ever steps were taken after the array failed seem to have done more damage than the failure itself.

If you want to try the create, the modified syntax according to that article should be something like this. First you need to zero the mdadm superblock on each of the four partitions so do that for all four:
```
sudo mdadm --zero-superblock /dev/sda3
(after that is done on each partition)
sudo mdadm --create --assume-clean --verbose --metadata=0.90 --level=5 --raid-devices=4 /dev/md0 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3
```

I think I didn't forget anything. :)

I see this as the only hope right now...

---

### Post by asker-styile on 2015-09-27
I'm currently trying to do a data recovery using a RAID recovery tool which is [ReclaiMe]("http://www.reclaime.com/library/qnap-recovery.aspx"). Well! doing recovery doesn't any harm and if I can see at least the files, I can pay for the software and just grab the bit that I wanted...

Once done, I can then try the assemble as I don't want to take any more risks now re-creating the array. Also, I brought a 3TB disk to do the disk image which unfortunately doesn't fit into it. And imaging, then recovering is a quite a lot of work I see and its double the work. So, let me first try the recovery method.

Failing to do so, will try your way... I'll keep you posted.

---

