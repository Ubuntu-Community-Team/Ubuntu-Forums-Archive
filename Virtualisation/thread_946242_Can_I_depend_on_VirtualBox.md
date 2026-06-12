---
title: "Can I depend on VirtualBox?"
date: 2008-10-13
forum: Virtualisation
---

### Post by HuBaghdadi on 2008-10-13
Hey,
I have Ubuntu installed in my DELL Inspiron 1520
Lately, I became a distro addicted, I want to try many flavor (OpenSolaris, FreeBSD, PC-BSD, openSuse, Debian, CentOS).
The problem is I don't have an extra PC to test other OS, in addition to I don't want to miss with my laptop (it is my central nervous system).
What is important to me is to know if X OS fully supports my hardware (audio, video, Bluetooth, WiFi ...) 
Can I depend on VirtualBox to tell me what I need to know?
Thanks.

---

### Post by kosmiciatakuja on 2008-10-13
I'm not sure I understood your question but if you want to check the compatibility between the 'guest' OS (the one you install under VirtualBox or any other virtualisation software) and your hardware (like bluetooth, wifi and so on) then virtualisation is *not* the way to go. 
This is because the virtualisation software (e.g. VirtualBox) simply simulates *a* computer, but it is not *your* computer. That is why for example it sometimes need special drivers for the simulated graphic or sound card, and those drivers will not be the same as you use on your normal OS. 

If you want to check if some OS is compatible with your laptop, I would simply go with dual booting: create a separate partition for other OSes and boot them with GRUB. 

hope this helps...

---

### Post by Rhubarb on 2008-10-13
VirtualBox presents itself to the Virtualised operating system (OpenSolaris, FreeBSD, PC-BSD, openSuse, Debian, CentOS) as a Virtual Computer.

So, an operating system that runs inside virtualbox can only see the virtual hardware that virtualbox presents.
The virtualised operating system will NOT see any hardware that is running on your physical computer.

As you say, X OS must be compatible with the virtual hardware that virtualbox presents, not with the hardware that's actually your hardware.

The easiest way, is to try running / installing an OS in virtualbox and see if it picks up virtualbox's virtualised hardware.  In most cases, it does fine.

Hopefully this makes some sense to you.

To add to kosmiciatakuja's comment, another way to test if an OS will work fine with your physical hardware, is to try out a live CD of the distro if it's available.
That way you won't need to install it / dual-boot it to see if it works or not.

---

### Post by HuBaghdadi on 2008-10-13
Regarding the Live CD,
What if the system I'm evaluating works prefectly except for the sound (which could be solved be downloading a driver for example).
I mean the Live CD doesn't give a 100% feedback, right?

---

### Post by snowpine on 2008-10-13
Short of actually installing it to your hard drive, using the Live CD is the best way to tell if a distro will work on your hardware. In your example, if sound doesn't work on the Live CD and you think you need to download a driver, simply download the driver and see if it fixes the problem. 

Virtualization will not tell you what you need to know.

---

