---
title: "Compiling 3.2.0-11.19 for Intel systems errors"
date: 2012-01-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xyzzyman on 2012-01-27
I've been having issues re-compiling the last 2 kernel releases. Turns out the dependencies are wrong if you disable CONFIG_AMD_NB (Which I do as I have an Intel system). The following patch fixes the dependency. Posting in case anyone else has a problem.

```
 arch/x86/pci/Makefile |    3 ++-
 1 files changed, 2 insertions(+), 1 deletions(-)

diff --git a/arch/x86/pci/Makefile b/arch/x86/pci/Makefile
index 6b8759f..d24d3da 100644
--- a/arch/x86/pci/Makefile
+++ b/arch/x86/pci/Makefile
@@ -18,8 +18,9 @@ obj-$(CONFIG_X86_NUMAQ)		+= numaq_32.o
 obj-$(CONFIG_X86_MRST)		+= mrst.o

 obj-y				+= common.o early.o
-obj-y				+= amd_bus.o bus_numa.o
+obj-y				+= bus_numa.o

+obj-$(CONFIG_AMD_NB)		+= amd_bus.o
 obj-$(CONFIG_PCI_CNB20LE_QUIRK)	+= broadcom_bus.o

 ifeq ($(CONFIG_PCI_DEBUG),y)

```

Source: [https://lkml.org/lkml/2012/1/12/149](https://lkml.org/lkml/2012/1/12/149)

---

### Post by xyzzyman on 2012-01-28
NVM... It's been fixed in the new 3.2.0-12.20

---

