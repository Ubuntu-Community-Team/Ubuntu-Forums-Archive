---
title: "VMWare Player and Linux 2.6.37?"
date: 2011-03-09
forum: Virtualisation
---

### Post by Quadunit404 on 2011-03-09
Anybody here manage to install the VMWare Kernel modules on a Linux 2.6.37 kernel yet? Obviously this requires you to either use an older alpha build of Natty or a custom kernel (which in my case is the latter.)

If it helps, here's the full text of /tmp/vmware-root/setup-9422.log:

```
Mar 09 18:02:45.656: app-140383639013120| Log for VMware Workstation pid=9422 version=7.1.3 build=build-324285 option=Release
Mar 09 18:02:45.656: app-140383639013120| The process is 64-bit.
Mar 09 18:02:45.656: app-140383639013120| Host codepage=UTF-8 encoding=UTF-8
Mar 09 18:02:45.656: app-140383639013120| Logging to /tmp/vmware-root/setup-9422.log
Mar 09 18:02:45.803: app-140383639013120| modconf query interface initialized
Mar 09 18:02:45.803: app-140383639013120| modconf library initialized
Mar 09 18:02:45.831: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.837: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.848: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.866: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.874: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.907: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.910: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.914: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.918: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.922: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.947: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.950: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.954: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.957: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.959: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:45.964: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:45.976: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:46.022: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.026: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.030: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.034: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.037: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.043: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:46.056: app-140383639013120| Your GCC version: 4.4
Mar 09 18:02:46.113: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.117: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.121: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.125: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.127: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.316: app-140383639013120| Trying to find a suitable PBM set for kernel 2.6.37.3-candela.
Mar 09 18:02:46.317: app-140383639013120| Building module vmmon.
Mar 09 18:02:46.317: app-140383639013120| Extracting the sources of the vmmon module.
Mar 09 18:02:46.326: app-140383639013120| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.37.3-candela/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Mar 09 18:02:47.166: app-140383639013120| Failed to compile module vmmon!
```

EDIT: After much searching through DuckDuckGo, Bing and the VMWare Communities forum I finally found a patch that works with all the Linux 2.6.37 kernels and a shell script to apply the patch. Now all the VMWare kernel modules are built and work perfectly. Setting to resolved.

---

### Post by fjgaude on 2011-03-10
Pray do tell, where is the shell script that does the job?

---

### Post by Quadunit404 on 2011-03-10
I'll bring it up whenever I find it in my Opera history. I'll link to the thread I found it in, ok?

You may need to modify the shell script for it to work, but TMK it shall work with all 2.6.37 kernels up to 2.6.37-9.

EDIT: [found it :D]("http://communities.vmware.com/thread/293321?start=0&tstart=0")

---

### Post by fjgaude on 2011-03-10
Okay, and thanks for the link. I think I'll wait until VMware comes out with a Player that works with Ubuntu 11.04.

---

### Post by Quadunit404 on 2011-03-11
That might be a while, seeing as to how the latest version of VMWare Workstation (and Player) was released back in November. I think it might be more worthwhile to apply the patches and install VMWare as it is right now.

---

### Post by fjgaude on 2011-03-11
Somehow we sense that VMware follows the release of Ubuntu to be compatible. We'll have to see... I think we will see new Players just after the 11.04 release in late April, not long from now.

---

### Post by Quadunit404 on 2011-03-11
They seem to be a month off, though, as Maverick was released in October and VMWare released a version of Workstation compatible with Maverick (and any other distro using Linux 2.6.35 as its kernel) in November.

We may not see another update to VMWare Player or Workstation until May or June if that is 100% true :|

---

