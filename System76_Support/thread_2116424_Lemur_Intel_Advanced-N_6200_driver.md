---
title: "Lemur Intel Advanced-N 6200 driver"
date: 2013-02-15
forum: System76 Support
---

### Post by M4rotku on 2013-02-15
Hey guys,

I just got a new wireless card (see thread [here]("http://ubuntuforums.org/showthread.php?t=2112792") to read about the adventure).

The new card came and I installed it, but my wireless still doesn't work.  Now the wireless option doesn't appear at all, as though my card is not properly installed.  I ran the System76 Driver application, and the wireless still doesn't work.  I then found the driver via Intel's website and ensured that the System76 Driver application had put the driver in the right spot, which it had.  Do I need to do anything else to get the wireless card to work?  Am I missing a step?

Many thanks,
M4rotku

---

### Post by ccrs8 on 2013-02-16
There may be a physical button on the laptop or a alt+ key combination to turn on wireless.

---

### Post by M4rotku on 2013-02-16
There is, and I have tried activating it via the alt+f11 to no avail.  Furthermore, whenever it has been disabled by hardware switch in the past, it has said so under the wireless option on the nm-applet menu.  Now when I look in the menu, there is no mention of wireless at all.  There is neither a list of wireless networks nor an "Enable Wireless" option next to the usual "Enable Networking".  It is as though my wireless chip doesn't exist.  However, I used bluetooth last night, so that is working.  I was under the impression that they are the same chip.

---

### Post by M4rotku on 2013-02-17
Update:  The wireless card works fine with Windows 7, so it is not a hardware issue.  Was I supposed to rebuild my kernel after running the System76 Drivers program?  I saw a non-ubuntu website (maybe Gentoo) which talked about rebuilding the kernel to include the new drivers, but I assumed that it only said so because Gentoo always builds its own kernels.

---

### Post by screaminj3sus on 2013-02-17
You should not have to do anything to get intel wireless to work under ubuntu, the drivers are included in the kernel and work out of the box. my system76 has intel 6235 centrino wireless n and it works fine in every distro I've tried. Very odd if its not working. I have another laptop with intel 6250 that also works out of the box, and another one with an older intel 4xxx that works out of the box.

---

### Post by ccrs8 on 2013-02-18
Try booting off of the Ubuntu live CD that corresponds to the Ubuntu version you are using.  Wireless should work "out of the box" in that environment.  Assuming it does, then you've just verified that it is something with your particular Ubuntu setup and not Linux/Ubuntu in general.

---

### Post by M4rotku on 2013-02-19
I don't have a blank cd (I left them at home when I came to school), and my 1 gigabyte flashdrive seems to be too small to use as a live-cd.  Is there any other way that I could test this?  I'll try to ask around to see if I can acquire a blank cd.

---

### Post by ccrs8 on 2013-02-19
Hmm...I use my 1GB USB stick as a LiveCD all the time.  None of the image files are more than 800MB.  Are you using the startup disk creator that comes with Ubuntu?  You may need to format the stick first?

---

### Post by M4rotku on 2013-02-19
I was using the startup disk creator, and it consistently failed at 96%.  That's why I thought that there wasn't enough room, despite the fact that there should have been.  I will try formatting the stick.  It was a fat32, but I'll switch it to ext3 and try again.

---

### Post by M4rotku on 2013-02-22
Alright, I got around the bootable usb problem by adding an iso entry into my grub.  I booted from the latest 12.10 iso image, and the wireless still had the same problem.  So it seems to be something ubuntu-specific, as opposed to being specific to my personal ubuntu system.  I say that it is ubuntu-specific because Windows 7 can use the wireless card, and it is working very well.  Thus I am thinking that it is not a hardware issue.  At this point, I am rather stumped.  It can't be that ubuntu isn't able to use the chip in general, because my bluetooth works perfectly, and I thought that it was the same chip providing both.  Any advice is greatly appreciated.

Many thanks,
M4rotku

---

### Post by M4rotku on 2013-02-24
Update:  I used Network Tools to check my various network interfaces, and I don't seem to have a wireless interface at all.  I have the usual eth0 and lo0, along with the one for virtualization, but no wireless.

---

### Post by ccrs8 on 2013-02-24
Looks like someone with openSUSE is having the exact same problem:
[http://forums.opensuse.org/english/get-technical-help-here/wireless/476961-problems-intel-advanced-n-6200-wifi-card.html](http://forums.opensuse.org/english/get-technical-help-here/wireless/476961-problems-intel-advanced-n-6200-wifi-card.html)

And here is someone with the same problem with Ubuntu a few versions back:
[http://ubuntuforums.org/showthread.php?t=1408856](http://ubuntuforums.org/showthread.php?t=1408856)

I'm really not sure what to tell you personally - hopefully something in those threads give you an idea.  I have the 6250 and it worked right out of the box.

---

