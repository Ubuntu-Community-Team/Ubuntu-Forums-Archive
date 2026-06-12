---
title: "VirtualBox Modules didn't install"
date: 2012-05-19
forum: Virtualisation
---

### Post by Haghiri75 on 2012-05-19
Hi All.

When I want to install virtualbox ; kernel modules (For example : vboxdrv) didn't install.

then I reboot and restart virtualbox ; but it doesn't work correctly. 
(I install it from *.run file or *.deb file)

Please Help Me!

---

### Post by 2F4U on 2012-05-19
Is there any particular reason why you are not installing from the official package repositories? Even if you don't want to use the version that comes with Ubuntu, Oracle is providing a ppa, which might be easier to use than compiling manually:

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Anyways, if you still want to manually compile, provide the error message that you get.

---

### Post by Haghiri75 on 2012-05-19
TnQ buddy ; but i use *.run file ; and I've downloaded it from virtualbox.org !

---

### Post by CharlesA on 2012-05-19
Run this:

```
sudo /etc/init.d/vboxdrv setup
```

---

