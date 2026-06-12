---
title: "Will my Win 7 serial become invalid if I accept Win 10 upgrade?"
date: 2015-08-13
forum: Windows
---

### Post by Neko_no_Nya on 2015-08-13
This might be a stupid question but I'm not sure how this works. I'm currently dual booting Windows 7 and Ubuntu 14.04. If I upgrade to Windows 10 using the free upgrade option, will I be able to install Windows 7 using my serial number or will that number now be associated with my Windows 10 install? I'd like to be able to install Windows 7 in a virtual machine if I take this...

---

### Post by Dreamer Fithp Apprentice on 2015-08-13
I'm surprised MS offers a free upgrade option to W-10 from W-7. That seems almost too good to be true. I'd drop their tech support an email and ask them to clarify this. That said, you may not get an accurate reply. MS is notorious for tech support people reading a cookbook of answers they don't understand themselves. I suspect that if you reinstall W-7 your serial number will work just fine, but I could be wrong. You might want to use Clonezilla to backup the W-7 system before you try the upgrade. Restoring it from the Clonezilla image to your hard drive will be easier than reinstalling (even assuming you have installation disks) if you don't like W-10. Or your machine may have a built in rollback procedure. Even so, having a Clonezilla backup image won't hurt. You could also use Clonezilla to install the W-7 image to a virtual machine and that might be the easiest way to do it. I suspect that would be a license violation if you didn't delete the installation on the hard drive before doing it, because having both would constitute having 2 Windows systems on one license, but I'm no lawyer. Technically, I suspect you could run a clone of your W-7 system on a VM under Ubuntu with no problem. There might be a problem updating it and keeping it secure. Legally, I suspect MS's position would be that a VM version counts as a second installation and requires a second license. This isn't an issue of having both 7 and 10 - it's an issue of having 2 Windows systems. You CAN set up a VM running under Ubuntu to boot from your actual Windows partion and I'm pretty sure (again, I'm no lawyer) that's NOT a license violation, but it is technically tricky and don't expect MS tech support to even understand your questions if you try. But that's not really your question. I suspect you can't LEGALLY have both a W-7 and a W-10 system based on the same license (which in practice means serial number) because that would constitute having 2 Windows systems on one license - the fact that one is virtual probably makes no difference, nor would the fact they are different editions. And of course I wouldn't advise you to attempt anything illegal. So you'll probably need to buy a second license if you wanted to do this. But I doubt they'd fault you for trying 10, reaching the conclusion it sucked more than 7 (which it does), and switching back. You could ask them for clarification on that. But I emphasize: Clonezilla is your friend.

---

### Post by Frogs Hair on 2015-08-13
> or will that number now be associated with my Windows 10  The win 10 activation code on my desktop is different than the code assigned to a Win 7 disk that I purchased. In the case of my laptop, the factory recovery partition remained in tact and have rolled back anyway which is possible for 30 days after upgrade . 

As for downloading a 7 ISO and using the code to activate as a legal disk the MS community  forum might be a better place to ask.

---

### Post by buzzingrobot on 2015-08-16
Pretty sure that when you do an upgrade to Win10, the activation transfers to that Windows 10 installation. You cannot apply a single activation to two separate installs. You do have 30 days after an upgrade to rollback to 7/8.1.

---

### Post by bashiergui on 2015-08-16
It also depends on the type of Win 7 license you have. If it's OEM then you won't be able to virtualize it at all. If you have the installation discs then I recommend trying to virtualize it now & see what happens.

---

### Post by jerrylamos on 2015-08-22
As part of Win 10 preview I had Win 10 installed in a separate partition created by ubuntu gparted.

After dual booting Win 7 and Win 10 a few times I couldn't see why I'd ever want to run Win 7.

So I upgraded the Win 7 to Win 10.  Kept all my data, files, applications, etc.  and for my tastes runs better than Win 7 but not ubuntu.

I run ubuntu from a usb SSD hard drive and dual boot the two Win 10's from the internal hard drive.  The Win 10 preview updated to Win 10 enterprise, and the Win 7 home updated to win 10 home.

After I run Win 10, the bios boot sequence gets screwed up so I have to do F1 or F12 or whatever to get the usb ubuntu to boot first.  An annoyance, but since I'm usually running ubuntu no big deal.

In past I've had "grub" royally screw up the internal hard drive so I don't let grub do anything to the internal hard drive.  Grub can play around with the usb drive and if grub screws up I have backups.

---

