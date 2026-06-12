---
title: "NVIDIA 180.22 update regularly?"
date: 2009-02-09
forum: System76 Support
---

### Post by darkknight045 on 2009-02-09
Is there a way to get the Nvidia driver 180.22 set up in the Hardware Drivers section Administration?  I pretty much hosed my system trying to getting something set up that would force me to manually recompile the Nvidia driver every time the Kernel updated.

I'm running a GazP5 if thats any help.

Help?

---

### Post by thomasaaron on 2009-02-09
If running...

sudo apt-get install nvidia-glx-180 

...doesn't get it to appear in Hardware Drivers, then probably not.

However, you probably should be running the 177 driver. I've not tested with the 180 driver, but I don't think that it is necessary or adds any additional functionality for your GazP5.

My understanding is that it provides support for some newer nVidia cards.

---

### Post by betrunkenaffe on 2009-02-11
My personal experience with 180 has been a general increased responsiveness to Compiz, although glxgears still has same fps performance. I ran into some glitches with the drivers not having the hue set correctly after the install so had to manually reset to defaults. (Video was blue in video players)

---

### Post by Lee_Machine on 2009-02-11
why would you wanna recompile the nvidia driver? That is what DKMS is for.

For me the 180 driver does not show up under Hardware Drivers, but does in Nvidia X Server Settings. Also while booting up it says loading nvidia drivers 180.22

I dowloaded it from the nvidia website when it came out. Probably why it doesnt show up.

---

### Post by thinman1189 on 2009-04-08
I just got 180 through updates yesterday and now I'm getting this bug. I'm on Serval Performance, 8.10.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/306315](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/306315)

[http://www.nvnews.net/vbulletin/showthread.php?t=123303](http://www.nvnews.net/vbulletin/showthread.php?t=123303)

Any ideas? Should I force an update to the newest version or is it going through System76 anytime soon?

---

### Post by thomasaaron on 2009-04-08
thinman, that bug pertains to Jaunty? Are you running Jaunty? If so, you are a bit ahead of the curve. We don't really work at squashing bugs on a new release until we actually get to them. 

That bug report said that reverting to the previous nVidia driver (via System > Administration > Hardware Drivers) fixed the problem. Have you tried that yet?

---

### Post by 3Miro on 2009-04-08
I have the 1.80 driver on my pangolin. I believe 1.80 not showing in the HW manager is due to a bug. What I did (after I already had 1.77) I installed

```

nvidia-180-kernel-source
nvidia-180-modaliases
nvidia-glx-180

```

and nvidia X-server setting is showing the 1.80 driver and the HW manager showed it up properly.

I did that on two machines, 1.80 had big positive effect on some bugs that were KDE related and pretty much nothing on the Gnome laptop.

---

### Post by smcoll on 2009-04-08
i did a "Mark All Upgrades" in the Synaptic Package Manager the other day and it included 1.80 in the Hardware Manager.  i already had the driver installed, but it wasn't listed there until i applied the upgrades.

---

### Post by thinman1189 on 2009-04-08
> **thomasaaron said:**
> thinman, that bug pertains to Jaunty? Are you running Jaunty? If so, you are a bit ahead of the curve. We don't really work at squashing bugs on a new release until we actually get to them. 

That bug report said that reverting to the previous nVidia driver (via System > Administration > Hardware Drivers) fixed the problem. Have you tried that yet?

Some of the people in the thread said that it also applied to intrepid, which I'm using.

```
Apr  7 19:39:45 ubuntu kernel: [  162.803625] ACPI: EC: missing confirmations, switch off interrupt mode.
Apr  7 19:42:33 ubuntu kernel: [  330.877802] NVRM: request_mem_region failed for 16M @ 0xc6000000. This can
Apr  7 19:42:33 ubuntu kernel: [  330.877802] NVRM: occur when a driver such as rivatv is loaded and claims
Apr  7 19:42:33 ubuntu kernel: [  330.877802] NVRM: ownership of the device's registers.
Apr  7 19:42:33 ubuntu kernel: [  330.878623] nvidia: probe of 0000:01:00.0 failed with error -1
```

---

### Post by thomasaaron on 2009-04-08
> That bug report said that reverting to the previous nVidia driver (via System > Administration > Hardware Drivers) fixed the problem. Have you tried that yet??

---

### Post by thinman1189 on 2009-04-08
177 seems to be working okay now. Little hang on startup but it's gone away. Any idea when an updated 180.* without the bug will be coming through System76?

---

### Post by thomasaaron on 2009-04-09
An fix won't come through System76. It actually will come down through Ubuntu. 

Since there are a number of bug reports on this one, I imagine it will come down fairly soon.

---

