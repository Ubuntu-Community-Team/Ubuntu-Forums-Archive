---
title: "Need Advice on a New Server Build &amp; RAID"
date: 2012-05-14
forum: Server Platforms
---

### Post by kentish on 2012-05-14
Hi 

Over the weekend one of my existing HDD developed a fault which broke the LVM in my server and resulted in a very large data loss - 3.5 TB for TV Shows and Films that I'd ripped. I had back ups of my music , documents and photos.

I now have to rebuild and will be buying a few new drives. I'd like peoples opinion of soft RAID versus cheap hardware raid.  

Presently I have 2 x 1tb drives and one 2TB with a bad sector.  Should I still use the 2 TB drive with a new 2TB along side it? 

Obviously I want as much storage as possible so was looking at ...

OS Drive 
array 1 - 2 x 1tb 
array 2 - 2 x 2tb 
array 3 - 2 x 2TB ( June pay day)

Interested hear your thoughts before I spend any money.

---

### Post by Jonathan L on 2012-05-14
Hi Kentish

> I'd like peoples opinion of soft RAID versus cheap hardware raid.Software RAID works perfectly well at this scale of performance.  I wouldn't recommend cheap hardware RAID at all: it isn't the functioning during normal circumstances you worry about, it's the performance and functioning during the abnormal you care about, and that's what's the least well tested in cheap hardware and firmware.  (Of course expensive hardware RAID works really well.)

I'd recommend making your RAID sets larger, ie, use RAID 5 not 1, so you get more efficient use of your storage.

> one 2TB with a bad sector.  Should I still use itI wouldn't.

You might care to read

[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

Hope that's helpful.

Kind regards,
Jonathan.

---

### Post by kentish on 2012-05-14
Thanks Jonathan, 

I will certainly have a read...

> **Jonathan L said:**
> 
[https://raid.wiki.kernel.org/index.php/Linux_Raid](https://raid.wiki.kernel.org/index.php/Linux_Raid)

Hope that's helpful.




I don't want to be in the same position again in the future so looks like I am dumping the 2 TB Drive then which is a shame. I start looking around for reasonable priced 2 TB drives.

Thought that I didn't care about the TV and Films but trying to find something on sky to watch over the weekend showed me how much I do:lolflag:

Cheers 

Mark

---

### Post by rubylaser on 2012-05-14
Have you looked to see if your drive is under warranty and to see if you can RMA it to the manufacturer?  I've done that with a number of disks over time.  With most hard drive manufacturers, you'd get at least a 3 year warranty for an internal hard drive.

---

### Post by kentish on 2012-05-14
Hi Rubylaser

> **rubylaser said:**
> Have you looked to see if your drive is under warranty and to see if you can RMA it to the manufacturer?  I've done that with a number of disks over time.  With most hard drive manufacturers, you'd get at least a 3 year warranty for an internal hard drive.

Oh, that's a good idea :cool:. I think I still have the original receipt so could work out how old the drive is. It was the first time I'd used a Samsung and most probably the last. Stick to Western Digital and Maxtor.

Mark

---

### Post by rubylaser on 2012-05-14
Since Seagate now owns Samsung, you should be able to use their RMA process [here]("http://www.seagate.com/about/contact-us/technical-support/") under the Warranty Assistance button.  You'll want to download the Seatools DOS image and run it.

If the drive passes the Seatools, don't RMA it, because they won't take it back without charging you.  If it does pass, I'd fill the disk with zeroes, so it can remap that bad sector, and you should be okay.  If it gives you an error code, then send that thing back.  Good luck :)

---

### Post by kentish on 2012-05-14
> **rubylaser said:**
> Since Seagate now owns Samsung, you should be able to use their RMA process [here]("http://www.seagate.com/about/contact-us/technical-support/") under the Warranty Assistance button.  You'll want to download the Seatools DOS image and run it.


Thanks for that, at work at the moment but will try that tonight. 

As the drive is currently part of a LVM I will have to removed and hope that I can still access the data on two devices. I really should created the LVM on top of the array and then I wouldn't be looking at 3.5TB of data loss :cry::cry::cry:

---

### Post by rubylaser on 2012-05-14
> **kentish said:**
> Thanks for that, at work at the moment but will try that tonight. 

As the drive is currently part of a LVM I will have to removed and hope that I can still access the data on two devices. I really should created the LVM on top of the array and then I wouldn't be looking at 3.5TB of data loss :cry::cry::cry:

You don't want to do that.  That will break your Logical Volume and would likely lead to data loss.

---

### Post by kentish on 2012-05-14
> **rubylaser said:**
> You don't want to do that.  That will break your Logical Volume and would likely lead to data loss.

I understand but that the drive with the bad sector and I can't access the data anyhow. I have tried repairing the LVM with xfs_check and xfs_repair but both fail with Fatal Error - Input / Output error.

I guess that I could try the seagate tool and then boot into a live ubuntu session and see what happens - fingers crossed eh?

---

### Post by darkod on 2012-05-14
Back to your original questions, I am no raid expert but I am reading about it a lot preparing for my home server.

One thing I like about software raid is that you can literary move the disks to another machine, and it should still work. For example, your board dies. You move the disks to another machine with linux, they should be working just fine. For accessing the data.

It doesn't even need to have linux, you can boot from the live cd, activate the arrays, and read the data.

With the cheap hardware raids (or fakeraids), you don't get any significant advantages and if something like teh board goes, I am not sure how easy it is to recover your data because it might be looking for the same controller to get the arrays going.

As for the disk with bad sectors, I wouldn't use it in any new array, it's pointless since you know it has bad sectors. If you can't buy enough new disks right now, it's better to create one of the arrays as raid1 with a single disk, like degraded, and add the other disk when you buy it. Of course, during this time you have no redundancy on this array. But that would be the same if using the bad disk, you can't seriously count on it.

---

### Post by kentish on 2012-05-14
Cheers Darko I think you've provided the solution I was looking for. I didn't know that you could create a single disk array and then change it later. That'll really help spread the cost over a couple of months (hopefully HDD prices will continue to drop!)

I won't use the 2TB but look at replacing it.

Thanks again.

---

### Post by darkod on 2012-05-14
rubylaser is the expert on raid and he can provide more exact commands how to create raid1 array when you have only one disk currently and simply add the second later. Google-ing this subject might also help.

Note that you are not creating the array again later, that would destroy the data. :) You only create it first time.

---

### Post by kentish on 2012-05-14
> **darkod said:**
>  Note that you are not creating the array again later, that would destroy the data. :) You only create it first time.

Ah that's good to know, I think that I might set up a virtual box and have a 'play' in a safe environment. At least if I break it I won't lose anything :-P

Mark

---

### Post by darkod on 2012-05-14
Most tutorials on google talk about creating the array with both partitions (disks) present. But it seems to create it with single partition it would be something like:

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 missing

Of course, instead of /dev/md0 and /dev/sda1 you will use the raid device and partition that you plan to use in your setup.

You can test that.

---

### Post by kentish on 2012-05-14
Ok, I think I have quite a bit of testing to do so I've downloaded virtual box and the latest ubuntu distro. This will give me an environment to play with before the new HDD's arrive later this week. 

I appreciate everyone taking the time to respond. Hopefully I can avoid my initial mistake by not backing up and not using a RAID array.

Thanks all ;)

---

### Post by rubylaser on 2012-05-14
> **darkod said:**
> Most tutorials on google talk about creating the array with both partitions (disks) present. But it seems to create it with single partition it would be something like:

sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sda1 missing

Of course, instead of /dev/md0 and /dev/sda1 you will use the raid device and partition that you plan to use in your setup.

You can test that.

This is exactly how you would want to do it :)

---

