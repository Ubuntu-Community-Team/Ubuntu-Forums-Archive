---
title: "Problem seting up GRUB in proper MBR"
date: 2015-06-17
forum: Ubuntu/Debian BASED
---

### Post by Richardo_Petri on 2015-06-17
Hey guys!

I'm a returning Linux user who have been away a couple of years.

I'm attemting to install a Ubuntu distro [Jessbuntu]("http://sourceforge.net/projects/jessbuntu64/") on a laptop (Amilo Si3655). But after installing i can not Boot into the OS.

This is teh steps I've taken.

1. Download Jessbuntu64.iso
2.Used Rufus to put it on a USB
3. Booted into the USB and Did a clean Install on the Amilo Laptop.
4.Removed the USB after install at witch point I got the Error message "Operating system not found"
5. Boot up with the Live-USB and do the apt-get for boot-repair with no succes. 
6.Reinstalled Jessubuntu, no succes, installed the Elemntary Dist, still not loading Grub in MBR.
7. went back to jessbuntu, Messed around wit boot repair several times using anything i could think of.
8. Made the boot repair print out the error log [http://paste.ubuntu.com/11733744/](http://paste.ubuntu.com/11733744/)

So now I'm calling on the great gurus of Ubuntu forums, why isent my OS booting, where and how should i place GRUB, or should i switch to some other bootloader?


So n

---

### Post by ubfan1 on 2015-06-18
Nothing looks bad.  Since you have only one OS on the hard disk, grub does not display unless you hold down the shift key as it boots.  If you can get grub, try some  commands (enter command mode with c), like set root=(hd  then TAB to get the completion of the expected 0, continue with ,TAB to get choices of partition msdos1)/ TAB to see if what you see are the expected root files.  Why choose such an old release, 12.04.5 would be the expected 12 release to use(or maybe even later, I don't keep up with the 12 point releases).

---

### Post by Richardo_Petri on 2015-06-19
I tried holding down shift when booting but I do not get acces to Grub.

I can enter Grub with the USB and try to boot from HDD but that does not work even though the files are installed in the hd. I have the same files on the HDD as on the USB. I can boot into the USB but not into the HDD.

---

### Post by grahammechanical on 2015-06-19
Have you set the BIOS/UEFI boot system to boot from the hard disk and not a USB port? USB memory sticks with an OS on them are often seen by the motherboard as an external USB drive. Remove the USB stick and the motherboard comes up with "operating system not found" because it is looking for a USB external drive which is no longer there.

Regards.

---

### Post by oldfred on 2015-06-19
Moved to Other OS.

You show grub installed to MBR.

But is this a newer system with UEFI, as you have installed in BIOS boot mode. So you must set UEFI/CSM to boot in BIOS mode from hard drive. 
Check your UEFI/BIOS settings.

---

