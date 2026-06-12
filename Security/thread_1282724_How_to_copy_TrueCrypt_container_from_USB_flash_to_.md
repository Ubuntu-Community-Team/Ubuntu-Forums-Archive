---
title: "How to copy TrueCrypt container from USB flash to CD?"
date: 2009-10-04
forum: Security
---

### Post by Oldhacker on 2009-10-04
Using Ubuntu 9.04, I successfully installed the latest Truecrypt.
Then, I made a hidden 3 GB container on a USB flash drive.
It can be mounted, and read normally. However, when I attempted to copy this container and burn it to a CD, all of the files on the CD are visible and unencrypted!

One after thought is that I should have created a 700MB container if I want to copy it to a CD. However, the problem is how to copy the container in encrypted form so that the files are not openly visible until I mount the CD, like I do the USB.

---

### Post by purport on 2009-10-04
Yeah, you can't put the 3 GB container on your CD. What you must be doing, then, is copying the encrypted files from the container while it's mounted. When you do this, Truecrypt is unencrypting the files "on-the-fly", which means any pasted material will be unencrpyted.

Create a new container for files f1,f2,...,fn with a size of M in MB such that size(f1)+size(f2)+...+size(fn) <= M <= 700 on your HD. Copy f1, f2,...,fn into it. Then write the container on the CD.

You obviously won't be able to modify the container, and therefore the files, once it's on the CD, so you shouldn't feel the need to make a container any larger than needed, unless you want to obfuscate the actual amount of data within the container (since you only know that size(f1)+size(f2)+...+size(fn) <= M).

But yeah, write the container. Not the files from the container having been mounted.

---

