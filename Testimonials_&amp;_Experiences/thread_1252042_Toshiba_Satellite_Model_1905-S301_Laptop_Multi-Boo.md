---
title: "Toshiba Satellite Model 1905-S301 Laptop Multi-Booting OS Success Story"
date: 2009-08-28
forum: Testimonials &amp; Experiences
---

### Post by LewRockwell on 2009-08-28
Toshiba Satellite Model 1905-S301 Laptop Multi-Booting OS Success Story

So here we have a Toshiba laptop of the late 2001/early 2002 vintage which came with Windows XP. The original BIOS has been upgraded, the original 256MB of ram was replaced with 1GB, the original 40GB hard drive failed after several years and was replaced with an 80GB, and wifi is provided via a PCMCIA D-Link AirPlus Model DWL-G630.

Our operation began with a complete random-write of the hard drive to securely erase and destroy the previous contents(including any nasties). Windows XP was reinstalled and brought up to SP3 with all updates to date.

Gparted was utilized from a *nix distro LiveCD to shrink the NTFS partition in several increments(as has been repeatedly described previously by numerous contributors to this and other forums). The highly suggested multiple defragmentations were performed after each reduction via Gparted. It is noteworthy to observe the Windows boot-up performing check disk after each partition size reduction(as it should, since it "sees" a different partition size). It is also notable that after Windows boots fully into the GUI it says "new" hardware has been found and a restart is necessary to complete it's installation(here we do as requested and restart). After the restart we then begin the process again to further reduce the NTFS partition.

We've included a screenshot of Gparted showing the current partitioning of the 80GB hard drive.

This unit is multi-booting Windows XP SP3, Ubuntu 9.04 Jaunty Jackalope, Mandriva Linux One 2009.1-GNOME, and Puppy Linux 4.2.1 via the Grub Bootloader.

All installed operating systems recognize and work properly with the PCMCIA Wifi Card previously mentioned and identified. It should be pointed out that with XP, Mandriva, and Puppy, the indicator lamps alternately flash as an indication of connectivity. With Ubuntu 9.04 only the activity lamp illuminates(we shall be investigating this further, but wanted to get this thread started asap).

We have previously reported on multi-boot successes with other equipment.

Final Thoughts:

We cannot stress enough the importance of having back-ups and proper data management and retention procedures in place BEFORE you have a problem.

You will be well served by learning proper partitioning of your storage devices.

You will be well served by learning proper editing, placement, and administration of your grub bootloader.

.

---

### Post by LewRockwell on 2009-09-21
yesterday the Toshiba received two additional operating systems:

PCLinuxOS Gnome 2009.2

[http://linuxgator.org/home/index.html](http://linuxgator.org/home/index.html)

the only issue we had with the install procedure was that the installer does not give the option to decline installing grub

so you are required to let it install and then go through the process of resetting grub to your previous menu.lst and cutting and pasting in the appropriate boot information to allow booting the additional operating system from your preferred grub setup

everyone should learn how to do that anyway as it is both fun and satisfying
(not to mention quite handy)

the same is true of proper partitioning

---------------------------------------------

The second new operating system was:

Puppy Linux 4.3

[http://www.puppylinux.org/downloads/official-releases/puppy-430](http://www.puppylinux.org/downloads/official-releases/puppy-430)

another great release and others like it too!

[http://desktoplinuxreviews.com/2009/09/21/puppy-linux-4-3/](http://desktoplinuxreviews.com/2009/09/21/puppy-linux-4-3/)

[http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Time-for-a-New-Puppy-Puppy-Linux-4.3](http://www.linux-magazine.com/Online/Blogs/Productivity-Sauce-Dmitri-s-open-source-blend-of-productive-computing/Time-for-a-New-Puppy-Puppy-Linux-4.3)

and Puppy gives you various installation options including the bootloader

as always...BACK-UP your valuable data FIRST
(you should already be doing this as part of your computing routine!)

and, as always...your mileage may vary, buyer beware, and buyer be aware

we now return you to your regularily scheduled programming

.

---

### Post by HappyFeet on 2009-09-21
I'm running Puppy on my 6 yr old Thinkpad and love it. Good choice. Rock on!

---

### Post by LewRockwell on 2009-09-22
here is a good review of Puppy:

[http://desktoplinuxreviews.com/2009/09/21/puppy-linux-4-3/](http://desktoplinuxreviews.com/2009/09/21/puppy-linux-4-3/)

.

---

### Post by LewRockwell on 2009-11-01
Here we see Ubuntu 9.10 Karmic Koala freshly installed and multi-booting via the new Grub 2

It should also be noted that this was required:

[http://ubuntuforums.org/showthread.php?t=1308317](http://ubuntuforums.org/showthread.php?t=1308317)


Full roster for this portion of the worldwide pleasure cruise:

Windows XP Professional SP3
Ubuntu 9.04 Jaunty Jackalope
Ubuntu 9.10 Karmic Koala
Puppy Linux 4.3.1
PCLinuxOS Gnome 2009.2
Mandriva Linux One 2009.1-GNOME

.

---

### Post by Glucklich on 2009-11-01
Yeah... Puppy is a great distro. But I think it could a bit more polished on it's default image. Not that "bling, bling" polished. Simple stuff polished. Like CrunchBang, for example. Simple stuff on the desktop and yet, one of the most beautiful.

That reminds me... I've been wanting to test one of Puppy's puplets for quite some time, named Macpup. One of those versions that uses Enlightment... those look pretty cool. And distinguished from the Macintosh's look. Not sure how light it is when compared to the original Puppy, though.

---

### Post by LewRockwell on 2009-11-02
> **Glucklich said:**
> Yeah... Puppy is a great distro. But I think it could a bit more polished on it's default image. Not that "bling, bling" polished. Simple stuff polished. Like CrunchBang, for example. Simple stuff on the desktop and yet, one of the most beautiful.

That reminds me... I've been wanting to test one of Puppy's puplets for quite some time, named Macpup. One of those versions that uses Enlightment... those look pretty cool. And distinguished from the Macintosh's look. Not sure how light it is when compared to the original Puppy, though.

macpup was ok

we checked it out

but we aren't using it daily

.

---

