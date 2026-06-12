---
title: "Ntfs Ftw?"
date: 2007-08-04
forum: The Cafe
---

### Post by allwin on 2007-08-04
Now that there is full NTFS support, more or less, in UBUNTU...do you think it would be possible to create a version of the OS which runs on NTFS without using EXT2/3 at all?  I suppose the swap partition would still have to be "swap" type, but I just wonder if it's possible to create a bootable system where all else was NTFS.  It might perform better and would be handier for folks like me who operate Windows side by side.  I know you can install drivers in Windows to see EXTn partitions, but that's just a little funky.  If the whole shebang could be NTFS, that might be an interesting alternative way to set up a desktop system sharing with Windows.

Any tips on how to do so, experimentally?  Or what would be the roadblock?  Could it get rid of the automatic FSK with 30 mounts deal at boot?

---

### Post by Nekiruhs on 2007-08-04
... So let me get this straight. You _want_ to deal with a filesystem type that has horrible fragmentation, no permissions, less efficient (speed wise).  All while ditching our working system for it? I fail to see any benifits in using the inferior. On your logic, windows should use Ext3, because I can install something to write to it, why can't I install my OS on it?

---

### Post by reyfer on 2007-08-04
I may be wrong, but NTFS is and will always be proprietary. There is now some degree of support for writing to it in Linux (it has always been capable of reading), but the full specifications are owned by MS. Besides, as I understand it, ext3 has more advanced features than NTFS, so I don't see Linux going for NTFS. Please correct me if I'm wrong.

---

### Post by aidanr on 2007-08-04
I don't see the point tbh, maybe you should look at wubi, and you can disable the disk checking in /etc/fstab by changing the last digit to 0 (I don't really recommend this though)

---

### Post by VChief on 2007-08-04
I'm sure somebody will do it. A few distros did it for FAT. But, honestly, I see no good reson for it. Ext3 is much better than NTFS (not to mention Ext3 is open source, unlike NTFS).

---

### Post by allwin on 2007-08-04
> **leeward said:**
> I'm sure somebody will do it. A few distros did it for FAT. But, honestly, I see no good reson for it. Ext3 is much better than NTFS (not to mention Ext3 is open source, unlike NTFS).

My tongue is firmly in cheek here...but can anybody cite a reference which indicates EXT3 is more efficient than NTFS, etc.  EXT2/3 are pretty old, but NTFS is a little more modern, I get the impression.  Just wonder what an honest side by side comparison would produce on actual hardware, etc.

---

### Post by Nekiruhs on 2007-08-04
> **allwin said:**
> My tongue is firmly in cheek here...but can anybody cite a reference which indicates EXT3 is more efficient than NTFS, etc.  EXT2/3 are pretty old, but NTFS is a little more modern, I get the impression.  Just wonder what an honest side by side comparison would produce on actual hardware, etc.
[Ok, here]("http://linux.wordpress.com/2007/04/15/why-doesnt-linux-need-defragmenting/")

---

### Post by maniacmusician on 2007-08-04
> **allwin said:**
> My tongue is firmly in cheek here...but can anybody cite a reference which indicates EXT3 is more efficient than NTFS, etc.  EXT2/3 are pretty old, but NTFS is a little more modern, I get the impression.  Just wonder what an honest side by side comparison would produce on actual hardware, etc.
ext3 is not that old; and it's not like there's no work done on it between releases. There has been a lot of work done on ext3 over the years and there still is work being done on it. It's levelling off a bit now because of ext4, but that's a good thing.

---

### Post by starcraft.man on 2007-08-04
> **allwin said:**
> My tongue is firmly in cheek here...but can anybody cite a reference which indicates EXT3 is more efficient than NTFS, etc.  EXT2/3 are pretty old, but NTFS is a little more modern, I get the impression.  Just wonder what an honest side by side comparison would produce on actual hardware, etc.

[Reference]("http://en.wikipedia.org/wiki/Comparison_of_file_systems")

Just to be factually accurate, NTFS and EXT2 were released in the same year 1993. EXT3 was released in 1999. Ergo, EXT3 is the newer FS (granted EXT3 is heavily built on EXT2 right? So I dunno if it really counts as a release... debatable). You can also see a feature for feature comparison below (almost all FS are indexed there).

If there is any FS that would be wonderful to have with Linux, it would have to be ZFS (least from benchmarks I've seen). It seems to trump most, yet it isn't GPL and even if it were I feel no dire compulsion to have it. In addition, per my philosophic view of software I don't really want it unless it is GPLed... I have good alternatives that are free. I certainly though don't see any need to put Linux/Ubuntu on NTFS.

---

