---
title: "Nvidia drivers won't load after upgrade from 11.10"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by UnSandpiper on 2012-04-11
I'm on a Lenovo T420 with Intel Sandybridge and discrete Nvidia GPU.

After upgrading from oneiric to precise, the nvidia drivers fail to load and falls back to vesa-nvidia drivers.

Also I don't have any any options in jockey although nvidia-current is installed:

```
sudo jockey-text
Additional Drivers
Searching for available drivers...

```

I've tried a bunch of things, purging nvidia drivers and xorg many times and also adding the x-swat pp, but nothing helped so far.

Now using bumblebee, which lets me at least run my external monitor via the Sandybridge GPU, but that only supports VGA and the image is so unsharp that I'm getting headaches.

Any more ideas what I could try to get the Nvidia drivers working again?

from /var/log/kern.log
```

Apr 11 16:07:03 ak-ubuntu kernel: [   11.648308] nvidia: module license 'NVIDIA' taints kernel.
Apr 11 16:07:03 ak-ubuntu kernel: [   11.648312] Disabling lock debugging due to kernel taint
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699707] NVRM: The NVIDIA probe routine was not called for 1 device(s).
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699710] NVRM: This can occur when a driver such as nouveau, rivafb,
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699711] NVRM: nvidiafb, or rivatv was loaded and obtained ownership of
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699711] NVRM: the NVIDIA device(s).
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699713] NVRM: Try unloading the conflicting kernel module (and/or
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699714] NVRM: reconfigure your kernel without the conflicting
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699715] NVRM: driver(s)), then try loading the NVIDIA kernel module
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699715] NVRM: again.
Apr 11 16:07:03 ak-ubuntu kernel: [   11.699716] NVRM: No NVIDIA graphics adapter probed!

```


Don't  understand what it is loading before nvidia because there is a lot of stuff blacklisted:
```

$ egrep 'nvid|nouv' /etc/modprobe.d/*.*
/etc/modprobe.d/blacklist-framebuffer.conf:blacklist nvidiafb
/etc/modprobe.d/nvidia-current_hybrid.conf:# This file was installed by nvidia-current
/etc/modprobe.d/nvidia-current_hybrid.conf:blacklist nouveau
/etc/modprobe.d/nvidia-current_hybrid.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-current_hybrid.conf:alias nouveau off
/etc/modprobe.d/nvidia-current_hybrid.conf:alias lbm-nouveau off
/etc/modprobe.d/nvidia-graphics-drivers.conf:# This file was installed by nvidia-current
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nouveau
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist lbm-nouveau
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nvidia-173
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nvidia-96
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nvidia-current-updates
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nvidia-173-updates
/etc/modprobe.d/nvidia-graphics-drivers.conf:blacklist nvidia-96-updates
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias nvidia nvidia_current
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias nouveau off
/etc/modprobe.d/nvidia-graphics-drivers.conf:alias lbm-nouveau off

```


But now I notice this in /var/log/Xorg.0.log
It is loading some Nvidia GLX module before it fails loading the actualy driver, coud that be it?
```

[    11.184] (II) Loading extension DOUBLE-BUFFER
[    11.184] (II) LoadModule: "glx"
[    11.184] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    11.361] (II) Module glx: vendor="NVIDIA Corporation"
[    11.362] 	compiled for 4.0.2, module version = 1.0.0
[    11.362] 	Module class: X.Org Server Extension
[    11.362] (II) NVIDIA GLX Module  295.33  Sat Mar 17 15:16:17 PDT 2012
[    11.362] (II) Loading extension GLX
[    11.362] (II) LoadModule: "record"
[    11.363] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    11.365] (II) Module record: vendor="X.Org Foundation"
[    11.365] 	compiled for 1.11.3, module version = 1.13.0
[    11.365] 	Module class: X.Org Server Extension
[    11.365] 	ABI class: X.Org Server Extension, version 6.0

```

---

### Post by UnSandpiper on 2012-04-11
Ah, disregard that.

Like it says in almost every post regarding this topic,
one has to apt-get remove nvidia-current and then actually REBOOT before installing that nvidia-current again.

Now compiz is crashing constantly, but my initial goal of getting the nvidia driver to load was successful.

---

### Post by cariboo on 2012-04-11
I have had good luck with installing nvidia-current-update without having to remove the nvidia-current driver.

---

