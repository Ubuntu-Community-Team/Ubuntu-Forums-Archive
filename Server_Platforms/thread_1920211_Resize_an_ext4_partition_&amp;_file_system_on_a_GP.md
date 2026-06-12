---
title: "Resize an ext4 partition &amp; file system on a GPT partition table"
date: 2012-02-04
forum: Server Platforms
---

### Post by Sab3r on 2012-02-04
I've got a md array with a GPT partition table and I had two partitions on it with ext4 file systems. Now I've removed the first partition and would like to resize the second partition so that it uses the whole array. 'parted' gives a warning that it shouldn't be used for resizing file systems, 'fdisk' doesn't support GPT tables, 'gdisk' doesn't provide partition resizing and 'resize2fs' can't resize partitions, only file systems. 

What else is there?
Also, I've read that it's impossible to enlarge a partition to encompass free space before the said partition, is that true?

---

### Post by oldfred on 2012-02-04
Do not use gparted or any of the standard partition tools on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by shumifan50 on 2012-02-04
Depending on the type and amount of data as well as its importance, I would strongly suggest backing it up, resize the partition and so losing all the data on the disk and then restoring the data from the backup. This is more of a problem with the boot disk, but I use PING's linux to boot off a CD and then tar the system disk to a USB disk. To recreate I do a basic install of Linux and then untar the backup using the PING linux again.

If you are going to resize a partition, I would VERY strongly recommend you make a full backup anyway - I don't trust any of the resizing tools out there.

Note: PING supports resizing partitions, but I would not use that feature. It can only cause big heartache later if the disk has undetected corruptions on it.

---

### Post by Sab3r on 2012-02-04
Oh damn. I don't have the funds to buy drives to backup everything, so I guess I'll just leave it be for the moment. 200GB's lost on a 5.5TB RAID-5 isn't the end of the world. 

One question though, is 'mdadm --grow' possible without being in danger of losing data?

Thanks.

---

### Post by hawkmage on 2012-02-04
You should not conciser your RAID 5 array as good as having a backup.  On a NAS forum I also frequent there is a common saying: "RAID is not a backup".  If the data on your 5.5TB RAID volume is important I would suggest finding some way to back it up.

---

### Post by Sab3r on 2012-02-05
Yeah I know. It's only a home file storage/server, 99% of the stuff on it can be found online. 

I've been running my server for years without any RAID arrays or backups and it's been fine. So now, with a RAID-5 array, it should be better than fine. :P 

If one drive fails, it can be swapped and nothing is lost. What are the odds of more than one drive failing?... 

"knock on wood"

---

### Post by shumifan50 on 2012-02-06
The probability of hardware failure is fairly slim, it is software corruption that is a bigger problem, like directory corruption. Consider this: How many system failures are caused by hardware and how many are caused by software? The answer is that hardware only accounts for about 3% of system failures. So, although protecting against hardware failure might give you a warm feeling, you need protection against software failure more.

---

