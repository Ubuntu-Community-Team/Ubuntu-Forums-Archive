---
title: "Gparted vs Acronis, how's this possible?"
date: 2008-11-13
forum: The Cafe
---

### Post by sicofante on 2008-11-13
Gparted took 2 hours to copy a freshly installed Ubuntu into another drive. I'm talking about 160 GB drives.

Acronis too 2 minutes to do the same task.

I can understand when there's a 10% difference, or even a 100% difference between two apps efficiency, but we're talking about bigger than 10000% differences here.

What's wrong with Gparted or what's the magic in Acronis?

---

### Post by Polygon on 2008-11-13
um, what do you mean?

gparted is a partioning program, and  acronis true image is "backup software for windows and linux...im confused on what your talking about.  are you talking about the ubuntu installer installing ubuntu? or...copying partitions?

---

### Post by mssever on 2008-11-13
> **sicofante said:**
> Gparted took 2 hours to copy a freshly installed Ubuntu into another drive. I'm talking about 160 GB drives.

Acronis too 2 minutes to do the same task.

I know nothing about Acronis, but obviously the two programs didn't actually do the same thing. I've never heard of a hard drive fast enough to copy 160 GB in 2 minutes. So clearly Acronis didn't copy the entire drive--at least, not at that time.

---

### Post by tom66 on 2008-11-13
Unless your drive can copy 1.33 GB/s, then...

---

### Post by daverich on 2008-11-13
> **tom66 said:**
> Unless your drive can copy 1.33 GB/s, then...

if the drive wasn't full, then it's quite feasable.

these programs don't record every single bit on the drive whether its used or not,- only the stuff that's needed.

Kind regards

Dave Rich

---

### Post by binbash on 2008-11-13
Dude they are different types of software.Gparted is a partiton manager other is backup software.And

---

### Post by Phreaker on 2008-11-13
Maybe the person is referring to Acronis Disk Director ?

---

### Post by Erunno on 2008-11-13
> **daverich said:**
> if the drive wasn't full, then it's quite feasable.

No, it's not. SATA 2 specifies a maximum transfer speed of 3 Gigabit/s (384 Megabyte/s), so it's totally impossible that a single drive can do this. You're confusing incremental backups with transfer speed.

EDIT:

Okey, reread what you wrote and I think I know what you are meaning. If gParted makes a block for block copy of the source hard drive then the time to copy will remain constant. If Acronis only copies the files regurarly than the time depends on the amount of files and how full the drive is. Is that what you mean?

---

### Post by daverich on 2008-11-13
> **Erunno said:**
> No, it's not. SATA 2 specifies a maximum transfer speed of 3 Gigabit/s (384 Megabyte/s), so it's totally impossible that a single drive can do this. You're confusing incremental backups with transfer speed.

EDIT:

Okey, reread what you wrote and I think I know what you are meaning. If gParted makes a block for block copy of the source hard drive then the time to copy will remain constant. If Acronis only copies the files regurarly than the time depends on the amount of files and how full the drive is. Is that what you mean?

yeah,- if theres 1gig of data on a 300gig drive, acronis only needs the 1 gig plus a bit of structure info to refresh the partition, whereas Gparted might need to recreate the whole 300gig.

Kind regards

Dave Rich

---

### Post by regomodo on 2008-11-13
#

---

### Post by Lem on 2008-11-13
If it's cloning you want, then clonezilla would have been the better free tool to use.

Very quick - I use it for mass cloning clients.

---

### Post by sicofante on 2008-11-13
> **Phreaker said:**
> Maybe the person is referring to Acronis Disk Director ?

> **Lem said:**
> If it's cloning you want, then clonezilla would have been the better free tool to use.

Very quick - I use it for mass cloning clients.
Sorry for the misunderstandings. The fact is that I've used both Acronis True Image's "Clone disk" utility and also Acronis Disk Director for resizing. The first compares very favorably to Clonezilla in speed terms, but what's really overwhelming is the little time it takes for the second to do something Gparted takes an eternity to do.

From a user's point of view, I couldn't care less what the software is doing while I'm watching. All I know is I get my disks copied or my partitions happily resized in less than 2 minutes with Acronis and more than two hours with Gparted or Clonezilla. (Yes, the disks are only partially filled.)

I can imagine Acronis is doing some clever choices about what space is full and what's empty. I just wonder why the FLOSS alternatives seem to be taking the brute force approach, making them look silly in comparison.

(BTW, Gparted was just unable to resize a boot NTFS partition. Acronis had no issues with it. That's what made me try Acronis again and then discover all this...)

---

### Post by Polygon on 2008-11-13
> **sicofante said:**
> 
(BTW, Gparted was just unable to resize a boot NTFS partition. Acronis had no issues with it. That's what made me try Acronis again and then discover all this...)

which is why i just resized my windows vista partition (also the boot partition) just 3 days ago with teh gparted that comes with intrepid. Im not sure how long it took, but it did. You have to repair the vista partiton with the vista installation cd cause it freaks out cause it cant find the partition after you resize  it, but after you repair it, its all good.

and also, just because SATA can acheve 3 gigs/second doesn't mean it can. there are other bottle necks, like the hard drive itself, the cpu, the motherboard...etc. no way it achieves that fast of transfer speed.

---

### Post by Mr_Or on 2008-11-13
Hello all!
I have Disk Director and it's pretty fast do it's work too ;)

from Acronis user guide:
Having copied a partition, you get the duplicate of all its data. Partition copy can be used: 
&#8226;  As a partition backup (or rather as a data backup) 
&#8226;  A system partition backup is advised if you want to upgrade the existing operating 
system 
&#8226;  **To quickly move all data from an old disk to a new disk **

---

### Post by billgoldberg on 2008-11-13
> **sicofante said:**
> Gparted took 2 hours to copy a freshly installed Ubuntu into another drive. I'm talking about 160 GB drives.

Acronis too 2 minutes to do the same task.

I can understand when there's a 10% difference, or even a 100% difference between two apps efficiency, but we're talking about bigger than 10000% differences here.

What's wrong with Gparted or what's the magic in Acronis?

Hard drives *(and most likely not even ssd drives)* aren't that fast, so what you are saying is impossible.

Edit: I might have misread that.

:p:p

---

