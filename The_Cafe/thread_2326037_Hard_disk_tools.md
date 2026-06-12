---
title: "Hard disk tools"
date: 2016-05-27
forum: The Cafe
---

### Post by fund_raiser on 2016-05-27
Hello

I am looking for software for hard disks with good extensive manuals to learn from about disks. Software for repairing MBR, regenerating hard disks, restoring data etc. It could be several programs not just one that deliver good manuals. I know there are lots of software applications for hdd but most of them have very skimpy manuals (ex. *MBR work*, *MBR tool*). Could you suggest some software applications that would suit me? Or maybe I should use some book - and after reading I would expand my knowledge and be able to use HDD tools and also be knowledgeable about hard drive disks. 
I seldom know how to use options in such software applications :(

thx

---

### Post by TheFu on 2016-05-27
There are data forensics/recovery classes taught all over the world. Perhaps that is what you seek? Scott over at MyHardDriveDied is great at this.

MBR is dead. Need to learn about GPT.  Most of this stuff is covered nicely in the wikipedia articles.  Reading those would get you well beyond what 99% of all IT people know.

Some topics:
* GPT
* MBR
* Disk Sectors
* file systems - in general and learn about the specific ones you use (ext2/3/4, NTFS, xfat, fat32, zfs, btrfs, etc.... )
* logical volume managers
* and of course the manpages for each of the tools you use - gparted, parted, fdisk, dd, ddrescue, testdisk, photorec .... 

However, it is usually 10000x easier just to have good backups than to gain all this knowledge.  Backups can solve so many issues that data recovery cannot, unless you plan to make a living doing these things, if that is the case, get thee to a data forensics class.

Of course, since all of this software is F/LOSS, you should get the source code and look through it.  There's nothing like looking at the code to learn more about how this stuff works.

---

### Post by oldfred on 2016-05-28
The author of gdisk has a lot of info on his site.
See all the pages on his site:
       GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html)

Also TestDisk.
       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by mastablasta on 2016-05-28
for work with disks, the disks should often be unmounted. 

have a look at various rescue distributions such as Ultimateboot CD, Hyren's boot cd and more.

the aplicaitons are preety easy to use and often self explanatory. if not the menues and guidance is enough to use them.

---

### Post by yoshii on 2016-05-28
Personally i disagree that MBR is dead.  MBR-BIOS/Legacy Mode still exists in many modern-built computers and some distros such as Puppy Linux still rely upon it.  
And most flash drives are still formatted as MBR/FAT32 also.  

But of course I digress from the main topic.

---

