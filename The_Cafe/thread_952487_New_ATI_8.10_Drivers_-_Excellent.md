---
title: "New ATI 8.10 Drivers - Excellent"
date: 2008-10-19
forum: The Cafe
---

### Post by Vince4Amy on 2008-10-19
I decided I'll have another go on one computer which I could not possibly switch to Linux because the ATI X1550 AGP card installed just didn't want to know when it came to Linux. All the past ATI releases could not work with this card however the new Driver works great and detects the card flawlessly.

---

### Post by handy on 2008-10-19
This is the oldest version in my /var/cache/pacman/pkg/ directory:

catalyst-8.3-2-x86_64.pkg.tar.gz

which I installed last March in Arch on an iMac, & I was shocked at the ease of installation.  I thought, after all of the bad things I'd read about ATi's drivers that I was going to be in for a hell of a fight, as I have had from time to time with nVidia's products.

The improvement is really noticeable with my GPU, DVD's played so badly that Arch on that machine was useless for playing DVD's.  The drivers have been improving & now play DVD's as good as my nVidia equiped machine.

Interestingly, the drivers under Leopard have always been & still are superior to those for Linux, but the gap is certainly closing.

I look forward to the day when I can play Guild Wars under Linux & it looks as good as it does under Leopard.

---

### Post by PartisanEntity on 2008-10-19
I'm looking forward to see how Ubuntu 8.10 functions on my wife's laptop because currently I am battling to get an ATI Radeon Xpress 1100 to stop lagging under 8.04 and it's no fun.

---

### Post by Vince4Amy on 2008-10-19
Yes installing the driver is so easy.

Download it
sudo sh drivername.run
Choose Automatic
sudo aticonfig --initial -f
Reboot

Easy.

---

### Post by Canis familiaris on 2008-10-19
Unfortunately Catalyst 8.10 had problems with WINE so I had to downgrade to Catalyst 8.9 (which IMO was a great version)

---

### Post by billgoldberg on 2008-10-19
> **PartisanEntity said:**
> I'm looking forward to see how Ubuntu 8.10 functions on my wife's laptop because currently I am battling to get an ATI Radeon Xpress 1100 to stop lagging under 8.04 and it's no fun.

I have the same card and the new drivers are much better.

---

### Post by Polygon on 2008-10-19
> **Vince4Amy said:**
> Yes installing the driver is so easy.

Download it
sudo sh drivername.run
Choose Automatic
sudo aticonfig --initial -f
Reboot

Easy.

not really...you do

sudo ./atidriverswhatever --buildpkg Ubuntu/hardy
<wait>
sudo dpkg -i *.deb
restart =)

---

### Post by snova on 2008-10-19
When everybody says "better", what are you referring to? Framerate? How much better?

---

### Post by Canis familiaris on 2008-10-19
> **snova said:**
> When everybody says "better", what are you referring to? Framerate? How much better?

bug fixes + faster frame rates + few enhancements to amdcccle + support for more cards
(these are mainly which I found for Catalyst 8.9, 8.10 is bad for me)

---

### Post by snova on 2008-10-19
Oh, good. Because on Windows I could get about 60 FPS on Stellarium but I haven't seen better than 20/30 since I switched. It's not too bad, though.

I just installed fglrx-control. Ahah! So that's what Catalyst is! That's helpful to know.

Now I should be able to download the new drivers from ati.amd.com and build a deb from them, right? That's what I'm trying.

---

### Post by Canis familiaris on 2008-10-19
> **snova said:**
> Oh, good. Because on Windows I could get about 60 FPS on Stellarium but I haven't seen better than 20/30 since I switched. It's not too bad, though.

I just installed fglrx-control. Ahah! So that's what Catalyst is! That's helpful to know.

Now I should be able to download the new drivers from ati.amd.com and build a deb from them, right? That's what I'm trying.

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by Vince4Amy on 2008-10-19
> sudo ./atidriverswhatever --buildpkg Ubuntu/hardy
<wait>
sudo dpkg -i *.deb
restart =)

To build the packages you need to install some dependences, you can install the ATI Driver using the automatic method with a clean 8.04.1 installation.

---

### Post by david_lynch on 2008-10-19
> **Vince4Amy said:**
> Yes installing the driver is so easy.

Download it
sudo sh drivername.run
Choose Automatic
sudo aticonfig --initial -f
Reboot

Easy.
Nah, no need to reboot - this is linux not windoze after all :lolflag:

Just reload X11 with CTL-ALT-BKSP or go to runlevel 1 and resume normally.

---

### Post by snova on 2008-10-19
Downloaded it, build the packages, and installed them.

I can't tell the difference, actually...

---

### Post by Vince4Amy on 2008-10-19
> Just reload X11 with CTL-ALT-BKSP or go to runlevel 1 and resume normally.

That works on OpenSUSE/Slackware but not Ubuntu.

Simply restarting X always results in a garbled display until I restart, this has never happened on OpenSUSE or Slackware.

---

### Post by Mazza558 on 2008-10-19
I swear fglrx is getting slower and slower. The free driver's overtaken it in terms of 2D rendering now.

---

### Post by handy on 2008-10-19
> **Mazza558 said:**
> I swear fglrx is getting slower and slower. The free driver's overtaken it in terms of 2D rendering now.

Perhaps that is so on your hardware.

---

### Post by Isilion on 2008-10-19
Hi ppl, sorry, but 8.10 ati driver isn working for me. more info at  this thread [http://ubuntuforums.org/showthread.php?t=766699](http://ubuntuforums.org/showthread.php?t=766699) .

---

### Post by kenbo on 2008-10-19
> **david_lynch said:**
> Nah, no need to reboot - this is linux not windoze after all :lolflag:

Just reload X11 with CTL-ALT-BKSP or go to runlevel 1 and resume normally.

Actually, Linux or no, rebooting DOES make a difference when it comes to installing ati/amd drivers.

---

### Post by Polygon on 2008-10-19
> **Vince4Amy said:**
> To build the packages you need to install some dependences, you can install the ATI Driver using the automatic method with a clean 8.04.1 installation.

...no you don't. I just did this on a clean 8.10 installation. I did not need to install any dependencies (or if it did, it installed it for me).

and its always better to use debs as they are much easier to remove and to upgrade.

---

### Post by eldragon on 2008-10-19
> **kenbo said:**
> Actually, Linux or no, rebooting DOES make a difference when it comes to installing ati/amd drivers.

yes, even if not being asked to reboot, getting DRI to work requires a reboot.

---

