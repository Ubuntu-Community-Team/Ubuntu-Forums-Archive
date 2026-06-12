---
title: "Ubuntu 14.04 runs very slowly in Win7 VirtualBox"
date: 2014-05-13
forum: Virtualisation
---

### Post by ele2 on 2014-05-13
Hi

The Ubuntu 14.04 version is running really slow in VirtualBox. I have enabled 3d video rendering and boosted the video memory to 256MB, but it is still slow
This is what i did: [http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html](http://namhuy.net/951/how-to-fix-slow-performance-ubuntu-13-04-running-in-virtualbox.html)

Vbox 4.3.10 with guest additions.

What else could i do to make it smooth?

Regards.

---

### Post by LastDino on 2014-05-13
What's your sustem config and what RAM and CPU are you alloting VM?

---

### Post by coffeecat on 2014-05-13
Support, not chat thread.

*Thread moved to **Virtualisation**.*

---

### Post by TheFu on 2014-05-14
[http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox)

---

### Post by Jake Sweeney on 2014-05-16
Try and allocate more CPU cores to the VM, or, if you wish, disable 3d graphics rendering on the virtual OS to maximise the frame-rate and put less pressure on your video card drivers

---

### Post by HiImTye on 2014-05-16
if they're using regular Ubuntu, that might actually make it slower, as it falls back to llvmpipe if you don't have 3D acceleration

try installing another desktop environment, Unity is pretty but slow. there's much faster ones such as LXDE and XFCE

---

### Post by TheFu on 2014-05-17
> **Jake Sweeney said:**
> Try and allocate more CPU cores to the VM, or, if you wish, disable 3d graphics rendering on the virtual OS to maximise the frame-rate and put less pressure on your video card drivers

More cores doesn't help usually.  1 or 2, no more. Installing with 2 (provided the hostOS has more than 2 cores!!!!!!) can make sense for Windows, so that a multi-core kernel gets installed.
I did some testing and found that enabling 3D graphics makes 14.04 desktop faster, but there are enough issues that it shouldn't be enabled during installation of the GuestOS still.
I did NOT test any Windows guests. Sorry.

---

