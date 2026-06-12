---
title: "Mantis cannot login to any xorg session"
date: 2023-05-06
forum: Ubuntu Development Version
---

### Post by Claus7 on 2023-05-06
Hello,

as the title shows, there is no way I can loggin to ubuntu xorg or ubuntu flashback (either compiz or metacity) or gnome classic xorg. Both ubuntu and gnome classic wayland are working fine.

Regards!

---

### Post by corradoventu on 2023-05-06
This is a new install (not an upgrade) of my Mantic. I logged out from Wayland session an logged in to xorg ... no problem.
```
corrado@corrado-n6-mm-0506:~$ inxi -SGx
System:
  Host: corrado-n6-mm-0506 Kernel: 6.2.0-21-generic arch: x86_64 bits: 64
    compiler: N/A Desktop: GNOME v: 44.0 Distro: Ubuntu 23.10 (Mantic Minotaur)
Graphics:
  Device-1: Intel RocketLake-S GT1 [UHD Graphics 730] vendor: Gigabyte
    driver: i915 v: kernel arch: Gen-12.1 bus-ID: 00:02.0
  Device-2: Logitech HD Webcam C615 type: USB driver: snd-usb-audio,uvcvideo
    bus-ID: 1-7:4
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 22.1.8 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: iris gpu: i915
    resolution: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.0.2 renderer: Mesa Intel Graphics (RKL GT1)
    direct-render: Yes
corrado@corrado-n6-mm-0506:~$ 
```

---

### Post by Claus7 on 2023-05-06
Hello,

> **corradoventu said:**
> This is a new install (not an upgrade) of my Mantic. I logged out from Wayland session an logged in to xorg ... no problem....


thank you for your response. I still cannot log in (either logging out and back in or just booting directly to xorg). Fresh installation under virtualbox. From you comment I guess that this might be related to virtualbox.

Regards!

---

### Post by ajgreeny on 2023-05-06
So can we take it from that, that your install of mantic is a VM in Virtualbox?

---

### Post by Claus7 on 2023-05-06
Hello,

> **ajgreeny said:**
> So can we take it from that, that your install of mantic is a VM in Virtualbox?

affirmative.

Regards!

---

### Post by Claus7 on 2023-05-13
Hello,

I installed gnome-boxes under synaptic and tried a new installation of mantic. The screen, during installation, is no longer small as in virtualbox. The switching between slideshow and command line is really slow. Trying to access the settings froze the virtual machine and I had to force shutdown.The good thing is that forcing shutdown is extremely fast. The whole process is really resource hungry. 

I tried not to tamper with anything during installation to see if it will get completed. After <10' using ssd the whole process seems that it had finished. 
The installation screen went off and it gave it position to ubuntu dock. No message informed that installation was over. I suppose that something went wrong. Also during installation this red line that fills up is really annoying I guess. 

edit: trying to shutdown the machine it did, yet now prompting me to press Enter as if the installation was over. Restarting it prompted me to install anew.

I tried this way of installation in case the loggin to xorg session was successful. Unfortunately, under circumstances, I cannot tell.

Regards!

---

### Post by Claus7 on 2023-05-28
Hello,

I tried today's iso under VB and faced no problem.

Regards!

---

