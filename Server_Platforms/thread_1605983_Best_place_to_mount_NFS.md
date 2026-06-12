---
title: "Best place to mount NFS?"
date: 2010-10-26
forum: Server Platforms
---

### Post by bertmanphx on 2010-10-26
Hello,
What is the most proper place to mount a NFS share?
I have an NFS server that shares up data to my network.  Should I mount it under /mnt/NFS, /media/NFS, or /home/user/NFS?

Under /mnt, I notice that a disk icon does not appear when using Gnome.


Thanks,

bertmanphx

---

### Post by HermanAB on 2010-10-26
Howdy,

The convention is that removable media is mounted automatically under /media, while static mounts controlled by /etc/fstab are mounted under /mnt.

So as not to confuse other people, make a directory under /mnt and edit fstab, but you can mount it anywhere else you please, if it is your machine and other people don't matter.

---

### Post by bertmanphx on 2010-10-26
Thank you!

---

