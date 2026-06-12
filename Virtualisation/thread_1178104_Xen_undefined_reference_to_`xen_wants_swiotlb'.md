---
title: "Xen undefined reference to `xen_wants_swiotlb'"
date: 2009-06-04
forum: Virtualisation
---

### Post by Leisenfelder on 2009-06-04
I get the below error when try to build linux-2.6.18
for Xen.  Does anyone have any ideas how I can fix it.





MODPOST vmlinux.o
 WARNING: modpost: Found 2 section mismatch(es). To see full details build your kernel with: 'make CONFIG_DEBUG_SECTION_MISMATCH=y'   GEN     .version   CHK     include/linux/compile.h   UPD     include/linux/compile.h   CC      init/version.o   LD      init/built-in.o   LD      .tmp_vmlinux1 arch/x86/built-in.o: In function `pci_swiotlb_init': /usr/src/linux-2.6-xen/arch/x86/kernel/pci-swiotlb.c:54: undefined reference to `xen_wants_swiotlb' make: *** [.tmp_vmlinux1] Error 1

---

