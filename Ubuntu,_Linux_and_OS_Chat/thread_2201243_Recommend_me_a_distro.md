---
title: "Recommend me a distro"
date: 2014-01-23
forum: Ubuntu, Linux and OS Chat
---

### Post by d.mayfair on 2014-01-23
that will work with NVidia sound as I'm having no joy with Xubuntu 13.10.

I will only be using it for video streaming

---

### Post by sudodus on 2014-01-23
Please describe your system with more details:

- computer brand name and model
- CPU
- RAM size
- graphics chip/card model (not only nvidia, because they are quite different)
- sound chip/card model (not only nvidia, because they are quite different)

and it will be easier to give you good and relevant advice :-)

---

### Post by d.mayfair on 2014-01-23
see my other thread here

[http://ubuntuforums.org/showthread.php?t=2200095](http://ubuntuforums.org/showthread.php?t=2200095)

---

### Post by lykwydchykyn on 2014-01-23
I doubt you're going to see significant difference in hardware support across distros; it's all down to the kernel.  Your best bet is probably going to be trying the newest kernel you can get your hands on.  Start with the kernel ppa here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download the kernel and kernel headers packages for your platform, install with software center, and reboot to the new kernel.  If it doesn't work, you can reboot back to the original kernel and remove the packages.

I'd recommend trying the 3.12-saucy kernel.

---

### Post by d.mayfair on 2014-01-23
> **lykwydchykyn said:**
> I doubt you're going to see significant difference in hardware support across distros; it's all down to the kernel.  Your best bet is probably going to be trying the newest kernel you can get your hands on.  Start with the kernel ppa here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Download the kernel and kernel headers packages for your platform, install with software center, and reboot to the new kernel.  If it doesn't work, you can reboot back to the original kernel and remove the packages.

I'd recommend trying the 3.12-saucy kernel.


I think I'd need more of a walk thru before I could do that,I'm a total novice when it come to Linux,I could do more harm than good lol

---

### Post by sudodus on 2014-01-23
It can take hours to test all combinations of settings in ***pavucontrol*** to finally find something that works.

You have Xubuntu 13.10 the currently newest version. Maybe the drivers of the next version that is being developed, [Trusty Tahr]("http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/61655/downloads"), to become 14.04 LTS, will work with your HDMI sound system. It is worth trying anyway, as well as Xubuntu 12.04 LTS.

You may be lucky with some other distro., but the Ubuntu based flavours, re-spins and distros are usually a good starting point. Try the most popular distros at this link [http://distrowatch.com/](http://distrowatch.com/). See the list at the right side of the page.

---

### Post by lykwydchykyn on 2014-01-23
Are you running 32bit or 64bit Xubuntu?

Hey, here's a good tutorial on kernel updating:

[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

Probably better than I could do for you.

---

### Post by d.mayfair on 2014-01-23
64 bit

---

### Post by sudodus on 2014-01-23
Then you can try the corresponding 32-bit version, that *might* have better drivers.

---

### Post by d.mayfair on 2014-01-23
Do you think I'd be better off with an older distro seeing as the computer is a few years old ?

---

### Post by sudodus on 2014-01-23
It depends on the nvidia chip/card. You can try both older and newer versions. That is why I suggested both 12.04 LTS and Trusty Tahr. Try them live (booted from CD/DVD/USB without installing).

Actually sound via HDMI is fairly new, so a newer version is at least as probable as an older one. But I also recommend that you try a lot with different settings in the menus of Pavucontrol in your current system.

You should also try several proprietary nvidia drivers.

---

### Post by d.mayfair on 2014-01-23
I'm just reading about Openelec + xbmc.
A guy installed that on the same machine as mine.That might be the way to go

---

### Post by lykwydchykyn on 2014-01-23
> **d.mayfair said:**
> Do you think I'd be better off with an older distro seeing as the computer is a few years old ?

Unless it's an antique, no; regressions or removals of drivers are pretty rare.

---

### Post by lykwydchykyn on 2014-01-23
> **d.mayfair said:**
> I'm just reading about Openelec + xbmc.
A guy installed that on the same machine as mine.That might be the way to go

Give it a shot; let us know what happens.

---

### Post by dbass81 on 2014-01-23
I'm using alsa instead of pulse audio.  I doubt it is the reason your sound card isn't working.  Always make sure your hardware is supported in the kernel before anything else.

---

### Post by d.mayfair on 2014-01-23
> **dbass81 said:**
> I'm using alsa instead of pulse audio.  I doubt it is the reason your sound card isn't working.  Always make sure your hardware is supported in the kernel before anything else.


How do I find that out ?

---

### Post by dbass81 on 2014-01-23
> **d.mayfair said:**
> How do I find that out ?

Open a terminal window and type "lspci |grep Audio" or just "lspci" and look for your Audio device.  Check what audio chipset your hardware is using.  There are websites like linux-drivers.org that are dedicated to listing supported Linux hardware.  If you are really hardcore you would download the latest kernel source from kernel.org, extract it, make menuconfig and look under Device Drivers -> Sound Card support.   Linux is really good about supporting older hardware, unless it is non-free hardware, then you need to download firmware for it like Realtek or Broadcom firmware.

---

### Post by d.mayfair on 2014-01-23
> **lykwydchykyn said:**
> Give it a shot; let us know what happens.

It's a non starter,it won't let me do a live install or install alongside my existing o/s and I'm not prepared to delete xp at this stage.

---

### Post by d.mayfair on 2014-01-24
Folks,I've sorted my sound issue so no need for another distro now.
Just need to get my dvd drive to work but that can wait for another thread lol
Cheers

---

### Post by dbass81 on 2014-01-24
> **d.mayfair said:**
> Folks,I've sorted my sound issue so no need for another distro now.
Just need to get my dvd drive to work but that can wait for another thread lol
Cheers

Can I ask what the problem/solution was to fixing your sound issue?

---

### Post by d.mayfair on 2014-01-24
It was the simplest of things.I'd tried an optical cable but no joy.However I'd already ordered another one off ebay (£1.20 inc postage so I wasn't expecting much ),anyway it arrived today,connected it up and lo and behold it worked,just like that.
Funny thing is the original cable works on another device....albeit with the odd crackle and pop.I might look at replacing that one now.

---

