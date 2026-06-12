---
title: "Auto Boot Flash Drive"
date: 2015-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by TheNightingale on 2015-08-20
Ok I've been searching the internet for about a week now, and I can't seam to find a solution. Pretty much what I am looking to do is to make a USB flash drive that when plugged into any pc, will restart the system, and auto boot into Ubuntu installed on the flash drive, without the user having to do anything at all except plug in the flash drive itself. The complicated part, which I can not find a solution to, is how to bypass the need for the user to manually change bios settings to allow booting from a flash drive.

---

### Post by grahammechanical on 2015-08-20
Do you want to also be able to by-pass any BIOS password protection?

What legitimate reason would anyone have for wanting to be able to this?

---

### Post by Bucky Ball on 2015-08-20
*Thread moved to **Ubuntu, Linux and OS Chat**.*

> **grahammechanical said:**
> 

What legitimate reason would anyone have for wanting to be able to this?

+1. Please explain what it is you're intending to implement. Helping you create a USB you can plug in to any computer that will over-ride the BIOS and boot itself is not something we would ordinarily do here.

---

### Post by ajgreeny on 2015-08-20
> **Bucky Ball said:**
> *Thread moved to **Ubuntu, Linux and OS Chat**.*



+1. Please explain what it is you're intending to implement. Helping you create a USB you can plug in to any computer that will over-ride the BIOS and boot itself is not something we would ordinarily do here.
And I very much doubt if it is even possible!

The BIOS (or UEFI if a more recent machine) runs before anything else, and boot device priority is set by that, not by what OS happens to be available on a disk of any sort that is attached to the computer.

---

### Post by Bucky Ball on 2015-08-20
> **ajgreeny said:**
> And I very much doubt if it is even possible!



I'll second that!

---

### Post by TheNightingale on 2015-08-20
I want it just for easy of use so I can plug it into any computer I have access to without always having to mess around in the BIOS. Pretty much to keep my friends and family from freaking out if I want to use my stuff on their pc.

---

### Post by VMC on 2015-08-20
You don't have to bypass the BIOS to accomplish that. Just boot the ubuntu usb drive. The BIOS shouldn't come into play.

---

### Post by TheNightingale on 2015-08-20
When I tired using it on my PC, I have an auto run program that restarts the computer then it just reopens windows, unless I hit f9 and chose to boot from the thumb drive under the bootable devices tab of the BIOS. What did I do wrong that I have to hit f9 and chose it?

---

### Post by TheNightingale on 2015-08-20
Unless I change the priority of my BIOS to boot from USB first instead of the C drive, which I don't want to do to other peoples computers.

---

### Post by Bucky Ball on 2015-08-20
Then you could just hit F9, it is often F12, or find out what the boot device menu key is for their machine. The general consensus appears to be that overriding the BIOS with your USB so when you boot the machine it automatically boots to USB, regardless of how the BIOS is set, is not possible.

---

### Post by QIII on 2015-08-20
Closed for Staff review.

---

### Post by QIII on 2015-08-20
The appropriate solution is to ask permission of the owners of the machines to use them and to ask the owners to make necessary changes to the BIOS/UEFI to allow booting from USB.  You may discuss with the owners their concerns with regard to safety, security and possible effect on the installed OS when booting Ubuntu in that manner.

Whether or not this can be done as you have presented is certainly an interesting academic and technical query.  However, a technical solution to modifying the BIOS/UEFI on plugging in a USB would, in effect, be a technical solution to hacking the BIOS/UEFI.  While one of the major BIOS/UEFI creators might be able to provide support with this, we cannot.   

The potential undesirable ramifications of providing technical support for such a hack publicly on the Ubuntu Forums are manifold.  Whatever your intent, we will not allow the provision of a ready technical solution to those who may choose to use that information to gain illicit, illegal or surreptitious access to private, public, corporate or official machines.  Disabling USB booting is often a first line defense against such unauthorized access.

This thread will remain closed.

---

