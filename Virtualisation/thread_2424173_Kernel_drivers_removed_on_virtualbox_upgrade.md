---
title: "Kernel drivers removed on virtualbox upgrade"
date: 2019-08-05
forum: Virtualisation
---

### Post by undecidable on 2019-08-05
Today virtualbox upgraded from 5.2.18 to 5.2.32.

As part of this upgrade, the kernel drivers were deleted from all 4 kernels in my system,
> Deleting module version: 5.2.18
completely from the DKMS tree.

then only rebuilt for the latest kernel:
> Setting up virtualbox-dkms (5.2.32-dfsg-0~ubuntu18.04.1) ...
Loading new virtualbox-5.2.32 DKMS files...
Building for 4.18.0-25-generic
Building initial module for 4.18.0-25-generic
...
DKMS: install completed.
Setting up virtualbox (5.2.32-dfsg-0~ubuntu18.04.1)

So now, if I reboot to anything other than the most recent kernel,
I can no longer use virtualbox.  
I get the (correct) message
> Kernel driver not installed (rc=-1908)

Does any one know why, annoyingly, updating virtualbox
deletes for all old kernels but doesn't rebuild them?

More importantly: 
How do I rebuild the kernel drivers for the other kernel versions on my system?
the script gave a hint:
> Use the dkms install command to reinstall any previous module version

Does anyone know how to do this?

---

### Post by undecidable on 2019-08-05
ha, once you know how to properly formulate the question,
you may find the answer.

The solution is here:
[unix.stackexchange.com/questions/205023/how-do-i-compile-dkms-module-for-multiple-kernel-image-versions-in-debian]("https://unix.stackexchange.com/questions/205023/how-do-i-compile-dkms-module-for-multiple-kernel-image-versions-in-debian")

To confirm what kernels you have:
```
apt list --installed linux-image*
```

To confirm what modules you need to build:
```
dkms status
```

Then to rebuild virtualbox for a particular older kernel:
```
sudo dkms install virtualbox/5.2.32 -k 4.18.0-20-generic
```

where 5.2.32 is the virtualbox version, and 4.18.0-20-generic is the kernel you are building for.

---

