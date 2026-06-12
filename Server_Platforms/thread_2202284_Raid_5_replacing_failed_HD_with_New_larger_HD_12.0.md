---
title: "Raid 5 replacing failed HD with New larger HD 12.04 lts"
date: 2014-01-28
forum: Server Platforms
---

### Post by speed32219 on 2014-01-28
I had a raid5 setup for video files with 4 1.5TB disks.  I found the server re-syncing at an incredibly slow speed and after running smart-tools I found the failing drive.  Replaced it with a 2 TB HD and have a couple questions.  

using mdadm commands 
I failed the problem drive
I removed the drive from the array.

I do not know if I need to format and setup the new dirve for linux raid, I do not use partitions just the whole drive.  I can not find out what needs to be done to prepare the new HD. After sending time googling I found where someone posted to just run this from the shell.   mdadm --manage /dev/md0 --add /dev/sdd (my failed drive).  That is what i did and below is the status of where it is in re-syncing.  Is this all that needs to be done, if so that was real simple?

$cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd[4] sdb[0] sde[3] sdc[1]
      4395022080 blocks super 1.2 level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      [=>...................]  recovery =  6.9% (101589380/1465007360) finish=725.1min speed=31336K/sec
      bitmap: 11/11 pages [44KB], 65536KB chunk

After it is finished syncing what commands should I run if any to possibly update the mdadm.conf so it will start after rebooting.

Also note that before the SDD drive had a location designation of [2] and is now change to [4].  Any problems with that?

Thank you for your replies.

---

### Post by speed32219 on 2014-01-28
Well after looking at the error logs, I guess I should have used parted and formatted the disk with ext3 and as a raid device.

**EDIT:**  Well I was wrong, it completed and sure enough it was added back into the array and everything is working and looking good.  

So now I know, purchasing a new drive that is formatted fat 32 all you need to do is replace the failing raid5/6 drive and enter
sudo mdadm --manage /dev/mdX --add /dev/sdX (X being the variable for the array and device being replaced) and it will auto re-sync.  Of course I did the commands while raid not mounted. SO now I have a 2 TB in place of a 1.5, looks like I need to start replacing the 1.5TB drives wtih 2.TB and grow the array.  I have three new 2 TB drives which I am going to add.  Once completed growing the new array I will reformat the 1.5TB drives and install in a 4 bay mediasonic enclosure and use the 6 TB to provide backup to my files on the raid5 array.

---

