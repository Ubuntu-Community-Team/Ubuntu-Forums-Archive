---
title: "Some tips"
date: 2007-12-17
forum: System76 Support
---

### Post by system77 on 2007-12-17
hi,
In general I'm talking here for Pangolin.

The tip is :
Do you know that you can use :

-two fingers touch on touchpad to simulate middle click ( in FF open the link in a new tab)
- three finger touch - right mouse click
- scrolling at the right edge of the touchpad with a finger DOES scrolling

For anyone who does not use Ubuntu or wants to know how some of the stuff work underneath :

1. If you want to have SD/MMC support add this to your local start script add 
something like this :

 device=`lspci -mm -d 1180:0832 | cut -f1 -d' '`
 setpci -s "$device" 0xCA=0x57
 setpci -s "$device" 0xCB=0x02
 setpci -s "$device" 0xCA=0x00

2. For sound support :
- compile kernel only with "Sound support", no ALSA or OSS. Then install the latest alsa-1.0.15, with drivers for snd_intel_hda

On Gentoo : add in make.conf
ALSA_CARDS="hda-intel"
and then
ACCEPT_KEYWORDS=~x86 emerge alsa-driver alsa-lib alsa-tools -av

3. For the wireless in Gentoo you need to emerge :
  emerge ipw3945 ipw3945-ucode ipw3945d -av
There is some new drivers in the new kernels iwli or some such, havent 
tested with them.
Of course you will need also support for WEP ..etc..but you can find them in kernel config.
In general it is good idea to install in your distro if you have NetwokManager package, I had some glitches but now handles the network config pretty well.
(The worst thing is that now you loose some low-level functionality i.e. you depend on something which has almost no way to influence. Some configuration can be found in g-conf)

4. I wasn't able to successfully make 2.6.23-gentoo-sources work with all these, YMMV. I used sabayon 2.6.22 kernel. 

In general when you try to change the distro be sure to save for reference 
somewhere :
  lsmod > lsmod.txt
  dmesg > dmesg.txt
  /etc/X11/xorg.conf
  gunzip -c /proc/config.gz > kernel_config.txt

5. gsynaptics does not work for configuration of touchpad (already was mentioned in some thread), so you will have to do manual changes in xorg.conf.
(currently i'm trying to make the touchpad less sensitive on touch, otherwise clicks happens all over the place ;))


You may put this in the wiki.

---

### Post by vkurup on 2007-12-17
I did not know the 2 and 3 finger tricks. Thanks!

---

### Post by palintheus on 2007-12-17
The 2/3 finger clicks also work on the daru2.

---

### Post by tedrampart on 2007-12-18
excellent find on the finger clicks.. was getting a bit sick of my macbook fanboy friend rubbing that in my face as a "macs are cooler cause of this" discussion......and its handy..

works on my gazp3!! going to use it from now on.

---

