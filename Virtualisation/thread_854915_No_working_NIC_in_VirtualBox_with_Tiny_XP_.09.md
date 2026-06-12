---
title: "No working NIC in VirtualBox with Tiny XP .09"
date: 2008-07-09
forum: Virtualisation
---

### Post by kooldino on 2008-07-09
I'm running Tiny XP .09 (basically a streamlined version of Windows XP).

However, I can't get the network "cards" working.  The OS recognizes the cards, and they are enabled in virtualbox, but when I got into the Device Manager, it says that the network cards cannot start.

I have the cards defined as follows:
Adapter 0:
PCNet FAST III 
NAT
Cable Connected (Checked)

Adapter 1:
PCNet PC II
NAT
Cable Connected (Checked)

When I try to use a method other than NAT, I'll generally get an error.

If I choose the Intel Adapter, it will set itself back to the PCNet FAST III.

I'm lost.

---

### Post by kooldino on 2008-07-11
bump

---

### Post by hajo9702 on 2008-07-11
I have the same problem.
I've even installed the driver pack from the TinyXP-CD with no luck.

---

### Post by kooldino on 2008-07-12
You think this is just a TinyXP issue, or a WinXP issue?

---

### Post by jgombos on 2008-07-17
I've solved this problem.  See my post in this thread:

  [http://forums.virtualbox.org/viewtopic.php?p=28979](http://forums.virtualbox.org/viewtopic.php?p=28979)

Also, shared folders doesn't work, perhaps because TinyXP removed an essential component for that to work.  But you can create an ISO image containing that AMD driver, and mount it as a CDROM.

---

### Post by hajo9702 on 2008-08-17
Thank you very much! This solved my problem too!
Just remember to restart your Windows right after the driver is installed before scanning for new hardware.

---

### Post by reidi on 2008-09-28
> **jgombos said:**
> I've solved this problem.  See my post in this thread:

  [http://forums.virtualbox.org/viewtopic.php?p=28979](http://forums.virtualbox.org/viewtopic.php?p=28979)

Also, shared folders doesn't work, perhaps because TinyXP removed an essential component for that to work.  But you can create an ISO image containing that AMD driver, and mount it as a CDROM.
#####################

Ubuntu 8.04
VirtualBox 1.6.4

I'm successfully running TinyXP rev09, option 3, with both local network shares, and WAN connectivity.

I installed the VirtualBox 1.6.4 Guest Additions.

I downloaded the VMware Accelerated AMD PCNet Adapter driver ([http://www.downloadatoz.com/driver/item_239216.html](http://www.downloadatoz.com/driver/item_239216.html)), used USB stick to transfer to the TinyXP VM, and installed.

---

### Post by carl689 on 2008-11-04
Instead of using the USB method I just "burned" the drivers to a disc image.  Which is then easily mountable in VirtualBox


I Have attached the iso image (compressed), simply extract and mount in virtualbox

---

### Post by richardgc on 2009-03-17
> **carl689 said:**
> Instead of using the USB method I just "burned" the drivers to a disc image.  Which is then easily mountable in VirtualBox


I Have attached the iso image (compressed), simply extract and mount in virtualbox

Sir, you are a legend. Thanks very much for posting the iso here and helping solve my problem.

:KS

---

### Post by Kajikitsune on 2011-07-08
OMG thank you so much for this topic.. I spent about 6 hours trying to figure out my virtualbox and this helped me fix this darn driver... Now to try and get my other programs to work on it :D yay learning.

as a side note for any other newbie to pc/linux/virtualbox.. I still had to go in and "install" the drive for the NIC. Carl's iso worked like a charm!

---

### Post by javiervidal on 2012-03-09
Many thanks, it's worked great for me.

---

