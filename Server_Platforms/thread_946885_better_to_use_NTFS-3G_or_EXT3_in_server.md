---
title: "better to use NTFS-3G or EXT3 in server"
date: 2008-10-13
forum: Server Platforms
---

### Post by 4heid on 2008-10-13
I am going to make a home server that needs to be accessible from Windows Vista and Mac OSX on an ubuntu machine.
The data drive will be a slave.
Which format is better to use for this?

---

### Post by Sam on 2008-10-13
ext3 without hesitation...

---

### Post by 4heid on 2008-10-13
i have a WD Mybook drive that was used previously as the mirror for my old server.
Whats the best way to use that with the new system I am making to use as a backup?
It was Raid1 before using software.

How can I do this with Ubuntu and is their any other linux software that will do the same backup style?

---

### Post by lykwydchykyn on 2008-10-13
You can do a software RAID, but personally I don't think RAID is the best choice for a backup strategy.  I personally think it's better to do a periodic copy to your backup media.  This way, you're not only covered if the drive fails, you're covered if you accidentally delete or overwrite a file, screw up an install, etc.

Granted, there are limitations to doing this -- you can't backup the complete system or live databases, just static data files and configurations.  

Check out Bacula, rdiff, or the rsync command if your needs are simple.

---

