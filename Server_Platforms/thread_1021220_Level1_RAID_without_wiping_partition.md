---
title: "Level1 RAID without wiping partition"
date: 2008-12-25
forum: Server Platforms
---

### Post by vladk2k on 2008-12-25
Hi

I have a server at home with a 80 GB hard drive split up in two partitions - system (10 GiB) and homes (66 GiB).
I have *ahem* acquired a new 80GB hard drive (actually, I've upgraded my desktop and left this one out) and I want to make a software RAID level 1 (mirroring) with the 66 GiB partition. This means I have to have a 66 GiB partition on the second drive (I'll probably use the rest 10 GiB fost something else), that is no problem as the disk is blank.
The problem is, however, that I wouldn't want to wipe the homes partition (with it bearing all my important data and everything else, including my home directory).

Is there any way to say something like "hey, you, 66 GiB partition, from now on you are mirrored on the other drive. Kindly copy all your data there and resume normal operation."?

I have Ubuntu 8.04 Server installed.

---

