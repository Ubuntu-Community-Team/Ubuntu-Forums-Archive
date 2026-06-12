---
title: "regular update borked video on my serval"
date: 2008-11-10
forum: System76 Support
---

### Post by majoridiot on 2008-11-10
i just did a regular update (not a distro upgrade) on my serval running 8.04 and it killed my nvidia driver somehow... it refuses to run in anything but low graphics mode, across all kernels from .17-.21

i have tried re-installing the nvidia packages (not envy) and the system 76 drivers, but still no love.  the nvidia drivers do not show in restricted drivers manager and it does not appear the modules are even being loaded.

i'm at a loss to explain why a simple upgrade caused this and really need to get this straightened ASAP... any help is appreciated.

---

### Post by thomasaaron on 2008-11-10
Try...

#Delete the nvidia driver
sudo apt-get --purge remove nvidia-glx-new  
#Backup your xorg.conf
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#Re-install the driver
sudo apt-get install nvidia-glx-new
#Rebuild your xorg.conf (use all defaults)
sudo dpkg-reconfigure xserver-xorg

Reboot your machine. It'll come up in low graphics mode.
Go to System > Admin > Hardware Drivers.
Is the nvidia driver there?

---

### Post by majoridiot on 2008-11-10
> **thomasaaron said:**
> Try...

#Delete the nvidia driver
sudo apt-get --purge remove nvidia-glx-new  
#Backup your xorg.conf
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#Re-install the driver
sudo apt-get install nvidia-glx-new
#Rebuild your xorg.conf (use all defaults)
sudo dpkg-reconfigure xserver-xorg

Reboot your machine. It'll come up in low graphics mode.
Go to System > Admin > Hardware Drivers.
Is the nvidia driver there?

worked like a charm, thomas... thank you!  running fine on kernel .19 now.  .21 still has issues. 

seemed the step i skipped was the remove... i only purged.  it's always the little things, eh?

thanks again!

---

### Post by thomasaaron on 2008-11-10
Wow! It worked?! :confused:

:lolflag:

Glad you're up and running.

Best,
Tom

---

### Post by majoridiot on 2008-11-10
> **thomasaaron said:**
> Wow! It worked?! :confused:

:lolflag:

Glad you're up and running.

Best,
Tom

yeah, i know... really heavy mystery stuff. ;)

thanks again.

---

