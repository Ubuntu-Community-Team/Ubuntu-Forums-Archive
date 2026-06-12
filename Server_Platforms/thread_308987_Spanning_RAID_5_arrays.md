---
title: "Spanning RAID 5 arrays?"
date: 2006-11-29
forum: Server Platforms
---

### Post by rossw on 2006-11-29
I am currently running a Windows 2000 Server which holds roughly 250GB of data. Unfortunately that 250GB is comprised of six 18.2GB and an untold number of 9.1GB SCSI drives. The entire system is fast approaching 10 years old and I'm starting to worry about the reliability of the drives since they are currently all part of a single spanned partition. The software RAID 5 option of Ubuntu is what made me think that I should switch the server over to Linux. There's just one catch, I have a little more than 100GB of space on each of two different capacities of drives (9.1 and 18.2). Naturally these won't play nice when trying to make a RAID 5 array and I'll end up losing 9.1GB on each of the 18.2 drives. For the simplicity of those who use the server (currently primarily by FTP and a windows share) I want to keep the data in one large file tree in a single partition. This brings me to my question:

Is it possible to create two RAID 5 arrays (one with 18.2GB disks and one with 9.1GB disks) and then span a partition across them? I know I'd need a drive of each capacity for parity but it's still preferable to only half utilizing all 6 of the 18.2GB drives. Any thoughts?

-Ross Wendell

---

### Post by 3DLover on 2006-11-29
I have used odd-sized drives to make raid's several times.  I'll describe my most recent project:

I had two 100GB drives, two 200GB drives, and two 300GB drives.  Six drives in total.  Since 100GB is the lowest common denominator among these sizes, I made as many 100GB raid partitions on every drive as I could.  Thus the 100GB drives got one partition each, the 200GB got 2 each, and the 300GB drives got 3 partitions.  This gave me 12, 100 GB partitions.

Now, I could of made a raid-5 out of those 12 partitions, but if one of those 300GB drives failed, it would take out 3 of the 12 parts and the raid-5 would fail.  So, I had to construct several raid-5's making sure that I did not use the same physical drive more than once for each raid array.  Since the largest drive held 3 partitions, I knew that I had to make at least 3 raid-5's.

so, here's my layout:
hda - 300GB - contains: hda1 hda2 hda3
hdb - 300GB - contains: hdb1 hdb2 hdb3
hdc - 200GB - contains: hdc1 hdc2
hdd - 200GB - contains: hdd1 hdd2
hde - 100GB - contains: hde1
hdf - 100GB - contains: hdf1

raid-5 #1 contains: hda1 hdb1 hdc1 hdd1
raid-5 #2 contains: hda2 hdb2 hdc2 hde1
raid-5 #3 contains: hda3 hdb3 hdd2 hdf1

FYI: My putting each of the 100GB drives (e and f) on different arrays, I spread out the average access times, and spread out the chance of failure.  (the 100GB drives are the oldest and slowest)

Then I take those three raid-5's and I can combine with LVM.  I now have a 900GB LVM volume, that is protected with raid-5 parity, and it's make up of odd sized drives.  Toss an ext3 onto that LVM volume, and you're data is pretty darned safe.

I hope this helps.  BTW, I created the volume that I just described entirely within the partitioning tool during Ubuntu's installation routine.  You can do this easily enough with shell commands, or possibly with an kde/gnome GUI.

-Ray

---

### Post by rossw on 2006-11-30
Awesome, that's just what I was looking for.

-Ross

---

