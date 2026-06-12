---
title: "How to convert to dual boot?"
date: 2011-04-19
forum: System76 Support
---

### Post by kotoro on 2011-04-19
What would be the safest procedure to take to resize the linux partition and back up the boot sector to allow windows 7 to be installed to a smaller partition on the drive? (I would like to be able to play some PC games in my off time, but will be running linux most of the time.)

What would be the necessary steps to backup the boot sector (grub), resize the partition, and restore grub after installation is completed?

Are there any contingencies that I would need to be aware of?

The machine is a serval professional, with all hardware upgraded to the best (except for HDD/CPU, I left CPU two levels down, and selected largest sata HD with no solid state)

---

### Post by wilee-nilee on 2011-04-19
> **kotoro said:**
> What would be the safest procedure to take to resize the linux partition and back up the boot sector to allow windows 7 to be installed to a smaller partition on the drive? (I would like to be able to play some PC games in my off time, but will be running linux most of the time.)

What would be the necessary steps to backup the boot sector (grub), resize the partition, and restore grub after installation is completed?

Are there any contingencies that I would need to be aware of?

The machine is a serval professional, with all hardware upgraded to the best (except for HDD/CPU, I left CPU two levels down, and selected largest sata HD with no solid state)


Take a look here, also you don't have to back up the boot sector. 
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)

But I would clone the partitions you do have before starting with clonezilla just to be safe.
[http://clonezilla.org/](http://clonezilla.org/)

I suggest clonezilla as I don't know if the system 76 computers have a backup partition.

---

### Post by ashickur.noor on 2011-04-19
Use remastersys to backup yout /. Then Install Windows. Then again install Ubuntu that you make from remastersys.

---

### Post by isantop on 2011-04-19
Actually, we have a fairly simple procedure available on the Knowledge Base. Backing up is always a good idea, but you won't have to reinstall Ubuntu, only GRUB.

[http://www.knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://www.knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

---

### Post by kotoro on 2011-04-26
Following those instructions seemed to work but I got warnings from grub about not being able to properly embed and something about unreliable blocks.

Also disk utility now complains that the partitions are not aligned. How should I fix this?

Based on what I read online I'm thinking maybe I should create a 1MB boot partition for grub so it doesn't bitch about the MBR being too small, but I'm not sure.

as for the misaligned partitions I tried to allocate 100GB to windows, but perhaps I need more guidance.

What can I do from here to make grub installed properly without --force flag being used and make disk utility happy about partition alignment. Also, does it even matter?

---

### Post by oldfred on 2011-04-27
If you are getting warnings you are installing grub to a partition like sda1 not to the MBR. Drives are sda, sdb etc. You have to have grub's boot loader in the MBR of the drive you boot.

Are the errors related to cylinders? They were obsoleted when hard drives went over 8GB and CHS cylinders, heads, sectors was converted to LBA - large block allocation.

New partitioning tools do align to 1 MiB (2048-sector) boundaries 

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ [COLOR=Red]/dev/sda[/COLOR]
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Note: on the grub install line there is no number at the end. You mount the partition sda5 in above example and install to the drive sda.

---

### Post by kotoro on 2011-04-27
I followed the instructions to the letter. I know not to attempt to install it to the partition, but it was still giving me that error.

I read somewhere that it could be related to the drive having 215MB logical sectors even though the physical sectors are 4096MB.

edit:

more /sys/block/sda/queue/*block_size
::::::::::::::
/sys/block/sda/queue/logical_block_size
::::::::::::::
512
::::::::::::::
/sys/block/sda/queue/physical_block_size
::::::::::::::
4096


sudo fdisk -l

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000055d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       76195   612032511+  83  Linux
Partition 1 does not start on physical sector boundary.
/dev/sda2   *       76195       76208      102400    7  HPFS/NTFS
/dev/sda3           76208       89249   104755200    7  HPFS/NTFS
/dev/sda4           89249       91202    15683958+   5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5           89249       91202    15683958   83  Linux
Partition 5 does not start on physical sector boundary.

---

### Post by oldfred on 2011-04-27
I do not know about the new 4k drives.

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by kotoro on 2011-04-27
sudo parted /dev/sda unit s print
Model: ATA ST9750420AS (scsi)
Disk /dev/sda: 1465149168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      1s           1224065023s  1224065023s  primary   ext4
 2      1224065024s  1224269823s  204800s      primary   ntfs            boot
 3      1224269824s  1433780223s  209510400s   primary   ntfs
 4      1433781251s  1465149167s  31367917s    extended
 5      1433781252s  1465149167s  31367916s    logical   linux-swap(v1)


If I understand correctly, all I have to do is make sure the partitions start & end at sectors that are multiples of 8, additionally I think the first partition is supposed to start at or after sector 64 to allow for the proper linux MBR to be installed. Can anybody guide me to how I can resize these partitions without losing data and what sizes I should use? Also how do I ensure that the partitions are moved to the correct location?

---

### Post by kotoro on 2011-04-27
UPDATE:
To System76 staff, please take note that some of your SATA HDD have physical sectors of 4096B and logical sectors of 512B, which complicates the partitioning. Following the instructions given on the website linked earlier will only work properly if you stick to partition sizes that match the underlying 4096 byte structure.  (by properly I mean it won't mess up partition alignments, assuming they were properly aligned to begin with. I really don't know that they were, since I didn't look for any warnings until after I set up dual boot the first time.)

Additionally it helps to calculate partition sizes that end at a cylinder boundary to eliminate warnings about that, though I doubt it matters very much as LBA doesn't really use cylinder addressing. Still, its usually good to do what you can to eliminate warnings as well as errors.

Would be good to create a small tutorial on restoring System76 in the event of a complete repartitioning/formatting. I figured it out based on the information in the upgrade tutorial, but it may not be obvious to everyone.

Since I had the misfortunate result of bricking the partition table, I have done my partitioning to set up the partitions that I will be using to install ubuntu, but first I am going to install windows to make it that much easier. (grub will be overwriting the bootloader and I can just update grub to see windows without having to load to the live disk again.)

Someone with good partitioning knowledge should write up a small tutorial for newbies to use as a reference. When we resize the partition to make space for windows, in the case of 4096 phys/512 log sectors, we have to be careful that the start of the partitions match the 4096 structure, and preferably the ends would be at cylinder boundaries, at the very least to shut up the warnings, and also to prevent performance degradation due to misaligned partitions.) There must be relatively simple formulas to use to take the drive geometry numbers and turn them into sector/cylinder start/end positions.

in any case if my partitioning worked correctly, i'll post my sizes along with my drive geometry to show how I resolved it.

(I was using parted to set the start/end positions and gparted to initiate formatting of those partitions after they were created, since parted doesn't like doing that for some reason.)

---

