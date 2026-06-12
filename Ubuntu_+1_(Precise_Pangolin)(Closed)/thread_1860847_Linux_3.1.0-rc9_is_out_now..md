---
title: "Linux 3.1.0-rc9 is out now."
date: 2011-10-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2011-10-15
Don't know if anyone noticed, but 3.1.0-rc9 (patched) is out now.

LINKAGE:  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc9-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-rc9-oneiric/)

Seems to be working fine in UbuPP...  ;)

```
vindsl@Zuul:~$ echo && date && lsb_release -sd || cat /etc/*release && uname -s -r && unity --version && echo && /usr/lib/nux/unity_support_test -p -f || echo && dpkg -s mesa-utils && echo

Sat Oct 15 03:10:40 MST 2011
Ubuntu precise (development branch)
Linux 3.1.0-0301rc9-generic
unity 4.22.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 280.13

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

```

---

### Post by ubupirate on 2011-10-15
3.1.0-rc9 has been on the Mainline Kernel listing since October 5th, so not exactly out "now". :P

---

### Post by zika on 2011-10-15
> **ubupirate said:**
> 3.1.0-rc9 has been on the Mainline Kernel listing since October 5th, so not exactly out "now". :PNevertheless it is fresher than "daily" or "current"... :)

---

### Post by ventrical on 2011-10-15
Thanks Vin.

---

### Post by Atamisk on 2011-10-15
i use rc7 on my desktop, and rc9 on my laptop. Both work great in 11.10, but my battery life is still too short...

TBH, i haven't even booted ubuntu's distributed kernel for Oneiric... :P

---

### Post by paul_in_london on 2011-10-15
> **ubupirate said:**
> 3.1.0-rc9 has been on the Mainline Kernel listing since October 5th, so not exactly out "now". :P

Yes, been using it since it came out. Seems to be working well.

---

### Post by ventrical on 2011-10-15
@VinDSL or all,

How do I set up my Precise system to get this repository for the rc kernels.?

thanks..

---

### Post by zika on 2011-10-15
> **ventrical said:**
> @VinDSL or all,

How do I set up my Precise system to get this repository for the rc kernels.?

thanks..As far as I know, You have to do it everytime, step-by-step on Your own. Or make a script.

---

### Post by VinDSL on 2011-10-15
> **ventrical said:**
> @VinDSL or all,

How do I set up my Precise system to get this repository for the rc kernels.?

thanks..

> **zika said:**
> As far as I know, You have to do it everytime, step-by-step on Your own. Or make a script.
I install kernels from CLI.

There are many ways of doing this, but here's the drill I use...

[LIST]
[*]Download the appropriate .deb files to ~/Downloads/Kernel (in my case)


[LIST]
[*]linux-headers..._i386.deb
[*]linux-headers..._all.deb
[*]linux-image..._i386.deb
[/LIST]


[*]Open a terminal
[/LIST]
```

cd Downloads/Kernel

sudo dpkg -i *.deb

sudo reboot

```

That's it.

Sometimes, installing a new kernel will require reinstalling nvidia-current.  It doesn't happen very often, but...

If you're met with a black screen @ boot, reinstalling your video drivers will usually take care of the situation.  ;)

---

### Post by MacUntu on 2011-10-15
Where the heck is 3.1? :D

I'm wondering: does anyone already know if Ubuntu will stick to 3.1 due to 12.04 being a LTS (given that 3.2 would take another 2-3 months)?

---

### Post by zika on 2011-10-17
New daily appeared today... ;)

---

### Post by zika on 2011-10-24
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.1-oneiric/)

---

### Post by ventrical on 2011-10-24
> **zika said:**
> As far as I know, You have to do it everytime, step-by-step on Your own. Or make a script.


Thanks zika .. yeah .. I did it from terminal.

---

### Post by ventrical on 2011-10-24
> **VinDSL said:**
> I install kernels from CLI.

There are many ways of doing this, but here's the drill I use...

[LIST]
[*]Download the appropriate .deb files to ~/Downloads/Kernel (in my case)
[LIST]
[*]linux-headers..._i386.deb
[*]linux-headers..._all.deb
[*]linux-image..._i386.deb
[/LIST]
[*]Open a terminal
[/LIST]
```

cd Downloads/Kernel

sudo dpkg -i *.deb

sudo reboot

```That's it.

Sometimes, installing a new kernel will require reinstalling nvidia-current.  It doesn't happen very often, but...

If you're met with a black screen @ boot, reinstalling your video drivers will usually take care of the situation.  ;)

Thanks VinDSl,

It worked really great! :)

---

### Post by lan3y on 2011-10-24
3.1.0-0301rc9-generic_3.1.0-0301rc9.201110181311 breaks things for me, anyone else having problems?

---

### Post by effenberg0x0 on 2011-10-24
> **lan3y said:**
> 3.1.0-0301rc9-generic_3.1.0-0301rc9.201110181311 breaks things for me, anyone else having problems?

No, not seeing any difference here. None of the bugs I know were fixed, no big change for me.

Regards,
Effenberg

---

