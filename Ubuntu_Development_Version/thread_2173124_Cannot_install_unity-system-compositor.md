---
title: "Cannot install unity-system-compositor"
date: 2013-09-08
forum: Ubuntu Development Version
---

### Post by kanton on 2013-09-08
Hello!

I made a fresh installation of Saucy (13.10) a week ago to tryout Mir. From what I have read, Mir is not installed by default so I suppose I'm still on X. I used these instructions for switching to Mir:

[http://www.jonobacon.org/2013/08/15/mir-update-and-testing-mir-in-ubuntu-13-10/](http://www.jonobacon.org/2013/08/15/mir-update-and-testing-mir-in-ubuntu-13-10/)
[http://linuxg.net/how-to-install-and-test-mir-on-ubuntu-13-10-saucy-salamander/](http://linuxg.net/how-to-install-and-test-mir-on-ubuntu-13-10-saucy-salamander/)

Unfortunately, none of these seem to work for me. I only keep getting a version depency error using: "sudo apt-get install unity-system-compositor" or trying the same with Synaptic.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-system-compositor : Depends: libmirserver1 (= 0.0.10+13.10.20130903-0ubuntu1) but 0.0.10+13.10.20130904-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

Is it possible to fiddle with it in some way to make it work? Or do I have to wait for further updates?

Thanks in advance,
Peter

---

### Post by howefield on 2013-09-08
Thread moved to the "*Ubuntu +1*" forum.

---

### Post by zika on 2013-09-08
Two things:

You might have to wait so that PPA consolidates itself (since You have a candidate that is newer than one desired by package You want to install, that is indicator of sort of transition time that occurs frequently on development PPAs...
You might try```
sudo apt-get dist-upgrade
```but be very carefulll in answering questions and read all questions really slow... ;)

---

### Post by Alan F on 2013-09-08
Just follow the instructions here ...

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

---

### Post by grahammechanical on 2013-09-08
I know who Jono Bacon is but sometimes even the best of us does not always know what they are talking about. Sorry Jono. The guide to follow is this one.

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

You do not need the demonstrations. You need to run

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```
```
sudo install unity-system-compositor
```
```
sudo restart lightdm
```

Your problem may come from not running

```
sudo apt-get dist-upgrade
```

That is like running apt-get upgrade but it is smarter. It fixes issues like the one that you have. Some wrongly think it upgrades to the next version of Ubuntu. Not true. Also, that second link is way out of date. Add the PPA suggested in that link and you will have to purge it to install unity-system-compositor.

Apparently restarting lightdm is important. And you will not notice any difference. The only way to tell if xmir is loaded is to run some commands. If the command does not report back then you are still on xserver.

```
grep -i LoadModule /var/log/Xorg.0.log
```
> 
[    20.311] (II) LoadModule: "glx"
[    20.328] (II) LoadModule: "xmir"
[    20.384] (II) LoadModule: "nvidia"
[    20.400] (II) UnloadModule: "nvidia"
[    20.400] (II) LoadModule: "nouveau"
[    20.400] (II) LoadModule: "vesa"
```
grep -i xmir /var/log/Xorg.0.log
```
> [    20.328] (II) LoadModule: "xmir"
[    20.328] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    20.332] (II) Module xmir: vendor="X.Org Foundation"
[    20.405] (II) NOUVEAU(0): Output XMIR-0 has no monitor section
[    20.405] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    20.405] (II) NOUVEAU(0): Output XMIR-2 has no monitor section
[    20.405] (II) NOUVEAU(0): Printing probed modes for output XMIR-0
[    20.405] (II) NOUVEAU(0): EDID for output XMIR-1
[    20.405] (II) NOUVEAU(0): EDID for output XMIR-2
[    20.405] (II) NOUVEAU(0): Output XMIR-0 connected
[    20.405] (II) NOUVEAU(0): Output XMIR-1 disconnected
[    20.405] (II) NOUVEAU(0): Output XMIR-2 disconnected
[    20.405] (II) NOUVEAU(0): Output XMIR-0 using initial mode 1680x1050

```
ls -l /var/log/lightdm/unity-system-compositor.log
```
> -rw------- 1 root root 62 Sep  8 11:29 /var/log/lightdm/unity-system-compositor.log

```
ps aux | grep unity-system-compositor
```
> root      1031  0.6  1.7 928812 17908 tty7     Ssl+ 11:29   0:28 /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
graham    3483  0.0  0.0  13652   956 pts/0    S+   12:36   0:00 grep --color=auto unity-system-compositor


This is what I get right now from my Saucy+xmir install. Note, none of this will work if we are using a proprietary video drvier.

Regards.

---

### Post by Alan F on 2013-09-08
..... and if he has previously followed the linuxg.net instructions he needs to purge the Mir ppa first as described in...

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

---

### Post by jerrylamos on 2013-09-08
At Beta 1 level
Acer Aspire 5253 Radeon 6310
drivers from .iso, nothing extra
It's using ati according to LoadModule
install unity-system-compositor, update, dist upgrade, reboot, ...

ps aux grep unity-system-compositor shows unity-system-compositor
so does synaptic
ps ax shows unity-panel-service
No mir in Xorg.0.log
Radeon 6310

seems to be defaulting to X

top shows Xorg, not mir nor xmir

Tried both with/without external monitor same thing.  Is there some sort of start command or script or exec missing?

Thanks....

BTW, last week I just got black screen unless booting in recovery mode, then screen working pretty crippled.

---

### Post by mc4man on 2013-09-08
> **kanton said:**
> Hello!

Unfortunately, none of these seem to work for me. I only keep getting a version depency error using: "sudo apt-get install unity-system-compositor" or trying the same with Synaptic.



Is it possible to fiddle with it in some way to make it work? Or do I have to wait for further updates?

Thanks in advance,
Peter
You have proposed repo enabled & only the mir libraries have been updated. So you'll need to wait till unity-system-compositor updates to match that version
Or disable proposed, remove any libmir packages installed from proposed, (if any), update your sources & try to install u-s-c again

---

### Post by vaskark2 on 2013-09-08
Hi. I'm trying to get Mir to work, too. I followed the instructions above. I disabled my proprietary drivers (nvida geforce 6200) and rebooted. Now my launcher and panel are not rendering properly, as seen here:

[http://i.imgur.com/lHsSMZ9.jpg](http://i.imgur.com/lHsSMZ9.jpg)

grep -i LoadModule /var/log/Xorg.0.log
[    21.873] (II) LoadModule: "glx"
[    21.923] (II) LoadModule: "nvidia"
[    21.924] (II) UnloadModule: "nvidia"
[    21.924] (II) LoadModule: "nouveau"
[    21.936] (II) LoadModule: "vesa"
[    21.937] (II) LoadModule: "modesetting"
[    21.938] (II) LoadModule: "fbdev"
[    21.938] (II) LoadModule: "nvidia"
[    21.939] (II) UnloadModule: "nvidia"
[    21.939] (II) LoadModule: "nouveau"
[    21.939] (II) UnloadModule: "nouveau"
[    21.942] (II) LoadModule: "vesa"
[    21.944] (II) UnloadModule: "vesa"
[    21.944] (II) LoadModule: "modesetting"
[    21.945] (II) UnloadModule: "modesetting"
[    21.945] (II) LoadModule: "fbdev"
[    21.945] (II) UnloadModule: "fbdev"
[    21.947] (II) LoadModule: "fbdevhw"
[    21.948] (II) LoadModule: "dri2"
[    22.284] (II) LoadModule: "fb"
[    22.285] (II) LoadModule: "exa"
[    22.296] (II) LoadModule: "shadowfb"
[    22.301] (II) UnloadModule: "vesa"
[    22.301] (II) UnloadModule: "modesetting"
[    22.301] (II) UnloadModule: "fbdev"
[    23.715] (II) LoadModule: "evdev"

So obviously I'm still on xserver. Can someone offer assistance?
Thanks ;)

---

### Post by grahammechanical on 2013-09-09
@vaskark2

Are you willing to try an experiment? Reboot and select Recovery Mode>Resume. When we do that we run on a sub-set of Nouveau called llvmpipe. It is the fall back mode for graphic cards that cannot run Unity 3D. It replaced the Unity 2D that came with 12.04. If the screen effect is the same it will tells us that you are running on llvmpipe and not full Nouveau. Did you active Nouveau in Additional Drivers? Disable proprietary drivers - yes. Activate Nouveau must also be a Yes because at the moment I do not think that xmir will load under llvmpipe.

Regards.

---

### Post by kanton on 2013-09-09
Mc4man's solution did it! Thanks a lot!

Too bad the Mir graphics is all messed up though... (a desktop trashed by stripes/blinds??!) Seems like I'm stuck with X for a while.

---

### Post by rrnbtter on 2013-09-10
Greetings,
Works fine for me x-mir right out of the box. Intel Mobile 4 Graphics, default drivers.

 ps aux | grep unity-system-compositor
root      1006  0.5  0.6 233488 27192 tty7     Ssl+ 11:25   0:07 /usr/sbin/unity-system-compositor --from-dm-fd 10 --to-dm-fd 13 --vt 7
rrnbtter  3766  0.0  0.0   4448   824 pts/0    S+   11:49   0:00 grep --color=auto unity-system-compositor

Thanks for all of the instructions.
PS I'm starting to feel real good about this!

---

### Post by vaskark2 on 2013-09-12
> **grahammechanical said:**
> @vaskark2

Are you willing to try an experiment? Reboot and select Recovery Mode>Resume. When we do that we run on a sub-set of Nouveau called llvmpipe. It is the fall back mode for graphic cards that cannot run Unity 3D. It replaced the Unity 2D that came with 12.04. If the screen effect is the same it will tells us that you are running on llvmpipe and not full Nouveau. Did you active Nouveau in Additional Drivers? Disable proprietary drivers - yes. Activate Nouveau must also be a Yes because at the moment I do not think that xmir will load under llvmpipe.

Regards.
K, I did what you suggested and rebooted. The problem is gone, but when I checked the Additional Drivers panel my NVIDIA driver was still selected. I selected Nouveau and applied the changes but it's seemed to have stalled. I suppose I'll try installing nouveau at the CLI, see if that works.

---

