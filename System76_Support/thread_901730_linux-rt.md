---
title: "linux-rt"
date: 2008-08-26
forum: System76 Support
---

### Post by Emblem Parade on 2008-08-26
Hi,

I just got my new Pangolin Performance, and it looks great so far.

Except... that I installed linux-rt (I need it for audio recording) and I can't get the graphics driver to work well. It keeps booting into low-graphics mode. I've tried to reinstall the system76 drivers on that kernel, but to no avail.

---

### Post by thomasaaron on 2008-08-27
The System76 driver doesn't compile nVidia on the PanP4n.

Try going to System > Administration > Hardware Drivers and activating nvidia.

If it is not there, try running:
sudo apt-get install nvidia-glx-new

Then try activating it from the Hardware Drivers utility.

So, did you do a fresh install?

---

### Post by Emblem Parade on 2008-08-27
Thanks for the tip!

I solved the problem by installing EnvyNG (package name: envyng-gtk, or envyng-qt if you are using KDE), which nicely installs the latest and greatest ATI/NVIDIA drivers. It basically does what the system76 driver installer does, and is a nice complement to it.

I think my confusion could have been avoided had the system76 driver installer told me exactly what drivers it was installing on my system in its UI.

So, yes, the Pangolin works great with a realtime Linux kernel (linux-rt), and I was up and recording music with Ardour within minutes. All the other drivers (webcam, wifi, etc.) seem to work.

---

