---
title: "NVIDIA 440 driver issue MX250, T490"
date: 2020-04-15
forum: Ubuntu Development Version
---

### Post by Steve Reaver on 2020-04-15
I have a Lenovo T490 with GP108M [GeForce MX250] running 20.04

The latest apt update seems to have hosed my DKMS module. When the system boots, SDDM will not start and journalctl shows the following.

```
Apr 16 12:24:14 stinkpad kernel: NVRM: API mismatch: the client has the version 440.82, but
                                 NVRM: this kernel module has the version 440.64.  Please
                                 NVRM: make sure that this kernel module and all NVIDIA driver
                                 NVRM: components have the same version.
```

Kernel version is 
```
Linux stinkpad 5.4.0-21-generic #25-Ubuntu SMP Sat Mar 28 13:10:28 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

and the strange thing is that contains the correct version of the nvidia module

```
bt@stinkpad:/lib/modules$ modinfo ./5.4.0-21-generic/updates/dkms/nvidia.ko
filename:       /lib/modules/./5.4.0-21-generic/updates/dkms/nvidia.ko
alias:          char-major-195-*
version:        440.82
supported:      external
license:        NVIDIA
srcversion:     058C3165C621D73A1F7436F
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        ipmi_msghandler
retpoline:      Y
name:           nvidia
vermagic:       5.4.0-21-generic SMP mod_unload 
```

Where is the wrong version loading from ??

If I do the following I can get a desktop to load

```
rmmod nvidia_uvm
rmmod nvidia_drm
rmmod nvidia modset
rmmod nvidia
modprobe nvidia
systemctl start sddm

```

Any help is appreciated.

---

