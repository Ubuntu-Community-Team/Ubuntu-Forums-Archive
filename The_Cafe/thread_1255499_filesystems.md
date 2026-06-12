---
title: "filesystems?"
date: 2009-09-01
forum: The Cafe
---

### Post by chris200x9 on 2009-09-01
I am wondering, was ntfs that revolutionary? I mean it showed up in xp and it's still in windows 7 while everyone is getting in on the zfs btrfs bandwagon, is microsoft going to be utterly murdered in terms of high performance file systems or is ntfs still a viable competitor?

---

### Post by SunnyRabbiera on 2009-09-01
Well NTFS is a mixed blessing, I mean yes in many respects its better then FAT the old windows filesystem.
But NTFS has a lot of weaknesses, its very easy to fragment and if your computer has a power outage there goes the neighborhood.
I do think its time MS got a new FS indeed, both Linux and OSX are putting them to shame.
By the way NTFS has been around since 1993.

---

### Post by &#32 Greg on 2009-09-01
WinFS was supposed to be released with, then shortly after Windows Longhorn (now Vista), but that never panned out :\

---

### Post by blur xc on 2009-09-01
> **SunnyRabbiera said:**
> Well NTFS is a mixed blessing, I mean yes in many respects its better then FAT the old windows filesystem.
But NTFS has a lot of weaknesses, its very easy to fragment and if your computer has a power outage there goes the neighborhood.
I do think its time MS got a new FS indeed, both Linux and OSX are putting them to shame.
By the way NTFS has been around since 1993.

My old windows computer has gone through dozens of power outages and "unclean" shut downs w/o ever giving me a single problem.  Most times, it didn't even to a disk check on the next boot up...  

I've read a few explanations of why ext3 is better and doesn't fragment, and there are always Windows zealots that claim ntfs is superior and doesn't fragment either.  My experience greatly testifies to the contrary.  My work (ntfs) HD is like 10% full, and was horribly fragmented.  After doing a defrag my CAD programs run substantially faster...

BM

---

### Post by Namtabmai on 2009-09-01
> **blur xc said:**
> My experience greatly testifies to the contrary.  My work (ntfs) HD is like 10% full, and was horribly fragmented.  After doing a defrag my CAD programs run substantially faster...

I think that's kind of the point the previous poster was trying to make.
You shouldn't have to defrag a filesystem. The point being filesystems such as ext3 etc don't fragment, or more correctly fragmentation isn't an issue with them and shouldn't effect the loading of applications let alone how fast the applications run once opened.

---

### Post by SunnyRabbiera on 2009-09-01
> **blur xc said:**
> My old windows computer has gone through dozens of power outages and "unclean" shut downs w/o ever giving me a single problem.  Most times, it didn't even to a disk check on the next boot up...  

I've read a few explanations of why ext3 is better and doesn't fragment, and there are always Windows zealots that claim ntfs is superior and doesn't fragment either.  My experience greatly testifies to the contrary.  My work (ntfs) HD is like 10% full, and was horribly fragmented.  After doing a defrag my CAD programs run substantially faster...

BM

for some though power outage + NTFS = doom

---

### Post by sydbat on 2009-09-01
> **Namtabmai said:**
> I think that's kind of the point the previous poster was trying to make.
You shouldn't have to defrag a filesystem. The point being filesystems such as ext3 etc don't fragment, or more correctly fragmentation isn't an issue with them and shouldn't effect the loading of applications let alone how fast the applications run once opened.^^This^^

+1

---

### Post by Namtabmai on 2009-09-01
> **SunnyRabbiera said:**
> for some though power outage + NTFS = doom

Totally, we use NTFS on systems at work that for various reasons don't have a software shutdown button, which means the machines ALWAYS get shutdown at the power switch.

It got so bad my boss asked me to modify a Linux cd to automatically fix one of the common problems that this causes.

---

### Post by blur xc on 2009-09-01
> **Namtabmai said:**
> I think that's kind of the point the previous poster was trying to make.
You shouldn't have to defrag a filesystem. The point being filesystems such as ext3 etc don't fragment, or more correctly fragmentation isn't an issue with them and shouldn't effect the loading of applications let alone how fast the applications run once opened.

It must be a cad thing.  Solidworks, for example, tosses files back and forth on the drive like crazy.  Once everything is open, it does run ok.  When you first open an assembly, it copies all the files from wherever to your local settings\tempsw folder.  This could be a hundred or more files.  It does automatic saves to these files, in case of a crash (which happens a lot) so it can attempt to recover your data (wich hardly works).  This folder fills up over time, and for some reason no one has explained to me, makes sw bog down if it gets too big.  So, every so often you have to empty it out.  And the process starts over again.  After a few weeks, SW takes a VERY long time to start up.  On a good day, with cleaned out folders and a freshly defragged drive, SW can take minutes to load up.  It only gets slower with time. 

I don't know how Pro E manages files, but it also takes several minutes to open.  It's quite annoying.

BM

---

