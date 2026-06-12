---
title: "xrdp frame rate low"
date: 2018-07-12
forum: Virtualisation
---

### Post by fabian.2908 on 2018-07-12
Hello,

I have set up a Virtual Machine via ESXi:

Ubuntu 18.04
CPU: 8 x 3.5Ghz
RAM: 64GB
SSD: 200gb
connection speed: ~800Mbit/s

I have only installed xrdp yet.

Connecting to it via my win10 surface book gives me a very low refresh rate. Opening firefox takes like 3 different renderings and 15 seconds. (My connection speed at home is ~200Mbit/s.)

Do you guys have an idea why it´s so incredibly slow && how to improve perfomance?

Thanks in advance

---

### Post by TheFu on 2018-07-12
Linux isn't Windows.

Too much RAM, too many CPUs.   Try 4G of RAM and 1 vCPU.  How does that work?  Seriously, over-provisioning because you can isn't a good idea for any desktop.  If you are trying to code Android or Java applications, make it 16G and 2 vCPUs.

Also, the DE used matters a bunch.  Unity/KDE/Gnome3 are "heavy" and will slow things down because each of them wants direct access to a GPU.  If you can't provide direct access to the GPU, then using a lighter DE or no DE is recommended.  Something like XFCE, LXDE, or Mate are commonly recommended.

Also, some Firefox users have had terrible performance issues running inside VMs since last October. Chromium still performs well, however. I'm a FF user, but on 1 of my VM desktops (I connect using x2go), FF performance is painful - like 30 seconds from user-input until something begins to happen. I've tried to correct it a few times and run the mainline FF from the updated repos, still performance sucks. There is 1 fix for my situation.  Disable all privacy firefox addons.  Oddly, that seems to solve it, but that is unacceptable to me.   I don't see this issue on a cheap laptop running firefox, however. 

If the issue happens with other browsers too, then it is likely a DNS/networking problem.

Anyways, hopefully when you search the mozilla forums for solutions, you'll find the 3-6 that I did and one of those will work for you.   I think the main solution was around disabling accessibility options.

Welcome to the forums.

---

