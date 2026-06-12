---
title: "PanP5 CPU stuck at lowest freq step upon resume from suspend"
date: 2009-10-31
forum: System76 Support
---

### Post by HotShotDJ on 2009-10-31
With the Power Manager set to the default "Ondemand" cpu governor, after waking from suspend, the CPU frequency is stuck at the lowest step (800 MHz for my P8700).  This occurs on a clean install of Ubuntu 9.10. If I switch to other governors via the CPU Frequency Monitor applet, they work as expected.  Manually setting the CPU frequency also works as expected.  However, when I switch back to "Ondemand" my system is again locked at 800 MHz.  Only a system reboot corrects the problem.

I'm using fully updated "out-of-the-box" Karmic -- no customized kernel, ppa's or tweaking of software (as I am prone to do) ... but I figure if I did that, it would make it difficult to get this problem debugged.  I've attached the output of "cpufreq-info" both before and after a suspend/wake cycle.  I don't see anything informative in there, but perhaps it might help somebody who knows what they are looking for.

EDIT:  I've also run "System76 Driver -> Support" and created the log archive.  I'm happy to send the resultant logs.tar file to you if you feel it will help you figure this out.

---

### Post by thomasaaron on 2009-11-02
Looks like you've found a bug, but it doesn't seem to be clear what the cause is. You probably should chime in there...

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186)

---

### Post by HotShotDJ on 2009-11-02
> **thomasaaron said:**
> Looks like you've found a bug, but it doesn't seem to be clear what the cause is. You probably should chime in there...

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/445186)I thought I had done a thorough search - but that bug report completely slipped by me.  I'll take the problem there.  Thanks, Tom!

---

### Post by HotShotDJ on 2009-11-02
Tom --

I've "chimed in" on that bug as you suggested.  Hopefully something will happen with it soon.  I'm wondering if your seeing this on any of your shop machines, or if anybody else is having this experience?

---

### Post by thomasaaron on 2009-11-03
Not yet, but it isn't the type of thing we look for in our testing. I'll have a look at it once I get through these next few days. Trying to help people through a lot of critical upgrade failures, but I can see the light at the end of the tunnel. :D

---

### Post by HotShotDJ on 2009-11-03
> **thomasaaron said:**
> Trying to help people through a lot of critical upgrade failures, but I can see the light at the end of the tunnel. :DI can only imagine what you guys go through every 6 months!  I see a Friday night happy hour in your future. :)  Just to let you know that the efforts you guys put in are well appreciated.  With Dell, their answer to problem upgrades (at least with their Linux boxes) is always to not upgrade -- if you want an upgraded OS, you need to buy a new computer. (ok, ok... I exaggerate.. but only a little bit. :))

Thanks for your hard work.  I can wait... and I always have Launchpad to feed my geek-wannabe tendencies.

EDIT:  YIKES... if you are online answering questions... that means that I need to go to work.  Later!  LOL!

---

### Post by thomasaaron on 2009-11-03
> I see a Friday night happy hour in your future.

Amen, brother. :popcorn:

---

### Post by imhavoc on 2009-11-05
Tom, My Daru2 is stuck at 800 MHz without ever suspending it.

For now I'm going to assume that this is a general Ubuntu bug, or a kernel bug, unless you have any other thoughts on the issue.

---

### Post by thomasaaron on 2009-11-05
Hi, Jody.

Did you do the online upgrade or a fresh install?

---

### Post by HotShotDJ on 2009-11-09
** ping **

---

### Post by thomasaaron on 2009-11-09
Thanks for the ping.

I just tested, and after resuming from suspend, my CPU had moved from 2.2 GHz to 1.6 GHz, but I was able to easily switch it back.

If I read your initial post correctly, you've got a fresh install, right? Not an upgrade?

---

### Post by HotShotDJ on 2009-11-09
> **thomasaaron said:**
> Thanks for the ping.

I just tested, and after resuming from suspend, my CPU had moved from 2.2 GHz to 1.6 GHz, but I was able to easily switch it back.

If I read your initial post correctly, you've got a fresh install, right? Not an upgrade?Yes.  I did a fresh install.  I'm able to get the CPU to scale back up manually.  Only the "ondemand" governor seems to be effected.  For example, after a suspend, if I set the governor to "conservative," automatic scaling returns (quite a bit of lag, but that's what the conservative governor is supposed to do).

---

### Post by thomasaaron on 2009-11-09
Oh. I'm sorry. I missed that.

I'm seeing that too. Definitely a bug, but I'm not sure there's much System76 can do about it. I think that bug report is going to be our best bet for now.

---

### Post by HotShotDJ on 2009-11-10
> **thomasaaron said:**
> I'm seeing that too. Definitely a bug, but I'm not sure there's much System76 can do about it. I think that bug report is going to be our best bet for now.Ok.  That is what we both had suspected.  Now that we know that the problem isn't unique to my machine, and therefore probably not faulty hardware, I agree that the bug report is the correct direction.

---

