---
title: "Anyone know what version nVidia driver is in the repos?"
date: 2010-05-29
forum: The Cafe
---

### Post by fatality_uk on 2010-05-29
I toasted my desktop install this morning so a clean sheet again, *NOTE TO SELF DO NOT UPGRADE

Anyway, need nvidia drivers and just wanted to check which version is in hardware drivers?


cheers

---

### Post by Frogs Hair on 2010-05-29
Here

---

### Post by WinterRain on 2010-05-29
Popping in a live cd and going to system-administration-hardware drivers (or synaptic) would have given you the answer.

---

### Post by fatality_uk on 2010-05-29
Cheers Frogs Hair
WinterRain im lazy :D

---

### Post by Shining Arcanine on 2010-05-29
Those are fairly old and out of date. The latest beta drivers are 256.29 while the latest stable drivers are 195.36.24:

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

---

### Post by Frogs Hair on 2010-05-29
The 195.36 driver in the repo is the Nouveau driver and can be used as well , but is no longer labeled as
Nvidia.

---

### Post by philinux on 2010-05-29
Nouveau is the open source nVidia drive that only supports 2d. nvidia-current which jockey will install is the closed source nvidia driver 195.36.15 version.

---

### Post by fatality_uk on 2010-05-29
Cheers Phil. I grabbed 195 from Hardware install.

But STILL puzzled why gparted ALWAYS leaves me with 2 or 3 little 1mb unpartition areas grrr :(

---

### Post by Shining Arcanine on 2010-05-29
I think that this is unrelated to the thread, but I use fdisk myself. That lets me control exactly how much space is used or wasted when making partitions.

---

