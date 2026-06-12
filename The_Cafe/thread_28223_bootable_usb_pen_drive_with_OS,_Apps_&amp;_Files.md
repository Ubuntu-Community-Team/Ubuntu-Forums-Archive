---
title: "bootable usb pen drive with OS, Apps &amp; Files?"
date: 2005-04-19
forum: The Cafe
---

### Post by willnapier on 2005-04-19
Hi there. I have been using Linux (Mandrake) for two years, and have now found Ubuntu (in the form of Kubuntu) and I'm very pleased with it. So much less hassle with installing new software thanks to packages.

My question:

USB pen drives are now pretty cheap. I know there is the 'LiveCD' and 'Knoppix' option, but is it / would it be possible to store your entire system, OS, Applications, Files and all - on a USB drive? I am envisaging a time (now?) when you could use exactly your own system whenever you want to, from any machine.

1) Is the above possible now or soon?

2) Would you be able to run such a system from USB under an architecture other than PC? Would you be able to plug the same system into an Apple and do your work?

With thanks for any advice.

Will

---

### Post by wmcbrine on 2005-04-19
Yes, there are distros that are made for this (but not Ubuntu). Here's one:

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by jdong on 2005-04-19
1GB of space (factoring in compression) is enough to store a single Knoppix image plus a practical amount of user data. That's about all that's practical.

In reality, most of us use 512MB or smaller, so there's less space to store.


Perhaps most concerning, USB flash media have a **limited number of writes**, so data could disappear without notice if you wear the media down enough (which is actually not too hard to do, considering it only takes 10,000 writes)

---

### Post by BWF89 on 2005-04-19
> when you could use exactly your own system whenever you want to, from any machine.
I think Yellow Dog Linux has a live CD that records your progress. When you exit out of Linux it automatically saves your progress onto the Live CD. Then when the cd gets full you just put in a new one and it will burn the OS and your progress onto it.

EDIT: [http://www.ubuntuforums.org/showthread.php?t=18793](http://www.ubuntuforums.org/showthread.php?t=18793) There it is.

---

### Post by poofyhairguy on 2005-04-19
[QUOTE=willnapier]
1) Is the above possible now or soon?[/QUOTE]

Yes. Damn Small Linux and Feather Linux work off of a USB drive.

[QUOTE=willnapier]
2) Would you be able to run such a system from USB under an architecture other than PC? Would you be able to plug the same system into an Apple and do your work?

With thanks for any advice.

Will[/QUOTE]


No on the second one. Unless you fit all of a Damn Small Linux and all of a PowerPC custom Debian install on a pen drive. Apple hardware cannot use software compiled for IBM hardware (the other way applies as well). Ubuntu has a PPC version, but that CD won't work on a regular PC for the same reason.

---

### Post by Sionide on 2005-04-19
Yeah, DSL works great from a USB Stick. The guy who created it made a PC which runs DSL off the usb hard disk and thus, with a small enough processor not requiring much cooling - it runs totally silently. Hrm, can't find the link now...

---

### Post by Kevanx on 2008-04-14
Sorry to regurgitate an old post, but I figure it's better to expand than add clutter with a new post with a very similar topic.

My question is: is it better to have bootable Linux, or Portable Apps?

I'm trying increasingly to have my data in a bunch of different places, but syncronized, and in using PCs at work, and ubuntu at home, I kind of like the idea of having part of my digital life portable. While I was backpacking (pre-linux, for me), I used a lot of [portable software]("http://www.portableapps.com/") to keep connected, but I recently came across [http://pendrivelinux.com/]("http://pendrivelinux.com/")
and I'm fascinated by this.

I like the idea of using a linux USB key like a prophylactic against windows ;-) , but I recognize that it might be unusable on some computers that aren't bootable, as well as computers that I am not able to reboot (public libraires for instance).

Questions:
1) Would files from a bootable drive be accessible without having to boot up in linux?

2) Could I have a linux boot, and have documents and portable (windows) apps accessible on the same thumb drive?

3) If it is better to have a wider usability (intel mac, pc, non usb-bootable), what would you prefer?

4) I heard [via this post ]("http://ubuntuforums.org/showthread.php?t=28223") that there are only 10,000 writes for USB drives? Does this mean that the lifespan would be exceptionally short with either of the two options?

Cheers,
K

---

### Post by az on 2008-04-14
> **Kevanx said:**
> 
Questions:
1) Would files from a bootable drive be accessible without having to boot up in linux?

2) Could I have a linux boot, and have documents and portable (windows) apps accessible on the same thumb drive?

3) If it is better to have a wider usability (intel mac, pc, non usb-bootable), what would you prefer?

4) I heard [via this post ]("http://ubuntuforums.org/showthread.php?t=28223") that there are only 10,000 writes for USB drives? Does this mean that the lifespan would be exceptionally short with either of the two options?

Cheers,
K
1 and 2, it's easy to configure your USB stick to have a FAT16 partition first, then followed by a bootable linux partition on it.  That way, the data on the FAT16 partition is available to both windows and Linux (live or not).

4 - The link is wrong (it points to this thread) and the data is not really accurate.  NAND devices cycle through each cell with every write.  That means it would take more than fifty (50) years of continual writing to reach the maximum safe number of writes that the cell can sustain.  Don't worry about it.

---

### Post by macogw on 2008-04-14
> **az said:**
> 
4 - The link is wrong (it points to this thread) and the data is not really accurate.  NAND devices cycle through each cell with every write.  That means it would take more than fifty (50) years of continual writing to reach the maximum safe number of writes that the cell can sustain.  Don't worry about it.

I had a drive run out of writes recently.  The thing is, if one cell goes, its entire row goes.  When I was using my flash drive for the sneakernet taking 4GB of data back and forth between old and new laptop, I apparently used up all the writes on a few cells so that large chunks looked full at all times, even went empty.

---

### Post by az on 2008-04-14
A typical USB flash drive is able to mark bad blocks as unusable.  I would think in your case it's a question of hardware defect from manufacturing , and not that the NAND write limit on a few cells has been reached.

A 4GB device is relatively new and I highly doubt you are anywhere close to reaching the write limit.

---

### Post by intense.ego on 2008-04-14
Using U3 compatible drives it is also possible to boot applications right off a USB disk, even on Windows

---

### Post by smartboyathome on 2008-04-14
> **intense.ego said:**
> Using U3 compatible drives it is also possible to boot applications right off a USB disk, even on Windows

It ONLY works on windows. And it takes space away from other things on your drive and don't give it back upon uninstall. If these two factors weren't true, I would be all for it.

---

### Post by Pijits_1 on 2008-04-14
There is a way to put an Ubuntu type distro (mind you, you'll need a pretty large Flash drive to use this to its full potential) The website is 

[HTML]http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/[/HTML]

This website is very useful.

I have had lots of problems getting a USB Os running but it does pay off.

Right not i have a Fedora distro that acts as a live cd but can be used for usb. If you can i recommend making a swap partition, even a 10MB one will suffice.

---

### Post by ice60 on 2008-04-14
i don't really use thumb drives, but i was half listening to a linux podcast the other day and someone mentioned a script for making slax bootable with a directory for saving the session. i looked it up and found this -
[http://polishlinux.org/linux/slax/slax-on-usb-drive](http://polishlinux.org/linux/slax/slax-on-usb-drive)
[http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/](http://www.pendrivelinux.com/2006/09/20/all-in-one-usb-slaxzip/)
[http://www.linux.com/articles/46267](http://www.linux.com/articles/46267)

is this what you're talking about?

EDIT. can i ask a quick question? do a lot of thumb drives come with software installed? i want to get a couple and was looking them up and saw this review about a SanDisk -
[http://www.amazon.com/review/R1H3CDDHZEJKZD/ref=cm_cr_rdp_perm](http://www.amazon.com/review/R1H3CDDHZEJKZD/ref=cm_cr_rdp_perm)

which one should i get?

---

### Post by smartboyathome on 2008-04-14
You can put SAM Linux on a USB drive if you want a modern+fast operating system. I like it, it is very useful. :D

---

