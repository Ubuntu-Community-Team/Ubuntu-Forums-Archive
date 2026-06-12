---
title: "Precise switches to xserver 1.11.3"
date: 2012-01-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2012-01-24
Precise is switching to new release version of xserver 1.11.3.
This means all input and video drivers (also proprietary ones) must be upgraded to the version built against xserver 1.11 branch.
The new abi is:
- xserver-video-abi-11
- xserver-input-abi-16

This canonical version of xserver contains the input system from xserver 1.12 branch, so it is different than almost any common PPA version.

For example:

xserver-xorg-core:
[https://launchpad.net/ubuntu/precise/amd64/xserver-xorg-core/2:1.11.3-0ubuntu8](https://launchpad.net/ubuntu/precise/amd64/xserver-xorg-core/2:1.11.3-0ubuntu8)

xserver-xorg-input-evdev
[https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.6.99.901-1ubuntu2](https://launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/1:2.6.99.901-1ubuntu2)

nvidia-current:
[https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2](https://launchpad.net/ubuntu/precise/amd64/nvidia-current/290.10-0ubuntu2)

---

### Post by Harry33 on 2012-01-24
Some more info on the other related xserver versions.

Xserver 1.10 (previous Precise xserver):
- xserver-video-abi-10
- xserver-input-abi 12

Xserver 1.11 (original) not in Precise:
- xserver-video-input-11
- xserver-input-abi-14

Xserver 1.12 (original rc1) not in Precise:
- xserver-video-input-12
- xserver-input-abi-16
This version is in Xorg-edgers PPA

---

### Post by VinDSL on 2012-01-24
Oh, my!  LoL!

I just looked at the latest upgrades (114 of them). GCC-4.5 & GCC-4.5-base worry me more than xserver.

Alrighty then, here goes nothing...  :D

---

### Post by Harry33 on 2012-01-24
> **VinDSL said:**
> Oh, my!  LoL!

I just looked at the latest upgrades (114 of them). GCC-4.5 & GCC-4.5-base worry me more than xserver.

Alrighty then, here goes nothing...  :D

I do not even have the GCC-4.5 installed. I only have GCC-4.6

---

### Post by Harry33 on 2012-01-24
BTW, this is the testing PPA for Canonical version of xserver 1.11:

Canonical X Staging PPA
[https://launchpad.net/~canonical-x/+archive/x-staging](https://launchpad.net/~canonical-x/+archive/x-staging)

---

### Post by VinDSL on 2012-01-24
I see.

Okay, well, I upgraded using the regular repos, and Liquorix is still working...


```
vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo

Tue Jan 24 01:36:26 MST 2012
Ubuntu precise (development branch)
Linux 3.2.0-1.dmz.4-liquorix-686
unity 5.0.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 290.10

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
Package: mesa-utils
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 132
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: i386
Source: mesa-demos
Version: 8.0.1+git20110129+d8f7d6b-0ubuntu2
Replaces: xbase-clients (<< 6.8.2-38)
Depends: libc6 (>= 2.4), libgl1-mesa-glx | libgl1, libx11-6
Description: Miscellaneous Mesa GL utilities
 This package provides several basic GL utilities built by Mesa, including
 glxinfo and glxgears.
Homepage: http://mesa3d.sourceforge.net/

vindsl@Zuul:~$ 

```

```
<snip>

[    18.544] X.Org X Server 1.11.3 Release Date: 2011-12-16
[    18.545] X Protocol Version 11, Revision 0
[    18.545] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    18.545] Current Operating System: Linux Zuul 3.2.0-1.dmz.4-liquorix-686 #1 ZEN SMP PREEMPT Sun Jan 22 01:00:13 UTC 2012 i686
[    18.545] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-1.dmz.4-liquorix-686 root=UUID=28a17342-3d9b-4306-96cf-3bd092645ce7 ro quiet splash nomodeset nouveau.modeset=0 vt.handoff=7
[    18.545] Build Date: 23 January 2012  05:39:24AM
[    18.545] xorg-server 2:1.11.3-0ubuntu8 (For technical support please see http://www.ubuntu.com/support) 

<snip>
```

Sooo, I'm a happy camper.  :D

---

### Post by VinDSL on 2012-01-24
Gotta say...

I'm rather disappointed with this UbuPP alpha.

I've grown accustomed to more breakage at this point in the dev cycle.  Don't think it's gonna happen.

Oh, well...  :)

---

### Post by kaldor on 2012-01-24
> **VinDSL said:**
> I've grown accustomed to more breakage at this point in the dev cycle.  Don't think it's gonna happen.

Oh, well...  :)

Time to move on to Fedora Rawhide! :KS

---

### Post by VinDSL on 2012-01-24
> **kaldor said:**
> Time to move on to Fedora Rawhide! :KS
LoL!  :D

---

### Post by dino99 on 2012-01-24
have made the genuine PP upgrades (no ppa) and get:

(WW) NVIDIA: This server has an unsupported input driver ABI version (have 16.0, need < 14.0).  The driver will continue to load, but may behave strangely.

 xorg-server 2:1.11.3-0ubuntu8
 Module ABI versions:
 	X.Org ANSI C Emulation: 0.4
 	X.Org Video Driver: 11.0
 	X.Org XInput driver : 16.0
 	X.Org Server Extension : 6.0

---

### Post by Harry33 on 2012-01-24
> **dino99 said:**
> have made the genuine PP upgrades (no ppa) and get:

(WW) NVIDIA: This server has an unsupported input driver ABI version (have 16.0, need < 14.0).  The driver will continue to load, but may behave strangely.

 xorg-server 2:1.11.3-0ubuntu8
 Module ABI versions:
     X.Org ANSI C Emulation: 0.4
     X.Org Video Driver: 11.0
     X.Org XInput driver : 16.0
     X.Org Server Extension : 6.0

Yes you can read that warning from xerrors.log, but it really does not harm.
It is just a reminder that nvidia-current_290.10 is not built against the ABI of xserver 1.12 branch. And that is the input system of the Canonical xserver 1.11.3.

You do have the line IgnoreABI=true in your /etc/X11/xorg.conf, don't you?

---

### Post by dino99 on 2012-01-24
> **Harry33 said:**
> Yes you can read that warning from xerrors.log, but it really does not harm.
It is just a reminder that nvidia-current_290.10 is not built against the ABI of xserver 1.12 branch. And that is the input system of the Canonical xserver 1.11.3.

You do have the line IgnoreABI=true in your /etc/X11/xorg.conf, don't you?

Thanks for the comments Harry :)

by the way this warning looks like an info rather a coming trouble, and i dont use xorg.conf at all :)

Just cosmetic false alarm :)

---

### Post by Harry33 on 2012-01-24
> **dino99 said:**
> 

  ... i dont use xorg.conf at all :)

Just cosmetic false alarm :)

OK, that means nvidia-current_290.10 works fine with Canonical xserver 1.11.3 too.
However, with xserver 1.12 rc1 one have to use xorg.conf with IgnoreABI=true option.

---

