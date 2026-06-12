---
title: "How ubuntu broke my thinkpad....yep the actual hardware"
date: 2014-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by jegpqjlk on 2014-11-02
I've been riding the train of linux/mint/buntu/etc for many years now. Back when slackware was a real distro, I'd run it on my PII/3's and have to manually configure everything, bleh.

Fast forward to now times and I've been using "mint 13" on some D600s quite problem free. I have a stack of them so it keeps me happily in laptops for a bit. I decide I need more, 1024x768 just isn't cutting it. I get a thinkpad Z61p, by golly a laptop that has a 1920xx screen and not a the widescreen equivalent of 1024x768. Times are good, maxing out the Win7 with DX11 drivers (the last/unofficial release and I think only way to run aero), getting better wifi, finally a 2nd hdd bay.

What do I put there you ask, mint 15, then 14, then 13 (unity+gnome3 = windows 8, kthx bye). Turns out the ATI card is no longer supported here either. Gone are the days of linux giving older HW a new life, at least with mainstream distros. So I get radeon working and its a bit buggy, doesn't support power management, glxgears has black cuts in full screen. Hey this gpu is getting a little hot.. Annoying OSS driver

Fast forward a few months, laptop feels hot, I run it in windows more now except when I need to program. Finally I break down and get msys, must be that GPU driver.... 

Then disaster strikes, a single line of purple pixel cuts through this beautiful screen... What happened?

I have some more driver troubles (hello gallium provided by vmware inc) and update to the "lts saucy" version of X and get some HW monitor on the task bar (yes mint still has that vs 1 program at a time and full screen flying widgets). Hey, why is the CPU hot too? More lines appear on the screen.... I now have 9, those temp gauges are almost reaching 90deg!

So guess what... it turns out thinkpad fan speed is broken, either because of the bios or the software or both. Its causing the fan to spin at the lowest setting. To this day, after seeing this bug from like '10 '11 in the report there is NO fix. 


I now know why these lines appeared. I know what besmirched my screen... Ubuntu. Had I realized sooner, maybe I could have prevented it. There were no warnings, no shutdowns. Without the sensor applet you'd be hard pressed to notice.And then you have to trust the abnormally high readings it gives you. So thanks, you broke my thinkpad.

---

### Post by Irihapeti on 2014-11-02
I'm sorry to hear that your laptop is damaged. Keep in mind, though, that the developers rarely visit this forum. The members and staff here are unpaid volunteers who give of their time to help others.

If you have a specific problem you'd like help to solve, please post in the support areas of the forums, giving as much technical detail as possible.

---

### Post by jegpqjlk on 2014-11-03
The word filter had already masked any curse words. Maybe as a mod it shows them unmasked?

There is no specific problem to "solve" anymore. This is OS chat, I've never had a computer damaged by linux, I didn't think it was possible without intentionally doing something like overwriting eeproms/bios with garbage, etc. Yet here it is.

---

### Post by sffvba[e0rt on 2014-11-03
I don't know all the details of your situation, nor do I know the exact details of the bug... however this does sound like a case of the hardware manufacturer not being open about their hardware making it very hard (and in this case possibly impossible) for the devs to fix the issue.  I am sorry that your hardware got damaged but find it strange that the fail safes build into hardware to throttle them down at extreme conditions didn't save it :(

---

### Post by QIII on 2014-11-03
> **jegpqjlk said:**
> The word filter had already masked any curse words. Maybe as a mod it shows them unmasked?

The point is that you should not be using language that invokes the filters.  That's a fail-safe and we edit posts when we find it.

It is very unfortunate your hardware was damaged.  That is frustrating ... and expensive.  You didn't need either.  But please bear in mind that the lack of support for older ATI hardware has nothing whatever to do with the Linux community in general or the Canonical developers in particular.  AMD decided to stop supporting their older hardware.  The open source community does what it can to make up for that, but they are really programming into a black box -- the hardware is still proprietary.  If you ask me, they are doing a wonderful job even making things work at all.

None of this is to say that your experience is not real, frustrating, maddening or expensive.  It is really a shame your machine was damaged.  That just stinks.

---

### Post by mastablasta on 2014-11-03
firstly the motherboard should shutdown if it is overheating.

secondly what is wrong with opensource drivers? they do not work well on your card? 

thirdly there might be a workarround/solution which would explain why the bug was never resolved. for example opensource drivers have imporved power management, there are TLP and i think jupiter or somethign like that which will regulate the fans and power consumption... 

finally - is hardware Linux certified? if not and then using wrong drivers you surely can destory it.

---

### Post by buzzingrobot on 2014-11-03
> **mastablasta said:**
> firstly the motherboard should shutdown if it is overheating.



Bingo. That it did not suggests a hardware fault, or, at least, some other kind of fault.

I'm a Lenovo user.  One's AMD and one's Nvidia. I've run a multiplicity of Linux distros on them, including a lot of Ubuntu's and derivatives. I'm not a gamer and the temps on both machines constantly remain quite low, well within their range. The AMD runs cooler than the AMD in the MacBook Pro that sat on the same desk for several years.

---

### Post by tgalati4 on 2014-11-03
There is *thinkfan*, a program that allows you to program the fan speeds versus temperature curve.  I've been using it for several years on my Thinkpad T43p.  Thinkpads are known to have GPU delamination problems.  It's a large chip, it gets hot (especially without dynamic clock being set), and the ball-grid-array solder connection does not hold up well to thermal cycles.  So you can blame Ubuntu, but I would also consider faulty hardware.  

You can set dynamic clocking using the open radeon driver in xorg.conf, but if your chip is showing defects, then there is not much you can do.

---

### Post by jegpqjlk on 2014-11-03
Luckily it didn't de-laminate. I noticed something was really wrong when temps hit 100C and got massive artifacts in desktop + 80c CPU. Thinkfan lets you get the fan up to 3000 rpm unless you set it to "un controlled" which is where it can get similar speeds as in windows.... without it the fan only spins at the lowest setting, slowly killing your laptop. There is pm in the OSS driver but its something like RV530 and there are only 3 states + no dynamic clocking. I don't think they even auto switch.


Why it doesn't shut down, who knows. Other people's thinkpads do in the bug I read from 2010ish. Things were fine in ubuntu 9 and then after that many newer thinkpads had the issue. The only "fix" was actually thinkfan. Something is bugged in thinkpad_acpi and nobody has fixed it for 4 years. I was considering "faulty" hardware but I think its a safe bet to blame linux after reading that bug thread.

>>>finally - is hardware Linux certified? if not and then using wrong drivers you surely can destory it.<<<

I know that's a thing now but coming from slack in 2000/2001 its rather cute.

---

### Post by rrnbtter on 2014-11-03
Greetings,
Ubuntu has a list available of certified hardware. They work very hard with willing vendors. Even at that, as a Linux user I am the architect of my own disaster. Ain't FOSS great?
PS Sorry to hear about your loss. I've come close to a few meltdowns myself. HW failsafe always stopped it however.

---

### Post by mips on 2014-11-04
> **jegpqjlk said:**
> Turns out the ATI card is no longer supported here either. Gone are the days of linux giving older HW a new life, at least with mainstream distros. 

There's a patch to make catalyst 13.1 work on newer linux versions, you will find it in Arch AUR, [https://aur.archlinux.org/packages/catalyst-total-hd234k/](https://aur.archlinux.org/packages/catalyst-total-hd234k/)

It's not linux taking away support it's AMD/ATI dropping support for older GPU chips, AMD/ATI do not support their chips for very long compare to nVidia or Intel. Another reason to avoid AMD/ATI.

---

### Post by /ADM on 2014-11-04
So you blame Linux, even though you were using a GPU driver.  It would be fair to blame Linux if your CPU blew on a specific kernel version (more likely to happen then for a kernel to blow a GPU) but a GPU is under the mercy of the OSS or Proprietary drivers.

---

### Post by jegpqjlk on 2014-11-04
can blame the driver or linx, I believe thinkpad_acpi is in the kerenel

that catalyst will be good on my desktop... won't work for a firegl 5200 though.

I used to like ATI/AMD, they are the go to proc if you don't want hidden things like intel AMT running around in your innards. I've never found NSAware in any amd stuff. The lack of driver support, gpu de-balling and poor new processor performance make me die inside a little.

---

### Post by RichardET on 2014-11-04
My Lenovo B590 has been running Ubuntu for a year  - fan rarely comes on, and it has very good power management.  The video is also good with the core i3.  I doubt the hardware failed because of Ubuntu.

---

