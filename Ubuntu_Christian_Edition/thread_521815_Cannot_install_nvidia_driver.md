---
title: "Cannot install nvidia driver"
date: 2007-08-09
forum: Ubuntu Christian Edition
---

### Post by Jjan on 2007-08-09
Need help installing drivers for my video card. I am brand new to Linux so I need details, Thanx.
This is what I have done and failed.
Downloaded the driver from nvidia.
ctrl alt f1
logged on as root
sudo /etc/init.d/gdm stop
sh NVIDIA-Linux-x86-100.14.11-pkg1.run

At this point I get a message saying Cannot open sh NVIDIA-Linux-x86-100.14.11-pkg1.run
Thanx for help.
Jjan

---

### Post by Majere on 2007-08-09
I had troubles manually installing the latest Nvidia drivers as well.

If you are new linux I suggest installing Envy. This program will automatically do all the installation and configuring for you

As root type
 apt-get install envy

Once installed start X and look under applications > System Tools

Hope that helps

---

### Post by logos34 on 2007-08-09
try
**sudo** sh NVIDIA-Linux-x86-100.14.11-pkg1.run

That's if you need the latest bleeding edge driver from nvidia

otherwise you can use envy as described above, or simply go to menu>Applications>add/remove>system tools>nvidia binary xorg driver

---

### Post by Jjan on 2007-08-09
OK I got it with Envy. Thanx...

---

