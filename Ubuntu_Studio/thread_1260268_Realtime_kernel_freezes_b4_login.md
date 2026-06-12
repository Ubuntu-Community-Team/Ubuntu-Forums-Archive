---
title: "Realtime kernel freezes b4 login"
date: 2009-09-07
forum: Ubuntu Studio
---

### Post by g-raf on 2009-09-07
I'm running 32bit Ubuntu Studio 9.04 and when i trying to load the realtime kernel, the computer freezes before reaching the login screen. I followed the advice given on the Ubuntu Studio documentation website: edit the /etc/security/limits.conf and change the "@audio - memlock unlimited" to another setting...i put the memlock on about 50% of the system memory. But the realtime kernel still freezes, just the same as before. 
Anyone have an idea about how to fix this?

---

### Post by Stochastic on 2009-09-07
Unfortunately some people's hardware and the 9.04 RT kernel don't play well together.  It sounds like your graphics hardware is what's triggering the freeze, since it's right before login.

You could try to install a vanilla kernel, this will give you recording capabilities, but at higher latencies.  Just after boot (but before freeze) press ctrl+alt+F1 to get to a tty login.  Log in with your user account and do ```
sudo apt-get install linux
sudo init 6
``` then when it reboots, use the vanilla kernel rather than the realtime one.

---

### Post by g-raf on 2009-09-07
I have an ATI graphics card, using ATI/AMD propriety FGLRX graphics driver. Is there any way i might be able to change my graphics card or driver in order to load the realtime kernel? My first priority is low latency audio production in the rt kernel. Have any ideas?

---

### Post by Stochastic on 2009-09-07
I have an ATI Radeon graphics card too, but since 9.04 I've been using the open source Radeon driver rather than ATI's closed source fglrx driver.  I find there's less headaches and errors with the Radeon driver.  Also, as of 9.04 it has been able to give me all the functionality of my card that I need (compiz, two monitors, etc...).  But I'm really no graphics driver wizard, ask in the Multimedia & Video section of the forums as to the best way to switch.

---

### Post by g-raf on 2009-09-07
Wow! Have you loaded realtime kernel and it worked with the open source ATI driver? I'm excited to try this out. Where did you find the open source driver? On synaptic or...where can i find it? But i'm only interested if it works in the realtime kernel.

---

### Post by Stochastic on 2009-09-07
It did load on my computer, but the kernel did have an occasional freezing problem (i.e. I wouldn't use it in a performance setting).  It should be in Synaptic, but really that's the extent of my knowledge on the subject.  Go ask in Multimeida & Video as to how to install it and remove the fglrx driver safely.

---

### Post by trulan on 2009-09-07
I ended up rolling back to 8.04 on my laptop due to 9.04 kernel issues, and installing backported versions of ffado, jack, and Ardour.  My desktop is quite happy on 9.04 though, so I've got one of each!

I have an NVidia graphics card so I'm no help there.

---

### Post by g-raf on 2009-09-10
I installed the open source radeon driver. It works, but not like the FGLRX driver was working. Can't play games or do anything with graphics. However! I can load up the realtime kernel now and that's great. Thanks for your help.

---

### Post by morgan_greywolf on 2009-09-12
I've found that the realtime kernel doesn't work well with AMD CPUs (Athlon, Athlon64, Opteron, it doesn't matter) and NVidia or ATI graphics cards with the realtime kernel installed, especially if you have AGP.

---

