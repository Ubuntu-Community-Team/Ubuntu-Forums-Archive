---
title: "1 hard drive 2 computers?"
date: 2008-02-10
forum: Windows
---

### Post by patrickaupperle on 2008-02-10
I have a hard drive (from my laptop) with windows xp on it. Could  I use this same hard drive in my desktop, or would there be problems?

---

### Post by Herman on 2008-02-10
If you're just going to use it as a data disk, you will probably have no problems.

EDIT: Does it contain Ubuntu as well, or only Windows XP? 
I don't know for Windows XP, but I know that you can do that with Ubuntu.

If you want to boot Ubuntu in it you would have some minor problems, but nothing that can't be solved with a little tinkering.

For one thing you would need to run [sudo dpkg-reconfigure xserver-xorg]("http://users.bigpond.net.au/hermanzone/p7.html") to make a new /etc/X11/xorg.conf file to get your operating system reconfigured for the different hardware. (Monitor, Keyboard, Mouse, etc).
That would take you a little time, maybe five or ten minutes the first time you boot.

There will be a backup of you old settings made automatically for you in /etc/X11/ with a number given to it, but you could also make your own backup as well. Try to remember to do this before you run sudo dpkg-reconfigure xserver-xorg,  ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_laptop
```Then you would be able to boot in recovery mode when you put the hard drive back in your laptop and do,
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_desktop 
``````
sudo cp /etc/X11/xorg.conf_laptop /etc/X11/xorg.conf
``` That will mean you can restore the laptop's xserver settings before booting with the hard drive in the laptop, and restore the desktop's xserver settings when the hard drive is plugged into the desktop.

Apart from than if there is already another hard disk or more in the desktop, you might just have to experiment with GRUB a little to get it to boot up for the first time, (presuming you want to boot it). The best way to experiment with GRUB is to use [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and then add the same commands to your /boot/grub/menu.lst file for future ease of booting.

Regards, Herman

---

### Post by zero-9376 on 2008-02-10
it would almost certainly not work and if it did windows would be very unstable. windows unlike linux does not detect and load modules/drivers at each boot but rather installs them on a more permanent basis, if you put the laptop drive in another system it will try to install drivers for that system possibly overwriting existing drivers and generally causing a big mess. Whats more windows will detect that its not running on the same hardware and you will be forced to re-activate it. All in all bad idea,

If you plug in your laptop drive with xp on it but DONT use it as the boot disk (boot from another windows/linux partition) then everything should be ok.

I interpretted "with windows xp' on it as meaning that you want to the desktop from that windows xp installation. Perhaps you could provide more info on the intended use?

---

### Post by Herman on 2008-02-11
Yeah and there would be legal reasons why you shouldn't do that with Windows XP too probably. :)

---

### Post by patrickaupperle on 2008-02-11
Yes I wanted to use the same harddrive to boot both. 
I  did not expect it to work, but thought i'd ask.

Thankyou all for the replies.

---

### Post by Bungo Pony on 2008-02-12
I can't see why you wouldn't be able to, unless you're connecting two computers to the same drive at the same time.

There are adapters that will let you plug a laptop hard drive into a normal PC's IDE cable. I own one.

The trouble I could see is the whole Windows Genuine Advantage not giving you the Genuine Advantage. In other words, you'll get nagged that you're using a pirated version of XP.

---

### Post by dca on 2008-02-12
However, you'll run into driver hell when the machine boots up and finds the chipset installed is for a laptop versus an aopen or other mobo.  Not to mention the CPU scaling and power settings versus sound/video/other drivers and what-not.  I'd bet a nickel you'll see a BSOD prior to the WinXP bootsplash...

---

### Post by patrickaupperle on 2008-02-12
I think I'd get to the boot splash, but not passed it. I'm not gonna try, though.

---

### Post by Bungo Pony on 2008-02-13
Although I haven't done it with WinXP, I've swapped hard drives in and out of various PCs and booted them up. It takes a while for Windows to detect all the new hardware.

However, I know WinXP handles drivers differently, so it may behave differently. Might be something for me to try out one day.

> **dca said:**
> However, you'll run into driver hell when the machine boots up and finds the chipset installed is for a laptop versus an aopen or other mobo.  Not to mention the CPU scaling and power settings versus sound/video/other drivers and what-not.  I'd bet a nickel you'll see a BSOD prior to the WinXP bootsplash...

---

