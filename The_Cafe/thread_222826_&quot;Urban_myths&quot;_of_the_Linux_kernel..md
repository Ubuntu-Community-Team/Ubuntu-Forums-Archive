---
title: "&quot;Urban myths&quot; of the Linux kernel."
date: 2006-07-25
forum: The Cafe
---

### Post by Virogenesis on 2006-07-25
I thought I'd share with you a fantastic, well written article about the linux kernel it covers alot and provides wonderful insight into the kernel.
Have a read 

[http://www.kroah.com/log/linux/ols_2006_keynote.html](http://www.kroah.com/log/linux/ols_2006_keynote.html)

---

### Post by aysiu on 2006-07-25
I have a bit of an issue with this whole idea of the Linux kernel having better hardware support. While factually true, this remark is also practically irrelevant to most desktop end-users, for two major reasons:

1. Most architectures Windows users don't care about. Do they care if Windows works on SPARC or PPC? Not really.

2. For devices Windows doesn't natively support, the device manufacturer will provide drivers for so that it will work in Windows.

Dell won't sell you a Windows computer without having installed and tested all the necessary drivers and utilities that will make your computer usable. They wouldn't just give you a vanilla Windows installation.

Likewise, Mac OS X needs to support only Mac computers (Intel or PowerPC--whatever they happen to be on at the moment). It doesn't have to support others. If you want peripherals for your Mac... you go to the Apple store.

If you want peripherals for your Ubuntu computer... where's the Linux store?

The real issue at hand is not the sheer number of devices, processors, and architectures an operating system has native support for.

What we need are clearly labeled products (for example, a Tux icon next to the wavy, colorful Windows icon or the square blue face chopped in half vertically) and preinstallation (for example System 76).

---

### Post by bonzodog on 2006-07-25
Just to say, as of 20:00 hrs UTC, the site has been Dugg, so is difficult to get to.

---

### Post by Engnome on 2006-07-25
> **aysiu said:**
> I have a bit of an issue with this whole idea of the Linux kernel having better hardware support. While factually true, this remark is also practically irrelevant to most desktop end-users, for two major reasons:

1. Most architectures Windows users don't care about. Do they care if Windows works on SPARC or PPC? Not really.

2. For devices Windows doesn't natively support, the device manufacturer will provide drivers for so that it will work in Windows.

Dell won't sell you a Windows computer without having installed and tested all the necessary drivers and utilities that will make your computer usable. They wouldn't just give you a vanilla Windows installation.

Likewise, Mac OS X needs to support only Mac computers (Intel or PowerPC--whatever they happen to be on at the moment). It doesn't have to support others. If you want peripherals for your Mac... you go to the Apple store.

If you want peripherals for your Ubuntu computer... where's the Linux store?

The real issue at hand is not the sheer number of devices, processors, and architectures an operating system has native support for.

What we need are clearly labeled products (for example, a Tux icon next to the wavy, colorful Windows icon or the square blue face chopped in half vertically) and preinstallation (for example System 76).

Linux support more out of the box, you boot it up and your hardware works (personal experience based on 4-6 computers) but with windows you have to hunt around the whole internet (often with another computer as your network card is not recognised) looking for the right driver.

---

### Post by aysiu on 2006-07-25
> **Engnome said:**
> Linux support more out of the box, you boot it up and your hardware works (personal experience based on 4-6 computers) but with windows you have to hunt around the whole internet (often with another computer as your network card is not recognised) looking for the right driver.
Yes, I know that.

I've installed Windows from scratch myself twice--and both times were nightmares trying to track down those drivers.

But from the perspective of a Windows user who does not install Windows (i.e., *most* Windows users) installation and native hardware support are non-issues.

Windows comes preinstalled and with all the drivers. Most hardware they will buy for their Windows systems will be Windows-compatible and include the necessary drivers on a CD.

---

### Post by prizrak on 2006-07-25
> **Engnome said:**
> Linux support more out of the box, you boot it up and your hardware works (personal experience based on 4-6 computers) but with windows you have to hunt around the whole internet (often with another computer as your network card is not recognised) looking for the right driver.

Very true, and I also agree with aysiu. I would like to point something else out though. While in Windows there is a need to hunt for drivers there is an extremely easy way to install them and in 99% of the cases the drivers are readily available (yes in some cases the company went bust and the latest driver is for 9x that won't work but it's pretty rare). In Linux the OOTB support is excellent I have yet to need to install a driver for anything other than my printer. However if the distro didn't detect your hardware the driver might not be easily (if at all) found and will NOT be easily installed in 90% of the cases. Installing the printer driver took me at least an hour and I happen to be IT/Programmer by trade as well as an experience Linux user. 

I also think that generally speaking when people say "Hardware Support" they really mean "peripheral support" for the most part Linux recognizes all the devices inside a computer and will work with them. In some cases it wouldn't support full functionality but at least they will work. Peripherals are a bit trickier, for instance Ubuntu refuses to recognize the "fn" key on my new laptop as a modifier key. I know that there is a program that allows you to get keycodes for all your keys and assign them as a shortcut/modifier but it's much more involved than installing the Acer driver.

---

### Post by aysiu on 2006-07-25
Basically, from an end-user's perspective:

Linux: "I need to install this myself. Most of the time it will automatically detect stuff. If it doesn't... I'm screwed."

Windows: "I don't need to install this myself. Thanks, Dell, for doing that for me. Thanks, Dell, for including the drivers and utilities, too. Thanks HP for including the printer drivers with the printer I just bought.'

In rare cases (like mine) for Windows: "Looks like I'm going to be installing Windows on this computer. What are these parts? Do I have to open up the machine to see what drivers I need? What do all these yellow question marks mean? How do I find this driver? Do I want to download it from this sketchy site?"

In rare cases (like Fuscia's) for Ubuntu: "I bought this from System 76. Thanks for having it just work. Hm. This media card reader doesn't work. That's okay. Everything else is cool."

---

### Post by H.E. Pennypacker on 2006-07-25
> However if the distro didn't detect your hardware the driver might not be easily (if at all) found and will NOT be easily installed in 90% of the cases. Installing the printer driver took me at least an hour and I happen to be IT/Programmer by trade as well as an experience Linux user. 

I had to install drivers for a fairly well known printer, and just doing that meant messing around with configuration files, doing something in the terminal, and doing a few other things.  In Windows, I'd run an installer, and it would do the work.  Now, keep in mind that the printer manufacturer actually released a Linux driver, but the installation part was still difficult.  There was no automated installation process that required clicks.  I actually had to get my hands dirty, something most people wouldn't tolerate.

I really wish Linux, when needed, would have an automated system for installing stuff like drivers.  Unfortunately, you have to open and edit files you've never heard of, not even knowing what those files are used for.  If you're like me, you're just following instructions someone else provided without knowing what those instructions entail.

> Windows: "I don't need to install this myself. Thanks, Dell, for doing that for me. Thanks, Dell, for including the drivers and utilities, too. Thanks HP for including the printer drivers with the printer I just bought.'

This is something I didn't take into account until reading your posts.  I didn't stop to think why everything was so simple with Windows: it was pre-installed, and all work was taken care of.  This unfair comparison to Linux distributions makes Windows look better, when it is not necessarily better at all!  I then started thinking about all the horror I faced installing Windows from scratch myself.  It was obvious the solution lied in your computer manufacturer pre-installing everything.

---

### Post by Engnome on 2006-07-25
> **aysiu said:**
> 
Windows: "I don't need to install this myself. Thanks, Dell, for doing that for me. Thanks, Dell, for including the drivers and utilities, too. Thanks HP for including the printer drivers with the printer I just bought.'

And including tons of bloatware so I have to reinstall anyway :mad: 

> 
In rare cases (like mine) for Windows: "Looks like I'm going to be installing Windows on this computer. What are these parts?

Had to do that yesterday on a computer, _nothing_ worked out of the box and the included drivers were not there/outdated.

Btw the last picture in that site is nice ;) Bug nr1 is on it's way to be handled.

ps. thx for the tip Virogenesis, great site.

---

