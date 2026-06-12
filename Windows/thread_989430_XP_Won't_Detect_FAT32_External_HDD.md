---
title: "XP Won't Detect FAT32 External HDD"
date: 2008-11-21
forum: Windows
---

### Post by BetaMaster on 2008-11-21
I have a 400GB external HDD I've been using in Ubuntu to store my music for some time now. I just rebooted into Windows because I'm getting a new iPod and wanted to update the firmware/transfer the library via iTunes, but my external HDD won't show up in XP! I tried it on my laptop too, and it won't show up in My Computer.

The device registers in the Device Manager as a USB Mass Storage device, and installs upon plugging it in, but it won't show up in My Computer, nor does it seem to receive a drive letter.

Any ideas what the problem could be?

EDIT
Looking in the Disk Management in Windows, apparently XP is perceiving my Fat32 drive as a GPT Protective Partition - something XP 32-bit can't access. Any idea why this would happen, or how I could fix it?

---

### Post by RealG187 on 2008-11-21
[http://computerhelpforum.org/forum/index.php?showtopic=11614](http://computerhelpforum.org/forum/index.php?showtopic=11614)

Apparently GPT is for 64 but, is your Ubuntu 64 bit?

---

### Post by BetaMaster on 2008-11-22
I'm currently using 32-bit Ubuntu but now that you mention it, when I formatted the drive to Fat32, I was running 64-bit Ubuntu.

I haven't tried this before, but is it possible to break a partition up into two partitions, and then afterwards delete one of the partitions and resize the remainder?
The reason I ask is, I don't have a place to put the current contents of my external drive, but I have more than enough space left on the drive to, say, split the drive into two partitions, move them to the second, delete the first, and resize the second to fill the drive - if that's possible.

---

### Post by K.Mandla on 2008-11-22
Moved to Windows Discussions.

---

### Post by andras artois on 2008-11-22
this happened to me, i was using a 500gb lacie external hard drive. I had to manually install the drivers for it. bit rediculous because any other computer it seemed to work fine.

---

### Post by BetaMaster on 2008-11-22
Should a drive automatically mount while resizing a partition to make it bigger in Ubuntu? That just happened to me. Right now I'm freaked out that it's going to damage my files or my drive, but gparted is still resizing the partition. It just says it'll take five and a half hours to finish. I too nervous to unmount the drive.

Should it take this long?

---

### Post by RealG187 on 2008-11-22
> **andras artois said:**
> this happened to me, i was using a 500gb lacie external hard drive

my 500  gb lacie works fine in ubuntu and windows, even though it said Linux  cant read it if i allocate all the drive to one partition. I think I used gparted or xp's disk manager. I know i did not use lacie's utility.

---

### Post by BetaMaster on 2008-11-23
Well, gparted had a problem moving the partition, and now I have a 400GB partition that shows up as having a total capacity of 160GB.

I guess I'll have to find some way to back up the data and format the drive.

---

