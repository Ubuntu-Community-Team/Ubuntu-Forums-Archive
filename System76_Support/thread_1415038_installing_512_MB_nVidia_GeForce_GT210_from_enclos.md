---
title: "installing 512 MB nVidia GeForce GT210 from enclosed CD?"
date: 2010-02-24
forum: System76 Support
---

### Post by savantelite on 2010-02-24
I have a new WildBeast that I plan to use for BlueCherry DVR. So I need to install my 512 MB nVidia GeForce GT210 in Xubuntu 9.04

The problem is they sent me a CD where the drivers looks like windows drivers? Am I missing something?

---

### Post by thomasaaron on 2010-02-24
We ship with Ubuntu, and the nVIdia drivers come stock with Ubuntu. You have to go with System > Admin > Hardware Drivers and enable them.

Does Xubuntu have an equivalent to System > Admin > Hardware Drivers?

---

### Post by curtishall on 2010-02-24
> **savantelite said:**
> I have a new WildBeast that I plan to use for BlueCherry DVR. So I need to install my 512 MB nVidia GeForce GT210 in Xubuntu 9.04

The problem is they sent me a CD where the drivers looks like windows drivers? Am I missing something?

We install the NVIDIA driver automatically but you will need to activate the NVIDIA driver using the steps that Thomas pointed out.  If the monitor or settings are not being detected properly you can run nvidia-xconfig in a terminal window, or run the GUI tool 'nvidia-settings'.

Thanks

---

### Post by savantelite on 2010-02-24
After repeated attempts with Hardware drivers while fighting my wireless card drops. I am attempting a new path. For the near term Regular System76 Ubuntu Supported Jaunty. And once Lucid LTS is released I will switch to that. 

For BluecherryDVR I will email there support so I can get access and directions to thier repos. 

Xubuntu is better for older systems.

---

### Post by savantelite on 2010-02-25
I have ubuntu jaunty 64 bit installed and have opened "hardware drivers"

It asks to activate driver "NVIDIA accelerated...(version 180) recommended or "NVIDIA ... (version 173)

I clicked on 180 and it wasn't able to download. I am trying the other and it is very very slow?

My internet works fine, so what is the problem?

---

### Post by curtishall on 2010-02-25
We currently only have 32bit packages available, so you'll want to install the 32bit version of 9.04.  Version 2 will have 64bit packages, but it's not out yet.

Thanks

---

