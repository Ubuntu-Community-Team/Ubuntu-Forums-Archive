---
title: "Standard partition filesystem for video editing in Ubuntu?"
date: 2016-01-30
forum: Ubuntu Studio
---

### Post by Bucky Ball on 2016-01-30
Hi all,

I am about to start storing and editing 1080p video and 48/24bit audio. The vid files are not going to be that huge, but a few gig at least. Having only ever done this kind of work on Windows a decade or so ago and Mac about seven years ago (to any serious extent) where NTFS and the Mac filesystem (can't remember the Mac one) were the 'normal', I'm wondering which filesystem which might be most suitable for the job in Ubuntu.

Have been looking at XFS. Seems good for larger files. Has its pros and cons but wondering what the general consensus is among video and audio editors, but particularly video. Is there a 'norm' for Linux when it comes to A/V work specifically (audio/video editing)?

---

### Post by yoshii on 2016-02-01
i don't know much about video editing, but for audio I use ext3 and have manually disabled "last file access" logging in /etc/fstab.  This is supposed to help improve disk I/O performance by reducing the number of times a file is written to.  Since file access timings aren't needed for most usage, it works out OK.  

I forget the exact syntax for disabling last file access time, but I remember it's called "noatime".  You could google for "noatime, fstab" and you'd find out though.  
Sorry I can't be of much help other than that.  

I chose ext3 because it has journaling for data integrity and it fails more gracefully than ext4's journaling according to the sites that I read.  Apparently ext3 is good for journaling except that if the journaling fails, it can result in data corruption.  For a while I even thought about maybe using ext2 with encryption turned off since it doesn't do journaling, and thus might be faster.  There's probably a way to manually disable journaling on ext3 and ext4, but it's probably a good thing to have it on, so I never tried that.  

I don't know anything about the other file systems except FAT and NTFS, and those aren't really desirable.

---

### Post by Bucky Ball on 2016-02-01
Thanks for your input. Yea, I figure there must be something more efficient than NTFS and definitely FAT. Maybe I'm wrong. :-k

---

