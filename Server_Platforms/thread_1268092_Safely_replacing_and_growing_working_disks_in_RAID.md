---
title: "Safely replacing and growing working disks in RAID"
date: 2009-09-16
forum: Server Platforms
---

### Post by bradtem on 2009-09-16
I have working RAID-5s but from time to time I have found I want to replace a disk that is working just fine, sometimes to put in a bigger one, or because I am moving things around, or perhaps I suspect the drive is near end of life.

Reading around, what I seem to get is that the way to do this is to add the replacement drive as a hot spare, and then fail the drive to be removed, and the RAID will rebuild onto the new drive.    That works, but it seems a strange way to do things.   This means you temporarily degrade your otherwise perfectly good array, and if there is a real failure on the other drives during this period, you could lose data or quite probably your entire array.    Indeed, if there is something as simple as a random bit error on your drives as it rebuilds, data could be lost which is actually still present on the drive that you "failed" out.   In many cases you will be reading stripes from disks that have not been read for some time.

Unless I am mistaken, you find yourself in a situation where you are at greater risk due to RAID rather than less, which violates the purpose of it.

Is there a way to change disks that does not have this risk, which rebuilds the new disk but uses the old disk if there is an error from the others?   I presume one could go offline, and just bit copy the old paritition to a new partition, and come back online but of course that requires being offline for some time and would fail if there are local errors on 2 drives (unlikey but possible) where an online build would not.

Question 2:

As noted, sometimes I have replaced drives with bigger ones, as the sweet spot in drive size gets bigger and bigger.  I have reached a point on one RAID where all the drives are bigger, and I want to grow the RAID to the new "smallest size" which is now 750gb instead of 500gb.   On the 750gb drive, the 500gb partition is followed by empty space, and I would like to just expand that partition, then tell the RAID to grow with mdadm size=max, and then expand the lvm on the newly grown /dev/md1.

Yet in playing with the tools like gparted, it seems they will not grow the partition into the empty space above it.   Is there a way to do this, or are we again faced with the idea that I should fail the old partition, delete it and recreate it grown, and add it back, forcing a pointless rebuild?   Or can I possibly grow the partition with some other tool while offline, ie. from a rescue disk or in single user mode?

---

