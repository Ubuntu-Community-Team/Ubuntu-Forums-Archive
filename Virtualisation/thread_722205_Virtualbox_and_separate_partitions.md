---
title: "Virtualbox and separate partitions?"
date: 2008-03-12
forum: Virtualisation
---

### Post by cdiem on 2008-03-12
Hi, maybe this question is asked many times before, but I couldn't find any info about it. 
So, to put it simple - I have installed Virtualbox. Do I need to repartition my hard drive and create a separate partition (for instance 20GB), in which I will run the virtualizations? Or do I just select "fixed-size-20GB", without creating a separate partition? If so, how would Virtualbox use these 20 GB - will it use it like any other data (for instance, 20GB documents etc.)? So is installing a new OS in Virtualbox just like an installation of a new program - but one with 20GB size?
Also, how many virtualizations may I have running? I'd like to test Solaris, BSD, etc. As I understand it, will I need to uninstall Solaris, for to be able to try FreeBSD afterwards, and then uninstall FreeBSD for to be able to run Archlinux afterwards, or can they exist together?

---

### Post by hyperair on 2008-03-12
**Do I need to repartition my hard drive and create a separate partition?**
- No. A virtual disk is a file.

**How would Virtualbox use these 20 GB - will it use it like any othe data?**
- Like I said, it's just a file. As such, all files stored inside the VM will be stored within that 20GB.

**How many virtualizations may I have running?**
- That depends on your computer's resources. If you have a lot of RAM, and a very fast CPU, you can run multiple VMs at the same time. However, if you have barely enough to run 1 VM at a time, that does not mean that you need to uninstall an operating system to install the next. You can have multiple VMs, just not running simultaneously. Think about it like a bunch of computers wired up to a single power socket, but the power socket only has enough power to turn on one at a time.

---

### Post by cdiem on 2008-03-12
Thank you very much!

---

