---
title: "New nvidia proprietary beta driver 302.07"
date: 2012-05-02
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-02
The newest nvidia proprietary driver version 302.07 (beta) can be downloaded from xorg-edgers.
Pay attention, however, that this build is only for xserver 1.12 branch.

This driver works fine with kernel 3.4.0-1.

---

### Post by effenberg0x0 on 2012-05-03
This is good news, finally.

It's also available on NVidia FTP. You can FTP/wget it from:

**32-Bit**
download.nvidia.com/XFree86/Linux-x86/302.07/NVIDIA-Linux-x86-302.07.run

**64-Bit**
download.nvidia.com/XFree86/Linux-x86_64/302.07/NVIDIA-Linux-x86_64-302.07.run

Regards,
Effenberg

---

### Post by markbl on 2012-05-03
So graphic card experts, what's the best way to go - install the xorg edgers crack pushers ppa, or use the 302.07 download file direct from the nvidia site?

---

### Post by cariboo on 2012-05-03
> **markbl said:**
> So graphic card experts, what's the best way to go - install the xorg edgers crack pushers ppa, or use the 302.07 download file direct from the nvidia site?

If you are a click-to-install enthusiast, using the xorg-edgers ppa is the easiest way to install the latest nvidia driver.

---

### Post by markbl on 2012-05-03
> **cariboo907 said:**
> If you are a click-to-install enthusiast, using the xorg-edgers ppa is the easiest way to install the latest nvidia driver.
It is just that using the edgers ppa means you pull in a lot more newer xorg stuff as well. Is that safe?

---

### Post by Harry33 on 2012-05-03
> **markbl said:**
> It is just that using the edgers ppa means you pull in a lot more newer xorg stuff as well. Is that safe?

Yes you do.
Xserver 1.12.1 and a number of accompanying drivers for example.
Then again xserver 1.12 branch works fine and that is what will be in Quantal anyway.

---

### Post by markbl on 2012-05-03
> **Harry33 said:**
> 
This driver works fine with kernel 3.4.0-1.
The current 12.04 kernel is 3.2.0-24. Now I am adding the xorg edgers ppa, should/must I upgrade to the 3.4.0-1 kernel version there?

---

### Post by Cheesemill on 2012-05-03
> **markbl said:**
> The current 12.04 kernel is 3.2.0-24.

Yes but the current 12.10 kernel is 3.4.0. This forum is for people testing 12.10 after all :)

---

### Post by effenberg0x0 on 2012-05-03
I think it's a matter of opinion. I try to keep my testing systems PPA free during the cycle, so I am sure to see the bugs in default packages. 

Regards,
Effenberg

---

### Post by dino99 on 2012-05-03
> **effenberg0x0 said:**
> I think it's a matter of opinion. I try to keep my testing systems PPA free during the cycle, so I am sure to see the bugs in default packages. 

Regards,
Effenberg

Does exactly the same way, only picking from ppa when there is no other choice. So reporting is far better as its fully genuine.

---

### Post by Harry33 on 2012-05-03
> **markbl said:**
> The current 12.04 kernel is 3.2.0-24. Now I am adding the xorg edgers ppa, should/must I upgrade to the 3.4.0-1 kernel version there?

Depends on how far away from Precise you are willing to go:
- xserver 1.12 will never come to Precise
- kernel 3.4 will never come to Precise

If you enable the xorg-edgers PPA, be sure to enable the Precise branch only.

---

### Post by fjgaude on 2012-05-03
> **Harry33 said:**
> Depends on how far away from Precise you are willing to go:
- xserver 1.12 will never come to Precise
- kernel 3.4 will never come to Precise

If you enable the xorg-edgers PPA, be sure to enable the Precise branch only.

Are you certain that kernel 3.4 will never to to 12.04 LTS? Because of lack of gcc 4.7? More?

---

### Post by 3vi1 on 2012-05-03
> **fjgaude said:**
> Are you certain that kernel 3.4 will never to to 12.04 LTS? Because of lack of gcc 4.7? More?

They never rev kernels for previous releases;  Precise will only receive 3.2 fixes.

---

### Post by VinDSL on 2012-05-03
> **markbl said:**
> It is just that using the edgers ppa means you pull in a lot more newer xorg stuff as well. **[COLOR="DarkRed"]Is that safe?[/COLOR]**
Can't say it's always safe, but at the moment, edgers et al. is working fine for me...  ;)


```
vindsl@Zuul:~$ echo && echo -n "Date/Time: " && date && echo -n "Release: " && lsb_release -sd && echo -n "Kernel: " || cat /etc/*release && uname -s -r && echo -n "Unity: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo || echo &&  dpkg -s mesa-utils && echo || echo && echo "Xserver xorg core:" && apt-cache policy xserver-xorg-core | grep Installed && echo

Date/Time: Thu May  3 17:57:02 MST 2012
Release: Ubuntu quantal (development branch)
Kernel: Linux 3.4.0-1-generic-pae
Unity: unity 5.10.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 302.07

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

Xserver xorg core:
  Installed: 2:1.12.1+git20120502+server-1.12-branch.ed33772a-0ubuntu0ricotz

vindsl@Zuul:~$ 
```

---

### Post by Yahoé on 2012-05-04
After upgrading to 302.07-0ubuntu1~xedgers~quantal1, upon reboot I have a  nice looking system but somehow I loose control of the keyboard and pad  onced logged in, but not at the  lightdm level, removing nvidia-current  fixes it.
Any idea why?

---

### Post by TerryT on 2012-05-10
My experience with the (64bit) 302.07 beta driver was not good.

The driver installed fine and seemed ok at first, but my X session would sometimes crash when playing video. This would kill everything and put me back at the login window. Everything has been fine after returning to the nouveau driver which compiz seems happy with on my system. I guess I need to wait for a future update.

My video hardware is GeForce 8800 GTS.

Terry

---

### Post by VMC on 2012-05-10
Ever since 12.04 went with the newer Xor, nothing works.

I've tried every conceivable nvidia driver know to man. They all look great as long as I don't touch anything.

Any activity is slow. R-clicking on any menu is painfully slow.

I think this all has to do with what nvidia hardware one has.

mine is 6 series 6150SE.

Quantal is "X.Org X Server 1.11.3", which I think is the same as Precise.

---

### Post by Harry33 on 2012-05-11
> **VMC said:**
> Ever since 12.04 went with the newer Xor, nothing works.

I've tried every conceivable nvidia driver know to man. They all look great as long as I don't touch anything.

Any activity is slow. R-clicking on any menu is painfully slow.

I think this all has to do with what nvidia hardware one has.

mine is 6 series 6150SE.

Quantal is "X.Org X Server 1.11.3", which I think is the same as Precise.

According to Nvidia.co.uk stable driver version 295.49 supports GeForce 6150 SE.
This driver supports xserver 1.12 too.

---

### Post by VMC on 2012-05-11
> **Harry33 said:**
> According to Nvidia.co.uk stable driver version 295.49 supports GeForce 6150 SE.
This driver supports xserver 1.12 too.

I tried each of these drivers on fresh installs. They all react the same - slow, sluggish, etc:

NVIDIA-Linux-x86_64-280.11.run
NVIDIA-Linux-x86_64-290.10.run
NVIDIA-Linux-x86_64-295.20.run
NVIDIA-Linux-x86_64-295.33.run
NVIDIA-Linux-x86_64-295.49.run
NVIDIA-Linux-x86_64-302.07.run

---

### Post by Harry33 on 2012-05-11
> **VMC said:**
> I tried each of these drivers on fresh installs. They all react the same - slow, sluggish, etc:

NVIDIA-Linux-x86_64-280.11.run
NVIDIA-Linux-x86_64-290.10.run
NVIDIA-Linux-x86_64-295.20.run
NVIDIA-Linux-x86_64-295.33.run
NVIDIA-Linux-x86_64-295.49.run
NVIDIA-Linux-x86_64-302.07.run

Nvidia-current_295.49 is also in the Quantal official repos (componet restricted).

---

### Post by Yellow Pasque on 2012-05-11
> **3vi1 said:**
> They never rev kernels for previous releases;  Precise will only receive 3.2 fixes.

Since Precise is an LTS release, it will receive optional backported kernels just like Lucid. Also, one can use 3.4 from the mainline kernel ppa.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by Harry33 on 2012-05-11
> **Temüjin said:**
> Since Precise is an LTS release, it will receive optional backported kernels just like Lucid. Also, one can use 3.4 from the mainline kernel ppa.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

Well no need to use the mainline 3.4.0 as the one in Quantal official repos will work fine, with Ubuntu patches.

---

### Post by philinux on 2012-05-11
> **effenberg0x0 said:**
> I think it's a matter of opinion. I try to keep my testing systems PPA free during the cycle, so I am sure to see the bugs in default packages. 

Regards,
Effenberg

+1. I really don't see the point in testing with ppa's and non standard installs.

---

### Post by VMC on 2012-05-11
> **Harry33 said:**
> Nvidia-current_295.49 is also in the Quantal official repos (componet restricted).

Is this better than nvidia drivers? I tried one of the nvidia official repos during a late Precise install, with the same results.

---

### Post by Harry33 on 2012-05-12
> **VMC said:**
> Is this better than nvidia drivers? I tried one of the nvidia official repos during a late Precise install, with the same results.

That is in official repos.
In Ubuntu it is build against xserver 1.11
and the one I use (from xorg-edgers)
is built against xserver 1.12.

The ones in official repos do contain the patch to build with appropriate kernel:
in Precise with kernel 3.2
and in Quantal with 3.4.

---

