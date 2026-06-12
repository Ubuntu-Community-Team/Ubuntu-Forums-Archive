---
title: "Multiple partitions in encrypted volume?"
date: 2009-05-28
forum: Security
---

### Post by u-slayer on 2009-05-28
I just set up my laptop with full-drive encryption using the alternate CD. I was able to create an encrypted volume, but it defaulted to ext3 with only one partition in it for root. 

I couldn't find any way to sub-divide the encrypted volume into a root partition, swap partition and data partition. Is there a way to go in with a live cd and resize the partitions in my encrypted volume?

---

### Post by rookcifer on 2009-05-28
If you just did a fresh install, I would recommend going back and starting over.  What you have to do is create a LVM (one big partition) that is encrypted and then create logical partitions for /, /home, swap inside it.  

This can be done and [this blog post]("http://oei.yungchin.nl/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/") shows you how, step by step.  It was written for 8.04 but works the same on Jaunty (tested it myself).

---

### Post by u-slayer on 2009-05-29
Okay thanks, that worked great. Now I just have to figure out how to mount my encrypted LVM partitions from a live-cd so I can back it up, but that should be pretty simple.;)

---

