---
title: "Ati Catalyst 10.6 is out!"
date: 2010-06-17
forum: The Cafe
---

### Post by fbkarsdorp on 2010-06-17
The new 10.6 ati catalyst propietary driver is out and has some nice improvements! First, the backlight issue (backlight couldn't be dimmed) is resolved, which is nice for laptop users. Second, and of of most importance, the slow window resize/ maximize etc. is no longer an issue. 2Ddirect is now stable and enabled by default. It's really fast! So, no need for the backclear or no-back-fill patches anymore! Finally...:D

---

### Post by evaarties on 2010-06-17
How long does it usually takes for the update to be applied automatically to a vanilla Ubuntu 10.04 ?

---

### Post by philinux on 2010-06-17
Moved to cafe.

---

### Post by Dilutu on 2010-06-17
unfortunatly, nothing for agp cards "yet"????

---

### Post by undecim on 2010-06-17
Strange. I've never had any of those issues.

---

### Post by sixstringmonk on 2010-06-17
Unfortunately the new drivers don't seem to fix the 2d vsync / tearing issue on the desktop and during video playback.

---

### Post by ubunterooster on 2010-06-17
> **evaarties said:**
> how long does it usually takes for the update  to be applied automatically to a vanilla ubuntu 10.04 ?
+1

---

### Post by fbkarsdorp on 2010-06-18
> **evaarties said:**
> How long does it usually takes for the update to be applied automatically to a vanilla Ubuntu 10.04 ?

As far as I know, it won't. Usually Ubuntu only supplies a new version of catalyst with a new version of Ubuntu, but no updates in between. Hopefully with this new version it will be available as a regular update, because for me, this is the first real progress made in about a year.

---

### Post by R33D3M33R on 2010-06-19
> **fbkarsdorp said:**
> The new 10.6 ati catalyst propietary driver is out and has some nice improvements! First, the backlight issue (backlight couldn't be dimmed) is resolved, which is nice for laptop users. Second, and of of most importance, the slow window resize/ maximize etc. is no longer an issue. 2Ddirect is now stable and enabled by default. It's really fast! So, no need for the backclear or no-back-fill patches anymore! Finally...:D

Unfortunately, the slow resize/maximize problem is still here on my computer. I'm using Kubuntu 10.04 with latest updates. I removed old driver by running fglrx-uninstall.sh, then ran the ati installer and finally updated xorg.conf with aticonfig --initial --force. As you can see by the displayed FPS in the top right corner of the attached screenshot, the performance drops from 100 FPS to 20-40 FPS when I resize the window. It doesn't matter if the effects are off/on -> the resizing is still slow. So what am I doing wrong?

Thanks for any ideas in advance.

---

### Post by sandyd on 2010-06-19
> **R33D3M33R said:**
> Unfortunately, the slow resize/maximize problem is still here on my computer. I'm using Kubuntu 10.04 with latest updates. I removed old driver by running fglrx-uninstall.sh, then ran the ati installer and finally updated xorg.conf with aticonfig --initial --force. As you can see by the displayed FPS in the top right corner of the attached screenshot, the performance drops from 100 FPS to 20-40 FPS when I resize the window. It doesn't matter if the effects are off/on -> the resizing is still slow. So what am I doing wrong?

Thanks for any ideas in advance.
This is a bug that was introduced when the devs decided to improve on the intel drivers.

Ive created a tutorial that teaches you how to remove the conflicting improvement, and it will fix this problem.

[http://dolphinaura.com/tutorials/linux-hacks-fixes/howto-make-fglrx-faster](http://dolphinaura.com/tutorials/linux-hacks-fixes/howto-make-fglrx-faster)

and this problem is only present in KDE.
and I replaced the  ati 3800 (this was the card that I wrote the tutorial with, but it will work with ALL ati cards) with a Nvidia GTX 260 a while ago, so no problems for me.

---

### Post by undecim on 2010-06-19
> **sixstringmonk said:**
> Unfortunately the new drivers don't seem to fix the 2d vsync / tearing issue on the desktop and during video playback.

I have this problem, too when using the default Ubuntu player, but if I use mplayer with the -vo gl option, it works fine (although it uses more CPU)

---

### Post by R33D3M33R on 2010-06-20
> **carlee said:**
> This is a bug that was introduced when the devs decided to improve on the intel drivers.

Ive created a tutorial that teaches you how to remove the conflicting improvement, and it will fix this problem.

[http://dolphinaura.com/tutorials/linux-hacks-fixes/howto-make-fglrx-faster](http://dolphinaura.com/tutorials/linux-hacks-fixes/howto-make-fglrx-faster)

and this problem is only present in KDE.
and I replaced the  ati 3800 (this was the card that I wrote the tutorial with, but it will work with ALL ati cards) with a Nvidia GTX 260 a while ago, so no problems for me.

I thought that Catalyst 10.6 fixes this bug without need for any hacks :confused:

---

### Post by handy on 2010-06-20
Catalyst 10.6, looks to have a variety of problems, some are finding that they have to turn off the 2D acceleration to get rid of the black box, or black interference on their display.

---

### Post by hamidoo on 2010-06-20
It worked gr8 for me now with my HD3650!
In the previous versions of catalyst (10.4,10.5) i had 2 major issues (unminimize delay and a massive memory leak that can be cleared by running glxinfo regulary).
Here is the simplest and safest way to update the proprietary drivers:
1- download the driver from ati and mark the file executable.
2-then generate the debs:
```
./ati-driver-installer-10-6-x86.x86_64.run  --buildpkg Ubuntu/lucid

```
3-then install the debs
```
sudo dpkg -i *.deb
```
4-go to catalyst control panel - information section and make sure that the catalyst version is 10.6.

All works perfect except the xv video overlay in gstreamer.

---

### Post by handy on 2010-06-20
> **hamidoo said:**
> ...
All works perfect except the xv video overlay in gstreamer.

Unfortunately not for all hardware configurations it would seem.

---

### Post by Tuchkata on 2010-06-21
Unfortunately I still have some video tearing when watching video. It's pretty better then before, but it still exists. Hopefully 10.7 will be the perfect one :D

---

### Post by sandyd on 2010-06-21
> **handy said:**
> Catalyst 10.6, looks to have a variety of problems, some are finding that they have to turn off the 2D acceleration to get rid of the black box, or black interference on their display.
+1
im getting this occasionally w/ cairo-dock, and its really anoying when you have a huge black box covering part of the screen....

---

### Post by Yes on 2010-06-21
If you're getting a black box, apparently it's because of a new method they use for 2D acceleration.  Running 'aticonfig --set-pcs-str=DDX,ForceXAA,TRUE' should force it to use the old method.  I haven't tested it much but it seems to have fixed the problem for me.

---

### Post by sandyd on 2010-06-21
> **Yes said:**
> If you're getting a black box, apparently it's because of a new method they use for 2D acceleration.  Running 'aticonfig --set-pcs-str=DDX,ForceXAA,TRUE' should force it to use the old method.  I haven't tested it much but it seems to have fixed the problem for me.
yeah, but I still prefer EXA over XAA.
the commands above just make it use a different type of rendering, which is older, and slightly slower. EXA rendering had no issues in 10.5, so I reverted to 10.5 already.

---

### Post by sandyd on 2010-06-21
add the issue to [http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36](http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36) :D
remember to refrence this topic in the last section, where it asks for a site.

---

### Post by AllRadioisDead on 2010-06-21
Glad I jumped off the ATI ship a while ago.

---

### Post by AgentLinux on 2010-06-22
How old is the "hardware drivers" update version on Ubuntu 10.04 compared to Catalyst 10.6 (June, 2010)?

---

### Post by Dilutu on 2010-06-22
Well I found out that this driver is the same for both pci and agp so I installed....Slight responsivness improvement and still have video tearing....

---

### Post by ]-Six-[ on 2010-06-25
Hello.
I also have a couple of problems with these drivers. Vmware Unity, which I love, seems to be broken as well as the screen sharing software that I use for work.

As I am not very experienced with Ubuntu, yet: Could someone help me uninstalling it and getting back to the Ubuntu 10.04 defaults? 

I followed the [steps here]("http://ubuntuforums.org/showthread.php?t=1511560") for installation. Can I now just run a similar

```
sudo apt-get remove --purge fglrx-kernel-source xorg-driver-fglrx fglrx-modaliases libamdxvba1
```

and then use package manager to load the same files from the ubuntu repository?  

Thanks a lot for any help and best regards,
Peter.

---

