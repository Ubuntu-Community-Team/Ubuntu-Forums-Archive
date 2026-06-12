---
title: "Server Raid1 won't boot after replacing hard disk"
date: 2017-03-27
forum: Server Platforms
---

### Post by purple-apple on 2017-03-27
Hello, I have just joined the forum and hope I'm posting in the right place.

I'm pretty new to Ubuntu/Server, so please bear with me, I would really appreciate your help.

A previous colleague set up a Ubuntu Server Raid1 with 2x1GB disks. He has left and it has been running alone for a few years!

I received an email from MDADM informing me that sdb is failing at the beginning of the month (this has now been failed and removed from the array), so I looked up all info I could and added a new hard drive replacing sdb and entered the following commands:

```
sudo sfdisk -d /dev/sda | sudo sfdisk --force /dev/sdb
mdadm --manage /dev/md0 --add /dev/sdb1
```

Running the following commands confirmed all okay with sda and sdb showing identical partition sizes and the UU - showing Raid mirrored.

```
sudo cat /proc/mdstat
sudo fdisk -l
```

I wanted to explain the above, because I feel that I didn't do all that was required - regarding the boot section at least. 

Now, last week I received another email from MDADM saying that sda is failing, and this has been removed from the array.

---

This is an automatically generated mail message from mdadm
running on server

A DegradedArray event had been detected on md device /dev/md/0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdb1[2]
      974477120 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>
```

---

So I repeated the procedure (the above scenario), removed the failing sda hard disk, inserted a new hard disk, but sdb will not boot -  I have a message saying 'Operating system not found'.

So I removed the new blank hard disk, put the failing disk sda back into the server and I can now boot okay. (sdb is the functioning part of the array - but won't boot.)

So what can I do to make sdb boot,  so I can remove the failing sda hard disk and put a blank hard disk in - in turn to add that to the Raid? 

(I looked into boot sector, mbr etc but I couldn't find anything concrete for my situation and as a new Ubuntu user I didn't want to ruin the partitions either playing with the mbr etc)

I have installed Grub2 onto sdb just in case it wasn't there and this didn't make any difference, still says 'No operating system found'. (I do remember at this point Grub2 when installing - said couldn't find volume twice and then said completed with no errors...)

I would like to also add that I'm working on this remotely, and do not have physical access to the server to run cds/usb sticks. Although I do have a non technical person to assist me who has been swapping the hard disks.

I'd appreciate any assistance possible, although this is daunting I have enjoyed the experience learning about Ubuntu server and will be installing it onto my laptop to learn more!

Below I'll paste some stat info you that may help:

---

HP Server, I believe it's a software raid using MDADM (But I'm not entirely sure it's software based).

The hard disks are Seagate Barracuda 1GB x2

Version Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-112-generic x86_64)

---

```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[2]
      974477120 blocks super 1.2 [2/1] [_U]


unused devices: <none>
```

---


```
sudo fdisk -l


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1949218815   974608384   fd  Linux RAID autodetect
/dev/sdb2      1949218816  1953523711     2152448   82  Linux swap / Solaris


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c5d00


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1949218815   974608384   fd  Linux RAID autodetect
/dev/sda2      1949218816  1953523711     2152448   82  Linux swap / Solaris


Disk /dev/md0: 997.9 GB, 997864570880 bytes
2 heads, 4 sectors/track, 243619280 cylinders, total 1948954240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/mapper/vg--data-lv--boot: 2344 MB, 2344615936 bytes
255 heads, 63 sectors/track, 285 cylinders, total 4579328 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg--data-lv--boot doesn't contain a valid partition table


Disk /dev/mapper/vg--data-lv--root: 995.5 GB, 995518054400 bytes
255 heads, 63 sectors/track, 121031 cylinders, total 1944371200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/vg--data-lv--root doesn't contain a valid partition table
```

---

### Post by SeijiSensei on 2017-03-27
See if you can go into the BIOS and tell the machine to boot off of the second drive, /dev/sdb.

---

### Post by purple-apple on 2017-03-27
I have attempted this with someone non technical looking at the screen (as I'm at a remote location), they said they could see the boot order including hard disk/cdrom etc, but not individual hard disks.  I think it is worth re-visiting though, so I'll ask him to take another look and I'll post what I find. Thanks a lot.

---

### Post by purple-apple on 2017-03-27
I haven't heard back from work yet. But just a thought, if he is unsuccessful in changing which hard disk boots in the BIOS, could we not just switch the SATA cable from sda to sdb? Or would that cause issues with Ubuntu Raid? Thanks.

---

### Post by slickymaster on 2017-03-27
*Thread moved to **Server Platforms**.*

---

### Post by purple-apple on 2017-03-27
Hi Slickymaster, thanks for moving my thread to the correct location and adding the comment boxes above.

Hi SeijiSensei. We had another look at the BIOS but couldn't see an area where could change the boot order of connected hard drives. Thanks.

---

### Post by darkod on 2017-03-27
After replacing sdb did you ever install the grub bootloader on it? You need to do this on each raid1 member if you want to boot with single disk. I see sdb1 already has the boot flag which is good because even though linux doesn't use it, some boards might decline booting if no hdd has a boot flag.

To install grub to sdb (when both disks are still present and you can boot the system), run:
```
sudo grub-install /dev/sdb
```

---

### Post by purple-apple on 2017-03-28
Hi Darkod, thanks for your suggestion, this could well be an issue or causing the problem. I didn't install Grub originally when adding the new hard disk to the Raid, but I did when I found the new hard disk wouldn't boot - I typed exactly what you typed above.  I do remember that it throw some errors when I did this, so I have just done it again to show you how the server responded. I can understand basically what it is saying, but I wouldn't know what to do about it? Thanks.

```
sudo grub-install /dev/sdb
Installing for i386-pc platform.
grub-install: warning: Couldn't find physical volume `(null)'. Some modules may                                         be missing from core image..
grub-install: warning: Couldn't find physical volume `(null)'. Some modules may                                         be missing from core image..
Installation finished. No error reported.
```

---

### Post by darkod on 2017-03-28
Hmmm, I have never seen such warning message. At the end it does say no error reported, so it looks like the warning is not about something crucial.

mdadm can be stubborn sometimes booting off one disk, which is quite worrying since that's what raid is supposed to do.

Can you post the output of following:
```
sudo parted -l
sudo mdadm --detail /dev/md0
```

Lets see what partitions you've got.

---

### Post by purple-apple on 2017-03-28
Hi Darko, sure, thanks a lot. I must admit (in other cases), I have seen Ubuntu prompt errors here and there which have not effected usage. Hmm I agree the final comment is nice that there are no errors, but slightly contradictory with the previous printed statements. It's a good learning experience for me though.

Here's the output from the commands you posted earlier:

```


sudo parted -l


Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  998GB   998GB   primary  ext2            boot, raid
 2      998GB   1000GB  2204MB  primary  linux-swap(v1)




Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               boot, raid
 2      998GB   1000GB  2204MB  primary




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--boot: 2345MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  2345MB  2345MB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--root: 996GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  996GB  996GB  ext4




Error: /dev/md0: unrecognised disk label

```



```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Mar 15 18:19:13 2013
     Raid Level : raid1
     Array Size : 974477120 (929.33 GiB 997.86 GB)
  Used Dev Size : 974477120 (929.33 GiB 997.86 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent


    Update Time : Tue Mar 28 12:40:46 2017
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


           Name : server:0  (local to host server)
           UUID : 13a6062c:e974f032:c3fbdc59:cc23335b
         Events : 1045242


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       2       8       17        1      active sync   /dev/sdb1

```

---

### Post by darkod on 2017-03-28
So this is with sda still connected and present. If you power off, replace sda with the new disk, it doesn't boot, right?

You can try adding the new disk as a third disk if you have a free sata slot (it will become sdc probably), then create the necessary partitions on it and add sdc1 to the array. After that power off and remove sda from the machine.

Just be careful and double check the letters after adding the new disk because depending on how you have them connected in the sata ports, the new one might not be sdc. Check before running any commands.

---

### Post by SeijiSensei on 2017-03-28
Reversing the cables should fix the sda/sdb problem if you want to give that a go.

---

### Post by purple-apple on 2017-03-28
@ Darko

Correct.

I have managed to get this checked out and there isn't a third sata cable, although there is a 3rd power cable.  I'd have to get a sata cable delivered there, if I can verify there is another sata port available - being a server there must be!

I'll keep this idea in mind, I'm going to request a cable swap which SeijiSensei has suggested and see what happens there first - as that can be done quickly.

Thanks a lot.

@ SeijiSensei 

Thanks a lot.

I'll get back to you soon.

---

### Post by purple-apple on 2017-03-28
@ Darko

Do you think adding the third hard drive would help? Because the one currently within the Raid is sdb which is the drive that won't boot, so I'd be adding the new drive sdc to join sdb... sda boots, but has been failed by the Raid. Let me know what you think, thanks.

@ SeijiSensei

I swapped the Sata cables, and put the blank hard disk back in, but we still received the 'Operating System not found' message. Thanks.

---

### Post by darkod on 2017-03-28
I am still not sure if it is issue with grub or mdadm. Because I have heard of cases here when raid1 array can boot with only disk #1 but not with only disk #2 even though it should. Which is what is happening to you too. But in most cases people were never able to find a logical reason for that issue...

If you suspect that grub-install warning does mean something, you can completely remove and reinstall grub. When the OS is booted that is easy to do, only you need to make sure you install it correctly before you reboot. :)

To completely purge and reinstall grub, you would do:
```
sudo apt-get purge grub-pc grub-common
sudo apt-get install grub-pc   (it will install all needed packages)
sudo grub-mkconfig
sudo grub-install /dev/sda /dev/sdb
sudo update-grub
sudo update-initramfs -u
```

That does the trick of reinstalling grub.

As for your question about the benefit of adding sdc, like I said, it makes a difference if grub or mdadm is the issue. If the only good grub is on sda, it won't boot without it. If mdadm complains booting with only disk #2 (sdb, degraded), by adding sdc you are making the array complete. So when rebooting it won't be degraded any more and it should boot. That would allow you to power off, take out sda, and then try booting again because you already have both disks present in the array (the disks will become "new" sda and sdb once the old disk is removed).

---

### Post by purple-apple on 2017-03-29
Just an update...

I purged and reinstalled grub to both drives. I still had this sort of warning below when installing to each drive. But having said that, the server reboots fine from sda so I'm going to ignore this for now. sdb actually progresses further with the blank disk also installed (after removing sda), although there are issues like mdadm create user root not found etc, a handful of these types and the system does not boot.

```
grub-install: warning: Couldn't find physical volume `(null)'. Some modules may                                         be missing from core image..
Installation finished. No error reported.

```

We have connected the third hard disk (new/blank) now, and have booted, I'm going to add the blank disk to the array as suggested. After reading your response,  I understood now what you were saying about adding the third drive. Your comments are interesting, when this Raid failed the first time earlier this month, the system would not boot until I replaced the failed disk.

I'll post back soon. Thanks a lot.

---

### Post by purple-apple on 2017-03-29
I entered the following to add sdc (blank hard disk) to sdb in the array, and sdc has appeared to have joined sda - which was previously failed from the array... This is strange.

I won't be able to do anything until tomorrow lunch time, but thought I'd post the results so far..

I suppose next, as planned, I'd take out sda, and attempt to boot sdb and sdc together, if sdc will boot add sdb to the Raid? (sda is a four year old array failed hard disk, sdb and sdc are both new this month). Thanks for your help.

```

sudo mdadm --manage /dev/md0 --add /dev/sdc1

sudo sfdisk -d /dev/sdb | sudo sfdisk --force /dev/sdc

sudo grub-install dev/sdc
sudo update-grub
sudo update-initramfs -u


```

I have ended up with sdc and sda, instead of sdc and sdb.

```


sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[3] sda1[2]
      974477120 blocks super 1.2 [2/2] [UU]


unused devices: <none>


```


Thought I'd post the command out again for parted and md0 detail:

```
sudo parted -l

Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               boot, raid
 2      998GB   1000GB  2204MB  primary




Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system     Flags
 1      1049kB  998GB   998GB   primary  ext2            boot, raid
 2      998GB   1000GB  2204MB  primary  linux-swap(v1)




Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               boot, raid
 2      998GB   1000GB  2204MB  primary




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--root: 996GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  996GB  996GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--boot: 2345MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  2345MB  2345MB  ext4




Error: /dev/md0: unrecognised disk label

```



```

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Mar 15 18:19:13 2013
     Raid Level : raid1
     Array Size : 974477120 (929.33 GiB 997.86 GB)
  Used Dev Size : 974477120 (929.33 GiB 997.86 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Wed Mar 29 20:11:37 2017
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : server:0  (local to host server)
           UUID : 13a6062c:e974f032:c3fbdc59:cc23335b
         Events : 1054986


    Number   Major   Minor   RaidDevice State
       3       8       33        0      active sync   /dev/sdc1
       2       8        1        1      active sync   /dev/sda1

```

---

### Post by darkod on 2017-03-29
I think you switched the sda-sdb order when trying out things or swapping sata cables. If you compare the latest parted output with the previous one, you can notice that the sda of that time had ext2 filesystem on sda1, while in the current output it is sdb1 that has the ext2 filesystem. So I think sda and sdb got swapped which makes it normal sdc to join sda in the array (because current sda is previous sdb, if that makes sense).

Also, about the order of the commands you posted, I hope you did the sfdisk command before the mdadm add because you should first create the partitions and only then join them to an array.

Anyway, the array looks good now and you can try powering down, removing the current sdb (because we assume that is the old sda), and try booting without it.

PS. Another thing I noticed in your server. You seem to be running LVM on top of the raid. In such case it would have been better to first make a small 1GB or 2GB partition(s) on each disk, and use that as raid1 array for separate /boot. These days LVM can work without separate /boot (earlier it couldn't) but it is still recommended to use separate /boot when using LVM. It also helps keep the boot files localized on that small partition as opposed to anywhere on a 1TB or 2TB disk.

But you have the server already set up, it would be too much of a hassle to introduce /boot now.

---

### Post by darkod on 2017-03-29
Now it is too late to make a comparison using lshw but just FYI for the future, you can easily get basic disk information including serial number with:
```
sudo lshw -c disk
```

But I am sure now sda and sdb are switched because if you compare post #17 with #10, first sda was model ST1000DM003-1CH1 and now sdb has that model number.

So, md0 containing sda1 and sdc1 is the correct setup.

---

### Post by purple-apple on 2017-03-30
I think you're right, the colleague changing the cables for me did say he may have mixed them up unfortunately.  I also checked my command history and have confirmed I did type sdb and sdc, so it couldn't have been sda.

Apologies about the incorrect posted order of commands, I did run the sfdisk command before mdadm - I double checked the command history to verify.

I'm waiting for my colleague to get back to me and then we can remove sdb (originally sda - this disk is four years old and should be significantly dusty in comparison, so he shouldn't fail here without a serial number!;) (Thanks for providing the command for the serial number, I'll make a note.)). I was curious though if the ext2 filesystem on sda is now on sdb and I remove it, well shouldn't that now be on the new sda or sdc... I'll ask for it to be removed and we will see what happens.

As for LVM, this is new to me - this Server was set up by a colleague so I'm not sure why he set it up this way, but it's useful to know and I'll look up LVM on the Ubuntu pages to have a read out of interest. 

I'll post back soon with the results, thanks for your help!

---

### Post by darkod on 2017-03-30
The filesystem (in this case ext2) does not "move" around when removing/adding disks. If the partition sdb1 is formatted ext2, when you remove the disk that is gone.

But in this case it shouldn't matter. With mdadm raid the partitions should not have any filesystem directly on them anyway, the filesystem is on the md device. This ext2 is probably some old remain that was not destroyed when the disk was reused for mdadm raid.

Easy way to see all filesystems and their UUIDs is:
```
sudo blkid
```

That should show you another filesystem on md0.

---

### Post by purple-apple on 2017-03-31
I see what you mean about the file system that makes complete sense, I think it concerned me that the disk we were going to remove has something unique on it... I understand now. I have put the output of 'sudo blkid' at the bottom of this post, where I can see ext4's on the mappers.

We physically removed sdb (previously sda). Rebooted and this worked fine as you thought. Although the Raid started rebuilding automatically again though or re-syncing, now the drives say sda and sdb instead of sda and sdc, this maybe normal?

I have rebooted again this morning, and the server boots fine.

We are getting a server warning, which I don't think is related to Ubuntu Server but thought I'd mention it - an amber power light shows instead of a green now since the raid failed - the post message says 

This is for the HP Server though not Ubuntu
Server Asset Text:
WARNING
02A1: BMC hardware not found or unresponsive.

Back to Ubuntu:

I'll put a few commands through for you to see what the current state is.

I have also put a question at the end also, thought I'd mention it here as it is way below.

How do you feel about the current set up?  Thanks a lot for your help.

[U]sudo cat /proc/mdstat
[/U]
```

sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[3] sda1[2]
      974477120 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```

[U]sudo parted -l
[/U]
```

sudo parted -l
Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               boot, raid
 2      998GB   1000GB  2204MB  primary




Model: ATA ST1000DM003-1SB1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  998GB   998GB   primary               boot, raid
 2      998GB   1000GB  2204MB  primary




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--boot: 2345MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system  Flags
 1      0.00B  2345MB  2345MB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg--data-lv--root: 996GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  996GB  996GB  ext4




Error: /dev/md0: unrecognised disk label



```

[U]sudo mdadm --detail /dev/md0
[/U]
```

sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Mar 15 18:19:13 2013
     Raid Level : raid1
     Array Size : 974477120 (929.33 GiB 997.86 GB)
  Used Dev Size : 974477120 (929.33 GiB 997.86 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Fri Mar 31 09:33:42 2017
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : server:0  (local to host server)
           UUID : 13a6062c:e974f032:c3fbdc59:cc23335b
         Events : 1055016


    Number   Major   Minor   RaidDevice State
       3       8       17        0      active sync   /dev/sdb1
       2       8        1        1      active sync   /dev/sda1



```

Is the above significant? For example there is a major 17 with number 3, compared to 1 with number 2. Thanks for your help.

[U]sudo blkid

[/U]```
sudo blkid
/dev/sdb1: UUID="13a6062c-e974-f032-c3fb-dc59cc23335b" UUID_SUB="0fa79439-cff7-81b6-be19-5ebadfeb4948" LABEL="server:0" TYPE="linux_raid_member"
/dev/sda1: UUID="13a6062c-e974-f032-c3fb-dc59cc23335b" UUID_SUB="8b420eab-f757-b15a-9f3e-82b090da1011" LABEL="server:0" TYPE="linux_raid_member"
/dev/md0: UUID="sA2cMJ-8ddI-Yphc-IpUO-pqFx-riW4-uDFZ1S" TYPE="LVM2_member"
/dev/mapper/vg--data-lv--boot: UUID="7842b0d8-298f-47bc-b103-eb007a23ae62" TYPE="ext4"
/dev/mapper/vg--data-lv--root: UUID="2d24a439-c84b-4446-a45e-dbf4b7ab86a4" TYPE="ext4"

```

---

### Post by darkod on 2017-03-31
It all looks good to me, except that there is /boot volume inside the LVM according to the blkid results. It is very weird to put /boot inside an LVM, but it can work.

It is normal the disks to be sda and sdb now that there are only two. mdadm uses the UUID of md0 to assemble the array on boot, so changing disk letters does not bother it. If you check /etc/mdadm/mdadm.conf you will find the same UUID for md0 as in blkid.

---

### Post by purple-apple on 2017-04-03
Thanks for pointing that out, I'll take a look into that. Do you think that may have caused the issue with the Raid not booting after replacing one of the disks / the troubles I have been experiencing?

Yes, I see the UUID in the madam.conf thanks for explaining.

Thanks.

---

### Post by darkod on 2017-04-03
What exactly, the /boot being a LV inside the LVM? Basically it should have worked, regardless that the setup is strange. The point of raid1 is to keep working when one disk fails. So it should... It shouldn't mind that you have LVM set up on top of the raid and how the LVM is designed.

But there are always strange unexpected things in IT, so this might be one of them... I don't think you will ever find the reason honestly...

---

### Post by purple-apple on 2017-04-03
I see, thanks very much for all your help, it has been much appreciated! All the best!

---

