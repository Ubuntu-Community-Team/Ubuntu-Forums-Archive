---
title: "Best Linux distro for &quot;instant on&quot;"
date: 2011-08-12
forum: The Cafe
---

### Post by crashnburn_in on 2011-08-12
What is the best such option now? Instant on for Email, Calendar or Some quick document / reading / surfing / reference work?

---

### Post by Henkdroid on 2011-08-12
If you just want surfing email and can cope with online calendars you should look at [jolicloud](http://my.jolicloud.com/welcome), you can preview it in the browser and I think there is some form of wordprocessor.

---

### Post by BrokenKingpin on 2011-08-12
I second Tiny Core.

Lubuntu on my netbook boots in like 8 seconds (running on an SSD)... if you setup Ubuntu with only openbox and a web browser I bet you could shave a few seconds off that time.

---

### Post by jerenept on 2011-08-12
Suspend instead of shutting down. Instant-on!

---

### Post by gutterslob on 2011-08-12
[Slitaz]("http://slitaz.org/") with [FAST_Boot_X]("http://doc.slitaz.org/en:guides:boottime") enabled. Nothing I've tried is faster. It actually boots quicker than the actual instant-on excuse for an OS that came included with my Lenovo s10-2 netbook. Yup, it's that fast. 

If you want a big distro (as in big repos and stuff), do a minimal Debian netinstall in EXT4, then install a lightweight WM and your required apps, then run [SMXI]("http://smxi.org/") to clear out unwanted xorg libraries, then install [e4rat]("http://e4rat.sourceforge.net/") and follow the [instructions]("http://lifehacker.com/5790311/e4rat-cuts-your-linux-pcs-boot-time-in-half-with-a-few-simple-commands") (note: only works with ext4 on traditional HDDs .... DO NOT install if you're on a SSD). My [GRML]("http://daily.grml.org/") (Debian based, but a lot better, imho) installed on an old Pentium Dual Core 1.8GHz with 1GB ram and standard 7200rpm HDD boots from Grub to prompt in around 7 seconds, with another 2 seconds to launch ScrotWM or EvilWM. Apps load faster also since e4rat profiles and reallocates everything you run during the first 2 minutes of your first boot after the install (read the instructions). Also works with Arch Linux, and is much more reliable compared to Finit or Quick-init. In fact, the thing that will annoy you more will be the time it takes from the press of your power-button to the Grub screen (unless you've got a relatively new rig with a quick-loading UEFI).

There's also Crux or Gentoo if you have the time to spare, I guess.

---

### Post by ninjaaron on 2011-08-12
If you install one of the chromium OS builds, your computer will boot in about 5 seconds and wake up in... like... zero.


But then you have to use Chromium OS.  Jolicloud is nice. They make you think you can't get a lot of software on it, but it has apt-get and I think it uses the Ubuntu Universe repos along with it's own.  But yeah, it's fast.

All the DIY distros can be extremely fast.  They usually don't have as many daemons and start-up apps as the "desktop-on-a-stick" distros, and you can pair it with a lightweight DE and display manager to improve speed even more.  You actually don't even need a display manager.  It's faster just as fast or faster to start X from the console.  Gentoo is one of the fastest because you compile your own kernel at boot, so it's not loading zillions of drivers you don't need and detecting hardware.

It is possible to compile custom kernels for Ubuntu and any other distro, and that will always improve boot speed.  I think that is part of OSX and Chromebook's secret; the kernels are compiled with specific hardware in mind, and therefore boot more quickly.  If you are inclined to tinker and you really want the speed, you could give it a shot.

---

### Post by kaldor on 2011-08-12
> **jerenept said:**
> Suspend instead of shutting down. Instant-on!

Until yesterday, my laptop had a 14 day uptime with suspend. Fun.

---

### Post by manzdagratiano on 2011-08-13
It's called Ubuntu :). On a more serious note, Gentoo with a lightweight WM and no login manager is the fastest I have seen; for something that isn't as time consuming to set up, Arch with say, Openbox is very close too!

> **gutterslob said:**
> [Slitaz]("http://slitaz.org/") with [FAST_Boot_X]("http://doc.slitaz.org/en:guides:boottime") enabled. Nothing I've tried is faster. It actually boots quicker than the actual instant-on excuse for an OS that came included with my Lenovo s10-2 netbook. Yup, it's that fast. 

If you want a big distro (as in big repos and stuff), do a minimal Debian netinstall in EXT4, then install a lightweight WM and your required apps, then run [SMXI]("http://smxi.org/") to clear out unwanted xorg libraries, then install [e4rat]("http://e4rat.sourceforge.net/") and follow the [instructions]("http://lifehacker.com/5790311/e4rat-cuts-your-linux-pcs-boot-time-in-half-with-a-few-simple-commands") (note: only works with ext4 on traditional HDDs .... DO NOT install if you're on a SSD). My [GRML]("http://daily.grml.org/") (Debian based, but a lot better, imho) installed on an old Pentium Dual Core 1.8GHz with 1GB ram and standard 7200rpm HDD boots from Grub to prompt in around 7 seconds, with another 2 seconds to launch ScrotWM or EvilWM. Apps load faster also since e4rat profiles and reallocates everything you run during the first 2 minutes of your first boot after the install (read the instructions). Also works with Arch Linux, and is much more reliable compared to Finit or Quick-init. In fact, the thing that will annoy you more will be the time it takes from the press of your power-button to the Grub screen (unless you've got a relatively new rig with a quick-loading UEFI).

There's also Crux or Gentoo if you have the time to spare, I guess.

Is this THE gutterslob from the #! forums? If so, I welcome you here and hats off to you! I have never used #!, but I have trolled a few of your posts on there to get dzen2 and scrotwm up and running!

---

### Post by coolglobal on 2011-08-13
If you want to stick with Ubuntu try: [http://ubuntu-mdis.weebly.com/](http://ubuntu-mdis.weebly.com/)

You'll have add your own specific applications after the install that you require.
Lower the swappiness value and try prelink.

---

### Post by coolglobal on 2011-08-14
You can also change the boot order in BIOS, to boot from the hard disk first. On the assumption that the hard disk is where the installation resides.

Edit:
Another change that can be made to an Ubuntu MDIS install that may improve the boot speed.

Remove the Splash Screen

Edit: /etc/default/grub
Find the following line and remove 'quiet splash': GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
So the line is like this: GRUB_CMDLINE_LINUX_DEFAULT=""
Then run: sudo update-grub

There is also profile: [http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/](http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/)


[FONT=monospace]
[/FONT]

---

### Post by coolglobal on 2011-08-15
It just occurred to me, I better tell you my start up time.
With the above measures my system boots in 25 seconds.
The desktop environment is GNOME 2.
This computer has an ordinary chip, an Intel Core2 CPU E7500 @ 2.93GHz, and 3.2GiB of memory.
Booting into a box environment would provide an improvement.

---

