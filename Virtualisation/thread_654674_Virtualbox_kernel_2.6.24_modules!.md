---
title: "Virtualbox kernel 2.6.24 modules!"
date: 2007-12-31
forum: Virtualisation
---

### Post by snakeeyes on 2007-12-31
Hi after upgrading my kernel to 2.6.24-2 which is Hardy's development kernel, I use Gutsy though. Are the kernel modules virtual box for this kernel available? Does any other virtual machine software work with this kernel?

---

### Post by capink on 2008-01-08
I am not sure but I think you can recompile them if you have virtualbox installed:

```
sudo /etc/init.d/vboxdrv setup
```

Also in virtualbox site there is a .run package which should work with custom kernels. But you will also need to run the above command after installing.

---

### Post by frup on 2008-01-08
As far as I understand every time your kernel is upgraded, you need to do this. With kernel source the process should be easy.

---

### Post by snakeeyes on 2008-01-08
No, its ok forget it. I tried compiling it and it didn't work. I don't think virtualbox supports this kernel yet.

---

### Post by echo6 on 2008-01-08
You need to recompile the vboxdrv module for your running kernel,  thus you need either the kernel-headers or kernel-source and do:

```
sudo apt-get install virtualbox-ose-source
```

---

### Post by snakeeyes on 2008-01-08
thanks!

---

### Post by 23meg on 2008-01-24
I'm not sure, but I think simply switching to Virtualbox 1.5.4 fixes this.

---

### Post by plun on 2008-01-24
> **23meg said:**
> I'm not sure, but I think simply switching to Virtualbox 1.5.4 fixes this.

I am sure....:) running 1.5.4

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Gutsys deb package works for Hardy.

The manual is a good start for "newbies"....:)
[http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

---

### Post by LaneLester on 2008-02-11
Great news! I thought I was going to have to wait for an update to the OSE version in the repositories.

Lane

---

