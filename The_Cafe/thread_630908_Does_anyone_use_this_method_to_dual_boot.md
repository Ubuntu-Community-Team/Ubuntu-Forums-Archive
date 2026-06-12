---
title: "Does anyone use this method to dual boot"
date: 2007-12-03
forum: The Cafe
---

### Post by hkq37 on 2007-12-03
I hesitate to post this in the tech forums because it may not be a sound method to dual boot so I will post it here to get some opinions 

This is my own personal workaround I have been using for quite some time now - after getting 'messed up' with boot loader menus (like LILO and GRUB ) and it's what it suits my level of competence ( low).
Like many new users I had dual boot problems.. messing up my MBR... being stuck with boot loaders after uninstallations.. essentially I am not confident in using them.

Because I have 2 hard drives  ( 1 for Xp, 1 for Linux) I just installed each operating system completely independent of each other ( i.e. I removed/unplugged the second one when I did my installs).
After installing each operating system  I plugged my drives back into my motherboard and set my BIOS to choose which disk I *usually* want to boot from -  *my default OS*
If I want the other OS to boot I press F11 during start up which brings up the disks and devicesboot menu then you can choose the other hard drive ( you have to remember which is which - easy it one is a Samsung and the other a Maxtor :P)


I understand its a very basic technique, but it keeps it simple and can seperate XP and Linux in your bootup options.
It may be something to consider if:
You have 2 disk drives
Are not sure or don't want to use GRUB
Want to have a dual booting computer
Your BIOS supports it ( most will now a days)

*BTW*
People who wish to , once they gain sufficient confidence, could still from this point switch to GRUB in the usual manner.

---

### Post by yatt on 2007-12-03
> **hkq37 said:**
> I hesitate to post this in the tech forums because it may not be a sound method to dual boot so I will post it here to get some opinions 

This is my own personal workaround I have been using for quite some time now - after getting 'messed up' with boot loader menus (like LILO and GRUB ) and it's what it suits my level of competence ( low).
Like many new users I had dual boot problems.. messing up my MBR... being stuck with boot loaders after uninstallations.. essentially I am not confident in using them.

Because I have 2 hard drives  ( 1 for Xp, 1 for Linux) I just installed each operating system completely independent of each other ( i.e. I removed/unplugged the second one when I did my installs).
After installing each operating system  I plugged my drives back into my motherboard and set my BIOS to choose which disk I *usually* want to boot from -  *my default OS*
If I want the other OS to boot I press F11 during start up which brings up the disks and devicesboot menu then you can choose the other hard drive ( you have to remember which is which - easy it one is a Samsung and the other a Maxtor :P)


I understand its a very basic technique, but it keeps it simple and can seperate XP and Linux in your bootup options.
It may be something to consider if:
You have 2 disk drives
Are not sure or don't want to use GRUB
Want to have a dual booting computer
Your BIOS supports it ( most will now a days)

*BTW*
People who wish to , once they gain sufficient confidence, could still from this point switch to GRUB in the usual manner.
I am doing the same thing. Vista seems to hate being chainloaded. If I do not do what you are doing I get a wonderful technicolor display. Linux works every ******* time. Go figure.

---

### Post by -grubby on 2007-12-03
well I've always used that. It's so much simpler

---

### Post by LaRoza on 2007-12-03
Vista has no trouble being chainloaded.

If you have another disk, and don't want it touched (or risk touching) during the install, just disconnect the disk, and then add it to grub after.

---

### Post by yatt on 2007-12-03
> **LaRoza said:**
> Vista has no trouble being chainloaded.

If you have another disk, and don't want it touched (or risk touching) during the install, just disconnect the disk, and then add it to grub after.I never get it to boot. I always end up with an 80s screen saver gone wrong.

---

### Post by LaRoza on 2007-12-03
> **yatt said:**
> I never get it to boot. I always end up with an 80s screen saver gone wrong.

Odd. I would like to have seen it, although I will probably not. I hope I do not have to deal with Vista again.

---

### Post by hkq37 on 2007-12-03
Cool. Thanks for your replies.. I think the relies so far show the uncertainty users have with dual boot. .
It's good to know users like me are using this system too, so probably helpful to new users as well.
Thanks for the feedback.

---

