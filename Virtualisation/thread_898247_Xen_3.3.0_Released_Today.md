---
title: "Xen 3.3.0 Released Today"
date: 2008-08-23
forum: Virtualisation
---

### Post by agent8131 on 2008-08-23
> 
This is a major new release with a host of new features including:
 - Power management (P & C states) in the hypervisor
 - HVM emulation domains ('qemu-on-minios') for better scalability,
performance and security
 - PVGrub: boot PV kernels using real GRUB inside the PV domain
 - Better PV performance: domain lock removed from pagetable-update paths
 - Shadow3: optimisations to make this the best shadow pagetable algorithm
yet, making HVM performance better than ever
 - Hardware Assisted Paging enhancements: 2MB page support for better TLB
locality
 - CPUID feature levelling: allows safe domain migration across systems with
different CPU models.
 - PVSCSI drivers for SCSI access direct into PV guests
 - HVM framebuffer optimisations: scan for framebuffer updates more
efficiently
 - Device passthrough enhancements
 - Full x86 real-mode emulation for HVM guests on Intel VT: supports a much
wider range of legacy guest OSes
 - New qemu merge with upstream development
 - Many other changes in both x86 and IA64 ports


[http://lists.xensource.com/archives/html/xen-devel/2008-08/msg00828.html](http://lists.xensource.com/archives/html/xen-devel/2008-08/msg00828.html)

---

