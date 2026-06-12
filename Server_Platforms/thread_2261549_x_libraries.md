---
title: "x libraries"
date: 2015-01-19
forum: Server Platforms
---

### Post by daniel201 on 2015-01-19
I've noticed a few x libraries installed on my home server, running Ubuntu Server 14.04.1. As I'm not running X, can they be removed?
They look like they have been installed with Samba/CUPs and QEMU.

```

libx11-data
  Reverse Depends: libx11-6 (2:1.6.2-1ubuntu2)
libx11-6
  Reverse Depends: libcairo2 (1.13.0~20140204-0ubuntu1)
  Reverse Depends: libsdl1.2debian (>= 1.2.15-8ubuntu1)
  Reverse Depends: libxext6 (>= 2:1.3.2-1)
  Reverse Depends: libxmuu1 (2:1.1.1-1)
  Reverse Depends: libxpm4 (1:3.5.10-1)
  Reverse Depends: libxrender1 (>= 1:0.9.8-1)
  Reverse Depends: qemu-system-x86 (2.0.0~rc1+dfsg-0ubuntu3)
  Reverse Depends: xauth (1:1.0.7-1ubuntu1)
libcairo2
  Reverse Depends: poppler-utils (>= 0.24.5-2ubuntu4)
poppler-utils
  Reverse Depends: cups (>= 1.7.2-0ubuntu1)
  Reverse Depends: cups-filters-core-drivers (1.0.52-0ubuntu1)
cups
  Reverse Depends: printer-driver-gutenprint (>= 5.2.10~pre2-0ubuntu2)
printer-driver-gutenprint
  Reverse Depends: cups-driver-gutenprint (5.2.10~pre2-0ubuntu2)
cups-driver-gutenprint
cups-filters-core-drivers
  Reverse Depends: cups-core-drivers (>= 1.7.2-0ubuntu1)
  Reverse Depends: cups-filters (>= 1.0.52-0ubuntu1)
cups-core-drivers
  Reverse Depends: cups (>= 1.7.2-0ubuntu1)
cups-filters
  Reverse Depends: cups (>= 1.7.2-0ubuntu1)
  Reverse Depends: printer-driver-gutenprint (>= 5.2.10~pre2-0ubuntu2)
libsdl1.2debian
  Reverse Depends: qemu-system-x86 (>= 2.0.0~rc1+dfsg-0ubuntu3)
qemu-system-x86
  Reverse Depends: qemu-kvm (>= 2.0.0~rc1+dfsg-0ubuntu3)
qemu-kvm
libxext6
  Reverse Depends: libcairo2 (1.13.0~20140204-0ubuntu1)
  Reverse Depends: libsdl1.2debian (1.2.15-8ubuntu1)
  Reverse Depends: xauth (1:1.0.7-1ubuntu1)
xauth
libxmuu1
  Reverse Depends: xauth (1:1.0.7-1ubuntu1)
libxpm4
  Reverse Depends: libgd3 (2.1.0-3)
libgd3
  Reverse Depends: libgphoto2-6 (>= 2.5.3.1-1ubuntu2)
libgphoto2-6
  Reverse Depends: libsane (>= 1.0.23-3ubuntu3)
libsane
  Reverse Depends: colord (>= 1.0.6-1)
colord
libxrender1
  Reverse Depends: libcairo2 (1.13.0~20140204-0ubuntu1)

```

Thanks

---

### Post by ian-weisser on 2015-01-19
If you want to know if a package can safely be removed, try
```
sudo apt-get autoremove **--simulate** <packagename>
```
and then read the list of removed dependencies carefully

---

### Post by daniel201 on 2015-01-20
Thank you :)

---

