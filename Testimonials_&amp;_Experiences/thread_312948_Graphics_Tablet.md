---
title: "Graphics Tablet"
date: 2006-12-05
forum: Testimonials &amp; Experiences
---

### Post by Dragonbite on 2006-12-05
Just want to put a testimony about (k)Ubuntu and my Graphics Tablet. Most of the time when I plug the my tablet, an [Adesso Cybertablet 6400]("http://www.adesso.com/products_detail.asp?productid=236"), it would move the cursor as a mouse, not as a tablet.
[CENTER][IMG]http://www.adesso.com/images/CyberTablet%206400.jpg[/IMG][/CENTER]
"As a mouse" means if I put the pen to the tablet on the left side and move it to the right, the cursor moves to the right, then if I pick up the pen and put it down again on the left side and move right the cursor will move from where I left off.  The tablet should hop the cursor to the left side when I put the pen onto the left side, and hop to the right side if I put the pen onto the right side.

I was running Kubuntu via live-CD and wanted to see if my tablet is recognized.  I was surprised that it worked AS A TABLET! It lagged behind me and crashed once but I attribute that to running off the Live-CD.

So I rebooted into the installed Edubuntu and sure-enough the tablet worked as a tablet! Woo Hoo!

Unfortunately the tablet and screen are not quite the same, as in I reach the bottom of the tablet and I still have about 1/5th or less of the screen to go. I can take over at that point with my mouse if I need to. I was using GIMP at that time.

I did not see any pressure sensitivity effects in GIMP, but I do not know if I have GIMP configured for it properly either.

So I have pressure-sensitivity and screen-tablet sizing difference to look at but I am very pleased with the non-Wacom tablet being detected as such.

---

### Post by keith11 on 2007-02-17
Hi, it was nice to know about your tablet working without any extra configurations. I have an Adesso Cyberpad and I tried installing wizardpen drivers for it as both the tablets look the same. But it is not working. Did you go with the default "Wacom" settings in your xorg.conf or you made some changes? Would you please share if you know how to make an Adesso Cyberpad in Ubuntu Edgy? Thanks.

Keith.

---

### Post by seijuro on 2007-02-17
I have a Wacom that works flawlessly in (K)(X)(Ed)Ubuntu all you have to do is install the wacom tools from the repo then edit xorg.conf to reflect the correct device (in wacom's case after the utils are installed its /dev/input/wacom) and take out any lines not needed like since mine is usb I don't need the force device line for the tablet pc etc. then restart X. Once it is set up correctly not only do you get pressure effects but you can assign different tools to parts of the stylus etc while in gimp by going to file -> preferences -> Configure Extended Input Devices.

---

### Post by Brigrat on 2009-01-17
I also have a cyberpad that I use at work.  I plugged it into my stinkpad T42 running Ubuntu 8.1.  It recognized it right away.  I can browse the device and see the files but can not open it up.  What software out there will open that file extension.

---

### Post by solwic on 2009-01-17
> **Dragonbite said:**
> Just want to put a testimony about (k)Ubuntu and my Graphics Tablet. Most of the time when I plug the my tablet, an [Adesso Cybertablet 6400]("http://www.adesso.com/products_detail.asp?productid=236"), it would move the cursor as a mouse, not as a tablet.
[CENTER][IMG]http://www.adesso.com/images/CyberTablet%206400.jpg[/IMG][/CENTER]
"As a mouse" means if I put the pen to the tablet on the left side and move it to the right, the cursor moves to the right, then if I pick up the pen and put it down again on the left side and move right the cursor will move from where I left off.  The tablet should hop the cursor to the left side when I put the pen onto the left side, and hop to the right side if I put the pen onto the right side.

I was running Kubuntu via live-CD and wanted to see if my tablet is recognized.  I was surprised that it worked AS A TABLET! It lagged behind me and crashed once but I attribute that to running off the Live-CD.

So I rebooted into the installed Edubuntu and sure-enough the tablet worked as a tablet! Woo Hoo!

Unfortunately the tablet and screen are not quite the same, as in I reach the bottom of the tablet and I still have about 1/5th or less of the screen to go. I can take over at that point with my mouse if I need to. I was using GIMP at that time.

I did not see any pressure sensitivity effects in GIMP, but I do not know if I have GIMP configured for it properly either.

So I have pressure-sensitivity and screen-tablet sizing difference to look at but I am very pleased with the non-Wacom tablet being detected as such.

This has nothing to do with your post, but how'd you get your screen name in green?  

Wicked awesome.  :P

Sorry... I'm a really curious person.  If I were a cat, I'd have been dead a long time ago.  :P

---

### Post by Brigrat on 2009-01-17
Hey didn't know it wa in green...COOOL, must been all those days in the western pacific in my younger days LOL.  I saw some posts somewhere where they were able to use gimp to see the files, I guess I'll keep lookin.

---

### Post by Dragonbite on 2009-01-17
My name is green because I'm the moderator of a forum (CT-Loco forum)

Actually these post reminded me my thoughts on trying to use WINE with the tablet! Perfect timing because I'm doing a presentation on Wine this coming Wednesday so we'll see if it works.

What I'm going to do is run the setup.exe (or equivalent) from the CD using Wine.

Cross your fingers and I'll try this weekend!

---

### Post by wandalalakers on 2009-01-18
I have a Wacom too (Bamboo) that works perfectly.

---

### Post by russu52 on 2009-01-18
i have a nisis graphics tablet. on ibex i just plug and use - if i'm not mistaken i used it even on ubuntu 7.1 (forgot it's codename) as a live cd. worked well too.

---

### Post by Dragonbite on 2009-01-18
My hopes of Wine working were dashed (for now) because my system doesn't see anything on the CD! 

I took a look at the system again, with the tablet attached.

```
$ lsusb
Bus 004 Device 003: ID 04a5:6004 Acer Peripherals Inc. (now BenQ Corp.) 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
[B]Bus 002 Device 002: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
[/B]Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

So I started focusing on Aiptek APT-2 Tablet. In Synaptic I found xserver-xorg-input-aiptek which > X.Org X server -- Aiptek input driver
This package provides the driver for Aiptek HyperPen USB graphics tablets.


But even installing that hasn't made a difference.

There is mention of a kernel module, but that needs to be researched more.

---

### Post by alephnull42 on 2009-01-26
Hi,

I have a recent positive experience with the "Aiptek Slim Tablet 600U Premium II"

This thread [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) mentions that "The 600U seems to use Wacom drivers" and points at this thread [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

To get it to work:
- Use Ubuntu 8.10 (version 8.04 recognized it as a mouse, but could not get the Wacom drivers to run, and the tablet was not in proportional mooe)
- Install the wacom-tools_0.8.1.6 and xserver-xorg-input-wacom_0.8.1.6 divers as indicated in the Wacom thread above (I also tried the most recent drivers 8.2.0 but these did NOT work, so stick with 8.1.6.)
- Reboot/Restart X
- Plug tablet into USB - works fine in proportional mode

Byee

---

### Post by Dragonbite on 2009-01-26
> **alephnull42 said:**
> Hi,

I have a recent positive experience with the "Aiptek Slim Tablet 600U Premium II"

This thread [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) mentions that "The 600U seems to use Wacom drivers" and points at this thread [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

To get it to work:
- Use Ubuntu 8.10 (version 8.04 recognized it as a mouse, but could not get the Wacom drivers to run, and the tablet was not in proportional mooe)
- Install the wacom-tools_0.8.1.6 and xserver-xorg-input-wacom_0.8.1.6 divers as indicated in the Wacom thread above (I also tried the most recent drivers 8.2.0 but these did NOT work, so stick with 8.1.6.)
- Reboot/Restart X
- Plug tablet into USB - works fine in proportional mode

Byee

I'm going to have to try that.  Currently I don't have 8.10 running on anything so I may just install 8.10 on an old box and see if will work with my Adesso before killing myself with upgrading my current systems only to find this doesn't work (and possibly bork my existing installations).

---

### Post by minimala on 2009-09-10
Hello, I'm running 9.04 Jaunty amd64 on an Intel Pentium D 820 2.8GHz 945G PC. I'm a newbie in Ubuntu and Linux, but I slowly get better. I have it as my primary, and only for now, OS for two weeks now and I have got working printer and file sharing accross my network, joysticks and everything else but I can't install my Genius MousePen 8x6 Tablet. The $ lsusb command returns it as:
```

$ lsusb
Bus 001 Device 005: ID 04e8:341b Samsung Electronics Co., Ltd SCX-4200 Series
Bus 001 Device 004: ID 0dda:2001 Integrated Circuit Solution, Inc. Multi-Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 5543:0005 **UC-Logic Technology Corp. Genius MousePen 8x6 Tablet**
Bus 004 Device 003: ID 12bd:a02f  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```It's obviously found by the system, but every guide on how to install it ends for me on "Install wizardpen", because the .deb package provided is i386. I have the i386.deb package and the tar.gz. I don't know how to compile the tar.gz for amd64, and I don't even know if it is possible... Every time I can't find a program with synaptic or aptitude or apt-get and have to download it as a tar.gz or tar.bz2, I just do not install it, because I cannot understand how it is done. Can somebody help me, I'll appreciate :)

---

### Post by smkoberg on 2009-11-06
I've tried all of the above and still nothing.
I'm running 9.10 trying to use an Adesso Cyber Tablet 12000. 

$lsusb recognizes 
Bus 002 Device 002: ID 08ca:0010 Aiptek International, Inc. Tablet

---

### Post by johnaaronrose on 2009-11-13
Dragonbite,
I seem to have same tablet as you. lsusb gives:
[FONT=monospace][B]Bus 001 Device 010: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet

[COLOR=Black]All,
[/COLOR][/B][/FONT][FONT=monospace]**[COLOR=Black]Pen doesn't work as well as a mouse. [/COLOR]**[/FONT][FONT=monospace][B][COLOR=Black]I installed CellWriter & Dasher using Synaptic. However, CellWriter not usable with pen tough OK with mouse. I don't understand how to make Dasher work, even using mouse.

PS I don't understand why bold enabled & not able to disable it on this post   
[/COLOR][/B][/FONT]

---

