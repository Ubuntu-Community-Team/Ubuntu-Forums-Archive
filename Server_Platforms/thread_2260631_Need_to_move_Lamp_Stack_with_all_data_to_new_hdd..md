---
title: "Need to move Lamp Stack with all data to new hdd."
date: 2015-01-13
forum: Server Platforms
---

### Post by guldberg72 on 2015-01-13
Hey. I am running Ubuntu 14.04 LTS Headless With LAMP Stack there is hosting a wordpress site and Owncloud. is there anyway to backup the whole Lamp stack and all of the data so i just can install Ubuntu 14.04 LTS Headless on my new HDD and then let a magical program do the rest ? or what is the recommenden and most easy method?

---

### Post by TheFu on 2015-01-13
Why not just clone the partition to the new HDD?  dd, gparted, or 10 other tools can do this. The key is boot off some other media (flash drive, CD/DVD) for the clone to be safe.

---

### Post by guldberg72 on 2015-01-13
well that sounds like a good solution ;) i think i will take a look at that

---

### Post by guldberg72 on 2015-01-13
hmm i have been looking around and there is multiple programs there can help me, but what is the recommended way to clone my hdd ?

---

### Post by TheFu on 2015-01-13
> **guldberg72 said:**
> hmm i have been looking around and there is multiple programs there can help me, but what is the recommended way to clone my hdd ?

Whatever way works, is the recommended way. In Linux, there are usually 10 or 100 different ways to get to the desired result.  

What works best for me isn't always best for someone else. We have different skill levels, experiences, and backgrounds.  Any of the disk cloning tools will work ... or this would be an excellent time to test the restore of those great backups you've been doing nightly, right?  

**A backup that cannot be restored is completely worthless and a waste of time.**

I would do it by restoring from a backup, but it is doubtful that you use the same backup tool that I do, so any help along that line wouldn't be useful to you, right? Just in case, here's how I'd do it: [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

---

### Post by guldberg72 on 2015-01-13
well thanks for the answer.

But my Ubuntu 14.04 LTS is running a Virtuelbox with a VM there is hosting my LAMP STACK. would it be possible to plug in my new hdd and then SSH to to the virtuel machine and the use the dd cmd. to clone the hdd?
> dd if=/dev/sda of=/dev/sdb bs=4096

---

### Post by TheFu on 2015-01-13
You cannot trust a dd on an open file system. If the OS is running, the file system is open and copying it in any way can result in a corrupted copy.  You can connect up a liveCD/iso and boot off that and connect the new HDD then use dd on the old VDI/hdd to the new HDD, if you like. It is a little complicated.

Why not just use vbox menu command: File --> Export Appliance?  It is a virtualbox feature.  Actually, you can just grab the VDI file and move that to a new machine, if you are willing to setup the VM again.

Whenever working inside a virtual machine, it is best to lead with that in most questions ... virtualization provides other options not available on physical installs.

---

