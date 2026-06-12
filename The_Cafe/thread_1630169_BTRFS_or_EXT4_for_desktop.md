---
title: "BTRFS or EXT4 for desktop"
date: 2010-11-24
forum: The Cafe
---

### Post by kainalu on 2010-11-24
What do you think? I'm bombing all 4 of my drives and reinstalling / restoring. at that time, I'm converting off EXT3. So, BTRFS, EXT4, or Other?

---

### Post by Spice Weasel on 2010-11-24
Xfs.

Btrfs is no where near ready/stable.

---

### Post by FuturePilot on 2010-11-24
Ext4 right now. BTRFS isn't even ready yet.

---

### Post by czr114 on 2010-11-24
btrfs is not stable, not optimized, and can't be fscked. It needs further development.

---

### Post by cariboo on 2010-11-24
Use ext4, BTRFS is glacially slow right now. As a side note, only the boot drive on my server is ext4, the other 7 are XFS.

---

### Post by Slug71 on 2010-11-24
Id wait on BTRFS until a separate boot partition is no longer needed.

---

### Post by ubuntu27 on 2010-11-24
If you want to be stable, go for Ext4.

---

### Post by madjr on 2010-11-24
btrfs is the future, but for now is not ready yet.

might be within next year or even default by next lts

---

### Post by chessnerd on 2010-11-24
In a few years, I might say "use BTRFS" but it just isn't ready for widespread use yet. So, I recommend ext4. I'd call it stable and reports of the infamous "data-loss" are now sporadic at best. I haven't had a problem with it since I switched to it over a year ago. All 3 of my Linux installs use it and all of them are fine.

---

### Post by kainalu on 2010-11-24
A couple of people mention XFS. What are the advantages or features that you like about that file system?

---

### Post by ezsit on 2010-11-24
For a desktop system, why do you need something other than ext3? Ext4 offers very little over ext3 for desktop use -- slightly faster recovery from improper shutdowns, but that's about it. I stick with ext3, its a file system, what do you need except stability?

---

### Post by Pogeymanz on 2010-11-25
> **ezsit said:**
> For a desktop system, why do you need something other than ext3? Ext4 offers very little over ext3 for desktop use -- slightly faster recovery from improper shutdowns, but that's about it. I stick with ext3, its a file system, what do you need except stability?

Speed.

My personal favorite is JFS. It uses significantly less CPU than the other filesystems and performs as well. It's developed by IBM, so it must be good. ;p

Also, XFS seems really good, especially if you have big files (movies, distro isos, etc.), but you need to set the right parameters for it, to get the most out of it.

I usually use:

/boot  ext2
/home  ext3/4 or XFS
/      jfs
/var   reiserfs
/tmp   reiserfs or ext2 depending on what I want to use the machine for.

---

### Post by Spice Weasel on 2010-11-25
> **kainalu said:**
> A couple of people mention XFS. What are the advantages or features that you like about that file system?

[LIST]
[*]Faster than ext3/ext4
[*]Has a cool name
[*]Can be defragged
[*]Very good at handling large files
[/LIST]

---

### Post by khelben1979 on 2010-11-25
I'd go for EXT4. 

EXT3 if the kernel in the distribution is lower than 2.6.30 to prevent data losses as the driver for EXT4 would be unstable.

---

### Post by donniezazen on 2010-11-25
> **cariboo907 said:**
> Use ext4, BTRFS is glacially slow right now. As a side note, only the boot drive on my server is ext4, the other 7 are XFS.

I make a root, a swap and home partition. Can i use XFS for all three or ext4 for root and XFS for other 2.

---

### Post by czr114 on 2010-11-25
After seeing this thread come back up again, I can't help but caution that using btrfs on anything but a test system is inviting trouble we probably can't help fix.

It may be the way forward, but depending on it right now is irresponsible.

---

### Post by Gremlinzzz on 2010-11-25
Ext4

---

### Post by Khakilang on 2010-11-25
I use what come with Ubuntu. So far ext4 has serve me well. No crashes or system hang. Maybe I am not a heavy user. I am sure they have tested the ext 4 thoroughly before release. So ext4 must be safe to use.

---

### Post by MasterNetra on 2010-11-25
My vote is for EXT4. Haven't had a issue with it. BTRFS not ready yet.

---

### Post by ukripper on 2010-11-26
Ext4 for time being

---

### Post by ukripper on 2010-11-26
> **khelben1979 said:**
> I'd go for EXT4. 

EXT3 if the kernel in the distribution is lower than 2.6.30 to prevent data losses as the driver for EXT4 would be unstable.

Good point!

---

### Post by Blue Beard on 2010-11-27
> **Spice Weasel said:**
> Xfs.

Btrfs is no where near ready/stable.

It depends on what you call stable.  I have being using btrfs for over a year without a single mishap.  The problem with corruption on power failure appears to be a hardware issue.  

The only issue I see is the lack of a fsck that repairs a corrupted drive.  See [http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg06277.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg06277.html)

That should be available soon.

Try using snapshots to save your directory before a software install.

---

### Post by Sammi on 2010-11-27
> **Blue Beard said:**
> It depends on what you call stable.  I have being using btrfs for over a year without a single mishap.  The problem with corruption on power failure appears to be a hardware issue.  

The only issue I see is the lack of a fsck that repairs a corrupted drive.  See [http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg06277.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg06277.html)

That should be available soon.

Try using snapshots to save your directory before a software install.
But even then, what is the benefit of Btrfs over EXT4?

---

### Post by kainalu on 2010-11-29
Fair enough, all. I think I'm going to go with :

/ EXT4
/home EXT4 (maybe JFS)
/Data XFS or JFS
/Backup EXT3 (current, I aint touchin it)

Thanks for all your help, community!

---

