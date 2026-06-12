---
title: "/home in separate partition during install"
date: 2009-11-16
forum: The Cafe
---

### Post by aspergerian on 2009-11-16
I'm not too experienced, having installed Heron on two netbooks which I still use. Many posts recommend installing /home on its own partition. I've been going round and round with an Acer 1410 solo core which began as Vista Home Premium. I've been re-confronting the install moment of automatic versus advanced and have tried each, repeatedly during this latest go around. The interface during install isn't quite as obvious (intuitive) as it could be. Bottom lines (for now):

I'd like to see a (clear) way to format entire disk because partitioning during install seems virtually if not totally locked into existing partitions. 

I'd like to see an install/partitioning screen that made making a separate /home partition easier.

---

### Post by Sealbhach on 2009-11-16
Yes, it can be a tad confusing. Best thing is to back up your data, shut your eyes and go for it. Maybe Psychocats can help you: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

.

---

### Post by cariboo on 2009-11-16
If you are familiar with partitioning drives, use the manual partitioning option, it is easy to use. I've never tried auto partitioning.

---

### Post by squilookle on 2009-11-16
I've had the separate /home partition in the past and its great to be able to upgrade by clean install or even switch distributions and keep the home directory. 

The only two resons I don't have a separate partition at the minute are

1. I installed Windows XP (after having not had it for a while) and I don't really have a large hard drive anyway, but I lost a chunk of it to Windows...
2. Its good to clean /home out every so often, otherwise there will be lots of rubbish in there that is not needed.

---

### Post by aspergerian on 2009-11-16
Tried that psychocats url. Found another too. Ended up with /home on separate partition that almost worked. System seemed to run fine until shutdown and reboot. Booting didn't occur, problems with files named /.ICEauthority and /home/tcb/.nautilus 

At this point, I'm giving up the quest for /home on a separate partition, have reinstalled 9.10 using entire drive. /home isn't on separate partition.

Would like in this thread to suggest to developers of next Ubuntu that the partitioning section of install be made clearer, more functional - especially for users who aren't too experienced. 

Offering /home on a separate partition during automatic install doesn't seem too much a next step, but an important one.

---

### Post by sgosnell on 2009-11-16
If you need some visual help, try running the live CD without making any changes to your system.  Run gparted, and you can wipe your HD and make two partitions on it of whatever size you want.  I tend to make the / partition smaller and /home larger, to allow for data storage.  After that, you'll end up with sda1 and sda2 for the partitions.  Run the install program, and select sda1 for / and sda2 for /home.

---

### Post by aspergerian on 2009-11-16
> **sgosnell said:**
> If you need some visual help, try running the live CD without making any changes to your system.  Run gparted, and you can wipe your HD and make two partitions on it of whatever size you want.  I tend to make the / partition smaller and /home larger, to allow for data storage.  After that, you'll end up with sda1 and sda2 for the partitions.  Run the install program, and select sda1 for / and sda2 for /home.

I'm trying that (somewhat). I didn't see in gparted a way to format the entire drive. The drive entirely (at this point) dedicated to 9.10 had ~230gb as sda1, with an ~9gb swap file at end of drive. I was able to split the 230gb into an additional two partitions -- one for /home, which I selected, another formatted as FAT32 (for now) because at some point (again) this computer will be dual boot because I'm still addicted to Photoshop CS4 (yes, I've tried gimp). 

For now, the re-install based on your suggestion is occurring. I selected sda1 to be /  

I hope that was correct. 

Thnx for the suggestion. Still wondering why formatting the entire drive (as a first step) was hard to find in gparted running from the install CD.

---

### Post by Exodist on 2009-11-16
> **aspergerian said:**
> I'm not too experienced, having installed Heron on two netbooks which I still use. Many posts recommend installing /home on its own partition. I've been going round and round with an Acer 1410 solo core which began as Vista Home Premium. I've been re-confronting the install moment of automatic versus advanced and have tried each, repeatedly during this latest go around. The interface during install isn't quite as obvious (intuitive) as it could be. Bottom lines (for now):

I'd like to see a (clear) way to format entire disk because partitioning during install seems virtually if not totally locked into existing partitions. 

I'd like to see an install/partitioning screen that made making a separate /home partition easier.


There are good and bad points to having a separate /home partition.
Good is its easier to reclaim your data if you must reinstall the entire OS.
Bad is fixed size, so if your HDD is small you may want to have as much room as possible. 

If you have a small (less then 120GB) hard drive that your dual boot. I would not create a separate /home partition. But larger should allow you to be more flexible with space.

I have my root / file system on a older 74GB WD Raptor and my /home on a newer 320GB WD Cavier. 


To set up the /home partition, you need to choose advanced settings. Create two partitions for linux. First for / root file system, this one must be bootable with the mount point / . The 2nd one just have the mount point set to /home. That about all it takes. 
Or at least that all I remember, it fairly easy.

---

### Post by aspergerian on 2009-11-16
> **Exodist said:**
> There are good and bad points to having a separate /home partition. Good is its easier to reclaim your data if you must reinstall the entire OS. Bad is fixed size, so if your HDD is small you may want to have as much room as possible. 

Thnx for the insights about hd sizes. 

My photo files become huge and live mostly on a separate HD, which usually is connected to photoshop computer while processing photos. I also do medical research and like to have files that are accessible by both Ubuntu and either Vista or w7. 

Meanwhile, I'm writing on a HP Mini 1000 running Heron only.

---

### Post by sgosnell on 2009-11-17
In gparted, just right-click on the partition, or select Partition from the menu, and select Format to...  You have to unmount the partition before you can do anything to it.

---

### Post by aspergerian on 2009-11-17
> **sgosnell said:**
> In gparted, just right-click on the partition, or select Partition from the menu, and select Format to...  You have to unmount the partition before you can do anything to it.

When I dare reinstall Vista or install w7 (so as to use my photoshop cs4) in what shall again be a dual boot computer (hopefully better arranged in hd), I'll remember this instruction.

---

