---
title: "Damaged Windows partition and Wiped Storage partition with TestDisk"
date: 2016-03-06
forum: Windows
---

### Post by RocketPenguin on 2016-03-06
I think I royally up this time.

So here is the story:
Friend asks me to try and recover a RAW partition on HDD B. I try to recover it via TestDisk on HDD A, which is running windows 7. HDD A has two partitions, the windows C partition, and a D storage partition.

In testdisk, two weird partitions show up, one of which is the RAW partition, and the other one is a Windows partition, for something like swap space or something, no idea. The RAW partition is some random size, like 11250gb. This is an old IDE HDD, so obviously false. the other one is 400gb. According to the disk manager in windows, that other windows partition is like 332gb, so I assume it is probably that.

Here comes the fun part.

After scanning one of these unknown partitions (PhysicalDisk0, PhysicalDisk1 if i remember correctly) and allow it to"write" the partition, i get blue screen of death, followed by windows no longer existing.

So i boot up ye old ubuntu, and fire up Gparted.

Windows partition is in an NTFS partition system, D partition is gone, and HDD B partition is nowhere in sight.

So, long story short, in efforts to recover one partition,
I killed three.

So the question is, 
How do I recover partition D on HDD A
How do I recover Windows partition, and make it bootable
And, how do I recover HDD B's partition?

Oh, and on a side note, i vow never to try and recover data again. After i get this fixed, of course.

---

### Post by Bucky Ball on 2016-03-06
*Thread moved to **Windows**.*

This appears to have nothing to do with Ubuntu technical support. Sorry to hear your plight. My only suggestion is Testdisk, but that got you into this. :|

---

### Post by RocketPenguin on 2016-03-06
Any recommended forums to ask this on then?

I was hoping i could get around making another account someplace unfamiliar... ](*,)

---

### Post by Bucky Ball on 2016-03-06
If this hasn't had any attention in 12 or so hours, simply post bump to get it to the top of the list again. You never know.

What were you running testdisk from in the first place? Live media?

---

### Post by goofprog on 2016-03-06
Try undelete tools.  To make windows bootable it was **chkdsk <drive> /mbr**
I personally hate recovering other people's computer data.  I loathe it so much.

---

### Post by RocketPenguin on 2016-03-06
> **Bucky Ball said:**
> If this hasn't had any attention in 12 or so hours, simply post bump to get it to the top of the list again. You never know.

What were you running testdisk from in the first place? Live media?

Was running it on Windows (Was debating on running in livecd Ubuntu, but since tutorial i was following used windows, i didn't want to over complicate it)
What I was trying to recover is on an entirely different physical HDD.


> **goofprog said:**
> Try undelete tools. To make windows bootable it was **chkdsk <drive> /mbr**
I personally hate recovering other people's computer data. I loathe it so much.


For which drive? [http://imgur.com/7LldEka](http://imgur.com/7LldEka)

And me too. Never doing it again.

---

### Post by goofprog on 2016-03-06
Try sda5 but in Windows it is not sda5.  It would have an assigned drive letter.  Maybe boot to a Windows rescue disk first and see if that recovers the drive.

---

### Post by RocketPenguin on 2016-03-07
> **goofprog said:**
> Maybe boot to a Windows rescue disk first and see if that recovers the drive.


I tried that, with a windows 7 universal disk.
After about 3 hours of it "Attempting Repairs", i gave up and shut the machine down

---

### Post by RocketPenguin on 2016-03-07
> **goofprog said:**
> Maybe boot to a Windows rescue disk first and see if that recovers the drive.

Tried running CHKDSK on a windows repair disk, gave me this error: [http://imgur.com/Vc3g3qD](http://imgur.com/Vc3g3qD)

---

### Post by RocketPenguin on 2016-03-07
UPDATE:

I fixed it!!

Basically, patience. I had to wait for TestDisk to scan the HDD... Then deep scan it... then I set the windows partition to (P)rimary, as well as the storage partition, rebooted, and it worked!

Moral of story: Data recovery tools are black magic.

Should probably still run CHKDSK though, right?

---

### Post by Bucky Ball on 2016-03-07
> **RocketPenguin said:**
> Moral of story: Data recovery tools are black magic.

Should probably still run CHKDSK though, right?

Yes and yes.

Well done. Please see first link in my signature and good luck. (I personally don't do anything with Windows anymore for others. I used to be the first one people would harass when something went wrong, but haven't touched it on a 'repair man' basis in years. Except on my own machines. :|)

---

