---
title: "Setting up RAID 1 array and clueless"
date: 2005-04-23
forum: Server Platforms
---

### Post by Tanizaki on 2005-04-23
I'm quite new to linux and Unbuntu and recycled an older box as a Samba server running 5.04. I would like to add two 250 GB drives in a RAID 1 array. Can I do this without wiping the current HDD, which will be the boot drive on the new system? I tried Googling and searching this forum for a how-to, but there was a lot of terminology I didn't know (LVM?), and as a novice, it's hard to know what's useful.

I'm quite clueless about this, but I imagine that software RAID would be ok. The box would be used to server audio and video files to me and my wife on our home network.

If anyone can point me to a good step-by-step tutorial, I would be very appreciative. I don't even know how I would set up the jumpers on the new HDDs. 

Please advise or I will have to go to Windows Server!

---

### Post by adeh on 2005-04-26
I have to admit, Windows server wins hands down in terms of setting up a RAID array. However, it is quite possible to do in Linux as well. It is really easy for a non-booting partition, and not so simple for a booting partition.

You can check this thread for some tutorials: [http://ubuntuforums.org/showthread.php?t=28177](http://ubuntuforums.org/showthread.php?t=28177)

I personally have done it many times with debian-testing (sarge) which is similar, but not exactly the same as Hoary, but should be close enough for the important points.

At the basic level, here are some tips:

1. HDD setup
Use 2 seperate  IDE or SATA channels, so each drive is a master on its own channel. This is really the only setup that makes sense for RAID, and it is also usually the factory default for the HDD jumpers.

2. RAID Levels
The most common and what you problably want is RAID1 which is basic mirroring. The drives are kept in sync, so if one dies the other still has all the data. reads are faster, but writes are slower.

3. LVM
LVM is Logical Volume Manager. It allows you to treat several partitions as one big disk, simplifying things if you have several disks. If you are only planning on having just 2 disks making 1 RAID partition, then it is not necessary.

4. tools
In Linux the RAID tool is called mdadm (Muilt-Disk Administrator), and each RAID array  is md0, md1...

The basic outline of what you would need to do is (for bootable raid):
1. get your system running on one disk (your orig)
2. plug in the second disk and create partitions to match the original disk
3. use mdadm to create some degraded arrays. basically, you create an md device with one good drive (the new one) and one "failed" drive (your orig)
4. copy the current drive to your new md device
5. boot into your new md device (this is where it gets a little tricky)
6. add your original disk into your raid array, and they re-sync themselves up.


piece of cake :)

good luck,
Adeh

---

### Post by tonym on 2005-04-26
There are good HOWTOs available.  Just Google for software raid howto and lvm howto.

---

### Post by steveM49 on 2005-04-26
I too am a n00b to servers and Linux as well as Ubuntu.  I took a simplified hardware approach and bought a motherboard that included SATA RAID. For a small amount of money (about $20) you could buy a PCI card that does similar work.

I got the system working on Sunday and before installing Warty, I followed the instructions for setting the RAID array to mirroring.  I then installed Warty (there were a couple of minutes of confusion while I sorted out whether the CDROM or the array was the start up disk.)  Everything seems fine now.

My next step will be to copy over the smb.conf files from the prior server, edit for the new one, and retire the old server.

So far the server / ubuntu / RAID1 experience has been a piece of cake.

---

### Post by s0c0 on 2005-05-01
I tried software raid 1 with 2 IDE drives on a Fedora Core 3 box last week.  The install went smooth, but when I took out the man drive the other disk would not take over!!!!

---

