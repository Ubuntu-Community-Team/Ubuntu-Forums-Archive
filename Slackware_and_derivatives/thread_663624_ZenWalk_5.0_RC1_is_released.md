---
title: "ZenWalk 5.0 RC1 is released"
date: 2008-01-10
forum: Slackware and derivatives
---

### Post by Antman on 2008-01-10
ZenWalk 5.0 RC1 is released. I am liking this version more and more as I try it out on my system. :guitar:

[http://www.zenwalk.org/modules/news/article.php?storyid=70]("http://www.zenwalk.org/modules/news/article.php?storyid=70")

---

### Post by DJiNN on 2008-01-11
Has anyone here tried the RC yet? Just curious about the differences between this & 4.8, and whether there's a big set of changes or not. 

I'll still D/L & give it a try though.... Zenwalk is nice after all. :)

---

### Post by Antman on 2008-01-11
So far I love the new Zenwalk. I tested it on my Desktop and two laptops. It works better with wireless then previous version and also now includes xorg 7.3.

Here is a description from the forum:
> Zenwalk 5.0 will be a major release, introducing several new systems. Firstly, version 5.0 is the first Zenwalk release to introduce the Freedesktop HAL system (Hardware Abstraction Layer). In the past Zenwalk had provided its own hardware hotplug system, but HAL has now been deemed mature enough to fit within Zenwalk's stability guidelines while giving unbelievable flexibility to hotplug and hardware detection in general.

Noticeable enhancements to Zenwalk found in version 5.0 are the numerous software updates including the latest Xorg 7.3 suite of X servers, drivers, fonts and other software packaged in a modular and easily manageable fashion. Other updates include the latest version of the Iceweasel web browser, the Icedove email client and hundreds more!

The modern and powerful Wicd wifi-browser and configure application replaces Wifi-radar, while the Intel' (TM) wireless device firmware is provided out of the box and is installed providing the user reads and accepts the Intel license, prompted at the end on the Zenwalk install process. This new licensing acceptance scheme allows users dependent on Non-FOSS drivers and firmware to fully support their hardware without need of searching as well as identifying Non-FOSS software for purists so that they may keep their system inline with their principles.

Following tradition Zenwalk's default desktop environment is XFCE and is now at version 4.4.2 sporting the legendary Zenwalk desktop layout with a completely new artwork design making Zenwalk 5.0 visually and functionally the most sober and elegant release to date.


Just note, if you have a 3945 wireless in your laptop, there is a workaround package that you'll have to install to get it to work. I couldn't get the default iwl3945 module to work. The ipw2200 wireless on my subnotebook worked like a charm however with no tinkering.

---

### Post by bonzodog on 2008-01-13
Yeah, zen 5.0 is nice. I did a clean zen core 4.8 install, then upgraded to /snapshot immediately, then installed the stuff I need from the snapshot repositories.
The only thing that appears to be broken so far is the attempt to package the nvidia drivers. That package really played up on me, so I removed it, and installed the drivers manually from nvidias site.

---

### Post by tommcd on 2008-01-15
> **DJiNN said:**
> Has anyone here tried the RC yet? Just curious about the differences between this & 4.8, and whether there's a big set of changes or not. 

I'll still D/L & give it a try though.... Zenwalk is nice after all. :)

I just put Zen 5 rc1 on my (intel based) Acer 3680 laptop. I had to boot the installer with <ata "acpi=off"> to get the installer to load. Without acpi=off it hung on enabling the IRQs. After that it installed fine, and I don't have to use acpi=off to boot with and all the hardware works. For laptops intel wireless firmware is now included, and wicd replaces wiif-radar as in Antman's post. Zenwalk continues it's tradition of using the latest packages and kernels, and remains light and fast. I will put Zen 5 on my desktop when it goes to final release.

---

### Post by K.Mandla on 2008-01-16
Shifted just a teeny bit to the Slackware subforum.

---

