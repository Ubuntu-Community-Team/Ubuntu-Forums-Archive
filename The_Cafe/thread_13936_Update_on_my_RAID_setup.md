---
title: "Update on my RAID setup"
date: 2005-02-03
forum: The Cafe
---

### Post by jdong on 2005-02-03
Hey everyone, just wanted to give you guys a status update on my 5-disk RAID5 setup...

First off, good news: Both Hoary and Warty support a RAID5 root partition, given of course that /boot is on a separate, non-RAID partition.


Bad news: Fedora Core and Ubuntu don't have the drivers for my 3rd IDE controller (PDC20378). The only distro with support was Gentoo, who merged a pre-2.6.11 libata patch into their 2.6 kernel early last month.

So, I'm here emerging xorg-x11.... I also somehow seriously messed up my mdadm command, because it claims that I have 5 devices and one SPARE, and one device is removed. So, it's here rebuilding a "spare"....

Hopefully by the time it's done rebuilding the last drive, the RAID will function like normal. It claims ~ 1hr left.


I've filed an enhancement request for the libata patch in Hoary. As soon as it's integrated, I hope to go back to Hoary... I really do not like to be stuck in Gentoo, but if it's the only distro to support my hardware, I'll go with it.

---

### Post by jdong on 2005-02-05
I've settled down into my RAID now... I can tell you first hand that redundancy works! LMAO (stupid mkswap... ;))

I've also isolated the two patches Gentoo has to support my IDE chipset, and submitted them through Bugzilla to Fedora and Ubuntu, so hopefully I can go back to one of them soon!

---

### Post by jdong on 2005-02-06
Trying to be a good Open Source citizen, I isolated the patch for the FastTrak 378 from Gentoo's kernel, and submitted it both to Ubuntu and Fedora.

---

### Post by TravisNewman on 2005-02-06
That's freakin sweet, hopefully you'll be able to stick with Ubuntu because of the backports (unless you just want to use Fedora).

---

### Post by jdong on 2005-02-06
Regardless of whether I run Fedora or Ubuntu on my desktop, I'll continue Ubuntu backports.

It's just now, I regard my current Gentoo setup as a temporary solution, and don't want to spend the time of setting up 2 chroot's with debootstrap, when any day at any moment Hoary's daily images could let me install Ubuntu.

I doubt Fedora's gonna include support before core 4, so I'll use Ubuntu until that day, and if Xen makes it into FC4, I'll switch to Fedora, if not, I'm staying with Ubuntu.

---

### Post by TravisNewman on 2005-02-06
Yes I had no doubt you'd still continue backports... it'd just make it much easier to stay with one distro.

And as far as Xen...
Xen works in Fedora Core 3 perfectly, just don't use the unstable rpm's ;) It's very simple to download the xen source and compile it to run in Fedora.

In Ubuntu, however, this does NOT work as it should. Lack of kernel support and all. Hopefully by the time Xen gets into Debian's sarge repo, the Dev release of Ubuntu at that time will include it, and make it work with Ubuntu, because as it is now, alsa and either fat or hdb don't work for me. But that's another topic.

My point is, you can get Xen going in Gentoo very easily instead of the 2 chroot's with debootstrap. And if we could get enough people wanting Ubuntu support, perhaps Xen 2.0.4 will include it, so you could just run 2 Ubuntu's instead of 2 Ubuntu's and something else.

---

### Post by jdong on 2005-02-07
Yay, support for my chipset is added to the newest Hoary kernel. I'll download tomorrow's daily install CD, and hopefully it works!

---

### Post by jdong on 2005-02-08
I'm pleased to say that I'm back in Hoary! Got everything working.

RAID setup was a snag -- Ubuntu's partitioner kept on telling me that I didn't have any free RAID partitions, no matter how many times I made/remade them! Finally, I had to create the RAID with mknod + mdadm , which did work.

Then, md and raid5 modules have to be added to /etc/mkinitrd/modules, and after that it works!

Using XFS currently -- it's supposed to be excellent for setups like mine.

---

### Post by Randabis on 2005-02-08
[QUOTE=jdong]I'm pleased to say that I'm back in Hoary! Got everything working.

RAID setup was a snag -- Ubuntu's partitioner kept on telling me that I didn't have any free RAID partitions, no matter how many times I made/remade them! Finally, I had to create the RAID with mknod + mdadm , which did work.

Then, md and raid5 modules have to be added to /etc/mkinitrd/modules, and after that it works!

Using XFS currently -- it's supposed to be excellent for setups like mine.[/QUOTE]
 Congrats. Great to have you back.

---

### Post by poofyhairguy on 2005-02-09
[QUOTE=jdong]I'm pleased to say that I'm back in Hoary! Got everything working.

RAID setup was a snag -- Ubuntu's partitioner kept on telling me that I didn't have any free RAID partitions, no matter how many times I made/remade them! Finally, I had to create the RAID with mknod + mdadm , which did work.

Then, md and raid5 modules have to be added to /etc/mkinitrd/modules, and after that it works!

Using XFS currently -- it's supposed to be excellent for setups like mine.[/QUOTE]

I'm glad Hoary is working well for you. If the dynamic universe falls through, I already have a few good idea for packages to backport (or port period).

---

