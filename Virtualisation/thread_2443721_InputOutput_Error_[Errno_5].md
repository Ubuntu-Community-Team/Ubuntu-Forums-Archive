---
title: "Input/Output Error [Errno 5]"
date: 2020-05-19
forum: Virtualisation
---

### Post by fleischer444 on 2020-05-19
Hi everyone, Im getting this error trying to install Ubuntu.

It tried the following without any luck:
Ubuntu 20.04
Ubuntu 19,04
Pop-OS 20.04
Tried having the VDI disk on an SSD and a regular disk
Disabled Hyper-V from Windows functions
Dynamic and fixed sizes for virtual drives

I have a 9700K, 16Gb Ram and an AUS motherboard. I have activated virtualization in bios.

Anyone have an idea what can couse this? Uses VM Ubuntu on my old 6700K without any issues.

---

### Post by jmginer on 2020-06-05
What is the host node OS?
what is the virtualization software you are using?

It's possible a HW issue, try to remove the number of components connected to the VM, like soundcard, webcam, etc...

---

### Post by danjones52 on 2020-06-24
I'm getting the same error
Windows 64bit host
Virtualbox 6.1.8
Ubuntu 20.04 desktop amd64
md5 hash validated 
Same ISO worked well on Hyper-V

Anyone having this problem have a solution? I had Hyper-V installed previously and I've uninstalled it without luck

---

### Post by danjones52 on 2020-06-24
I uninstalled VirtualBox 6.1.8, and installed Virtualbox 6.1.10 and had a smooth install and OS was running fine for 3+ hours without crashing or having any issues.

---

