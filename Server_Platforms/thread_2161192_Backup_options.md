---
title: "Backup options"
date: 2013-07-09
forum: Server Platforms
---

### Post by samkarpluk on 2013-07-09
As rightly pointed out in another thread, after setting up a new server, I need to be thinking about a backup strategy.

I have set up a raid 5 array on 3 2TB drives and the OS on a 128GB SSD.

I have a Samba share on the array which houses all of the shared data that I want to back up. Currently there about 500 GB of data in the share.

I have a 1TB external usb drive (WD My Book), which I partitioned, set up with an ext4 filesystem, and mounted on / as /media/mybook. Last night I installed rsnapshot, and ran it against the Samba data I want backed up. It is currently running hourly snapshots to the mybook mount. I'll be unmounting this and taking it off site soon, so as to at least have an offsite copy of the data.

I'm looking for some suggestions in the following areas:

I need some options for backing up the system so I can get up and running quickly if, say, the main OS disk fails. Recommendations for this?

I have three internal hard-drives of various sizes (>500GB) kicking about. I'm thinking of buying a three disk usb enclosure and using these disks in a backup / offsite rotation scenario. I'm looking for some advice on how to accomplish this. For example, I could use rsnapshot and rotate which drive is currently active. Is that a good approach?

---

### Post by CharlesA on 2013-07-09
Clone the main OS drive with something like Clonezilla or you could just [use tar]("http://www.aboutdebian.com/tar-backup.htm"). I prefer the Clonezilla route myself.

As far as making a backup plan, I'm in a similar boat. I am upgrading the drives on my RAID array and plan on hooking up the old drives to my old server (Circa 2010ish) and using that as a extra backup set for my main server. it might not be idea as the drives are old, but it should help get me up and running in the event something terrible happens. :p

As far as backing up the main server goes, I do dailies via cp and rsync (which will probably be replaced with rsnapshot, if I get around to it..), monthlies are done the same with and I do two full backups monthly.

I use rsync for all backups - My plan for backing up to the old server is to use rsync over ssh.

Hope that helps.

---

### Post by samkarpluk on 2013-07-09
Thanks CharlesA.

I will check out clonezilla.

I may try one of these units to repurpose my spare hard-drives: [http://us.ncix.com/products/?sku=62116](http://us.ncix.com/products/?sku=62116)

---

### Post by CharlesA on 2013-07-09
> **samkarpluk said:**
> 
I'm may try one of these units to repurpose my spare hard-drives: [http://us.ncix.com/products/?sku=62116](http://us.ncix.com/products/?sku=62116)

I haven't used one of them myself, but I've heard those work very well.

---

