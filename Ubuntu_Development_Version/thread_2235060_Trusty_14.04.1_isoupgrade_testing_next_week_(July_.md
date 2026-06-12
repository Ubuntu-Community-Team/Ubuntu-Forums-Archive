---
title: "Trusty 14.04.1 iso/upgrade testing next week (July 21st - 24th)"
date: 2014-07-18
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2014-07-18
For those of us who get a kick out of installation and upgrade testing the first point release of Trusty is due next Thursday, July 24th:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

From looking at the QA Tracker it looks like all of the flavors are participating:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

A few days ago I discovered that the Trusty image links there are broken:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1341731](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1341731)

Maybe a confirmation would help, but I did post a message at edubuntu-devel:

[https://lists.ubuntu.com/archives/edubuntu-devel/2014-July/003870.html](https://lists.ubuntu.com/archives/edubuntu-devel/2014-July/003870.html)

I also did cc Stéphane Graber but no response yet. It's easy to workaround though.

The #1 ugly bug I'd like to see squashed is this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I subscribed the release team in hopes they'd at least respond but no luck so far :(

And my two favorite pet peeves:

[https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

I know Tim Lunn would like to crush this:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1262068](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1262068)

But Ubuntu GNOME has no testers with Optimus graphics so we're stuck :redface:

If you're so inclined please help test your favorite flavor :guitar:

---

### Post by craig10x on 2014-07-18
Is there a test iso for 14.04.1 64 bit desktop (unity)?  Would it run in a live session... had some spare time this weekend and i was curious to test it out....if someone could provide a direct link to it...i never tried the iso testing site before ;)
(That is assuming they are working right now)...

---

### Post by mc4man on 2014-07-18
nv

---

### Post by kansasnoob on 2014-07-18
> Also they have current 14.04 kernel instead of the lts one

The 3.13 series kernel is LTS (the only one supported for the full 5 years):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

That HWE EOL thing with Precise is turning out to be a nightmare. I suspected it would be so I've kept all of my Precise installs on the original series kernel.

---

### Post by craig10x on 2014-07-18
got you...thanks ;)

---

### Post by mc4man on 2014-07-19
nv

---

### Post by ventrical on 2014-07-19
> **kansasnoob said:**
> The 3.13 series kernel is LTS (the only one supported for the full 5 years):

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A14.04.x_Ubuntu_Kernel_Support)

That HWE EOL thing with Precise is turning out to be a nightmare. I suspected it would be so I've kept all of my Precise installs on the original series kernel.


No kidding !  And try explaining this to a complete noob - I mean people who just expect applications to work and not have to  engage CLi or terminal etc.. and that leaves migration assistants like me with several extra baby-sitting hours. Trusty has somehow been able to repair itself after a wait for updates but Precise seems to be deprecating on newer machines.

---

### Post by ventrical on 2014-07-19
> **kansasnoob said:**
> For those of us who get a kick out of installation and upgrade testing the first point release of Trusty is due next Thursday, July 24th:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

From looking at the QA Tracker it looks like all of the flavors are participating:

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds)

A few days ago I discovered that the Trusty image links there are broken:

[https://bugs.launchpad.net/ubuntu-qa-website/+bug/1341731](https://bugs.launchpad.net/ubuntu-qa-website/+bug/1341731)

Maybe a confirmation would help, but I did post a message at edubuntu-devel:

[https://lists.ubuntu.com/archives/edubuntu-devel/2014-July/003870.html](https://lists.ubuntu.com/archives/edubuntu-devel/2014-July/003870.html)

I also did cc Stéphane Graber but no response yet. It's easy to workaround though.

The #1 ugly bug I'd like to see squashed is this:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)



Is exactly why I will not do a side by side hdd install on newer mobile laptops with Sandy Bridge and above.  I have resorted to  creating USB flash drives with some success but trying to teach&train new converts to understand that their USB flash drive is an actual hdd is like trying to tell a small child that Captain Kirk did not say "Beam me up , Scotty". ;(

---

### Post by xeizoo on 2014-07-19
> **ventrical said:**
> Is exactly why I will not do a side by side hdd install on newer mobile laptops with Sandy Bridge and above.  I have resorted to  creating USB flash drives with some success but trying to teach&train new converts to understand that their USB flash drive is an actual hdd is like trying to tell a small child that Captain Kirk did not say "Beam me up , Scotty". ;(

It IS a hdd, but an awfully slow hdd which explains why it's not so funny to run an OS from a flash drive, SSD is-the-**** ...

---

### Post by ventrical on 2014-07-21
> **xeizoo said:**
> It IS a hdd, but an awfully slow hdd which explains why it's not so funny to run an OS from a flash drive, SSD is-the-**** ...


They run just fine here. Faster than some of my 7200rpm hdds and that's ver 2.0! SSDs rock , of course.

---

### Post by kansasnoob on 2014-07-21
Anyone willing to bet on this being delayed :D

---

### Post by kansasnoob on 2014-07-22
> **kansasnoob said:**
> Anyone willing to bet on this being delayed :D

I would have been wrong :lolflag:

---

