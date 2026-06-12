---
title: "mac hard drive -- special requirements?"
date: 2011-12-12
forum: The Cafe
---

### Post by Docaltmed on 2011-12-12
I know this question is incredibly OT (not to mention incredibly stupid), but this forum is the only place where I trust I'll get a correct answer.

I've got to get an external HDD for an Apple laptop. I've never even seen one before, but I know that the Mac is pretty closed up, hardware-wise.

Can I just get a plain old USB external HDD, format it in FAT32, and call it a day? Or do I have to pay the Apple surcharge to get one that is specifically Mac-compatible?

---

### Post by RealityMaster on 2011-12-12
Get an enclosure and format away...although I wouldn't use fat32, but you certainly can.

---

### Post by Docaltmed on 2011-12-12
Really, it doesn't have to be FAT32? What formats can I use for a Mac external drive? I figured FAT32 would be my only choice, can I use NTFS? ext4?

---

### Post by RealityMaster on 2011-12-12
NTFS, hfs, or fat32.  NTFS would be what I would use, secure, journaled, and can be read almost anywhere.

[http://hints.macworld.com/article.php?story=20090913140023382](http://hints.macworld.com/article.php?story=20090913140023382)

If you want native NTFS check this out.

---

### Post by KiwiNZ on 2011-12-12
Are you using the HDD purely on your Mac? if so I would format in Mac OS extended Journaled , if you wish to use it on other devices I would format in Fat32

---

### Post by Docaltmed on 2011-12-13
It's going to be Mac-only, so I'll format it accordingly.

Thanks for your help, everyone. I knew I'd get sound advice here.

---

### Post by Lars Noodén on 2011-12-13
If it's not journaled then you can also read HFS+ in Ubuntu with the help of the packages hfsplus, hfsutils, and hfsprogs.

---

### Post by BrokenKingpin on 2011-12-15
> **KiwiNZ said:**
> Are you using the HDD purely on your Mac? if so I would format in Mac OS extended Journaled , if you wish to use it on other devices I would format in Fat32
++

FAT32 will work across Linux, Mac, and Windows.

---

### Post by N00b-un-2 on 2011-12-15
In my experience (as much as I hate to admit it) the best format for storage that is accessible between Linux, Windows, and OSX is NTFS.  There are FOSS drivers for NTFS on both OSX and Linux, and data reliability is good (I haven't had any issues with corruption).  NTFS also has the advantage of not being limited to file segments no greater than 4GB like fat32.  When FAT32 was developed they never thought that 4GB of data in one file would ever be a reality, however a DVD iso will take up just over 4GB of space, and something like an .mkv file ripped from a BlueRay can take up in excess of 20GB.
As a primary Linux user, I've tried using EXT3 as a format for shared data, but EXT3 support on Windows is glitchy at best using EXT2IFS or EXT2FSD and virtually impossible to get working on OSX (using FUSE modules which will often require manual mounting of EXT partitions manually).  Paragon does make drivers for NTFS and EXT3 on OSX but they are not FOSS applications and they are not cheap.  If you are primarily a Mac user, you may want to try HFS+ to store data to a shared drive, but in order to have read/write access to the drive outside of OSX you will need to disable journaling on the partition which drastically decreases data reliability.  There are FOSS drivers for HFS+ on Linux, and there are both FOSS and proprietary (which use a Java VM to browse) drivers (Also made by Paragon) for HFS+ on Windows but neither solution is truly transparent.

To reiterate, my recommendation is to use NTFS.  Its well supported and reliable on all platforms.  That is my opinion and should anyone disagree I'd welcome some input.

---

### Post by N00b-un-2 on 2011-12-15
Oh and one other thing!  I would recommend formatting the drive using GParted, not that formatting on Windows or OSX can't be accomplished.  Just keep in mind that Windows does goofy things with drives sometimes (creating hidden partitions and such).  On OSX, you can use Disk Utility to partition, but if you do and you plan on using the disk on any non Mac computer ever, I would strongly recommend that you make certain to format the partition table as MBR (OSX Disk Utility defaults to GUID, aka GPT which is not supported on all computers.  MBR on the other hand is)

---

### Post by sgaap on 2011-12-15
Tbh, i would stay away from ntfs, if you are using it primairily for osx i'd use HFS+ (non journalled if you want to be able to write to it in other operating systems)

I had several ntfs partitions on my linux/osx/windows workstation and its the only FS with which I had dataloss due to FS related corruption (on multiple systems even).

---

### Post by N00b-un-2 on 2011-12-15
> Tbh, i would stay away from ntfs, if you are using it primairily for osx i'd use HFS+ (non journalled if you want to be able to write to it in other operating systems)

Yes, but for the reasons I outlined in my first post HFS+ is not a good solution for cross compatibility.  I agree that the hierarchical file system is superior to NTFS, but in terms of compatibility it lags far behind.  The most stable and compatible platform of course would be FAT32 but as I mentioned, it suffers from a 4GB file size limit, making it all but unusable for things like data backups.  Also, when you get down to the minutia of how the file systems work, both HFS and FAT32 are TERRIBLY inefficient (depending on how the drive was formatted a 1kb file can physically take up the same amount of space as 512kb file on the drive)  NTFS isn't any better though.  EXT3 is by far the most efficient file system in my opinion, but it sorely lacks good support outside of linux (unless of course you want to pay money to support a data platform that is free and open source).

---

### Post by sgaap on 2011-12-15
> 
Yes, but for the reasons I outlined in my first post HFS+ is not a good solution for cross compatibility. 

My point was that its not worse then ntfs in that respect, hfs+ is even readable in windows 7 these days (altough win 7 has still very poor FS support).

---

### Post by N00b-un-2 on 2011-12-15
it's been a while since I booted into my Windows 7 partition, but I'm fairly certain it's incapable of detecting my HFS+ partition without installing third party software like MacDrive or Paragon HFS for Windows.  As far as data corruption goes, I'm sorry to hear that your NTFS partition failed.  However, that being said I've never experienced that issue.  But depending on what method I used to access HFS+ from Windows, I did experience some data corruption when writing.  Read Only mounting works well, but for my purposes it's virtually useless.

I have my computer partitioned like this:

/dev/sda1 Primary HFS+ -- has Mac OSX on it
/dev/sda2 Primary NTFS -- has Windows 7 on it
/dev/sda3 Extended
   /dev/sda4 Logical EXT4 -- has Ubuntu on it
   /dev/sda5 Logical SWAP   
   /dev/sda5 Logical NTFS -- data partition accessible by Win OSX & Ubuntu with common folders, ie; Documents, Music, Photos... symlinked or junctioned to it that way all my data is in the same place.

---

