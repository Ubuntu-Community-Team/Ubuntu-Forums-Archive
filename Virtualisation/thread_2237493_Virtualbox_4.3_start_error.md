---
title: "Virtualbox 4.3 start error"
date: 2014-08-02
forum: Virtualisation
---

### Post by Domgoa on 2014-08-02
Greetings all, 

Whenever is run virtualbox and press the start button i amd presented with this error  message.

 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I have googled the problem and yet to find a solution. 

I am runing Ubuntu 12.04 LTS.

Please help me.

---

### Post by Elfy on 2014-08-02
Have you tried doing what it suggests? 

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by Elfy on 2014-08-02
Thread closed. Please do not post duplicates, it dilutes community effort.

---

