---
title: "&quot;ext3_new_block: Allocating block in system zone&quot; from RAID5 device"
date: 2008-11-12
forum: Server Platforms
---

### Post by tan_ce on 2008-11-12
I just set up a RAID-5 composed of 3 new Western Digital USB hard drives, each 1TB large. The three drives are connected to the system through a USB hub. The total size of the array is 2TB, formatted as ext3 (largefile4). 

I know this USB raid is slow (about 15MB/s slow...), but we ran out of space, SATA ports, and USB ports in the system unit. That's what we get for having to run a server on a budget. We are planning to use the array for semi-long-term storage of large files (DV-AVI files), and decided that sacrificing speed for the redundancy was alright.

Anyway, I moved a large file into the array. Later, while reading the file, I got a read error halfway into the file. I thought it might have been a freak incident as the array was still being resynced when I formatted and copied files in. Also, /proc/mdstat said that all three drives are fine, so I reformatted it again.

I had just started to copy files into the newly formatted array when two of this kind of message pops up on my tty:

```
EXT3-fs error (device md0): ext3_new_block: Allocating block in system zone - blocks from 131334144, length 1
```

I'm starting to suspect the "freak incident" was not a random incident... Does anyone know if anything else could be causing this? (besides hardware failure?)

---

### Post by tan_ce on 2008-11-17
Just an update, in case anyone was interested.

I was stacking four of the hard drives on top of each other. (Only three of them are in the raid.) After noticing that the lone drive that wasn't in the raid was also showing signs of trouble, I separated them and it made an almost instant recovery. I'll be trying the raid again soon and see if maybe I was just overheating the drives.

Does anyone know if overheating can indeed cause this kind of trouble?

---

