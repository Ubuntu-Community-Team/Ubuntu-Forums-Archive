---
title: "VirtualBox 32-bit error"
date: 2008-09-01
forum: Virtualisation
---

### Post by OisinT on 2008-09-01
hey hit an error while trying to install virtualbox that I'm not sure how to fix.

thanks

```
Checking for 32-bit support: 
  Cannot compile 32-bit applications (missing headers and/or libraries)!

```

---

### Post by lazyart on 2008-09-01
try ```
sudo apt-get install build-essential linux-headers-`uname -r`
``` to include the tools you need to complie.

---

### Post by OisinT on 2008-09-01
> **lazyart said:**
> try ```
sudo apt-get install build-essential linux-headers-`uname -r`
``` to include the tools you need to complie.
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.24-21-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  kbuild libxalan110 virtualbox-ose-modules-2.6.24-20-generic libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

---

### Post by karlwilbur on 2009-01-21
Having same issue trying to install on my laptop:
Linux karl-laptop-2 2.6.24-22-generic #1 SMP Mon Nov 24 19:35:06 UTC 2008 x86_64 GNU/Linux

Just updated kernel, but missing 32-bit support. Needed to run:

```
sudo apt-get install g++-multilib
```

---

