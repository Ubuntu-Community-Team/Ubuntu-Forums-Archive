---
title: "Proposed xserver-1.19 testing"
date: 2017-03-15
forum: Ubuntu Development Version
---

### Post by mc4man on 2017-03-15
It's being proposed to be used in 17.04 thru a FFe. At least here on 2 different nvidia/optimus laptops it's currently a total bust. (at least for an ubuntu session..
Test ppa
[https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging](https://launchpad.net/~canonical-x/+archive/ubuntu/x-staging)
bug report
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1671799](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1671799)

Here once xserver is upgraded a reboot fails unless nvidia drivers are installed. If they are installed (before or after upgrade, no matter) then boot ups work whether using nvidia or intel drivers/gpu
If the nvidia drivers are subsequently removed then boot ups again fail.

Certainly could use some user testing on various hardware...

---

### Post by dino99 on 2017-03-16
Timo has identified the problem now; so the fix might come very soon :P

---

### Post by zika on 2017-03-16
Found some spare time just to give HU to those that have GA given below to be cautious:
```
Calculating upgrade... DoneThe following packages have been kept back:
  xserver-xorg-core xserver-xorg-input-evdev xserver-xorg-input-libinput xserver-xorg-input-synaptics xserver-xorg-input-wacom xserver-xorg-video-amdgpu xserver-xorg-video-fbdev xserver-xorg-video-mach64 xserver-xorg-video-neomagic xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
``````
The following packages have unmet dependencies: xserver-xorg-video-nouveau : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                       - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-video-cirrus : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                      - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-input-vmmouse : Depends: xorg-input-abi-22 which is a virtual package, provided by:
                                       - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-video-intel : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                     - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-video-ati : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                   - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-video-radeon : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                      - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


 xserver-xorg-video-mga : Depends: xorg-video-abi-20 which is a virtual package, provided by:
                                   - xserver-xorg-core (2:1.18.4-1ubuntu9), but 2:1.19.3-1ubuntu0.1 is to be installed


The following actions will resolve these dependencies:


     Remove the following packages:                                               
1)     xserver-xorg-input-vmmouse [1:13.1.0-1ubuntu2 (now)]                       
2)     xserver-xorg-video-all [1:7.7+16ubuntu2 (now, zesty)]                      
3)     xserver-xorg-video-ati [1:7.8.99+git1703111948.9a71445~y~padoka0 (now)]    
4)     xserver-xorg-video-cirrus [1:1.5.3-1ubuntu3 (now)]                         
5)     xserver-xorg-video-intel [2:2.99.917+git1703111933.ead1a0a~y~padoka0 (now)]
6)     xserver-xorg-video-mga [1:1.6.5-1 (now)]                                   
7)     xserver-xorg-video-nouveau [1:1.0.13+git1610290500.1516d35~y~padoka0 (now)]
8)     xserver-xorg-video-radeon [1:7.8.99+git1703111948.9a71445~y~padoka0 (now)] 


     Leave the following dependencies unresolved:                                 
9)     xserver-xorg-video-all recommends xserver-xorg-video-intel       
```with that PPA. Yes, I do have very fresh packages but ABI is, again, a culprit... ;)
There is a bypass but...

---

### Post by dino99 on 2017-03-16
Zika,
no such problem met while upgrading on ubuntu; so might be related to your flavor or own config. Maybe run bleachbit/gtkorphan/autoremove or whatever you wish.

---

### Post by zika on 2017-03-16
> **dino99 said:**
> Zika,
no such problem met while upgrading on ubuntu; so might be related to your flavor or own config. Maybe run bleachbit/gtkorphan/autoremove or whatever you wish.I do not see any problem either, just notice that PPA is still being filled since aforementioned drivers are not produced yet... ;) Once they are it {sh,c}ould be really usefull. In the meantime there are several other PPA's that are (almost) up-to date... ;) If it were the only one used on this install it might be without any warning/collision but, then, it would not produce similar up-to-date effect. It would be usefull if I were to use NVidia, that is true...

---

### Post by mc4man on 2017-03-16
The staging ppa would be short term & geared towards relatively fresh 17.04 installs so some of those mentioned packages wouldn't be an issue as they no longer are used
(- cirrus, vmmouse, mga are gone, the meta video package has fewer dependencies than in past..
The padoka ppa's intel package is  versioned higher than the staging so it's not updated, ect.

---

### Post by zika on 2017-03-17
Things are moving ahead as we speak... ;)
Just to clarify: I'm not complainig, I just gave HU so no one makes a mistake...
Update&#8321;: Done (but not yet in all configurations)... ;)

---

### Post by dino99 on 2017-03-19
Doing some libreoffice calc work, i've discovered an unexpected problem: wanting to select some columns & rows (> 200 cells) to apply some sort criterias, the mouse is doing some erratic jobs, like losing partial or total selection, or moving it instead of continuing to select cells.
Detials reported on the FFE bug mentioned at #1
Can you also check that issue if you have a spreadsheat where you can do some testing ?

---

### Post by #&amp;thj^% on 2017-03-19
> **dino99 said:**
> Doing some libreoffice calc work, i've discovered an unexpected problem: wanting to select some columns & rows (> 200 cells) to apply some sort criterias, the mouse is doing some erratic jobs, like losing partial or total selection, or moving it instead of continuing to select cells.
Detials reported on the FFE bug mentioned at #1
Can you also check that issue if you have a spreadsheat where you can do some testing ?

I can also see the same behavior here in "libreoffice calc".
If you add a link for your bug report.... I will add effects me too.
Thanks for confirming dino99.
Regards
Non Related:
EDIT: BTW you guys are going to like the changes in "xserver-1.19"
Been using it for a couple months now on Arch.
```
$ pacman -Qi xorg-server
Name            : xorg-server
Version         : 1.19.3-1
Description     : Xorg X server
Architecture    : x86_64
URL             : http://xorg.freedesktop.org
Licenses        : custom
Groups          : xorg
Provides        : X-ABI-VIDEODRV_VERSION=23  X-ABI-XINPUT_VERSION=24.1
                  X-ABI-EXTENSION_VERSION=10.0  x-server
Depends On      : libepoxy  libxfont2  pixman  xorg-server-common  libunwind
                  dbus  libgl  xf86-input-libinput  libpciaccess  libdrm
                  libxshmfence
Optional Deps   : None
Required By     : compiz  nvidia-utils
Optional For    : None
Conflicts With  : nvidia-utils<=331.20  glamor-egl  xf86-video-modesetting
Replaces        : glamor-egl  xf86-video-modesetting
Installed Size  : 3.47 MiB
Packager        : Laurent Carlier <snip>@gmail.com>
Build Date      : Thu 16 Mar 2017 08:49:41 AM MDT
Install Date    : Sat 18 Mar 2017 07:08:31 AM MDT
Install Reason  : Explicitly installed
Install Script  : Yes
Validated By    : Signature


```

---

### Post by dino99 on 2017-03-19
1fallen

thanks for your comments; the link is the one posted on 1st post here. Timo has made also a comment and suggested it was related to xserver-xorg-input-libinput; which was not installed on my system; will do a new test tomorrow with it installed.

---

### Post by mc4man on 2017-03-19
> **dino99 said:**
> 1fallen

thanks for your comments; the link is the one posted on 1st post here. Timo has made also a comment and suggested it was related to xserver-xorg-input-libinput; which was not installed on my system; will do a new test tomorrow with it installed.

Well by default both xserver-xorg-input-synaptics & xserver-xorg-input-libinput are installed in  Ubuntu image installs. If one is using an ubuntu session then ..synaptics is used, if on a gnome session then ..libinput is used. 
(synaptics has been rebuilt, libinput hasn't though you could in about 30 secs after getting source & deps..

One way to tell which you're using is to open System Settings > Mouse and Touchpad, screen 1 is with libinput , screen 2 with synaptics.

---

### Post by mc4man on 2017-03-19
> **1fallen said:**
> 
EDIT: BTW you guys are going to like the changes in "xserver-1.19"
Been using it for a couple months now on Arch.

Could you mention one or two things that are clearly better?

---

### Post by #&amp;thj^% on 2017-03-20
@dino99 Thanks for the information will look closer now.
> **mc4man said:**
> Could you mention one or two things that are clearly better?

Sorry about that...;) I was a bit rushed yesterday.
> Some of the new features for xorg-server 1.19 include the Windows-DRI extension, modesetting DDX and PRIME improvements, threaded input support, XWayland enhancements and more, GLAMOR improvements, the PRIME synchronization support, and a wide range of other changes. This is a big release with it being almost a year since X.Org Server 1.18 rather than the usual six month release cadence. 

If I also could add...there seems to be alot of folks running Hybrid Nvidia Chips that were not happy when it broke their systems...so it seems that ethier disabling the onboard chip in Bios, or removing (Uninstalling) the driver, proved to be a smoother transition.
My view for my specs, is better integration with themes, and flickering. (BTW I did not see any of this with dedicated Nvidia GTX 560 Ti on my tower) 
That's about all I can add so far.

---

### Post by aljosa2 on 2017-03-24
any news?

---

### Post by mc4man on 2017-03-25
> **aljosa2 said:**
> any news?
I would suspect the FFe will go thru for 17.04.
(- as far as PRIME synchronization in an ubuntu session I don't see it working. anyone with inclination to test & proper hardware can comment here
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304)

---

### Post by harry332 on 2017-03-28
So here it is.
The xserver 1.19.3 in Zesty proposed now.

[https://launchpad.net/ubuntu/+source/xorg-server/2:1.19.3-1ubuntu1](https://launchpad.net/ubuntu/+source/xorg-server/2:1.19.3-1ubuntu1)

---

### Post by mc4man on 2017-04-02
As far as PRIME synchronization, atm just doesn't work in Ubuntu, at least thru nvidia-prime
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1674304)

---

