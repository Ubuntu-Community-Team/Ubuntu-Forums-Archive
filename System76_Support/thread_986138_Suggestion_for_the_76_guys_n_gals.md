---
title: "Suggestion for the 76 guys n gals"
date: 2008-11-18
forum: System76 Support
---

### Post by jeamer on 2008-11-18
Hey, 

So I have 2 suggestions for the people setting up the laptops over at system76, and perhaps Tom can just tell me why it is they set the lappies up this way. After reading a few threads with the same issue as myself, I confirmed that I wasn't the only one with issues. Why is the root partition set up to be so small? Resizing partitions is a pain, and it seems like the root was never set up to be able to handle any kind of distro upgrade (I continually remove applications from my root partition, and only ever hover around 400 MB free). My suggestion is to set up the partitions with a few extra GB for some breathing room when upgrades come around. My root is currently set up for ~7 GB. 

Second, if this isn't possible (or maybe do it anyways), perhaps provide a link on the knowledge76 site that deals specifically with resizing a boot partition? The resize for Windows pretty much outlines it, but a dedicated tutorial would be nice, especially since it looks like it MUST include this tutorial:

[http://ubuntuforums.org/showpost.php?p=1308395&postcount=1](http://ubuntuforums.org/showpost.php?p=1308395&postcount=1)

to deal with a hosed GRUB. If I hadn't read this thread before hand, I would have been a lot more spazzy when I reached a GRUB screen of death after several hours of resizing partitions off a liveCD.

Thanks, looking forward to input!

:guitar:

---

### Post by thomasaaron on 2008-11-18
> So I have 2 suggestions for the people setting up the laptops over at system76, and perhaps Tom can just tell me why it is they set the lappies up this way. After reading a few threads with the same issue as myself, I confirmed that I wasn't the only one with issues. Why is the root partition set up to be so small? Resizing partitions is a pain, and it seems like the root was never set up to be able to handle any kind of distro upgrade (I continually remove applications from my root partition, and only ever hover around 400 MB free). My suggestion is to set up the partitions with a few extra GB for some breathing room when upgrades come around. My root is currently set up for ~7 GB.

We once set them up for 5GB. Only a few computers went out with this scheme. We realized early on that it was problematic, so now we set them up with a 10GB root partition (which is pretty standard).

> Second, if this isn't possible (or maybe do it anyways), perhaps provide a link on the knowledge76 site that deals specifically with resizing a boot partition?

That's a great idea. Is there anybody in the community that would like to volunteer to write it? (If not, I'll definitely do it.)

---

### Post by gpstar on 2008-11-18
burn a SuperGrub CD and boot off that to fix and restore your MBR and or a hosed grub.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

and use the GParted Live CD to resize/edit/repair your partitions (it is great for resizing and re-ordering your partitions)

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

the System Rescue CD is handy too which has a nice collection of programs including gparted and others if you need to do any recovery work

[http://www.sysresccd.org/Screenshots](http://www.sysresccd.org/Screenshots)

but the SuperGrub and GParted live cd's should be good enough for most people.

---

### Post by MorphWVUtuba on 2008-11-18
And, although it's not as lightweight as gParted LiveCD or Parted Magic, any Ubuntu Desktop live CD has the gParted application underneath the System>Administration menu.

---

### Post by thomasaaron on 2008-11-18
Yeah, I prefer the Ubuntu Live CD. It's got Partition Editor (gparted), and it's useful for as a basic recovery tool. PLUS, it's a familiar environment for Ubuntu users.

---

### Post by jeamer on 2008-11-18
Agreed. I may write something up if you want, maybe next week as I am totally gerfangled with term projects right now.

Really all it needs to include is 1 extra step added to the windows installation instructions on how to swap off and move and resize etc (obviously take all the windows crap outta there), then copy n paste the grub of death tutorial on.

Have previously underestimated the power of the Ubuntu livecd as a recovery tool. Nice to know you can (almost) always boot into something.

---

### Post by Spr0k3t on 2008-11-19
Hey Tom... with the 8.10 it may be advised to create a bootable USB key using the ISO image.  I have twelve different USB keys I keep near me in case I need them... I've found updating these keys are much easier than having to burn various ISOs for use.

Perhaps the tutorial could include multiple different methods... from using the existing install to burning a CD to resize from there.

---

### Post by thomasaaron on 2008-11-20
Spr0k3t,

How do you create the USB drives?

Whenever I've created bootable USB drives, I've always just used the "dd" command to transfer the .iso to the drive. Is that how you do it?

---

### Post by Spr0k3t on 2008-11-23
> **thomasaaron said:**
> How do you create the USB drives?

Whenever I've created bootable USB drives, I've always just used the "dd" command to transfer the .iso to the drive. Is that how you do it?

With the latest version of Ubuntu (8.10), it's an option from 'System/Administration/Create a USB Startup Disk'

Also, the FSF has released a new version of FUSBi ([http://aligunduz.org/blog/2008/11/fusbi-031-released/](http://aligunduz.org/blog/2008/11/fusbi-031-released/)) which would help as well.  I think a modification to that app to add Ubuntu as a downloadable iso would be fairly easy to do.

---

### Post by thomasaaron on 2008-11-24
DARN! I can't believe I didn't see that! I only do this all day every day!

Thanks.

---

