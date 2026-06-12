---
title: "Suggest which file system to use"
date: 2011-08-02
forum: Server Platforms
---

### Post by TheR on 2011-08-02
I am upgrading my (as I call it) archive server. It is server used for archiving anything from user files, to images, backup data etc... lots of files of different sizes.

It has 8 WD320RE disks in RAID5 for total little above 2T space. Disks were working perfectly good for 4 years. I will be replacing them with 8 WD2000RE disks in RAID-5, somewhere around 12T of usable space.

I am currently using RaiserFS as file system, because it was hip at the time and as turned out once, when I had to copy data to other disk, is about 20% more efficient than ext3. I can save about 20% more data on Raiser.

My question is. What file system do you suggest for using with new configuration considering that space is more valuable than speed.

Thanks
TheR

---

### Post by Lars Noodén on 2011-08-02
Here is one [study on the overhead required by file system metadata](http://rwmj.wordpress.com/2009/11/08/filesystem-metadata-overhead/). Ext3, Ext4, and Reiser all look comparable there.  JFS and Btrfs use much less overhead.  I'd look at btrfs first.

---

