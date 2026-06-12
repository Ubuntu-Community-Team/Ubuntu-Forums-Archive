---
title: "Nvidia support with serp4 and Ubuntu 9.04"
date: 2009-05-24
forum: System76 Support
---

### Post by andrewdied on 2009-05-24
Does Ubuntu have the Nvidia drivers for the serp4 laptop with Ubuntu 9.04?  I have the System76 2.3.5 driver loaded, and I re-applied 2.3.4 when I upgraded to 9.04 from 8.10.  (I got the 2.3.5 driver through the regular upgrade process.)

What I'm seeing is when my screen saver kicks in, the draw speed is slow and jerky.  I saw that before on an upgrade where the nvidia driver didn't get installed.  In Synaptic package manager I see several nvidia packages installed, such as xserver-xorg-video-nv and some modaliases, but don't see the nvidia-glx-dev packages installed, nor nvidia-settings.  I'm always hesitant to randomly install graphics driver packages since the results can be very bad.

Is there something easy I've missed in the upgrade?  Ubuntu uninstalled many of my closed source (or just non-Ubuntu main) packages, and I think some key nvidia packages went with it.

Thanks for the help.

---

### Post by thomasaaron on 2009-05-26
We used to actually install the nvidia drivers via the System76 Driver. We don't do that anymore. Now you have to go to System > Admin > Hardware Drivers to enable the proprietary nVidia drivers.

---

