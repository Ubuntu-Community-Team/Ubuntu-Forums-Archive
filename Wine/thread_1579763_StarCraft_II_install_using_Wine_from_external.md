---
title: "StarCraft II install using Wine from external"
date: 2010-09-22
forum: Wine
---

### Post by Joe_Ib on 2010-09-22
I was curious on how to go about installing StarCraft II onto my Ubuntu computer using my external (if possible).  Any help is always appreciated and Thank you ahead of time for your time and help :).

---

### Post by beastrace91 on 2010-09-22
Like external hard drive? If so the easiest way is to just move your **~/.wine** folder to your external hard drive and then symlink the directory back in.

If you need a hand doing this please post the output of **df -h** while the external is attached and mounted on the system.

Also just as a heads up - if the external drive is formatted to vfat (fat32/16) I personally could not get Starcraft 2 to run from a vfat drive (but moving the files to an ext4 drive worked fine).

~Jeff Hoogland

---

