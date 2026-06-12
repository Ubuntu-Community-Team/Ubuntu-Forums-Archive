---
title: "Xen: Fatal page fault"
date: 2013-02-26
forum: Virtualisation
---

### Post by llemes4011 on 2013-02-26
So, I'm trying to install Xen on Ubuntu 12.10, and everything goes well until I try to boot into the Xen hypervisor. My PC immediately crashes with the following error:
```

(XEN) ****************************************
(XEN) Panic on CPU 0:
(XEN) FATAL PAGE FAULT
(XEN) [error_code=0000]
(XEN) Faulting linear address: 0000000000000000
(XEN) ****************************************

```
Then says that it's going to reboot in 5 seconds, but just hangs.

All the bugs that I could find about this are from a couple years ago or more. I tried asking on the ##xen IRC channel, and no on responded. 

I have an AMD 1090T Black Edition CPU (x86_64), 8 Gigs of RAM, and I'm booting off of an SSD (Not that I think that should matter). I've enabled IOMMU in the BIOS and AMD-SVM is enabled as well. 

I'm at a loss. I've never tried to install Xen before, and I was following this guide from the Ubuntu help pages:
[https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen)

Thanks,
Neil

---

### Post by tgalati4 on 2013-02-26
What version of Xen are you trying to install?

According to:

tgalati4@Mint14-Extensa ~ $ apt-cache search xen
.
.
.
xen-docs-4.1 - Documentation for Xen
xen-hypervisor-4.1-amd64 - Xen Hypervisor on AMD64
xen-system-amd64 - Xen System on AMD64 (meta-package)
xen-tools - Tools to manage Xen virtual servers
xen-utils-4.1 - XEN administrative tools
xen-utils-common - Xen administrative tools - common files
xenomai-doc - Xenomai documentation
xenomai-runtime - Xenomai runtime utilities
xenstore-utils - Xenstore utilities for Xen
xenwatch - Virtualization utilities, mostly for Xen
xen-hypervisor-4.1-i386 - Xen Hypervisor on i386
xen-system-i386 - Xen System on i386 (meta-package)

And:

tgalati4@Mint14-Extensa ~ $ apt-cache depends xen-system-amd64
xen-system-amd64
  Depends: xen-hypervisor-4.1-amd64
  Depends: xen-utils-4.1
  Conflicts: xen-system-amd64:i386

Is it possible that you installed a 32-bit version?  Even though they both have amd64 in the name, there is a 32-bit (i386) version.

I'm trying to install on a 12.04 server, but my laptop is showing 4.1 available on 12.10.

Once the version is verified you might want to grab 4.2 or wait a couple of weeks for 4.3.

---

### Post by llemes4011 on 2013-02-26
It looks like I have 4.1, and the 64 bit version. There's a 32 bit conflict though.

would removing the xen-system-amd64:i386 help?

```

root@neil-laptop:/home/neil# apt-cache search xen
...
xen-docs-4.1 - Documentation for Xen
xen-hypervisor-4.1-amd64 - Xen Hypervisor on AMD64
xen-system-amd64 - Xen System on AMD64 (meta-package)
xen-tools - Tools to manage Xen virtual servers
xen-utils-4.1 - XEN administrative tools
xen-utils-common - Xen administrative tools - common files
xenomai-doc - Xenomai documentation
xenomai-runtime - Xenomai runtime utilities
xenstore-utils - Xenstore utilities for Xen
xenwatch - Virtualization utilities, mostly for Xen
xen-hypervisor-4.1-i386 - Xen Hypervisor on i386
xen-system-i386 - Xen System on i386 (meta-package)

```and

```

root@neil-laptop:/home/neil# apt-cache depends xen-system-amd64
xen-system-amd64
Depends: xen-hypervisor-4.1-amd64
Depends: xen-utils-4.1
Conflicts: xen-system-amd64:i386

```

---

### Post by tgalati4 on 2013-02-26
The only way 32-bit would be installed is a positive hit with:

```
apt-cache policy xen-system-i386
```

The *conflicts* note is telling you that installing one will uninstall the other.  So you need to verify exactly what got installed and also check your BIOS switches.  It's possible that you have to flip a few switches to get it to work.  I've only installed Xen on older Dell PowerEdge servers.  I'm not familiar with AMD hardware.

From the wiki page, IOMMU should be supported out-of-box, but you might try turning it off to see if it boots:

 IOMMU (IO Memory Management Unit) support from CPU/BIOS/chipset is needed for Xen IO Virtualization. IOMMU makes it possible to dedicate PCI device securely to a Xen VM by using Xen PCI passthru. Intel IOMMU is called Intel VT-d, and AMD IOMMU is called just AMD IOMMU. 

You might try version 4.2 from xen.org or wait a few weeks for 4.3.

---

