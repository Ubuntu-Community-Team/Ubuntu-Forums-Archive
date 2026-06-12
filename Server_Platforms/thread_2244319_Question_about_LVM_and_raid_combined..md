---
title: "Question about LVM and raid combined."
date: 2014-09-15
forum: Server Platforms
---

### Post by PlugInPrius on 2014-09-15
I know what LVM is and have been using raid 1 and 5 for years but what I cannot find is why should I use LVM and raid?

I want to learn something new and from what I have found LVM and raid can work together but what I cant find is what is the real benefit of using the two together and how to properly implement it.

The first thing I would like to know is should you start with LVM and put raid 1,5,6 on top or should you start with a raid 1,5,6 and put LVM on top?

The next question is what is the benefit of having the two combined? Can I take my eight 2TB drives in LVM raid 5 and replace one drive with a new 4TB drive and use the extra space in the safety of a raid or can all drives be upgraded one by one and the end result would be more space? Basically is it possible to upgrade the drives to gain more space over time?

Usually I can find what I'm looking for but once again I cannot find a site that explains the two together. Mostly what I find is how to articles that just tell you how to do it and not why its done the way it is and the features of the two combined. Most of the time I just dont know the right terms to search for.

Any help would be greatly appreciated even if its a link to a site that explains it all.

---

### Post by oldfred on 2014-09-15
Moving your thread to the server sub forum where those who know RAID may be able to help.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

 [URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup
[/URL] Sysadmins: Everything they told you about backup WAS A LIE
[URL="http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/"]http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/


[/URL]

[URL="http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup"]
[/URL]

---

### Post by SeijiSensei on 2014-09-15
LVM gives you the ability to create virtual partitions on top of the RAID device.  I've taken one of two routes in the past:

1) Partition the drives initially into the sizes I want, then use mdadm to create multiple RAID devices by combining the matching partitions.

2) Use mdadm to create a single RAID device that runs the full extent of the physical device.  Then install LVM on top of the RAID device to divide up the space and assign it to mount points.

These days I'm more likely to create a separate RAID device and mount it as /home or under /media.  I don't bother with RAID on the OS partitions any more.  It's not much work to reinstall a distribution and copy over the backup.

---

### Post by nerdtron on 2014-09-15
My opinion:

Why use LVM on top of RAID? You know you can "dynamically increase/decrease logical disks using LVM but if you already setup up RAID, and then your storage is maxed out, LVM can't help you since you can no longer add physical disks without rebuilding the raid array. Why use LVM in the first place if you are locked down and can't add any more hard drives.

Point taken. It is still possible to add more physical drives, if your server can accommodate additional drives and then setup another raid array and add those drives to the LVM. Although this is certainly possible, but you don't see yourself doing this in the near future then I think you don't need LVM. It just adds overhead on your hard drive read/write.

Then again, LVM is still useful in some cases. Like for managing virtual machines, since you don't use RAID on them. You can make your virtual machines use LVM so that you can expand their drives/partitions on the fly. Another use is if you are serving a file server on which you assign logical partitions to users. You can expand/shrink the partitions base on user needs. Just like number 2 on what Seiji Sensei said, although the max limit of your total storage is still the limit of the RAID.

Back to your question:
> The next question is what is the benefit of having the two combined? Can  I take my eight 2TB drives in LVM raid 5 and replace one drive with a  new 4TB drive and use the extra space in the safety of a raid or can all  drives be upgraded one by one and the end result would be more space?  Basically is it possible to upgrade the drives to gain more space over  time?

**Setup LVM and then partition them, then setup RAID?** Nope. When you setup LVM, it is like have a single hard drive (even if you use multiple volume groups or physical groups), so if you pull out a drive on you 8x2TB LVM configuration, the whole LVM you'll lose data. You won't benefit on raid at all since the LVM is broken.

**Setup RAID and the partitions, then setup LVM?** Yes, correct way. Then again, your max storage is the capacity RAID array. You can't just swap drives and then magically increased the storage on a RAID array.

---

### Post by PlugInPrius on 2014-09-16
OK this is some info I was looking for.

I would like to play around with LVM just to learn more about it.

What interests me is the snapshot option of LVM. I've been using two drives in a raid 1 for years just as a poor mans backup for every computer I build. Mostly just to keep the computer up and running while I get a replacement drive if one happened to fail. As cheap as drives are I just do this for every computer. What I'm currently doing without the UEFI bios crap is have first partition on each drive as 1GB /boot raid 1, second partition as 8GB swap raid 1, and the rest of the drive as raid 1 for /. I do a similar thing to my 8 drive media server except the last partition is raid 5 or 6. Kind of a waste of space for all raid 1 boot and swap but it works.

If I was wanting to do this same setup but with LVM would I just make both drives a whole raid 1 partition and then let LVM do the /boot /swap and / ?

Since grub does not like raid 5/6 do I still need to make /boot raid 1 and then let LVM do the rest on top of a raid 1/5/6 or will grub work with say an 8 drive raid 6 with LVM on top for /boot /swap and / ? I hope thats not confusing.

Would this change a little with UEFI bios?

---

### Post by nerdtron on 2014-09-16
> If I was wanting to do this same setup but with LVM would I just make  both drives a whole raid 1 partition and then let LVM do the /boot /swap  and / ?

You can't do LVM on /boot either.

So you want a config that work on 8x2TB drives, with RAID 6 so that you won't have to worry about failing drives right?
One solution: get a dedicated RAID card that supports 8 drives. This way, the RAID card will do the work for you so you don't have to worry configuring the raid on the OS.

Another solution: 
Get 2 smaller drives, say 500 GB, setup in RAID1 and here lies the OS, swap and boot.
Then all remaining drives, configure them on RAID6 and make one big mount point for your data in this. You can also setup LVM on this drive if you like.

I'm thinking of another drive layout, but I think it can be a little complicated and not quite sure if it will work.

---

### Post by PlugInPrius on 2014-09-16
So I could just do a raid 1 across the 8 drives for /boot and then the rest of the drive as raid 6 then LVM on top of the raid 6?

---

### Post by nerdtron on 2014-09-16
> **PlugInPrius said:**
> So I could just do a raid 1 across the 8 drives for /boot and then the rest of the drive as raid 6 then LVM on top of the raid 6?

I think you are familiar enough on RAID to suggest this, which is also what I would suggest next. A bit difficult on replacing drives though since you deal with 2 different raid arrays. But this setup should work.
If you have the machine you can set it up like this and then remove a drive and see what happens on the array. Better test the raid first before dumping all your data in there.

---

### Post by PlugInPrius on 2014-09-16
Yes I will be testing it first. The whole point is to see how LVM works and how I could use it. Its kind of hard to learn something new with Linux when everything just works after a first config and you dont have to fool with it every day like you do with microsoft OS's. 

I know having the 8 boot partitions in the raid 1 is kind of a waste but If I fill up my motherboard with 8 drives of the same size then I think that would be my only option as far as keeping the system up. I know that setup works well as I'm currently using it on my media server. I've failed drives individually and the system still booted from every drive.

So if the proper way is to have a boot partition in raid 1 then the second partitions as raid 6, then let LVM do the /swap and / I should be OK.?

Why would this a bit more difficult on replacing drives? When I replaced a drive it automatically rebuilt everything the drive needed. Or does LVM cause the difficulty?

---

### Post by nerdtron on 2014-09-16
> So if the proper way is to have a boot partition in raid 1 then the  second partitions as raid 6, then let LVM do the /swap and / I should be  OK.?
Yep!

> Why would this a bit more difficult on replacing drives? When I replaced  a drive it automatically rebuilt everything the drive needed. Or does  LVM cause the difficulty?
Really? They just rebuild automatically and you don't have to issue any mdadm --assemble or any mdadm commands? I believe you still have to instruct raid to drop the failed drive, insert a new drive, then instruct to rebuild again.

---

### Post by PlugInPrius on 2014-09-16
Well I did not mean "automatically". I actually used a disk manager. I think its palimpsest. It said the raid was degraded and I clicked repair and it took care of the rest. This was all after I took out the old one and put in the new one. I powered down the server to do it as I needed to swap out other stuff at the time. 

Thanks for everyone's help. I think I can figure out the rest by playing around.

---

