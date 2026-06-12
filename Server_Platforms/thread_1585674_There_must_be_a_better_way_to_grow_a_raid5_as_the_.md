---
title: "There must be a better way to grow a raid5 as the disks get bigger"
date: 2010-09-30
forum: Server Platforms
---

### Post by bradtem on 2010-09-30
Many years ago I started a RAID 5, and over the years as I have purchased larger disks, I have replaced drives in the Raid 5.  Eventually I get to a point where all 3 disks are larger than they were when I last resized the RAID, and so one would like to expand the RAID.

The methods I have seen described on the web seem immensely time consuming and also risky, to do something that should take almost no time at all.   It is suggested you must delete each RAID component partition in turn (degrading the RAID), create a new larger partition and then add that into the RAID, which will cause a rebuild.  That rebuild will still be the same old size until you do the last disk, and in fact that rebuild will be the exact same bytes, except for the metadata about the sub-partition, and the location of the metadata, which I believe goes at the new end of the partition.

So that means hours of rebuilding -- and the risk that rebuilding entails if there is an undetected error on the other disks -- all to do nothing but update the metadata!   Note that in this case the partition is being grown in place, expanded to fill empty space that sits after it.

Finally, it is time to do the physical replacement of the last small drive with a new big one.  Again you would create a degraded RAID and rebuild onto the new big disk.  You might have to first do the repair before you do the mdadm --grow, I am not as sure if you can do all those at once.  I'm trying to recall if the grow --size=max will cause another rebuild of the RAID, more hours of slow system.

Now for the new larger drive, we do have to get the data from the old one to it, and a disable/add/rebuild is as fast a way to do that as any since we are limited by write to the new drive.  But it's a much riskier way that the way I would imagine, which would be to block copy the old small drive to the new big one with dd, though that requires downtime while you do it.

To get specific right now I have two 1TB drives and a 750, and I am swapping the 750 for a 2TB.   The drives are not fully RAID, because I also have an raid-1 root file system on two of them, as well as swap, and a raid-0 /tmp filesystem on all 3 of them etc.  For simplicity say there is 700GB of RAID-5 on each drive, with 250gb spare space on the two 1TB drives.

You may ask, why do the 1TB drives have shorter 700gb raid partitions and empty space after them?  Why didn't I build the RAID 5 into the full rest of the drive when I put those in, even if only 700GB would be used by the RAID?   That's because it will be some time before the next size-change, and it seems a shame to waste that spare space.  What I like to do with it is throw up temporary partitions for use as scratch.  In particular one good use is to have a partition there that can hold rsync mirrors of other machines which are updated regularly.   It is not a crisis if a drive failure loses the mirror so that's OK on only one drive.

Anyway is there any advice on a better way to do this?   I suppose I should do the larger drive replacement first, though I can't do the grow until all 3 partitions are larger.  I notice that parted refuses to grow raid partitions into extra empty space presumably because of that metadata issue.  

Would it work better if the metadata were at the front of the partitions?  Could I do it then?  What is the way to move it?

Finally, is there a way to do a fully safe drive replacement when a drive has not actually failed?  I have always found it odd and risky that we just tell the system to consider as dead a perfectly good drive.   If the system knew it was just replacing a good drive that is still online, it could in many cases just copy the blocks if they are unchanged, writing any new blocks to the new drive or both.   However, more to the point, if during the rebuild, it was found there was a read error on one of the other drives, there would be no need for immediate panic.  You could survive it, all the data would still be present.   Such rebuild errors are rare, but not a never thing, and doing 4 extra rebuilds just seems to ask for trouble.

---

### Post by arnavk007 on 2010-10-01
change the drive and reboot
as far as raid is concerned you should have used raid 0 coz raid 5 is very very time consuming maintaining it will kill you

---

### Post by bradtem on 2010-10-01
That's hardly useful advice.   Drive failure is too risky to do RAID 0.   Raid 5s are work but they could be a lot better.   Things like x-raid have worked on improving the ease of management of RAID.

---

### Post by SeijiSensei on 2010-10-01
I was pretty sure you could just add the new drive into the array using mdadm.  A quick Google search brought up this: [http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/)

---

### Post by bradtem on 2010-10-01
> **SeijiSensei said:**
> I was pretty sure you could just add the new drive into the array using mdadm.  A quick Google search brought up this: [http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/)

No, that's the procedure for adding a disk to an array, ie. changing it from being a 3 disk array to a 4 disk array.   

The procedure for replacing a disk (keeping it a 3 disk array) is normally advised as marking the disk to be removed as bad, and then adding in the new disk (or having already added it in as a hot spare is even better).  This causes the RAID to rebuild onto the new disk, which is fine, but the problem is that during this period you are running in the risky N-1 disk state and if you have an undetected read error on one of those disks you just trashed your RAID.

This is so against the RAID approach because you are actually putting yourself at more risk by having a RAID than in not having one.   A bad block on a regular drive is just a bad block, you just lose that file.

This procedure is different from the procedure to grow the size of the individual RAID components because they are now on bigger partitions than they were initially sized for.   That's what you get to do at the end once you have replaced all your disks.   I don't recall if that also does a rebuild, there is no reason it should do so, but I have heard reports of it.

The ideal situation, which I am wondering if anybody knows how to do, would be to grow the partitions into empty space, and tell the raid that you did that so it would move its metadata and accept the new partition.

In addition, what I would also hope you could do is replace a drive hot, so that while it is copying to the new drive, the old drive remains available to reconstruct data if any errors occur in building the new drive.

I have not found a way to do these things but they seem so obviously the right way to do it if you are trying to be fault tolerant.

---

### Post by arnavk007 on 2010-10-02
if you can afford then use raid 1
but i think using raid 3,5 gives you more data storage like raid 0 but you want to avoid data failure
but the problem is this you arent able to make head or tail of your raid setup

---

### Post by SeijiSensei on 2010-10-02
> **bradtem said:**
> No, that's the procedure for adding a disk to an array, ie. changing it from being a 3 disk array to a 4 disk array.   

This procedure is different from the procedure to grow the size of the individual RAID components because they are now on bigger partitions than they were initially sized for.   That's what you get to do at the end once you have replaced all your disks.   I don't recall if that also does a rebuild, there is no reason it should do so, but I have heard reports of it.

Sorry, I misread your original request.

Did you read the material at the [RAID wiki]("https://raid.wiki.kernel.org/index.php/Linux_Raid")?

If you can back up the array and rebuild it, one alternative you might consider is running [LVM]("http://tldp.org/HOWTO/LVM-HOWTO/intro.html") on top of the array.  LVM gives you the option to create and resize logical disk partitions as needed.

---

