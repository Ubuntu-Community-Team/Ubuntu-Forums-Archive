---
title: "Stability: 810 Rock-Solid, 904, 910 unreliable.  Why?"
date: 2009-11-14
forum: Testimonials &amp; Experiences
---

### Post by rnsc on 2009-11-14
I would appreciate any general comments.  Details are below, but I find 810 to be rock-solid, 904 to be unreliable, 910 to not be usable at all.  So I reloaded 810 again.  This is a troubling trend.

I moved from Suse to 810 and found it to be rock-solid for the last 10 months.  As I tried to upgrade to 904, both as an upgrade, then twice as a clean install, I kept getting mdadm segmentation faults.  I went back to 810 and the same hardware has been rock solid again.

I recently tried 910 and did not fare as well.  It crashes very quickly, and hard.  The X system simply hangs.  Sometimes as the "cylon" is going during boot, sometimes after boot, once with a scrambled display, but always requiring the power button to recover.  I never got it to run long enough to create a second account.  I installed it a few days ago, then looked at it harder this morning.  Two new clean installs, many reboots.  Can't make it go.

I did a clean install of 810 and it has been running for 5 hours - easily 30-40 times longer than it would run 910 before crashing.

This is on TWO sets of hardware:

Asus P3B-F Intel 440Bx With 800MHz P3 with 750MB ECC SDRAM and an nVidea 5200, been running for geez 8 years or more reliably.  And it is now reliable again with 810 (again).

Asus P4C800-E Intel 875 with a 2.8GHz Prescott P4 with 2GB DDR and and the *original* ATI Radeon (R300?) (I have a bunch, and they have run with all of the versions of Linux).  This motherboard, processor, and memory is new to me, but it would not run 910 for more than a few minutes, and has been running for hours with 810.

These are VERY different systems, with amazingly similar and repeatable results.

Has the general population seen a big drop in reliability of Ubuntu?  Or Linux in general (Is it the kernel)?  I though the bad old days of quirks and bugs as the best it gets were gone, but 904 and 910 have been MUCH worse than anything I have seen.

I am concerned about my long term ability to run Linux at this rate.  How long will Canonical provide updates to 810, and will the on-line files to install be available?  

Thanks.

---

### Post by mikewhatever on 2009-11-14
Various releases work better for some and worse for others. Both 8.10 and 9.04 had serious regressions with Intel graphics, for example. I don't know what the problem is in your case, but, well, use what works. 8.10 is supported till April 2010, and there is also 8.04, supported till June 2011. Hopefully, till that expires, one of the newer version starts playing nicely with your hardware.

---

### Post by cariboo on 2009-11-14
I've seen several threads complaining about the same thing, no one has said what the problem is, just that they have gone back to an earlier release. Just saying it crashes doesn't help, if we don't know what the problem is how can anyone do anything to solve it.

---

### Post by coffeecat on 2009-11-14
I think I can see what your problem might be with one machine:

> **rnsc said:**
> nVidea 5200

Are you using the proprietary nvidia driver? This is almost certainly considered a legacy chipset by nvidia and no longer supported. As far as I can see it is not supported in the proprietary nvidia drivers that would be installed in Karmic. Probably true of Jaunty as well. Intrepid would be using an older nvidia driver which is perhaps why the 5200 works OK in Intrepid. But if you're using the open-source 'nv' driver, I don't know. 

I have next to no experience of ATI cards, but...

> **rnsc said:**
>  the *original* ATI Radeon (R300?)

... might be more or less the same story. Old card no longer supported by the proprietary driver. Certainly some of the symptoms you describe could be related to graphics card issues.

My experience with a nvidia 8600 (one machine) and Intel graphics (laptop) in Karmic is good. Solid, reliable, fast-booting, enjoyable to use.

---

### Post by mikewhatever on 2009-11-14
Nvidia geforce FX 5200 is reported to work on both 9.10 and 9.04, compiz and all.

[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

---

### Post by coffeecat on 2009-11-14
> **mikewhatever said:**
> Nvidia geforce FX 5200 is reported to work on both 9.10 and 9.04, compiz and all.

Thanks for the information and link.

I've just double-checked in Synaptic. The 173 driver supports the 5200, but not the 185  it seems so it would be interesting to know which driver the OP was using.

**Edit:** hmmm - curious that in the screenshots in that link, the Hardware Drivers app was recommending the 185 driver. :|

---

### Post by mikewhatever on 2009-11-14
> **coffeecat said:**
> Thanks for the information and link.

I've just double-checked in Synaptic. The 173 driver supports the 5200, but not the 185  it seems so it would be interesting to know which driver the OP was using.

**Edit:** hmmm - curious that in the screenshots in that link, the Hardware Drivers app was recommending the 185 driver. :|

Indeed, FX 5200 requires nvidia-glx-173. Perhaps that site isn't as reliable as I though.

---

### Post by Eagles18 on 2009-11-14
I like 9.10 better than the others because it is more stable -on my laptop- than all of the others.It is,also, the only one that flawlessly suspends my laptop.

---

### Post by thiebaude on 2009-11-14
I've had no problems at all with Ubuntu 9.10, i've been using Ubuntu since 6.06 and no problems,except with 9.04 and the intel regression problem, and that was a work around that.3 weeks ago i had a computer built for me, and no longer use Intel, I have AMD dual core.

---

### Post by trixman on 2009-11-14
> **rnsc said:**
> I would appreciate any general comments.  Details are below, but I find 810 to be rock-solid, 904 to be unreliable, 910 to not be usable at all.  So I reloaded 810 again.  This is a troubling trend.

I moved from Suse to 810 and found it to be rock-solid for the last 10 months.  As I tried to upgrade to 904, both as an upgrade, then twice as a clean install, I kept getting mdadm segmentation faults.  I went back to 810 and the same hardware has been rock solid again.

I recently tried 910 and did not fare as well.  It crashes very quickly, and hard.  The X system simply hangs.  Sometimes as the "cylon" is going during boot, sometimes after boot, once with a scrambled display, but always requiring the power button to recover.  I never got it to run long enough to create a second account.  I installed it a few days ago, then looked at it harder this morning.  Two new clean installs, many reboots.  Can't make it go.

I did a clean install of 810 and it has been running for 5 hours - easily 30-40 times longer than it would run 910 before crashing.

This is on TWO sets of hardware:

Asus P3B-F Intel 440Bx With 800MHz P3 with 750MB ECC SDRAM and an nVidea 5200, been running for geez 8 years or more reliably.  And it is now reliable again with 810 (again).

Asus P4C800-E Intel 875 with a 2.8GHz Prescott P4 with 2GB DDR and and the *original* ATI Radeon (R300?) (I have a bunch, and they have run with all of the versions of Linux).  This motherboard, processor, and memory is new to me, but it would not run 910 for more than a few minutes, and has been running for hours with 810.

These are VERY different systems, with amazingly similar and repeatable results.

Has the general population seen a big drop in reliability of Ubuntu?  Or Linux in general (Is it the kernel)?  I though the bad old days of quirks and bugs as the best it gets were gone, but 904 and 910 have been MUCH worse than anything I have seen.

I am concerned about my long term ability to run Linux at this rate.  How long will Canonical provide updates to 810, and will the on-line files to install be available?  

Thanks.

i use hardy heron 8.04 very solid you can try that out

---

### Post by rnsc on 2009-11-14
Thanks for the comments.  I realize it was not actionable.  At other times I have dug in, spend weeks trying to track down things, etc.  At this point in time I just need a PC that works.

Regarding the video drivers in general, although I have used the proprietary drivers, for the last year I have just used the whatever the default install uses.  I have not had any significant problems with either.  This applies to ATI and nVidea.

Regarding the mdadm problem, I did document it in detail, as did many other people.  This is a real mystery because I have used md and lvm in Suse since around 2001, on many machines, switching to Ubuntu for 810, and never had any problems until 904.  It has always been a dream.

Regarding the video problems with 910, they are sporadic.  Sometime it hangs before boot is complete.  It locks up good.  Even a console switch goes not work, or control-alt-delete.

Perhaps a useful thing would be an automated survey with about 2 or 3 questions with -2, -1, 0, +1, +2 responses asking how it is on a relative and absolute scale, e.g. (1) Is it good or bad, (2) Is it better or worse than your previous installation, (3) On balance does it meet your needs.

If things are going south, it might be time to stop rolling in new stuff as fast.  Or perhaps there should be two concurrent release streams - one for people who just want it to work, even if it is a little dated, and one for people who want the cutting edge.

Thanks for the comments.

---

### Post by Onesimus on 2009-11-15
> **rnsc said:**
>  If things are going south, it might be time to stop rolling in new stuff as fast.  Or perhaps there should be two concurrent release streams - one for people who just want it to work, even if it is a little dated, and one for people who want the cutting edge.


But there are two concurrent release streams.  The LTS (Long Term Support) which is released every two years, and those that are released every 6 months.  You get to choose which one is best suited for your needs.

---

### Post by Jazzy_Jeff on 2009-11-15
> **Onesimus said:**
> But there are two concurrent release streams.  The LTS (Long Term Support) which is released every two years, and those that are released every 6 months.  You get to choose which one is best suited for your needs.

+1 on LTS. This is the way to go if you need a machine to just work. The newer releases are for people that like to dig in and get their hands dirty :D. I like tweaking my machine, so I like the new releases.

---

### Post by Zoot7 on 2009-11-15
Why not just install Hardy and use it until it's lifetime is up as regards support? Lucid will have been out nearly a year at that time and should be pretty rock solid by then.
I think once Lucid hit's I'll be LTS -> LTS myself.

---

### Post by Riffer on 2009-11-15
As someone else suggested, its your video drivers.  I know earlier this year nVidia decided not to continue to support legacy cards (which yours is) and suggest that you continue to use the 173 series.  As to your ATI card, its always been a problem if you try and use the proprietary drivers.  Yes I know ATI has made great grounds this year in Linux support, but with the age of your card etc. etc.

Also I have noted that the linux kernel has been slowly taking out support for older legacy hardware (not just graphics cards)and as Ubuntu is fairly cutting edge with the kernel it uses I wouldn't doubt if this could be a source of problems.

At this point I would use the 173 series driver for your nVidia machine, and try the open source driver for your ATI card.

And FYI I upgraded to 9.10 from 9.04 and it went flawless (first time an upgrade did) and I'm happy and very impressed with this latest version.  

P.S.  I found this at ATI driver FAQ's page

Q2:  	  Which ATI graphics cards can use this driver?
A2: 
The ATI Proprietary Linux driver currently supports Radeon 8500 and later AGP or PCI Express graphics products, as well as ATI FireGL 8700 and later products. We do not currently plan to include support for any products earlier than this. Drivers for earlier products should already be available from the _DRI Project_ or _Utah-GLX project_.

Maybe go and check out those suggestions.

---

### Post by TBerk on 2009-11-16
> **mikewhatever said:**
> Nvidia geforce FX 5200 is reported to work on both 9.10 and 9.04, compiz and all.

[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-9.10-desktop-nvidia-geforce-fx-5200)

It's been awhile since I checked but I do believe that's the video card I am running.

I'm using 9.10 (Now mostly Studio without the eyecandy.)

I'm currently defaulting to the Nvidia ver 173 driver. no problems. 

btw- my hardware is a dual core Intel CPU running 3GHz and 768M RAM. I (think) its non-ECC. 

Other than when I was trying to upgrade from 9.04 to 9.10, I haven't had anything like those problems.

In fact I had 9.04 run on half a doz differing system over the last year, no real basic problems.


berk

---

### Post by armandh on 2009-11-16
out less than a month; DUH!

I look at the release date as 
the date the real testing begins.

I'll put a new release on a test sled
but my wife's lap top befault boots 8.04

---

