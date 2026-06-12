---
title: "Kernel 3.18RC3"
date: 2014-11-02
forum: Ubuntu Development Version
---

### Post by Doug S on 2014-11-02
I got an error trying to install the Ubuntu kernel 3.18RC3 just now:```
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() could not open moddep file '/lib/modules/3.18.0-031800rc2-generic/modules.dep.bin'
```I had purged 3.18RC2 first. I'm going to try to build the kernel.org version using the ubuntu config file, as I normally do.

Correction: There is no error. (it helps to not forget and purge the same kernel currently running. Duh!)

Edit: Kernel seems to be working fine.

---

### Post by fooman on 2014-11-03
seems good so far here...

```
Current Date/Time: Mon Nov  3 07:41:45 EST 2014
Distro Release: Ubuntu Vivid Vervet (development branch)
Kernel Release: Linux 3.18.0-rc3-foomans-custom-kernel
Gnome Release: GNOME Shell 3.12.2
Unity Release: unity 7.3.1

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 480/PCIe/SSE2
OpenGL version string:  4.2.0 NVIDIA 304.123
```

also,  fastest boot with systemd that i have seen on this rig:

```
$ systemd-analyze 
Startup finished in 3.485s (kernel) + 4.627ss (userspace) = 8.112s
```

---

