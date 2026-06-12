---
title: "Looking for sosurce for 9.04 UNR iso"
date: 2009-12-03
forum: System76 Support
---

### Post by Eyore15 on 2009-12-03
I've had it.  I upgraded to 9.10 and now have no audio, little wireless, and the Funct +F3 combination for the external monitor only works about 1/3rd of the time.  I want to take the system back to 9.04.  Problem is, that I can't find a site with the 9.04 UNR iso.  Does anyone have a source?

tnx

mcm

---

### Post by drewbenn on 2009-12-03
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by adaucourt on 2009-12-03
> **Eyore15 said:**
> I've had it.  I upgraded to 9.10 and now have no audio, little wireless, and the Funct +F3 combination for the external monitor only works about 1/3rd of the time.  I want to take the system back to 9.04.  Problem is, that I can't find a site with the 9.04 UNR iso.  Does anyone have a source?

tnx

mcm

here (bottom of page):
[http://releases.ubuntu.com/releases/9.04/](http://releases.ubuntu.com/releases/9.04/)

---

### Post by thomasaaron on 2009-12-03
[http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)

---

### Post by Eyore15 on 2009-12-04
> **thomasaaron said:**
> [http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)

I haved a starling.  I upgraded to 9.10 before all the advisories saying not to do that.

To summarize:  Since I upgraded to 9.10 ...

I have no audio
I've got the obvious wireless issue
Problems with the external monitor.  Selecting"function - F3", works about 1/3 of the time.

mcm

---

### Post by vttay03 on 2009-12-04
I'm really not trying to be smart or single anyone out here, but I really can't agree with everyone who says they weren't warned or are complaining about the System76 driver issue with the Starling and UNR 9.10.  This was posted by System76 the day 9.10 came out:

> **thomasaaron said:**
> It's here, and it's slicker than... well, it's just really slick!

Make sure you back up any important files before upgrading! While the upgrade process seems to be going smoothly, there is always potential for problems. (On release day, Ubuntu's upgrade servers tend to get busier than a one-armed wallpaper hanger!)

STARLING USERS: The wireless driver for Karmic is requiring a complete re-write. We're almost finished with it, but we would like for you to wait until the next 2.3.* driver is released. It shouldn't be long... maybe another week. We'll post here when it is ready.

EVERYONE ELSE: To perform an online upgrade directly from Jaunty to Karmic, please follow the instructions here...

[http://knowledge76.com/index.php/KarmicUpgrade](http://knowledge76.com/index.php/KarmicUpgrade)

Since then, there have been numerous posts warning users with the Starling NOT to upgrade to UNR 9.10.  I have stuck with UNR 9.04 and it works wonderfully with the driver version 2.3.9.  If it is any help to someone who has reduced functionality on their Starling right now, I would suggest reverting back to UNR 9.04 with driver version 2.3.9.  Again, I'm really not trying to be argumentative, I just wanted to point this out since it seems to be a recurring issue...thankfully, there's a sticky on the top of the forums now.

---

### Post by Eyore15 on 2009-12-04
> **vttay03 said:**
> I'm really not trying to be smart or single anyone out here, but I really can't agree with everyone who says they weren't warned or are complaining about the System76 driver issue with the Starling and UNR 9.10.  This was posted by System76 the day 9.10 came out:



Since then, there have been numerous posts warning users with the Starling NOT to upgrade to UNR 9.10.  I have stuck with UNR 9.04 and it works wonderfully with the driver version 2.3.9.  If it is any help to someone who has reduced functionality on their Starling right now, I would suggest reverting back to UNR 9.04 with driver version 2.3.9.  Again, I'm really not trying to be argumentative, I just wanted to point this out since it seems to be a recurring issue...thankfully, there's a sticky on the top of the forums now.

And as has also been noted, it quickly got "buried" by a bunch of other messages.  Several of us pointed out that it would have been better had a sticky been in place from the beginning.  Yes, it was my fault for not digging enough.

---

### Post by jdb on 2009-12-04
> **Eyore15 said:**
> Yes, it was my fault for not digging enough.

Not really, it's hard to look for what you don't know you need.

jdb

---

### Post by Eyore15 on 2009-12-05
> **thomasaaron said:**
> [http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)

OK. call me as dumb as a box of rocks, but I can't figure this out.

I need a special program to make a usb bootable device for the img file; I get that.

The program is at PPA for Oliver Grawert 

once there it gives the directions to add the ppa to your software sources; I did that.

The only software package listed on the site is qemu-arm-eabi 

when I went to synaptic to get the package, I get this description:

this package is a hacked up version of qemu using the qemu-arm-eabi patchset from [http://qemu-arm-eabi.sourceforge.net/](http://qemu-arm-eabi.sourceforge.net/) ported to the 0.10.5 ubuntu package it enables you to use an arm chroot environment natively through the binfmt-misc kernel module.

That doesn't sound to me much like a program that will generate the desired usb bootable drive.

What am I doing wrong?

I'm trying to revert my starling to 9.04 using the instructions at system76's knowledge base

tia

mcm

---

### Post by allersj on 2009-12-05
Mark,

You're looking for usb-imagewriter, right?  Did you try find it in the Synaptic Package Manager first?  It should be available in Ubuntu's universe repository.

John

---

### Post by drewbenn on 2009-12-05
> **Eyore15 said:**
> I need a special program to make a usb bootable device for the img file; I get that.

The program is at PPA for Oliver Grawert 

I think you actually want the USB Startup Disk Creator. I *thought* it was installed by default, under System | Adminstration | USB Startup Disk Creator.  If not, I think the package name is 'usb-creator', or you can get it from the Software Center (the new name for Add/Remove in 9.10)

---

### Post by Eyore15 on 2009-12-06
> **drewbenn said:**
> I think you actually want the USB Startup Disk Creator. I *thought* it was installed by default, under System | Adminstration | USB Startup Disk Creator.  If not, I think the package name is 'usb-creator', or you can get it from the Software Center (the new name for Add/Remove in 9.10)

I was following the system76 knowledge base which points to Oliver's PPA.  It doesn't give the name (usb-creater) anywhere in the instructions.  Me thinks system76 needs to update their knowledge base page.  Tnx for getting me pointed in the correct direction.

---

