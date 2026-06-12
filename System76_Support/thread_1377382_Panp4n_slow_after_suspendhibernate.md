---
title: "Panp4n slow after suspend/hibernate"
date: 2010-01-10
forum: System76 Support
---

### Post by 3Miro on 2010-01-10
Lately I have been having problems with my Panp4n, after suspend/hibernate the graphics sets very slow. Some of the things that happen:

- compiz cube is choppy
- windows take longer to open/minimize
- Hulu player gets very choppy (cannot be used)
- Windows under virtual box takes longer to start and it takes even longer for it open any app, then you can see how it is drawing the screen line by line
- wine games get slower
- youtube also seems to get slower
- regular apps that do not involve graphics work fine

Reboot fixes all of those issues and the problem is present in both Gnome and XFCE. My guess is it is nvidia driver issue.

This is my wife's laptop so I am not sure exactly when the poblem first appeared.

PS: Just noticed that the new kernel 2.6.31.17 has the old problem with not detecting the battery. I switched back to 2.6.31.16 and I will see if the other issues also exist.

Correction: the battery monitor was broken by the suspend/hibernate process. After reboot, it works fine.

---

### Post by HotShotDJ on 2010-01-10
Add the CPU Frequency monitor to one of your panels.  Then, after a suspend/resume cycle, open a few applicationns.  Watch the Frequecy monitor.  I'll be willing to bet that it is stuck at the lowest step.  This happens on my PanP5.  I have found no solution.

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186)  -- Unfortunately, nothing is happening with it... I'm not even sure if developers even look at bug reports anymore. (I'm very frustrated with Karmic, aka Ubuntu ME).  Then again, I'm writing this while in hospital... so that might be effecting my mood.

---

### Post by solotwit on 2010-01-10
I'm having the same issue, thank you.

---

### Post by 3Miro on 2010-01-11
> **HotShotDJ said:**
> Add the CPU Frequency monitor to one of your panels.  Then, after a suspend/resume cycle, open a few applicationns.  Watch the Frequecy monitor.  I'll be willing to bet that it is stuck at the lowest step.  This happens on my PanP5.  I have found no solution.

Here is the bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186)  -- Unfortunately, nothing is happening with it... I'm not even sure if developers even look at bug reports anymore. (I'm very frustrated with Karmic, aka Ubuntu ME).  Then again, I'm writing this while in hospital... so that might be effecting my mood.

I will not have access to my wife's laptop for some time now so I cannot check this specific thing, however, by all indication the problem was GPU not CPU one. But then again, I might be wrong. Besides CPU has nothing to do with the Battery.

On my other Laptop and my Desktop 9.10 worked better then anything else I have tried. I have been using Ubuntu since 7.04 on my desktop and I can say this is the first version that had no problems or whatsoever, it however, seems to have a entire horde of issues with System76 machines. Which in itself makes no sense.

I hope you get out of the hospital soon. Oh, and if you have anger to vent, try a windows forum, it may be more fun.

---

### Post by HotShotDJ on 2010-01-11
> **3Miro said:**
> I hope you get out of the hospital soon. Oh, and if you have anger to vent, try a windows forum, it may be more fun.My doctor will tell me today when I can go home. Hopefully soon.  Hmmmmm.... venting in a windows forum could be fun.. or at the very least, therapeutic.  "I was crying because I had no shoes.  Then I met a man who had no feet"

---

### Post by miniyak on 2010-01-12
ive never noticed this clock down the cpu, but i have really payed attention to the gpu.

I have seen performance in certain applications decrease after suspend however.
In particular VBA, there is a world of difference playing your fav. retro game at 700% vs. %250, lol

---

### Post by smcoll on 2013-01-10
This is an older thread, but it perfectly describes an issue i've long had with my panp4.  i generally avoid suspending it altogether, as a consequence.

i took HotShotDJ's advice and monitored the CPU frequency.  What i found is that my machine starts at 2401MHz on AC power, and 1600MHz on battery power.  After i suspend, it resumes at 800MHz and i have the behavior 3Miro listed.

Aside from this and the low battery life, i've been pleased with my panp4.

---

### Post by samalex on 2013-01-14
> **smcoll said:**
> This is an older thread, but it perfectly describes an issue i've long had with my panp4.  i generally avoid suspending it altogether, as a consequence.

i took HotShotDJ's advice and monitored the CPU frequency.  What i found is that my machine starts at 2401MHz on AC power, and 1600MHz on battery power.  After i suspend, it resumes at 800MHz and i have the behavior 3Miro listed.

Aside from this and the low battery life, i've been pleased with my panp4.

I've always ran into this after suspend, both on Ubuntu 9.04 which shipped with my PanP5, then Ubuntu 10.04, and again on Xubuntu 12.04 which is what I'm running now. I keep the widget running to show the CPU speed, and I have a small script I wrote that will kick it up when I need the extra power.  I don't think it's a S76 problem but just something with Ubuntu in general.

---

### Post by smcoll on 2013-01-14
Yeah.  i marked the bug report at [https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/364514](https://bugs.launchpad.net/ubuntu/+source/cpufrequtils/+bug/364514) as "this affects me".  Would you mind sharing the script you use to reset the frequency?

---

### Post by smcoll on 2013-12-28
Still having this issue in 13.10.  My present workaround is to use the tray icon supplied by 'indicator-cpufreq' to manually set the cpu governance after a resume.  i'm using `$ cpufreq-info` to verify the results.  Surprised that this issue has gone on several years.

---

