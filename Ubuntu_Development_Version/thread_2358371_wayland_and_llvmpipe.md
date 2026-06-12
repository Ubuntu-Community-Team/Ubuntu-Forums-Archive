---
title: "wayland and llvmpipe"
date: 2017-04-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-04-12
Develpment question:

Will wayland use llvmpipe like ubuntu-desktop has so often done since trusty, literally bricking the performance of an install?

Regards..

---

### Post by #&amp;thj^% on 2017-04-12
Hey Vent have a look at this: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
> 
Supported Ubuntu versions:
- 16.04 (xenial)
- 16.10 (yakkety)

For forum support see: [http://goo.gl/qoUpWK](http://goo.gl/qoUpWK)

=== Introduction ===
This PPA provides updated X (2D) and mesa (3D) free graphics drivers for radeon, intel and nvidia hardware. Updates packages provide:
 * OpenGL 4.5+ support and new OpenGL extensions: [http://mesamatrix.net](http://mesamatrix.net)
 * packages built against llvm-3.9
 * gallium-nine support installed by default. Read the specific section below
 * VDPAU, OpenMAX IL Bellagio, VAAPI and XvMC Gallium3D accelerated video drivers (see below)
 * OpenCL support (mesa-opencl-icd package), including updated libclc
 * r600 LLVM compiler, enabled with R600_DEBUG=llvm env var
 * optional GLAMOR acceleration on radeon (>= r300), and nouveau drivers
 * i915 gallium driver replaces by default i915 classic driver
 * experimental ilo (intel) and virgl (virtio-gpu) gallium drivers (see below)

I have it working on 17.04 also

---

### Post by ventrical on 2017-04-12
Thanks 1fallen,

I was hoping I did not have to use a ppa. Trying to encourage a new convert(s) it makes it so difficult to babysit.. I guess thats the way the cookie crumbles. The reason I am asking is  that I was hoping *well I am about to try) and see if wayland  will use llvmpipe emutlator on gnome3 as it does on unity7.
Downloading now.
Yes.. xubuntu too..;)

---

### Post by #&amp;thj^% on 2017-04-12
> **ventrical said:**
> Thanks 1fallen,

I was hoping I did not have to use a ppa. Trying to encourage a new convert(s) it makes it so difficult to babysit.. I guess thats the way the cookie crumbles. The reason I am asking is  that I was hoping *well I am about to try) and see if wayland  will use llvmpipe emutlator on gnome3 as it does on unity7.
Downloading now.
Yes.. xubuntu too..;)

Understood.... then this will probably be a real pain for a newer user, as there is some editing to be done with /etc/X11/xorg.
You know I hate holding my breath here....but it really should be fixed soon...Yeah I know>> famous last words, Right?:lolflag:
Regards

---

### Post by ventrical on 2017-04-24
@1fallen

Good news! On a system I have be using as a bare metal tester I was getting llvmpipe with all my ubuntu-desktop installs. I installed ubuntu-gnome 17.04 and upgraded to 17.10 and now it is using the nVidia  open_source driver. whew!!

Regards..

---

### Post by #&amp;thj^% on 2017-04-24
Hey Hey! That is Great news....less baby sitting now for the new converts.
BTW I had noticed very little performance differences between the two drivers....non-factor here.
How is yours doing...might still be a bit early though on a fresh install and all.
Let me know after some use...if you think about it.
Thanks vent.

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Hey Hey! That is Great news....less baby sitting now for the new converts.
BTW I had noticed very little performance differences between the two drivers....non-factor here.
How is yours doing...might still be a bit early though on a fresh install and all.
Let me know after some use...if you think about it.
Thanks vent.

I left it below with the wayland peformance:


[https://wiki.ubuntu.com/U%2B1/Blog#preview](https://wiki.ubuntu.com/U%2B1/Blog#preview)

but it is an older box.

Regards..

---

### Post by ventrical on 2017-04-24
> **1fallen said:**
> Hey Hey! That is Great news....less baby sitting now for the new converts.


Uh  :)   wish I could share the same sentiments. This happened during trusty beta testing of a Kubuntu install. It was working just beautifully and then, all of a sudden, one update later and it was trash.:) .. but I share your enthusiasm... I mean .. What! Me worry?hehehehe :)


Regards..

---

### Post by ventrical on 2017-04-25
Surprise!

Installing from <nomodeset> same machine.

---

