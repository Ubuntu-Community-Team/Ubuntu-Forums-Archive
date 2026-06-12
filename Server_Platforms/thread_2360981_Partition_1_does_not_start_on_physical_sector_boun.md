---
title: "Partition 1 does not start on physical sector boundary"
date: 2017-05-10
forum: Server Platforms
---

### Post by gian on 2017-05-10
Hello All,

I have an old home server with a degraded Raid 1 array, made of two couples.

The first has / and /home, the second has only /Archive.

I do have backups, but I would like to pull the data out of the working disks anyway: there is always something to learn.

While I can mount the disk with /Archive on a desktop running Ubuntu 16.04 with mdadm (the disk is inside an USB enclosure), I can't do the same with the disk that has the root partition.

Examining the disk with fdisk -l, I have:

Disk /dev/sde: 1,8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: F7F5F9A5-8E96-4770-B755-6EFB6573C02A

Device        Start        End    Sectors  Size Type
/dev/sde1        34       1987       1954  977K BIOS boot
/dev/sde2      1988   58595738   58593751   28G Linux RAID
/dev/sde3  58595739   70314489   11718751  5,6G Linux RAID
/dev/sde4  70314490 3907029118 3836714629  1,8T Linux RAID

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.

Where to go from here? Thanks for your advice,

Ciao,

-Gian

---

### Post by TheFu on 2017-05-10
Well, you should backup any data on sde and repartition being careful to stay on 4096 byte boundaries for each partition.  Then restore.
By not being on physical sector boundaries (misaligned), there is a 20-30% performance hit.   
[http://www.storagereview.com/the_impact_of_misalignment](http://www.storagereview.com/the_impact_of_misalignment) 
[https://www.ibm.com/developerworks/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/library/l-linux-on-4kb-sector-disks/)

If you use parted or gparted to do the partitioning, they will automatically handle the alignment. Not all versions of fdisk do this, which appears to be the issue you have.  I find it easier to avoid fdisk use.

---

### Post by gian on 2017-05-10
TheFu,

thanks for your kind reply.

the disks have been removed from the server because port 22 looks closed now, so no ssh access and no backup of data is possible.

I have gparted on my desktop, will look how to align automatically the drive.

I wonder if the BIOS boot partition is the problem: should I remove it?

-Gian

---

### Post by TheFu on 2017-05-10
Alignment is for each partition.  The earlier partitions don't impact the following ones usually if each is started on a properly aligned location.

---

### Post by oldfred on 2017-05-10
The bios_grub partition is required for grub to install correctly with gpt partitioned drives.

All current partition tools align partitions correctly by default and have for several years.
Windows started when Windows 7 was released and Linux about a year later.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[URL="http://ubuntuforums.org/showthread.php?t=1685666"]http://ubuntuforums.org/showthread.php?t=1685666
[/URL]
 sudo parted /dev/sda unit s print
sudo parted /dev/sda align-check opt 

[URL="http://ubuntuforums.org/showthread.php?t=1685666"]
[/URL]

---

### Post by gian on 2017-05-11
Thanks, Oldfred,

I will try that.

I would like to preserve data on partitions 2 and 3: would it be useful to delete partitions 1 and 3 before alignment?

---

### Post by darkod on 2017-05-11
If you want to copy the data first, I would do that first. That message about partition alignment is only for information, the disk will still work. So if you don't have recent backup, copy the data first.

After that, because you already have current copy of the data, you can think about alignment or simply destroying these partitions and create new ones that are aligned.

If you try alignment now before copying data, I understand that process as moving the partition little, which means it does carry little risk. You don't even have to align them, especially if you will not be using this disk as it is soon (you said it is one half or degraded array, what do you plan to do with it?).

---

### Post by TheFu on 2017-05-11
As others above have said, misalignment isn't a data-loss issue, it is about performance. If you've seen it, you feel the poor performance.  As more people get SSDs, it isn't really noticed. It is a spinning-rush (HDD) issue.

I know that fdisk for 12.04 didn't do the alignment on release of that distro. As someone with a 12.04 system until about a month ago, I never knew exactly which version of fdisk did or didn't do the alignment as desired automatically.  fdisk could be forced, through careful selection of the start sector, to be aligned.  It didn't support GPT either, at least when the OS was released.

Similarly, I don't know if the 14.04 version of fdisk handles the alignment issue either.  I've had 14.04 systems which were misaligned. Think it was fdisk that allowed it at the time.  I suspect the version of fdisk in 14.04 and later was updated to handle alignment AND GPT, but having a newer version doesn't fix all the installs that happened prior to the fdisk update.  Many people still have lots and lots of 14.04 systems.  I do.

I prefer the fdisk menus/options, but parted is what I've used since it was easier than calculation sector alignment.  Not everyone has a GUI for their systems, especially when disks are being managed 10K miles away.

---

### Post by gian on 2017-05-11
I assumed I could not mount the drive BECAUSE partitions were not properly aligned: am I wrong?

This array has been spinning for years, so I will replace the drives with 2x 4TB new ones.

However, for some reason, at the moment I cannot ssh to the server: port 22 is closed. Maybe a read only FS?

So, I imagined to use the drive with an external USB enclosure and copy the data to the new array, but I cannot mount it.

BTW, I can mount the sound disk of the second array, which failed, but that one has no BIOS boot partition.

---

### Post by TheFu on 2017-05-11
Mounting doesn't care about partition alignment.
Hard to manage a system that isn't running ssh.  One of my systems, using SSD, switches to read-only about once every other week.  I reboot it. Haven't been able to determine the root cause, but it isn't an important box and I have backup religion, so I'm not worried.  Losing the SSD would be a minor inconvenience.  I have a spare that is 2x larger within arms reach. Just haven't gotten around to swapping them.

I've never seen the need for a separate boot partition, except when using LVM or whole disk encryption. Never needed one for GPT disks either.  None of my systems use UEFI to boot, that is an important differentiation.  I think there is a special partition necessary for UEFI - just never needed it myself.

I've never setup RAID on OS disks.  Just for data.

---

### Post by darkod on 2017-05-11
Did you try to assemble the array and mount it, or to mount the partitions directly? In mdadm arrays it is the array that holds the filesystem and although it might be possible for raid1 I have never actually tried to mount partitions directly. You should mount the arrays.

After you connect the disk to the machine where you want to read it, first thing to check if whether the partitions are read correctly.
```
lsblk
sudo blkid
```

Does that find the partitions? Show us the output and explain which partitions are from the arrays.

Also check if mdadm is maybe trying to assemble it:
```
cat /proc/mdstat
```

Does that show any arrays?

We need to know that first before suggesting how to mount it.

---

### Post by gian on 2017-05-15
as I learnt that alignment doesn't matter for mounting, I looked elsewhere.

Loading mdadm on a live CD did the trick, and I could pull data off the disks.

---

### Post by darkod on 2017-05-15
If you have solved this then please mark it as solved. You can do that in Thread Tools above the first post.

---

