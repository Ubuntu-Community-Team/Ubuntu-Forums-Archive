---
title: "Open Source hd repair tools"
date: 2009-02-11
forum: The Cafe
---

### Post by Metallion on 2009-02-11
What's your favourite tool to use when repairing bad sectors on a hard drive? I'm looking for one of those and flame wars about which app pwnz the other in the cafe are always the best way to learn. ^_^

Let's not forget to include windows tools here as well. I want to hear about all of them. ;)

---

### Post by prshah on 2009-02-11
> **Metallion said:**
> What's your favourite tool to use when repairing bad sectors on a hard drive?

If by "repair" you mean "test, recover and mark unusable" then fsck (in combination with badblocks) is by far the best I've used.

---

### Post by Herman on 2009-02-11
:) I agree with prshah, if you have bad sectors in your hard drive, back up your data and re-install your operating system and data on a new hard disk. 
No software can fix bad sectors in a hard disk. Bad sectors are areas of the hard disk where the magnetic properties have deteriorated to the point where those sectors are relatively unreliable for data storage.  
Every hard disk has a few bad sectors, even when it's brand new, and over time, a few more will normally develop. 
There's an area of spare sectors in every hard disk that can be automatically swapped for bad sectors invisibly to the operating system and the user by the hard disk's firmware. It is only when that supply of spare sectors is exhausted that bad blocks show up in your file system. When that happens, you know your hard disk drive is on it's way out. Buy a new one and replace it.
Software can hide badblocks temporily by telling the file system not to use them, and that will 'sweep them under the carpet' for a while and give you more time, but soon your hard disk will die. Replace it ASAP.

---

### Post by Metallion on 2009-02-11
Test, recover and mark unusable is indeed what I mean. I do think there are some programs who can recover data from bad sectors if it isn't too badly damaged and copy it to another place, am I right?

---

### Post by az on 2009-02-11
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)
[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

Use Gddrescue to image the drive.  It will read and re-read the bad blocks until it gets a good read.  All you need is one good read.

Image the drive to a file on another drive, or image the partition to a partition of the same size on another drive, then mount the partition and save your files.

You cannot fix the bad block on the damaged drive itself.   Well, you could, but data recovery assumes your data is worth more than sparing a $100.00 hard disk that's going to fail again anyway.

---

