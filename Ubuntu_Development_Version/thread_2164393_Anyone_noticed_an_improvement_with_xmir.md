---
title: "Anyone noticed an improvement with xmir?"
date: 2013-07-31
forum: Ubuntu Development Version
---

### Post by grahammechanical on 2013-07-31
I am in my Ubuntu saucy+mir installation. I ran the update for today which brought in updates to libmir and the kernel, which in turn forced a restart. At first I did not notice it but I now see only one cursor arrow and that jumping of the insertion point when correcting typing no longer happens. Am I running on xmir? Well I have checked. What do you think?

```
grep -i LoadModule /var/log/Xorg.0.log
```
> 
[    37.743] (II) LoadModule: "glx"
[    37.781] (II) LoadModule: "xmir"
[    37.786] (II) LoadModule: "nvidia"
[    37.787] (II) UnloadModule: "nvidia"
[    37.787] (II) LoadModule: "nouveau"
[    37.787] (II) LoadModule: "vesa"
[    37.788] (II) LoadModule: "modesetting"
[    37.788] (II) LoadModule: "fbdev"

```
grep -i xmir /var/log/Xorg.0.log
```

> [    37.739] xorg-server 2:1.14.2-0ubuntu3+xmir1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    37.781] (II) LoadModule: "xmir"
[    37.782] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    37.785] (II) Module xmir: vendor="X.Org Foundation"
[    37.791] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    37.791] (II) NOUVEAU(0): Printing probed modes for output XMIR-1
[    37.791] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)
[    37.791] (II) NOUVEAU(0): Output XMIR-1 connected
[    37.791] (II) NOUVEAU(0): Output XMIR-1 using initial mode XMIR mode of death
[    37.792] (**) NOUVEAU(0):  Driver mode "XMIR mode of death": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[    37.792] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz eP)


Now, from that I would say 'yes.' But we have been fooled before. And I do not notice a watermark. Is anybody else seeing this?

Regards.

---

### Post by mc4man on 2013-07-31
Slight improvement here
It's running with --enable-input=false so no 2nd cursor.
At least with this nvidia hardware (8400m), nouveau continues to be poor under xmir
vsync is broken totally
alt+f2 may not work
a full screen Dash can be problematic
log outs & restarts can show images from vram instead of plymouth
maybe more - no time atm

---

### Post by cecilpierce on 2013-07-31
All I get is:

grep -i xmir /var/log/Xorg.0.log
[   608.219] xorg-server 2:1.14.2-0ubuntu3+xmir1

and no [ 37.781] (II) LoadModule: "xmir" with grep -i LoadModule /var/log/Xorg.0.log

I have type=unity in 10-unity-system-compositor.conf, any idea ?

p.s. im using nvidia driver

---

### Post by mc4man on 2013-07-31
I'm heading out -  all the relevant here - 
>  grep -i xmir /var/log/Xorg.0.log
[    25.500] xorg-server 2:1.14.2-0ubuntu3+xmir1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    25.536] (II) LoadModule: "xmir"
[    25.536] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
[    25.643] (II) Module xmir: vendor="X.Org Foundation"
[    25.678] (II) NOUVEAU(0): Output XMIR-1 has no monitor section
[    25.678] (II) NOUVEAU(0): Printing probed modes for output XMIR-1
[    25.678] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)
[    25.678] (II) NOUVEAU(0): Output XMIR-1 connected
[    25.678] (II) NOUVEAU(0): Output XMIR-1 using initial mode XMIR mode of death
[    25.678] (**) NOUVEAU(0):  Driver mode "XMIR mode of death": 71.0 MHz (scaled from 0.0 MHz), 49.3 kHz, 59.9 Hz
[    25.678] (II) NOUVEAU(0): Modeline "XMIR mode of death"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz eP)

grep -i LoadModule /var/log/Xorg.0.log
[    25.519] (II) LoadModule: "glx"
[    25.536] (II) LoadModule: "xmir"
[    25.655] (II) LoadModule: "nvidia"
[    25.673] (II) UnloadModule: "nvidia"
[    25.673] (II) LoadModule: "nouveau"
[    25.674] (II) LoadModule: "vesa"
[    25.674] (II) LoadModule: "modesetting"
[    25.674] (II) LoadModule: "fbdev"
[    25.675] (II) LoadModule: "nvidia"
[    25.675] (II) UnloadModule: "nvidia"
[    25.675] (II) LoadModule: "nouveau"
[    25.676] (II) UnloadModule: "nouveau"
[    25.676] (II) LoadModule: "vesa"
[    25.676] (II) UnloadModule: "vesa"
[    25.676] (II) LoadModule: "modesetting"
[    25.676] (II) UnloadModule: "modesetting"
[    25.676] (II) LoadModule: "fbdev"
[    25.677] (II) UnloadModule: "fbdev"
[    25.677] (II) UnloadModule: "vesa"
[    25.677] (II) UnloadModule: "modesetting"
[    25.677] (II) UnloadModule: "fbdev"
[    25.678] (II) LoadModule: "dri2"
[    25.678] (II) LoadModule: "fb"
[    25.679] (II) LoadModule: "exa"
[    25.679] (II) LoadModule: "shadowfb"
[    25.759] (II) LoadModule: "evdev"
[    25.798] (II) LoadModule: "synaptics"

 ps afx | grep unity-system-com |grep -v grep
  971 ?        S      0:00  \_ /bin/sh /usr/sbin/unity-system-compositor.sleep --enable-input=false --from-dm-fd 8 --to-dm-fd 13 --vt 7
  974 ?        Sl     0:03  |   \_ /usr/sbin/unity-system-compositor --enable-input=false --from-dm-fd 8 --to-dm-fd 13 --vt 7

apt-cache policy lightdm
lightdm:
  Installed: 1.7.5bzr1634saucy0
  Candidate: 1.7.9-0ubuntu1
  Version table:
     1.7.9-0ubuntu1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
 *** 1.7.5bzr1634saucy0 0
        100 /var/lib/dpkg/status

cat  /etc/lightdm/lightdm.conf.d/10-unity-system-compositor.conf 
[SeatDefaults]
type=unity
unity-compositor-command=unity-system-compositor.sleep --enable-input=false

---

### Post by ventrical on 2013-07-31
I had to roll back to an earlier version about a week and a half ago. It was completely busted after upgrade but u was still able to roll back. Will try an update now. (Intel)

---

### Post by grahammechanical on 2013-07-31
> **cecilpierce said:**
> All I get is:

grep -i xmir /var/log/Xorg.0.log
[   608.219] xorg-server 2:1.14.2-0ubuntu3+xmir1

and no [ 37.781] (II) LoadModule: "xmir" with grep -i LoadModule /var/log/Xorg.0.log

I have type=unity in 10-unity-system-compositor.conf, any idea ?

p.s. im using nvidia driver

This is the problem > p.s. im using nvidia driver 

It has to be Nouveau at the moment. Canonical is negotiating with relevant proprietary driver developers about getting their drivers to work with mir.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

At least it seems that one noticeable bug has been fixed but I am seeing the insertion point jump in the terminal as well as the messed up shutdown screen.

---

### Post by ventrical on 2013-07-31
On my Dell (Intel)

ventrical@ventrical-Dell-DV051:~$ grep -i LoadModule /var/log/Xorg.0.log
[    97.639] (II) LoadModule: "glx"
[    97.641] (II) LoadModule: "intel"
[    97.642] (II) LoadModule: "vesa"
[    97.642] (II) LoadModule: "modesetting"
[    97.643] (II) LoadModule: "fbdev"
[    97.648] (II) LoadModule: "fbdevhw"
[   100.122] (II) LoadModule: "dri2"
[   100.122] (II) UnloadModule: "vesa"
[   100.123] (II) UnloadModule: "modesetting"
[   100.123] (II) UnloadModule: "fbdev"
[   100.185] (II) LoadModule: "evdev"
ventrical@ventrical-Dell-DV051:~$ grep -i xmir /var/log/Xorg.0.log
[    97.633] xorg-server 2:1.14.2-0ubuntu3+xmir1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    97.648] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.9+xmir15871-2~saucy1 (Chris Halse Rogers <chris@cooperteam.net>)
ventrical@ventrical-Dell-DV051:~$ 

It identified the right driver but is not working. This obviously is a regression.

edit:

The intel graphics hardware I am using on my Old Dell Dimension is probably obsoleted and I have had no luck with ATi or newer nVidia cards

---

### Post by cecilpierce on 2013-07-31
Sorry, I had to go back to nvidia for now, the nouveau just goes crazy. 
Im using the 304 nvidia, wonder if the 319 works any better ?

---

### Post by mc4man on 2013-08-01
> **cecilpierce said:**
> Sorry, I had to go back to nvidia for now, the nouveau just goes crazy. 
Im using the 304 nvidia, wonder if the 319 works any better ?
319 doesn't benefit my card but certainly may for others.

Atm, at least here, the u-s-c/mir ppa doesn't work with the nvidia drivers, (log in to a non-3d session), hopefully it will between now & whenever xmir is dropped into 13.10
By work mean fallback to X with no issues when using the nvidia driver.
 That  may prove to be the best option for 13.10 users with nvidia adapters to get away from poor xmir & nouveau performance if it's not vastly improved.

---

### Post by cecilpierce on 2013-08-01
I dought if nvidia will make a driver for mir, they were thinking about wayland awhile back but hanen't heard any news yet, at least wayland works with either. Wait and see what happens.

---

### Post by installshield on 2013-08-01
Does anyone see todays updates as of now? It wants to bring in unity8 packages and wants to remove indicators...:(

---

### Post by mc4man on 2013-08-01
> **installshield said:**
> Does anyone see todays updates as of now? It wants to bring in unity8 packages and wants to remove indicators...:(

Doesn't 'want' to install unity8 here, it's available to install ('new in repository') & nothing to remove - 
Ex.
> $ sudo apt-get  install  unity8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdee-qt5-3 libhud2 libqdjango-db0 libqmenumodel0 libqt5qml-graphicaleffects libqt5svg5 libqt5xmlpatterns5
  libunity-action-qt1 libusermetricsoutput1 qmenumodel-qml qtdeclarative5-dee-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-window-plugin qtdeclarative5-xmllistmodel-plugin sqlite3 ubuntu-ui-toolkit-theme unity8-fake-env
  unity8-private usermetricsservice
Suggested packages:
  sqlite3-doc
Recommended packages:
  indicator-battery indicator-time
The following NEW packages will be installed:
  libdee-qt5-3 libhud2 libqdjango-db0 libqmenumodel0 libqt5qml-graphicaleffects libqt5svg5 libqt5xmlpatterns5
  libunity-action-qt1 libusermetricsoutput1 qmenumodel-qml qtdeclarative5-dee-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin qtdeclarative5-unity-notifications-plugin
  qtdeclarative5-window-plugin qtdeclarative5-xmllistmodel-plugin sqlite3 ubuntu-ui-toolkit-theme unity8
  unity8-fake-env unity8-private usermetricsservice
0 upgraded, 23 newly installed, 0 to remove and 11 not upgraded.
Need to get 8,555 kB of archives.
After this operation, 17.8 MB of additional disk space will be used.

---

### Post by mc4man on 2013-08-03
With unity8/mir  on a desktop install likely being pushed back to 14.10 then they'll have plenty of time to get xmir/unity/compiz fixed up by 14.04
*appears here that they'll need the extra time, at least for nvidia

---

### Post by ventrical on 2013-08-04
> **mc4man said:**
> With unity8/mir  on a desktop install likely being pushed back to 14.10 then they'll have plenty of time to get xmir/unity/compiz fixed up by 14.04
*appears here that they'll need the extra time, at least for nvidia


 Thanks for that news.  I had it working  on (Intel) Dell Dimension and (ATi) Radeon but could not get it up with nVidia nouveau. After update/upgrade the Intel and ATi installs no longer work , are severly impaired and won't roll back to X. Of course those are i386 installs. Might as well try amd64.

---

### Post by mc4man on 2013-08-04
> **ventrical said:**
> Thanks for that news.  I had it working  on (Intel) Dell Dimension and (ATi) Radeon but could not get it up with nVidia nouveau. After update/upgrade the Intel and ATi installs no longer work , are severly impaired and won't roll back to X. Of course those are i386 installs. Might as well try amd64.

At least thru 14.04, while I'd prefer nouveau of this laptop, worst case will be interested if 'fallback to X' works & if so does it show ill effects just by having xmir mesa packages installed.
(currently it does have poor performance with xmir libs & unity-system-compositor disabled.

If I understand correctly, -  if prop drivers are installed the idea would be to fallback, currently maybe it does though hard to tell because I can't get 3d support with nvidia drivers enabled, just a Desktop with no compiz/unity.

One make or break for me thru 14.04 is whether there is any horizontal tearing, anywhere,  inc. videos. Without any xmir libs I have absolutely none, with xmir libs installed it's all over the place in spades. 
(when they were working on improving no tearing in compiz during 12.04 dev there was no concern with tearing in videos, never could understand that though as things worked out tearing was eliminated here everywhere.

For testing I have some short movie clips that where good tests of vsync, though I don't go around posting them.
Here is a short tear test vid if interested, the 'pole' should never break, either in a window or fullscreen.
(right click on link> 'save link as'  teartest.mp4
[http://ubuntuone.com/6XdNK246Q4sGUp5X6RexIT](http://ubuntuone.com/6XdNK246Q4sGUp5X6RexIT)

---

### Post by ventrical on 2013-08-04
> **mc4man said:**
> At least thru 14.04, while I'd prefer nouveau of this laptop, worst case will be interested if 'fallback to X' works & if so does it show ill effects just by having xmir mesa packages installed.
(currently it does have poor performance with xmir libs & unity-system-compositor disabled.


  It actually works as if it thinks it is still in xmir. The Unity Dash is absolutely useless (Intel) and it takes eons to  snap off the dash and to shut down.

as for 64bit .. Just downloaded the daily and I still have those horizontal bars in Ubiquity so I do not have hi-hopes for xmir desktop at present.

Thanks .. you saved me $700 I was going to spend on an Intel i7 with HD Intel graphics mobo.

---

### Post by mc4man on 2013-08-04
> **ventrical said:**
> It actually works as if it thinks it is still in xmir. The Unity Dash is absolutely useless (Intel) and it takes eons to  snap off the dash and to shut down.

An interesting thing here with nouveau (8400m), is to maximize the Dash

---

