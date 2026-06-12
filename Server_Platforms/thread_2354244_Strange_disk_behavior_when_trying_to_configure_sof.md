---
title: "Strange disk behavior when trying to configure software raid 1"
date: 2017-03-01
forum: Server Platforms
---

### Post by jefkebazaar2 on 2017-03-01
I am experiencing some really strange behavior when trying to setup software raid 1 on Ubuntu.

  I have 2 disks of 2TB. I was trying to setup my raid with on both  disks an 8GB partition for swap, a 1GB partition for /boot and a third  partition with the rest of available size for mounting /.
  However, I needed to redo it multiple times, since I always was  forgetting one thing or another, before I finally got the hang of what I  wanted and how to set it up.
  Now however, I can't configure software raid at all anymore.

  I create the 3 partitions on both disks using the manual partitioner. 
 Next I proceed to the step "setup software raid". When I get in this step, sometimes the ubuntu installer complains that  there are no active raid partitions to configure (although in the  previous step I could see all 3 partitions on both disks, configured as  physical raid volumes. Even if I reboot the system with a live ubuntu cd  and use gparted, it shows the 3 raid partitions on both disks, however  ubuntu can't find them during install).

  On other tries, when I proceed to the step to configure sofware raid,  the raid configuration tool only shows one or multiple of the  configured raid partitions, but never all of them. (example it shows the  3 raid partitions on one disk but only 2 on the other disk, again  although they are all clearly there, created in the previous step of the  manual partitioning. Even rebooting the system again in a live ubuntu  environment using gparted shows all 3 of them on both disks, available  as raid partitions).

  I have no idea what is going on. I have tried multiple times to  reformat the entire disks using gparted, fdisk, ... from a live ubuntu  and trying over, however every time I get this strange behaviour: no  raid partitions found, only some found, ... and yet, booting in a live  linux environment, they are right there on the disks...

  Sometimes, when trying to reformat the disks from a live ubuntu,  after failing the raid install yet again, I can't even remove some of  the raid partitions with gparted or disks and need to resort to example  fdisk to complete reformat the disk (keeps saying that some of the  partitions are locked/busy).

  Is this one of my disks that is completely fubar and that needs to be  replaced or is there something else going on here? 
Seems like there is some partitioning issue with my disks because of  trying too many times to setup the software raid 1 that is like  "permanently engraved" in the disk. Not even reformatting the disks  seems to solve it...
  Thanks in advance for any help!!

---

### Post by darkod on 2017-03-01
If you already created swap space on the disks, the installer is mounting it so it can use it. This happens even during installation. That is probably the message about the partition/disk being busy.

Also, if creating partition with Gparted in advance, make sure you do NOT format them. mdadm raid is set up with the partitions unformatted because the md device will hold the filesystem. That's why I prefer doing partitions with parted because Gparted by default is formatting them unless you change the option.

From live mode (live cd), show us:
```
sudo parted -l (small L)
```

Lets see the partitions you've got.

---

### Post by jefkebazaar2 on 2017-03-01
Alright, I'll have to do that this evening, at work now.  I can say however, I have done the following several times: 
- boot from live cd 
- use gparted, remove all partitions etc, format the disks as either GPT or MSDOS  
- (if some of the old partitions are locked, indeed as you said always swap, I use fdisk to remove them)
 - I reboot again in the live cd, I check again using gparted: both disks have no partitions. 
- I boot in the ubuntu server installer, choose manual partitioning, both disks show up, completely empty, so the installer sees NO partitions left
 - I select both disks, have them create a new partition table on both. 
- I then create the 3 partitions on both disks, they all appear in the partitioner, no issues there. 

- I proceed to "configure software raid": I have some of my raid partitions missing, although they did ALL show up with the same size, the same config (example /boot as bootable raid partition), ...   in the previous overview screen of the manual partitioner.
For some reason, when going from creating the raid partitions to configuring the software raid, the installer doesn't see some of the created raid partitions anymore (sometimes one, sometimes several, sometimes it even claims there are no raid partitions found), although they were just created...  

I have for example had the following: when configuring software raid, it sees both /boot partitions, both swap partitions but only one /-partition on one of the disks. I create in raid the 2 /boot, the 2 swaps, it even lets me create the /-raid partition in raid 1 although I can only select one partition (the other one it doesn't show)!!! I finish raid config. I get back in the overview screen of the partitioner, and suddenly it shows 4 raid partitions...: the swap I created, the /boot I created, the /-partition (which is weird, because it was missing one of the necessary partitions) and another swap raid partition (which seems to be the one that I removed using gparted from the livecd, the one that was locked -> suddenly this old deleted raid partition pops up again...)  Like I said, totally weird behaviour, never seen something like this before...

---

### Post by jefkebazaar2 on 2017-03-01
By the way, just found this, this looks similar to the issues I'm seeing:
[https://mikebeach.org/2013/10/25/cannot-delete-a-raid-swap-partition-during-ubuntu-installation/](https://mikebeach.org/2013/10/25/cannot-delete-a-raid-swap-partition-during-ubuntu-installation/)

---

### Post by darkod on 2017-03-01
I wouldn't go deleting partitions during installation. Either start with blank disk (new partition table), or have the partitions created (not formatted) in advance so you only need to use them in the installer.

I have done a number of installation but I have never found these issues you are describing in the installer partitioner.

Also, not sure if you are aware, but if you decide to use GPT tables on the disks then grub2 needs a small 1MiB partition without any filesystem and with the bios_grub flag active. You can make it first partition on the disks. This is because grub2 doesn't fit on gpt MBR, it's smaller than msdos MBR.

---

### Post by jefkebazaar2 on 2017-03-01
Me neither, I had done some working software raid 1 configs in the past already.
That's why I'm starting to wonder if one of my two (brandnew) HD's is already fubar for some reason or another...

And by the way, had this weird behavior both with the debian jessy installer and with the ubuntu 16.04 LTS installer.

---

### Post by jefkebazaar2 on 2017-03-01
My current layout on the system:

root@ubuntu:~# parted -l
Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1024MB  1023MB  primary  ntfs         boot, raid
 3      1024MB  1992GB  1991GB  primary               raid
 2      1992GB  2000GB  8191MB  primary               raid


Model: ATA WDC WD20EZRX-00D (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1024MB  1023MB  primary               boot, raid
 3      1024MB  1992GB  1991GB  primary               raid
 2      1992GB  2000GB  8191MB  primary               raid

---

### Post by jefkebazaar2 on 2017-03-01
When proceeding with the partition layout mentioned above to the next step, configuring software raid 1, I only have the following partitions to choose  from to create RAID1: 
- /dev/sda1 (1024MB) 
- /dev/sdb1 (1024MB) 
- /dev/sdb3 (one of the big partitions) 

 That's it... So yet again, I can't explain what's going on... Seems like the disks are completely fubar...

---

### Post by darkod on 2017-03-01
Hmmm, it is a possibility. By the way, why does sda1 have ntfs filesystem? Not that it matters, because ext4 would go over the raid. But I still prefer "clean" partitions.

Maybe the disks are really bad. I would give it one more try creating the partitions first in live mode using parted. Sorry can't be much more help, you are doing it correctly...

---

### Post by jefkebazaar2 on 2017-03-02
You're never going to believe this...
Yesterday evening I tried again, but what I did different was:
- from the ubuntu installer, I decided to first "erase all data" on all found partitions, whether they were "left over from a previous attempt" or whether I just created them in the installer.
- next I rebooted from a livecd, used the tool "testdisk" to overwrite the MBR and zero out the partition tables (2 functions available from testdisk).
- next I tried another raid install, but this time, I re-arranged my partitions:
1) previous times I placed /boot at the beginning, swap at the end and / in between.
2) Now I decided to create swap as primary, place at beginning, next /boot as primary, place at beginning and then add / as primary.
3) this time I explicitely checked that / should be re-formatted too (was not switched on by default when creating that partition).

And this time... it installed, full 100% and bootable too. Problem solved, but I have no idea what the problem was and what specifically solved it...

---

### Post by darkod on 2017-03-02
Great. Please mark the thread as solved. You can do that in Thread Tools above the first post.

I think the MBR zero out helped. There must have been some weird/confusing remains in the partition table. Anyway, it's working now.

---

### Post by jefkebazaar2 on 2017-03-02
Done, thanks for the help!

---

