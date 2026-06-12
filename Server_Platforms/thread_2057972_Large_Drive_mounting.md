---
title: "Large Drive mounting"
date: 2012-09-14
forum: Server Platforms
---

### Post by Templerun on 2012-09-14
I am trying to install a Seagate 3TB HDD to my already running Ubuntu Server installation (12.04). The HDD fails to show up with mounting options. Tried GParted/GPT/Webmin based partitioning tools all goes well till I hard-reboot it. The drive fails to mount again ... I am going to use it as Dump only so no problems of having any boot records on this. I would prefer a single large partition. Some of the threads I am going thru already ...

[http://knowledge.seagate.com/article...S/FAQ/218575en]("http://knowledge.seagate.com/articles/en_US/FAQ/218575en")
[http://www.rodsbooks.com/gdisk/index.html](http://www.rodsbooks.com/gdisk/index.html)

My original thread what I am going to do finally ...

[http://ubuntuforums.org/showthread.php?t=2047901](http://ubuntuforums.org/showthread.php?t=2047901)

Since, this is a problem which any person might face. I have opened a new thread for it. Configuration ... Gigabyte G-33 mother-board, q6600 Intel CPU, 8GB of RAM

Please suggest something step by step to get my 3TB HDD to mount properly even after full shut-down.

---

### Post by oldfred on 2012-09-14
What mode is BIOS in for the drive? For new drives the AHCI is usually required. Is BIOS up-to-date?

---

### Post by darkod on 2012-09-14
Can you post the output of:
```
cat /proc/partitions
sudo parted -l
```

---

### Post by Templerun on 2012-09-14
> **darkod said:**
> Can you post the output of:
```
cat /proc/partitions
sudo parted -l
```

major minor  #blocks  name

   8        0  976761527 sda
   8        1  455078125 sda1
   8        2          1 sda2
   8        5  513303552 sda5
   8        6    8376320 sda6
   8       16 1953536567 sdb
ajit@ubuntu:~$ sudo parted -l
[sudo] password for ajit: 
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  466GB   466GB   primary   ntfs            boot
 2      466GB   1000GB  534GB   extended
 5      466GB   992GB   526GB   logical   ext4
 6      992GB   1000GB  8577MB  logical   linux-swap(v1)


Error: Invalid argument during seek for read on /dev/sdb 

sdb is the 3TB HDD here

---

### Post by Templerun on 2012-09-14
> **oldfred said:**
> What mode is BIOS in for the drive? For new drives the AHCI is usually required. Is BIOS up-to-date?

I will try AHCI and report back

---

### Post by darkod on 2012-09-14
The SATA mode in BIOS should be AHCI. After you double check that, you can write new gpt table on the disk anyway. I assume the disk is new and doesn't have any data. In that case, use parted and try:
```
sudo parted /dev/sdb
print
mklabel gpt
quit
```The print command might give the same error as earlier, I just used it to make sure sdb is the 3TB disk before writing blank partition table. :)

If you want to create partitions, you can also try parted. Are we talking only about linux type partitions or also ntfs?

---

### Post by Templerun on 2012-09-14
> **darkod said:**
> The SATA mode in BIOS should be AHCI. After you double check that, you can write new gpt table on the disk anyway. I assume the disk is new and doesn't have any data. In that case, use parted and try:
```
sudo parted /dev/sdb
print
mklabel gpt
quit
```The print command might give the same error as earlier, I just used it to make sure sdb is the 3TB disk before writing blank partition table. :)

If you want to create partitions, you can also try parted. Are we talking only about linux type partitions or also ntfs?

I parted it as u said and hard rebooted to check if it got mounted. Well! now not only it not mount, it is saying it is 2000GB now.

sudo parted -l
[sudo] password for ajit: 
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  466GB   466GB   primary   ntfs            boot
 2      466GB   1000GB  534GB   extended
 5      466GB   992GB   526GB   logical   ext4
 6      992GB   1000GB  8577MB  logical   linux-swap(v1)


Model: ATA ST3000DM001-9YN1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

---

### Post by darkod on 2012-09-14
It said that earlier too, only you didn't notice it. The last line of the cat /proc/partitions output says 1953536567 which is close to 2 billion bytes (2TB), not close to 3 billion as it should be.

At least now there is no error reported.

This might be an issue with the fact that it's a 4KB sector disk, not a 512B sector. It might not get the size right.

The BIOS might not be recognizing it as 3TB also. Can you look more carefully in BIOS whether it's reported as 2TB or 3TB. Not only the model number, we know that is correct, parted can also see it as ST3000DM001, but whether BIOS reports the actual size as 3TB.

If BIOS sees it as 2TB, all programs will see it like that too.

Right now I think you will have no problems creating partitions with parted, but you need to solve the 2TB issue.

PS. Also, you said that "now it doesn't mount". What do you expect to mount? There are no partitions on it. It doesn't work that way. You first need to create a partition with a filesystem, and then mount it at some mount point. Right now there is nothing to mount.

---

### Post by oldfred on 2012-09-14
I do not know much about the new 4k drives, but have some links:

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by Templerun on 2012-09-14
> **darkod said:**
> It said that earlier too, only you didn't notice it. The last line of the cat /proc/partitions output says 1953536567 which is close to 2 billion bytes (2TB), not close to 3 billion as it should be.

At least now there is no error reported.

This might be an issue with the fact that it's a 4KB sector disk, not a 512B sector. It might not get the size right.

The BIOS might not be recognizing it as 3TB also. Can you look more carefully in BIOS whether it's reported as 2TB or 3TB. Not only the model number, we know that is correct, parted can also see it as ST3000DM001, but whether BIOS reports the actual size as 3TB.

If BIOS sees it as 2TB, all programs will see it like that too.

Right now I think you will have no problems creating partitions with parted, but you need to solve the 2TB issue.

PS. Also, you said that "now it doesn't mount". What do you expect to mount? There are no partitions on it. It doesn't work that way. You first need to create a partition with a filesystem, and then mount it at some mount point. Right now there is nothing to mount.
It did not show up as 3TB on post either but I was able to set it up alright later thru Webmin&#347; partitioning tool. Now even that is refusing to take it as 3TB?!! How do I roll it back so I can show you that it actually worked before. Infact all is well till the time I do not shut down completely. It starts showing errors after that. Any further suggestions to make it work the way it should.

---

### Post by darkod on 2012-09-14
I don't know webmins partitioning tool. But if the disk was not correctly recognized from the start, using any partitioning tools to "make" it correct can actually have opposite effect. Maybe because of this it didn't survive a reboot and keep the size.

First starting from BIOS it should be recognized as 3TB. If that is not so, I wouldn't try to make it be "correct" with any partitioning tool. That can just mess up the cylinders/heads/sectors relationship.

I'm not sure what's best to do right now. I have never had a case so far that a disk wasn't recognized as the correct size.

---

### Post by SeijiSensei on 2012-09-14
Have you looked to see if there is a more recent BIOS?

---

### Post by Templerun on 2012-09-15
> **SeijiSensei said:**
> Have you looked to see if there is a more recent BIOS?
No! No luck on Bios front, all that is available is an update for the video chipset thru Bios and couple of COM port and stuff updates. I have talked to the retailer he might agree for a trade in if HDD is sell able. I will pick up 2x2TB instead and few other things that I was thinking of adding later.

---

### Post by Templerun on 2012-09-15
Anyone trying this on a later date please also try this method with a special note to configure Kernel also ... "Set **CONFIG_EFI_PARTITION** to y to compile this feature". I wish I could try and report but the disk is already out of my system and ready to be replaced.

[http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html](http://www.cyberciti.biz/tips/fdisk-unable-to-create-partition-greater-2tb.html)

---

### Post by oldfred on 2012-09-15
That info is from 2007 and for RedHat. It is now a bit dated.

Several users have posted with systems of 16TB or more.

---

