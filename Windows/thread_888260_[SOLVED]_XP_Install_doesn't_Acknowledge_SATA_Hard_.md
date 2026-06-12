---
title: "[SOLVED] XP Install doesn't Acknowledge SATA Hard Drives"
date: 2008-08-12
forum: Windows
---

### Post by Tindytim on 2008-08-12
Reinstalled all of the components of my computer into a new case, and on a new motherboard. I've had to reformat both SATA drives (I was prepared for such an event). I reinstalled Ubuntu just fine, but when I boot from the Win XP install disc it doesn't acknowledge either SATA hard drive in my computer, instead wanting to install on my external USB drive.

For some reason my old Ubuntu install still appears on GRUB (I wanted so switch which drives each OS was installed on).

I'm wondering if this is an issue with the SATA or RAID drivers, but I didn't have this issue on my various other XP reformats before, so that leads me to believe it may be a BIOS issue (I have never flashed my BIOS before, and would like to find if that even is the issue).

Help? Wrong place?

---

### Post by hardyn on 2008-08-12
you know when you are installing and you are promped to "press f6 for 3rd party drivers"?  that is why that is there.  XP cannot natively talk to SATA2 devices.

you either have to get a driver onto the machine using a CD or floppy when prompted; however, better to remaster an install disk with the sata drivers, SP3, IE7, and whatever else you would like.  I had to do that reciently to put XP onto a new dell notebook.  google "slipstreaming xp"  there is a tool to make this job pretty painless, but the name escapes me.

the easy easy but somewhat lame way is to set the IDE compatibility mode in the bios.

---

### Post by Dremora on 2008-08-13
turning off RAID may work, failing that, try integrating the driver with nlite

---

### Post by Tindytim on 2008-08-13
I would try that, but I don't have access to a windows machine I can install things on.

I guess I'll have to burn off some SATA/RAID drivers.

---

### Post by billgoldberg on 2008-08-13
> **Tindytim said:**
> Reinstalled all of the components of my computer into a new case, and on a new motherboard. I've had to reformat both SATA drives (I was prepared for such an event). I reinstalled Ubuntu just fine, but when I boot from the Win XP install disc it doesn't acknowledge either SATA hard drive in my computer, instead wanting to install on my external USB drive.

For some reason my old Ubuntu install still appears on GRUB (I wanted so switch which drives each OS was installed on).

I'm wondering if this is an issue with the SATA or RAID drivers, but I didn't have this issue on my various other XP reformats before, so that leads me to believe it may be a BIOS issue (I have never flashed my BIOS before, and would like to find if that even is the issue).

Help? Wrong place?

Older SP1 and SP2 disks ship without SATA drivers.

You will have to slipstream your cd and include the drivers or download a new copy from the web (illegal) or buy a new cd (is that still possible?).

I had the same problem with my SP2 cd, and I had to slipstream it.

---

### Post by K.Mandla on 2008-08-13
File a bug report. :lolflag:

Okay, sorry, that was dumb. 

Moved to Windows Discussions.

---

### Post by Tindytim on 2008-08-13
Well Since I cannot install Nlite on Ubuntu, looks like I'll be installing Vista.

---

### Post by dca on 2008-08-13
XP Professional installer CD has no SATA support, you need to copy drivers to either USB drive or USB floppy drive.

---

### Post by Tindytim on 2008-08-13
Can't seem to find proper SATA Drivers for my Western Digital Caliver SE 250GB drives. Are there generic Drivers that I could use? Or maybe just a large package of various SATA drivers? Size is of no issue as long as it would fit on a Single Layer DVD.

---

### Post by dca on 2008-08-13
You need drivers for the SATA controller on the motherboard, not the drive.

---

### Post by blazercist on 2008-08-13
I have a modified ISO with SATA support that I made for myself because of this problem, but sharing it is illegal.  M$ ftw, huh.

---

### Post by koji042 on 2008-08-13
You should be able to find SATA drivers for your motherboard on the manufacturer's website. Just search up your motherboard and find the "SATA RAID" drivers (They usually have those two words in the driver name). Then you can slipstream the file into a new install disc, put it in a floppy and do a clean install, or just install it into your existing XP installation (You should have an unknown RAID device or something in your device manager).

Hope that helps.

---

### Post by Tindytim on 2008-08-13
Turn out Vista has some issues with my Drives as well.

And thanks dca, that makes a lot more sense (I am using a different motherboard).

I may have found the correct drivers, so I'll try that now.

EDiT: Doesn't seem to be the right driver. I'll keep looking.

---

### Post by Tindytim on 2008-08-14
Well changing the BIOS options didn't help. Combination and RAID/ATA, for both XP and Vista.

[http://ubuntuforums.org/showthread.php?p=5584892#post5584892](http://ubuntuforums.org/showthread.php?p=5584892#post5584892)
Help?

---

### Post by hardyn on 2008-08-14
> **blazercist said:**
> I have a modified ISO with SATA support that I made for myself because of this problem, but sharing it is illegal.  M$ ftw, huh.


No sharing the disk isn't... sharing the key is.

---

### Post by RetiredInMaine on 2008-08-31
If I understand your problem you want/need a dual boot system. Have you tried running XP under VMWaere? Since VMWare uses the underlying OS it should work. That way you can switch between Windows and Ubuntu without rebooting. 

VMWare is available from the repositories, at least for the 7.04 and 7.10 releases. There is a "how to install XP under VMWare" on the internet, sorry I don't remember the URL, but google should find it.

Hope this helps

---

### Post by erickghint on 2008-08-31
I've had this same problem before... really all we did was turn off native sata in the bios. works like a charm. you can leave it off after installation or just turn it back on.

---

### Post by Tindytim on 2008-08-31
I'm sorry, this issue has been solved, I'm not sure how to change the thread title to reflect that.

---

### Post by erickghint on 2008-08-31
select solved from the thread tools on the top right of the post :)

---

