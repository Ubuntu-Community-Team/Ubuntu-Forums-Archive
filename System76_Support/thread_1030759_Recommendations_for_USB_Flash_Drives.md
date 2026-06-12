---
title: "Recommendations for USB Flash Drives"
date: 2009-01-04
forum: System76 Support
---

### Post by DomIncollingo on 2009-01-04
Can anyone recommend a good USB flash drive (preferably with 4 GB capacity) that will work "out of the box" on System 76 laptops?  My Serval came with an LG flash drive that works great.  However, I would like to buy an additional flash drive, and I can't find a local store that carries the LG brand.

I've had a bad experience with a Patriot USB flash drive in the past (it just would not work with Linux), so I'd like to make sure that any USB drive that I buy will work "out of the box" with Ubuntu.

On a side note, does System 76 sell USB flash drives separately?

Thanks very much.

Dom

---

### Post by Spr0k3t on 2009-01-04
I swear by corsair voyager drives.  Not only do they work fantastic on any system, they directly support FOSS.  System76 does have flash drives available... but I'm not sure about separately.  The key to finding a good flash drive is to stay as far away from U3 as possible.

---

### Post by compholio on 2009-01-04
> **DomIncollingo said:**
> Can anyone recommend a good USB flash drive (preferably with 4 GB capacity) that will work "out of the box" on System 76 laptops? ...

I purchased a bunch of 8 GB Sony Microvault drives and they worked fine out of the box.  However, I eventually ended up reformatting most of them so I could use symbolic links (stupid crippled VFAT filesystem).

---

### Post by jdb on 2009-01-04
I've never run across one that didn't work.

As compholio said, it will be more compatable with linux if your reformat it to ext2 or ext3
(read/write/execute modes, access/modify/status times, owner/group, link, etc.),
but don't do it if you ever want to use it on a windows box.

The largest I've tried is a 16 gig Kingston & it works great.

jdb

---

### Post by compholio on 2009-01-04
I didn't think to mention this earlier, but if you reformat to ext2/ext3 you'll want to disable the "reserved blocks" or you'll lose a lot of space (they are for the super user and are not used on external drives).  You also may wish to disable the journal (which can be done by just formatting as ext2 in the first place), but I don't recommend it since it can cause accidental data loss (VFAT does not have a journal either, so if you're comfortable with that level of risk then it's not a problem).

---

### Post by rushikesh988 on 2009-01-04
I have read in a magazine that the scandisk pen drives are best in performance such as transfering speed and life too

---

### Post by jdb on 2009-01-04
> **compholio said:**
> I didn't think to mention this earlier, but if you reformat to ext2/ext3 you'll want to disable the "reserved blocks" or you'll lose a lot of space (they are for the super user and are not used on external drives).  You also may wish to disable the journal (which can be done by just formatting as ext2 in the first place), but I don't recommend it since it can cause accidental data loss (VFAT does not have a journal either, so if you're comfortable with that level of risk then it's not a problem).

Thanks, I just used:

mke2fs -j -m 0

on some non-system partitions & got about 5% more space.

Anyone thinking of doing this, be aware it erases everything on the partition.
It was a good test of my backups :p

jdb

---

### Post by compholio on 2009-01-04
> **jdb said:**
> Thanks, I just used:

mke2fs -j -m 0

on some non-system partitions & got about 5% more space.

Anyone thinking of doing this, be aware it erases everything on the partition.
It was a good test of my backups :p

jdb

That's because you should use tune2fs on existing ext filesystems, mke2fs (and mkfs.ext2 and mkfs.ext3) will build completely new ext filesystems on an empty partition or wipe an existing filesystem and build a fresh one.

---

### Post by jdb on 2009-01-05
> **compholio said:**
> That's because you should use tune2fs on existing ext filesystems, mke2fs (and mkfs.ext2 and mkfs.ext3) will build completely new ext filesystems on an empty partition or wipe an existing filesystem and build a fresh one.

I knew what I was getting into with the mke2fs, I just didn't know any other way to do it.

I've used tune2fs to label partitions and set the check interval frequency but I never paid any attention to the other things it could do.
Heck, I didn't even know about reserved blocks.

I just used it on some really big non-system partitions and it worked great, thanks.

jdb

---

### Post by OldDirtyTurtle on 2009-01-05
I've had outstanding luck with a Sandisk MicroCruzer.  I bought a 512mb version in 2003 and it is still going strong.  Get this - it has been through the washer and dryer in my jeans 3 times with no loss of data.  It has taken unintended swims in rivers (in my pocket for no good reason while kayaking) and always lived.  It still works.

I've got a Titanium MicroCruzer that has been pretty fickle.  

I also have a 2Gb MicroCruzer that is great, once I wiped U3 from it.

So there you go - I'm 2 for 3 with SanDisk.

I agree with killing U3 regardless of how you intend to use it.  I keep my formatted in FAT because I jump around alot.

---

### Post by DomIncollingo on 2009-01-05
Thanks very much for all the replies.  I've done a little research, and it looks like my local Frys has some Corsair Flash Voyager drives that are reasonably priced.  I like the fact that the Corsair folks advertise that their flash drives have Plug & Play support for Linux, so I think I'll give them a try.

Thanks again for all the input.

Dom

---

### Post by Spr0k3t on 2009-01-06
Great choice DomIncollingo... Don't forget that if you ever lose your cap, Corsair will replace it for free.

[http://www.corsair.com/helpdesk/cap_replacement_request.aspx](http://www.corsair.com/helpdesk/cap_replacement_request.aspx)

---

### Post by OldDirtyTurtle on 2009-01-07
Oh man...  I gotta have one of these:

[http://www.corsair.com/products/survivor/default.aspx]("http://www.corsair.com/products/survivor/default.aspx")

Nothing says overkill like knurled metal casing.

I love it.

---

