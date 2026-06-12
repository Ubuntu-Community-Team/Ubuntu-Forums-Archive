---
title: "Seeking RAID 5 opinions and guidance"
date: 2011-05-13
forum: Server Platforms
---

### Post by ThrillSeeker on 2011-05-13
Hello everyone,

Here is my brief hardware and software detail in my production environment :  AMD Phenom X4 3.4gHZ (Over clock to 4gHZ, 8G of Memory, 1TB 7200rpm Harddrive,  Running Ubuntu server 10.10

My web production environment were pieced together 3 weeks ago.  Here is my dilemma...started out with less that 40 users and now hitting 4,000 unique users per day.  Now I am thinking I need faster write to disk and backup of data so I am thinking about putting together a Raid5.  

I preparation for this.  I have bought a new motherboard, AMD Phenom X4 3.6, and 2 more 2TB 7200rpm (Currently, I have a 2TB 7200rpm not used much)

Been digging around this forum for posts with raid setup but still not sure how to seamlessly moving the some 10Gig of data from my current running prod environment once I have RAID5 installed on this new machine via the LIVE Ubuntu Server CD.

If you have any input or advice from your experience I would appreciated very much with a few brief sentences to guide me in the right direction.  Thanks.

(Never schooled in linux but have been playing around since the classic xbox modding days):KS

---

### Post by aphatak on 2011-05-13
I have been using Linux software RAID-5 for a couple of years now.  My server is configured with six 1TB disks, giving a usable capacity of 5TB.  This array runs in a dedicated box and mounted as an NFS volume by client computers in the network, and is backed up on another similar RAID-5 configuration, dedicated to backup.

Some of the lessons I learnt -
[LIST=1]
[*]Have at least one spare disk in your RAID set.  Now, that means you really can't have a three-disk RAID-5 setup, you need four disks.  Configure the fourth disk as a spare, so if one disk fails, the RAID software automatically starts using the spare drive and rebuilds the array without interrupting service.
[*]Never, never, *never ever* run your RAID box without a UPS.  I did, and paid for it:  when power failed, *two* disks got corrupted at the same time, and I spent a frantic day recovering the whole RAID array.
[*]Install your OS on a separate volume.  Linux doesn't need much space, so you can get away with a tiny little hard drive.  Then you spend the money you saved on getting a fast (like 10,000 RPM) drive (or a 15,000 RPM drive if you have a money-tree in your backyard).
[/LIST]
If this set-up belongs in a business, the option of growing feathers, turning chicken, and having the whole lot hosted, needs to be looked at as well.

I do not know how much difference a RAID-5 array will make to the speed; if the 8GB RAM in your set-up is not fully used up by your application, the OS will automatically use as much of the remaining RAM as it can as a cache anyway, so that would speed up the access, especially if you serve static pages.

---

### Post by ratcheer on 2011-05-13
My opinion is rarely valued around here, but after a 34 year IT career in database management, I strongly prefer RAID 1+0 (aka RAID 10). It gives high performance from the striping, then 100% redundancy from the mirroring. A properly configured system can continue uninterrupted after the failure of any drive. To recover after such a failure, the mirror only need be reestablished to the single replacement drive, not the entire stripe set.

The only real negative of RAID 1+0 is the expense, as 50% of total drive space goes to the mirroring.

You asked for my opinion and I gave it.

Tim

---

### Post by ThrillSeeker on 2011-05-13
Woow thank you for your fast reply gentlemen....looks like today is my lucky Friday 13th.  Lots of deep advices after having just skimmed through your post.  Still tied up with working remotely and will digest your advices in detail later.  

Thanks

---

