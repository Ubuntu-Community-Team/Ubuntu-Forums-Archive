---
title: "nvida + linux + system76"
date: 2012-02-14
forum: System76 Support
---

### Post by runny6play on 2012-02-14
Is it possible to get nvidas switching tech. That allows seemless transison between the intergeted and nvida gpu.. to work under linux on system 76's

---

### Post by isantop on 2012-02-14
The technology you're referring to is called Optimus, and it has absolutely no support in Ubuntu. It actually causes a lot of problems, and can lead to computers ending up stuck on the integrated GPU, leaving the discreet GPU useless. For this reason, none of our laptops feature support for it.

---

### Post by ctsdownloads on 2012-02-18
Officially, yes there is no Optimus love on Ubuntu. _*Unofficially*_, there is a "hack work-a-round" that may not be supported by Ubuntu and I recommend asking about potentially voiding any PC warranties before trying it (hardware related warranties). Also understand that neither option is "truly" the same, rather a means of offering the same benefit. If you don't know if a voided warranty could  happen, **ask** your PC seller before messing with this. Personally,* I DON'T run it myself* because of the reasons listed above. It is dangerous and could cause big problems.
/End disclaimer.

The option is called: [Bumblebee]("http://ubuntuportal.com/bumblebee-3-0-tumblewed-nvidia-optimus-gpu-switching-for-linux-has-been-released-how-to-install-bumblebee-3-0-on-ubuntu/").

A safe tool I use on a number of laptops, is a power management applet called [Jupiter]("http://www.jupiterapplet.org/index.html"). It offers the following:
[http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=About](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=About)

It won't do anything with the GPU, but it will help with CPU usage and overall power consumption. It helps quite a bit with the newer Linux kernel and its own power saving functionality.

---

