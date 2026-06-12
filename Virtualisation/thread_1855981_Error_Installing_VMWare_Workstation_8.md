---
title: "Error Installing VMWare Workstation 8"
date: 2011-10-07
forum: Virtualisation
---

### Post by Pescador12 on 2011-10-07
Hi all,

I'm using Kubuntu 11.04 and after installing the workstation 8 version, a message appears saying that  "...several modules must be compiled...", then I click install.

An error occurs:
 > Unable to build kernel module.

See log file /tmp/vmware-root/modconfig-21640.log for details.What is wrong?

Thanks

---

### Post by 2F4U on 2011-10-07
So what is in the log file?

---

### Post by dcstar on 2011-10-10
> **Pescador12 said:**
> Hi all,

I'm using Kubuntu 11.04 and after installing the workstation 8 version, a message appears saying that  "...several modules must be compiled...", then I click install.

An error occurs:
 What is wrong?

Thanks

Install the **build-essential** & **linux-headers-generic** packages

---

### Post by Pescador12 on 2011-10-10
Ok, that solved the problem!

Thanks

---

### Post by dcstar on 2011-10-11
> **Pescador12 said:**
> Ok, that **solved** the problem!


Then **mark** the thread!

---

### Post by Pescador12 on 2011-10-18
I've searched but didn't see where to mark...

By the way, I had a problem with the VMWare Workstation 8, because my hardware doesn't supports. So now I've installed the VMPlayer 3.1, and have the same problem.

This is the log file:
```

Out 18 12:27:00.193: app-3077813952| Log for VMware Workstation pid=10433 version=7.1.5 build=build-491717 option=Release
Out 18 12:27:00.193: app-3077813952| The process is 32-bit.
Out 18 12:27:00.193: app-3077813952| Host codepage=UTF-8 encoding=UTF-8
Out 18 12:27:00.193: app-3077813952| Logging to /tmp/vmware-root/setup-10433.log
Out 18 12:27:00.562: app-3077813952| modconf query interface initialized
Out 18 12:27:00.563: app-3077813952| modconf library initialized
Out 18 12:27:00.641: app-3077813952| Your GCC version: 4.6
Out 18 12:27:00.664: app-3077813952| Your GCC version: 4.6
Out 18 12:27:00.701: app-3077813952| Your GCC version: 4.6
Out 18 12:27:00.754: app-3077813952| Your GCC version: 4.6
Out 18 12:27:00.791: app-3077813952| Your GCC version: 4.6
Out 18 12:27:00.915: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:00.930: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:00.946: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:00.960: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:00.975: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.036: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.057: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.069: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.077: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.086: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.099: app-3077813952| Your GCC version: 4.6
Out 18 12:27:01.133: app-3077813952| Your GCC version: 4.6
Out 18 12:27:01.374: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.381: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.389: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.397: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.407: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.417: app-3077813952| Your GCC version: 4.6
Out 18 12:27:01.442: app-3077813952| Your GCC version: 4.6
Out 18 12:27:01.543: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.552: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.560: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.567: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:01.577: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:02.085: app-3077813952| Trying to find a suitable PBM set for kernel 3.0.0-12-generic.
Out 18 12:27:02.087: app-3077813952| Building module vmmon.
Out 18 12:27:02.087: app-3077813952| Extracting the sources of the vmmon module.
Out 18 12:27:02.123: app-3077813952| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/3.0.0-12-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.6.1
Out 18 12:27:04.821: app-3077813952| Failed to compile module vmmon!

```Any help?

---

