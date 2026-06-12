---
title: "Anyone finding Ubuntu 12 somewhat slow when loaded with a few apps?"
date: 2013-01-06
forum: The Cafe
---

### Post by os2 on 2013-01-06
Here is my subjective review, which counts a fair bit IMO.

I haven't use Linux in years. I last used RedHat in 1998..2001.

I'm testing this Ubuntu 12 distro out at the moment. Together with OpenSuse 12.

Anyway with a moderately decent machine (Core2, 4GB), Ext4 FS, the system spiritedly springs to life but after having loaded ***just a few*** apps (say 1.5GB load on RAM), the feel and responsiveness is a little slugish. The performance becomes less consistent. Admittedly Windows XP/7 seems to fair better here.

I must admit OpenSuse is a touch faster than Ubuntu 12, and smaller in RAM too, to start with but even that system turns mildly sluggish after a variety of apps have loaded.

Standard experience works great and Fallback even better. But the depreciable performance is noticeable in both cases after some loading. It just turns into a question of scale it would seem.

Your thoughts..

---

### Post by Rocklobster690 on 2013-01-06
12.04 or 12.10?

---

### Post by os2 on 2013-01-06
Here is what I've tried thus far:

Mythbuntu 12.04, (Stock kernel)
Ubuntu 12.10 (Stock kernel)
OpenSuse 12.2 (3.4.x, 3.7.1)

I mean the performance is not sluggishly slow, it's sluggish none-the-less and noticeable at that after having loaded the system just a little.

---

### Post by deadflowr on 2013-01-06
Not really.
But then again it depends on what apps you're running.
You can load a whole boatload of apps that are light resource usage or you can load a few apps that are heavy.
I would think mythbuntu uses heavy resources. 
I do know that video decoding/encoding apps tend to be really heavy.

---

### Post by os2 on 2013-01-06
Which resources does Mythbuntu really use apart from Myth?

I mean Ubuntu is slow in comparison to both MythB and OpenSuse.

Sure lite apps and heavy apps. But after only 1.5/4 GB-load?

---

### Post by deadflowr on 2013-01-06
RAM is only part of the resource equation.
CPU usage is far more critical, in terms of causing sluggishness.
You can run a program that utilizes very little RAM, but is heavy on CPU and even then it'll become sluggish.

---

### Post by sudodus on 2013-01-06
> **os2 said:**
> Here is what I've tried thus far:

Mythbuntu 12.04, (Stock kernel)
Ubuntu 12.10 (Stock kernel)
OpenSuse 12.2 (3.4.x, 3.7.1)

I mean the performance is not sluggishly slow, it's sluggish none-the-less and noticeable at that after having loaded the system just a little.

It is also important to know what graphics card/chip you have in order to give good advice.
--
If you choose speed and responsiveness before eye-candy, I suggest that you download either of these

- Xubuntu with the light-weight desktop environment XFCE
- Lubuntu with the ultra-light-weight desktop environment LXDE

or simply install xubuntu-desktop or xfce or lubuntu-desktop or lxde into your Ubuntu system.

I think that Ubuntu 12.04 is more mature than 12.10 (less bugs). Furthermore it is a long time support (LTS) release with support until April 2017, while the Xubuntu specific packages have LTS until April 2015. Lubuntu 12.04 and other versions (12.10 ...) have only 18 months of support from the release date.

- Ubuntu Studio has selected XFCE instead of any gnome 3 desktop environment system, and that flavour is designed for picture, audio and video processing and showing/playing.

---

### Post by os2 on 2013-01-06
Thanks a bunch.

Anyone know if the Fallback mode in Gnome 3 uses GPU hardware acceleration? Or are the limited-graphics and effects in Fallback mode simply emulated (thru CPU)?

---

### Post by os2 on 2013-01-06
> **sudodus said:**
> It is also important to know what graphics card/chip you have in order to give good advice.


I was hoping not get into that as in this case performance is fine at the outset but only degrades under load.  Suffice to say GPU is excellent for a 2D environment.

You can never have enough power and responsiveness but I want to do the best I can with the hardware I have (and that means certainly migrating away from Windows ;)) -- as should everyone IMV.

---

### Post by sudodus on 2013-01-06
> **os2 said:**
> I was hoping not get into that as in this case performance is fine at the outset but only degrades under load.  Suffice to say GPU is excellent for a 2D environment.

You can never have enough power and responsiveness but I want to do the best I can with the hardware I have (and that means certainly migrating away from Windows ;)) -- as should everyone IMV.

If you have Intel graphics, the built-in graphics driver is good. If you have nVidia graphics, a built-in proprietary is probably offered, and will probably improve the performance, but not for all cards. If you have Radeon ATI graphics, it is similar. The support for old such cards is not very good, but better for new cards. Some of these drivers offer excellent cooperation with the hardware, so that you can run advanced tasks, 3D graphics, and use the graphics card to process video (so that the CPU(s) will be available for other tasks.

If the computer slows down way before the RAM is crowded, check the CPU load with ```
top
``` in a terminal window or use gnome-system-monitor (GUI). If the CPU load does not come close to 100%, maybe your system is too swappy (will begin to swap before RAM is crowded). That can be tweaked according to this link.

[[COLOR="Red"]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Mikeb85 on 2013-01-06
I find Ubuntu 12.04 and 12.10 faster than Windows 7, but significantly slower than openSUSE.  I still use it though because it's convenient and I like the Unity DE, but both my machines run it pretty well.  (one is a Core 2 Duo with 4 GB ram running 12.04, the other a ThinkPad T530 with i7 and 8 GB of ram running 12.10).  

If your machine is slightly older as it sounds like yours is, maybe running Debian or openSUSE with XFCE or LXDE would be what you need?  Heck, even openSUSE KDE is significantly quicker than Ubuntu with Unity.

---

### Post by os2 on 2013-01-06
> **sudodus said:**
> It is also important to know what graphics card/chip you have in order to give good advice.
--
If you choose speed and responsiveness before eye-candy, I suggest that you download either of these

- Xubuntu with the light-weight desktop environment XFCE
- Lubuntu with the ultra-light-weight desktop environment LXDE

or simply install xubuntu-desktop or xfce or lubuntu-desktop or lxde into your Ubuntu system.

I think that Ubuntu 12.04 is more mature than 12.10 (less bugs).  Furthermore it is a long time support (LTS) release with support until  April 2017, while the Xubuntu specific packages have LTS until April  2015. Lubuntu 12.04 and other versions (12.10 ...) have only 18 months  of support from the release date.

- Ubuntu Studio has selected XFCE instead of any gnome 3 desktop  environment system, and that flavour is designed for picture, audio and  video processing and showing/playing.

A number of excellent suggestions. Assessing the DMs will be my next task.

> **sudodus said:**
> 
If the computer slows down way before the RAM is crowded, check the CPU load with ```
top
``` in a terminal window or use gnome-system-monitor (GUI). If the CPU load does not come close to 100%, maybe your system is too swappy (will begin to swap before RAM is crowded). That can be tweaked according to this link.

[[COLOR=Red]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")


Thanks for this tip. Makes a noticeable difference to low-end usage.

---

### Post by os2 on 2013-01-06
> **Mikeb85 said:**
> I find Ubuntu 12.04 and 12.10 faster than Windows 7, but significantly slower than openSUSE.  I still use it though because it's convenient and I like the Unity DE, but both my machines run it pretty well.  (one is a Core 2 Duo with 4 GB ram running 12.04, the other a ThinkPad T530 with i7 and 8 GB of ram running 12.10).  

If your machine is slightly older as it sounds like yours is, maybe running Debian or openSUSE with XFCE or LXDE would be what you need?  Heck, even openSUSE KDE is significantly quicker than Ubuntu with Unity.

Amen to that. But with this same hardware config Ubuntu-Unity was unusable for me. Perhaps something has to be said about the plethora of code running the DM's.

---

