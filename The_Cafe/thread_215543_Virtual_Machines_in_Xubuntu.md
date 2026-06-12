---
title: "Virtual Machines in Xubuntu"
date: 2006-07-14
forum: The Cafe
---

### Post by maniacmusician on 2006-07-14
Hey guys,

How good are vm clients on your computers, if you use them? Can they run windows reliably? I'm thinking of replacing my windows install with xubuntu, because right now windows is hogging my good computer. And if xubuntu is this fast on my old junker, i'm sure I can make it fly on a new machine. And also, I want to put my graphics card to good use lol. 

But there are definitely a couple of windows programs i'm not ready to let go of...so do you recommend me using a VM client to get around this? I've never used one before, so how easy is it to set up? How much of a performance drop do you notice? And is it reliable/does it crash often? It's definitely a step up from wine, right? which one would you recommend? I've heard of a few like VMplayer, Xen, and easyvmx for "building" a vm (i have no idea what that means)

I'd love to hear your replies,

Thanks

---

### Post by fluffington on 2006-07-14
I use [VMWare Server](http://www.vmware.com/products/server/), and  so far, it works great.

---

### Post by maniacmusician on 2006-07-14
do you have any details on it? like, where do you store the files that you use in windows? can a windows VM read your linux ext3 file system?

---

### Post by maniacmusician on 2006-07-14
bump

---

### Post by fluffington on 2006-07-14
> **maniacmusician said:**
> do you have any details on it? like, where do you store the files that you use in windows? can a windows VM read your linux ext3 file system?

Virtual machines are installed onto disk image files or hard drive partitions (the latter is a bit of a pain to set up, though). Windows cannot natively read anything other than FAT and NTFS filesystems, and VMWare restricts it from ever seeing the physical hard drive anyway. I've found that the easiest way to transfer files between the host and various virtual machines is to set up a FAT32 partition and give each VM direct access to it.

---

### Post by Moodel on 2006-07-14
I installed VMware server this week and it took me about 20mins to install and configure.

Its easy to set up and to use and pretty much all the info is available on this forum.

I currently run Novell, SUSE, Solaris and Win2K3 images for software testing :D

---

