---
title: "Hard Drive Config"
date: 2007-03-10
forum: System76 Support
---

### Post by palintheus on 2007-03-10
I have interested in purchasing a System76 laptop, but have been wondering how the hard drives are configured. Is it just one partition, or is the home and boot partition seperate. Is this something that can be requested?

---

### Post by AusIV4 on 2007-03-11
On my gazelle there's a root partition and a swap partition. If you want to set it up differently, you could use a live cd to resize the root partition and format a partition for the home partition, then mount that at /home. I generally recommend this, as it makes re-installing the system a breeze, if that ever becomes necessary.

---

### Post by palintheus on 2007-03-11
I did that on my home system after I installed ubuntu with just the root and swap, but was wondering if it can be requested to have a root, home, and swap

---

### Post by voidmage on 2007-03-11
> **palintheus said:**
> I have interested in purchasing a System76 laptop, but have been wondering how the hard drives are configured. Is it just one partition, or is the home and boot partition seperate. Is this something that can be requested?
I asked Carl about this once and he basically said that it isn't possible to request hard drive configs, but repartitioning is easy enough with the liveCD.

---

### Post by crichell on 2007-03-11
voidmage is right - we don't provide custom partitioning schemes; however, adjusting with a LiveCD is pretty easy.  We have a "adding windows" how to that describes repartitioning.  You'd follow the first steps.

[http://knowledge76.com/index.php/Main_Page](http://knowledge76.com/index.php/Main_Page)

---

