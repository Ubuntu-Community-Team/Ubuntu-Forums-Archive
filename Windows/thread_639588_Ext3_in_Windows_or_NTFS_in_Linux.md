---
title: "Ext3 in Windows or NTFS in Linux?"
date: 2007-12-13
forum: Windows
---

### Post by Curtisc on 2007-12-13
Right now, I'm using FAT32 to share data between Windows and Linux.  However, I'd like to get away from FAT32.  I've been able to read and write ntfs from Linux as well as ext3 from Windows.  At this point it seems like an arbitrary decision, so I thought I'd ask the community - which do you feel is more stable and a better option for cross-platform data sharing, ntfs or ext3?

---

### Post by actam on 2007-12-13
there is a driver for windows that make it capable to read ext3
(named for ext2 but ext3 too)
[http://www.fs-driver.org/](http://www.fs-driver.org/)

Edit: I prefer ext3...

---

### Post by Curtisc on 2007-12-13
Thanks for the reply.  I'm leaning towards ext3 too right now since I use Linux more often than Windows, but I'd be concerned about Windows being more likely to screw up than Linux.  Do you have any experience with either filesystems getting corrupted because the other OS messed with it?

---

### Post by rsambuca on 2007-12-13
Both work decently, although access times is definitely a little slower than the native filesystem.  Therefore, use which the filesystem for whichever OS you use the most.

---

### Post by coffeecat on 2007-12-13
The fs-driver only supports the ext2 part of the ext2/3 filesystem which means that it doesn't support the journalling function. How much this matters, I'm not sure, but I have seen reports of problems/bugs with it. This may or may not be true - you can't believe everything you read on forums after all. :wink:

There is, however, one situation where I find the Linux/Unix system of permissions in ext3 to be a nuisance. If I format an external USB drive as ext3, it's always automounted with root privileges only as the default, and I've never worked out how to change the hal/dbus configuration to get it to be mounted for my user account. Since I'm the only one using my machines, this would be perfectly OK. This is where FAT32 and NTFS are more convenient - though I hate to say it. I don't have to chown things, or do anything else, as root.

I know the OP didn't stipulate whether he was thinking of external drives or a shared internal partition, but I'd like to add to the original question since I'm posting from my Mac Mini. What fs (other than FAT32) would others choose for external drives to be used with Linux, Windows **and** Mac OS?

---

### Post by Curtisc on 2007-12-13
> **rsambuca said:**
> Both work decently, although access times is definitely a little slower than the native filesystem.  Therefore, use which the filesystem for whichever OS you use the most.

That does make sense; however, with old-ish P4 system and IDE drive I haven't noticed anything.  My plan is to use the native file system for tasks that require speed (Photoshop scratch space, etc), and then use the cross-platform storage space for things like music, movies, photos, documents, etc.

@coffeecat: I'm using an internal drive, but I know what you mean about the externals.  Mac OS X does okay with NTFS, but I had a hard time getting it to read and write ext3. 

 I read something about the ext2 support from Windows - I think it has something to do with data recovery in the event of a system crash.  I'm guessing that means that Windows can't write to the journal, so if something happens while Windows is using the drive, it can't be recovered as easily (a full fsck must be performed).  If this is the case, it seems like it might tip the odds in favour of using NTFS, assuming that Linux can use all the features of NTFS.

---

### Post by Dr. C on 2007-12-15
It depends on which version of Windows.

[http://www.fs-driver.org/]("http://www.fs-driver.org/") supports NT4, 2000, XP, and 2003 but does not support Vista, the ME/9.x series or the 3.xx series or earlier.

---

### Post by rsambuca on 2007-12-15
> **FineE said:**
> It depends on which version of Windows.

[http://www.fs-driver.org/]("http://www.fs-driver.org/") supports NT4, 2000, XP, and 2003 but does not support Vista, the ME/9.x series or the 3.xx series or earlier.

It works for me in Vista.  You just have to select Windows XP emulation mode when you install it.

---

### Post by SunnyRabbiera on 2007-12-15
EXT3 as it has no real fragmentation issues like NTFS

---

