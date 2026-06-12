---
title: "POP! OS update crashes nvidia driver"
date: 2021-12-06
forum: Ubuntu/Debian BASED
---

### Post by nicolas-santorsola on 2021-12-06
[FONT=book antiqua][SIZE=2][B][FONT=arial]Hi everyone.

I installed POP! OS 20.04 on an old machine with EVGA Nvidia GeForce GTX 560 graphics card.

As soon as it boots it gets stuck at 640x480 resolution. I solved it uninstalling nvidia-driver-470 and installed 390 instead.

The problem is that the driver breaks once I install the updates on the system.

I manage to narrow down the packages that break the driver to:[/FONT][/B]

[SIZE=3][FONT=arial narrow]linux-generic (5.15.5)
linux-headers-generic (5.15.5)
linux-image-generic (5.15.5)
linux-libc-dev (5.15.5)
linux-system76 (5.15.5)[/FONT][/SIZE]
[B][FONT=arial]
They install in batch over the current version 5.13.0.

Does anyone know how to solve the issue or debug it?

I have already tried to reinstall the driver before booting, however it fails not being able to find the module.

After restarting I get wrong refresh rate in the monitor 95.6 instead of 60.

When the version 5.15.5 installs it finishes with error:[/FONT][/B][/SIZE][/FONT]

[SIZE=3][FONT=arial narrow]Building module:
Cleaning build area...
unset ARCH; [! -h /usr/bin/cc] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j6 NV_EXCLUDE_BUILD_MODULES=" KERNEL, UNAME=5.15.5-76051505-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/5.15.5-76051505-generic/buil LD=/usr/bin/ld.bfd modules...........(bad exit status:2)
ERROR (dkms apport): kernel package linux headers-5.15.5-76051505-generic is not supported
Error! Bad return status for module build on kernel: 5.15.5-76051505-generic (x86_64)
Consult /var/lib/dkms/nvidia/390.144/build/make.log for more information[/FONT][/SIZE]


[FONT=arial][SIZE=2]Thanks for reading.[/SIZE][/FONT]

---

### Post by jeremy31 on 2021-12-06
So are there additional PPA's that have linux-generic install the 5.15 kernel?

---

### Post by nicolas-santorsola on 2021-12-06
> **jeremy31 said:**
> So are there additional PPA's that have linux-generic install the 5.15 kernel?

How do I find out?

I installed everything else manually one by one but those 5 packages.

---

