---
title: "The only thing that keeps me away from Linux"
date: 2010-07-09
forum: Testimonials &amp; Experiences
---

### Post by MadCookie on 2010-07-09
Hi!

In November I bought a new laptop, and sold mt desktop. In the beginning there was no support for my sound card, and poor graphics support, but the support was added in later Linux kernel. I could finally start testing Linux, but because of school I had little time, and I had to have some software that ran poorly in Wine.

But now, as school is over I have been able to try some different things. I tried hackintosh, but I could not get sound or graphics card working, and i tried several Linux distributions to see which one that worked best. The only distro that worked well enough for be was Ubuntu (10.04 or later), and of cource Ubuntu forks :P

Now there is only one issue I have, that keeps me from using it as my main OS. Battery life! In Windows 7 I can push my battery life to about 3 hours 50min, but with default sittings it lives for about 3 hours. In Ubuntu my laptop runs  2 hours...

I don't know if it is related, but when I run Linux my fan goes wild, and my processor gets very hot. After a short time it gets up to about 80 C.
Actually the way my computer behaves when i run Ubuntu is about the same as it behaves when I am playing CoD MW2 in 720p with craphics settings set to normal, except i get about 1h 30min on battery when I play CoD, and 2h in Ubuntu when doing nothing! I find that pretty insane!

---

### Post by mikewhatever on 2010-07-09
What happens if you turn off desktop effects? What process uses cpu the most? Take a look at the System Monitor to find out.

---

### Post by Jazzy_Jeff on 2010-07-10
> **mikewhatever said:**
> What happens if you turn off desktop effects? What process uses cpu the most? Take a look at the System Monitor to find out.

+1 on this. I turned it off on my laptop and had a lot more battery life.

---

### Post by simosx on 2010-07-10
Most probably there is an issue with your BIOS that causes the heating in Ubuntu.
Specifically, the first thing I would check is if there is any BIOS update from Dell.
Then, I would google for 'UBuntu DSDT' which will bring you to the Ubuntu Forums DSDT discussion; the DSDT is part of the BIOS and describes your hardware so that the operating system can do powersaving properly. In many cases the DSDT is messy and Linux is not able to use it, hence the high temperature.

Another possibility is that the Radeon driver you have installed does not have good power saving features for Linux yet. There are two options; the open-source driver and the proprietary ATI driver. Investigate which has the issues and give a try for one or the other.

---

### Post by digitalcitizenx on 2010-07-18
There is an application called powertop that could help you find more ways to save your battery power.

There is a discussion on it somewhere, but can't seem to find it.

That may help you save battery power. In the discussion many of the posters say it is adding run time on battery power.

Here's something:

[http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/](http://ubuntu-tutorials.com/2008/06/19/extend-your-battery-life-with-powertop/)

---

### Post by Hman242 on 2010-07-18
Ubuntu does use more power compared to Windows unfortunately. As a simple way to increase battery life I would set the power preferences to use the least power, turn the display brightness down, and then turn off desktop effects.

---

### Post by Doobie9 on 2010-07-22
You could try Jupiter: [http://sourceforge.net/projects/jupiter/](http://sourceforge.net/projects/jupiter/)

Even though it's for Aurora, it works perfectly on my Eee 1000 (running Mint/Ubuntu). My battery life with WiFi on went from five hours up to six. Without Wifi I can get around eight hours (for use for reading, or to shut-off periodically between loading websites when I'm surfing for the long haul). This is with Compiz enabled, btw. 

This computer does have the SuperHybridEngine, so your mileage may vary even though it is supposed to work on all laptops. I used powertop in conjunction with jupiter to verify its efficacy. Before I could get the power use only down to about 8 watts (with WiFi) and now it gets ~7 watts. Without WiFi it's in the range of 6 watts.

This computer came with Linux, and it always sort of frustrated me to know that decent power management (the included Xandros got similar battery life) was possible on Linux but not with a Super-Awesome-New-Linux. I'm not frustrated anymore, and now I'm quite proud of my Linux 100% netbook. And by that I mean that everything works completely without a single snag 100% hardware-wise (except for the software problems I introduce by experimenting all the time with it).

Sorry for kind of going on a tangent there.

---

