---
title: "How well will Ubuntu 14.04 support x86 touch devices? Which will work well (Surface?)"
date: 2014-03-05
forum: Ubuntu Development Version
---

### Post by Nickolai_Leschov on 2014-03-05
I'm considering buying an x86 laptop/tablet for use with Ubuntu. Something between [MS Surface Pro 2 and Lenovo ThinkPad Yoga]("http://www.youtube.com/watch?v=-1UWFeBPwZM").

How well will touch devices like that be supported in Ubuntu 14.04?
There's a thread called [Will Ubuntu work on the Surface Pro 2 like it did on the original?]("http://ubuntuforums.org/showthread.php?t=2183946") (it can be made to work, though not "out of the box")
How much better can I expect 14.04 to be and in which areas: do necessary kernel mods and device drivers make it to 14.04? Does the interface and programs accommodate touch devices better? Though [full convergence may not come before 15.04]("http://news.softpedia.com/news/Mark-Shuttleworth-Says-Ubuntu-Will-Achieve-Full-Convergence-with-15-04-Before-Windows-412569.shtml"), Canonical is moving in the direction of better support for touch devices, right?

I'm using 13.10 32-bit on [ThinkPad X200]("http://www.thinkwiki.org/wiki/Category:X200") right now (8 GB RAM, SSD, with a docking station + monitor, keyboard and mouse at work).

Here's the thread for running Ubuntu on MS Surface Pro 2 specifically: **[Does it make sense to buy Surface Pro 2 for use solely with Ubuntu?]("http://ubuntuforums.org/showthread.php?t=2209247")**

---

### Post by grahammechanical on 2014-03-06
This thread may help you:

[http://ubuntuforums.org/showthread.php?t=2193327&highlight=thinkpad+yoga](http://ubuntuforums.org/showthread.php?t=2193327&highlight=thinkpad+yoga)

Now, I know that you are going to say that the thread is about 13.10 but on this section of the forum we find out things by installing and testing ourselves. So, unless one of us is already running Trusty Tahr on the Yoga, I advise to wait until 14.04 is released and then install it and see. 

Regards.

---

### Post by rifak on 2014-03-06
Seriously be careful with the Yoga's. I've gone through two of the newer one's and both have had the wireless card locked, with no way of unlocking. This was on both Ubuntu and Windows, so I'm pretty certain that they are having some serious hardware issues. I have an Asus Zenbook (with touchscreen) and I am currently running 14.04 with full touch support. I get multi-touch gestures and accurate touch calibration with the screen. The only thing that is slightly weird about the touch interface is that you can't do things like swipe/scroll without specifically using the scrollbars (at least from what I can tell). There may be some workarounds for this, but I'm not too concerned about touch interfaces anyways so it's no big deal for me.

---

### Post by Nickolai_Leschov on 2014-03-08
> [COLOR=#000000]Seriously be careful with the Yoga's. I've gone through two of the newer one's and both have had the wireless card locked[/COLOR]What do you mean by 'locked'?
As I understand, there is only one type of wireless adapter available on the [ThinkPad Yoga]("http://shop.lenovo.com/us/en/laptops/thinkpad/yoga-series/yoga/"), so I can't choose another one.

---

### Post by rifak on 2014-03-08
> **Nickolai_Leschov said:**
> What do you mean by 'locked'?
As I understand, there is only one type of wireless adapter available on the [ThinkPad Yoga]("http://shop.lenovo.com/us/en/laptops/thinkpad/yoga-series/yoga/"), so I can't choose another one.

By "locked", I'm referring to the actual hardware being completely locked from the OS. I know that a lot of the Lenovo Yoga laptops have had wifi issues (both connectivity and the OS switch not able to be toggled on-off) and the two that I've had both became unable to toggle on-off after booting into the BIOS. Also, it wasn't a BIOS setting or anything like that, the Wifi adapter was enabled in the BIOS. The first one that I had, I didn't even boot into Windows. Before even turning it on, I swapped out a fresh hard drive, booted straight to the BIOS to enable USB legacy boot, then installed Ubuntu. Once installed, there was absolutely no way to turn the wifi on. I then put the original hard drive in and setup Windows. Even after doing that, Windows was also unable to toggle the wifi, so I returned the laptop. On the second one, I booted it up, ran through the Windows setup, and wifi worked. I applied all the Windows updates, restarted a couple times, and everything was fine. Then, I booted into the BIOS, turned the USB legacy boot on, installed Ubuntu, then wifi was back to the toggle problem. I then re-installed Windows, and wifi was completely inaccessible. I then returned it again and opted for a completely different laptop (Asus Zenbook). I really think there is either a hardware issue where there is some locking/freezing mechanism that is problematic, or the BIOS has a serious bug in it that cuts off the wifi adapter after entering in. Do some google searches for Lenovo Yoga wireless/Lenovo Yoga wifi and you'll see all of the problems people have been having.

---

### Post by DrPotoroo on 2014-03-21
I am using a surface pro (version 1, rot 2) and testing the 14.04 builds. Touch and pen support is great out of the box until I connect an external monitor. Then the touch input spans both screens. I actually think that could be ok for the pen since you see a pointer ... but it is terrible for finger touch.

---

