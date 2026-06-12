---
title: "VirtualBox-Removed VM-Deleted Files-Want to wipe that area of hard disk space"
date: 2016-10-16
forum: Virtualisation
---

### Post by Mark_McDonald on 2016-10-16
As the title stated, I want to do several passes to wipe just that section of hard drive that was used for that VM.

I have a PC that only has one hard drive, its 500GB HDD and W7 Pro 64 bit OEM is installed. I bought the PC refurbished from BestBuy. So I want to sandbox a few things I do, to keep the rest of the hard drive safe.
Long story short, I got a bunch of junk installed, and I want to reformat and reinstall the O/S. Then use VirtualBox with a Linux Distro. But when I remove and delete all the files from the Linux Distro to play around with another Linux distro, I want to wipe that section of hard drive 16 times. 

Is that possible?
Or will I have to partition the hard drive. I dont even know if I can format one partition or not.
I do happen to have a spare 120GB SSD, which I plan to put the same OEM O/S on, but fresh install. Then format and wipe the 500GB HDD.
That leaves me with putting the VM in its own partition on the SSD, or on a seperate HDD, which is itself partitioned.

---

### Post by Zero_Bytes on 2016-10-19
You could write zero's to all the unused space if you want, try [http://manpages.ubuntu.com/manpages/trusty/man8/zerofree.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/zerofree.8.html)

---

