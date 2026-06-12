---
title: "safely move ntfs parition? (sda1)"
date: 2007-08-28
forum: Windows
---

### Post by stairwayoflight on 2007-08-28
Hello,

I need to (safely) move my vista ntfs partition sda1 to install obsd at the beginning of the drive. gparted won't let me move the partition.

Is it safe to simply create a part of the same size/type with fdisk, then copy it over with dd? (eg. from sda1 to sda3)

(I have borked my vista partition a couple of times, the only option is the factory restore part or the recovery cds, then the 2+ hours to prune the beast down and shrink the vista part again...what a pain... a "sure fire" technique would be great)

Stairway

---

### Post by stairwayoflight on 2007-08-30
(In case anyone else wants to try this)

I figured out what works for me (finally). This is a laptop, so in case anyone else wants to know, I removed some unnecessary cruft from the windows vista install (you never can remove enough), used the vista disk utility to shrink the ntfs volume. Then I fired up knoppix, and gparted (or qtparted?) shrank it further for me, though neither let me move the partition. I created another ntfs partition with fdisk, just larger than the first (sda1). Then I copied vista over via:
dd if=/dev/sda1 of=/dev/sda3 bs=1M
I wanted 2 things out of this laptop: support for my hardware, and a unix(-like) environment. I like bsd, so if I need windows for my webcam there is no compelling reason to switch to linux. I am not especially fond of the debian method of kernel upgrades, etc.
However, if I want to use bsd on a centrino, the 3945abg card from intel is better supported by openbsd than free, and since obsd must install close to the beginning of the drive I had to move my vista partition or lose it.
I can't vouch for the stability of doing this, but it seems to work.

---

### Post by marx2k on 2007-08-30
Did you try using the GParter LiveCD? I've not had issues moving partitions around, though it takes FOREVER if there's lots of info to move since Im guessing it's physically moving every bot of info over to another part of the platter

---

