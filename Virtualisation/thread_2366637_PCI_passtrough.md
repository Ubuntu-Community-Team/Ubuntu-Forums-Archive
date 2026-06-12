---
title: "PCI passtrough"
date: 2017-07-20
forum: Virtualisation
---

### Post by vanili on 2017-07-20
Hi all,

I'm trying to implement PCI passtrough via virtualbox from Ubuntu 17.04.

I already ensured that I have iommu turned on, pci is put to stub, pci driver unbind, and pci is set to vfio-pci. However virtualbox still crashes at the start, and there are those strings in the kernel log
```

Jul 20 11:20:41 epitt-PC kernel: [  291.454812] vboxpci: detected device: 1093:2a80 at 11:00.0, driver <none>
Jul 20 11:20:41 epitt-PC kernel: [  291.454869] pci-stub 0000:11:00.0: claimed by stub
Jul 20 11:20:41 epitt-PC kernel: [  291.454897] vboxPciFileWrite: error -19
Jul 20 11:20:41 epitt-PC kernel: [  291.455034] vboxpci 0000:11:00.0: vboxPciOsDevInit
Jul 20 11:20:41 epitt-PC kernel: [  291.455101] vboxpci 0000:11:00.0: region 0: mmio fc501000+4096
Jul 20 11:20:41 epitt-PC kernel: [  291.455104] vboxpci 0000:11:00.0: region 1: mmio fc500000+4096
Jul 20 11:20:41 epitt-PC kernel: [  291.455130] vboxpci 0000:11:00.0: got irq 20
Jul 20 11:20:41 epitt-PC kernel: [  291.886452] vboxpci: created IOMMU domain ffff949bd8b71488
Jul 20 11:20:41 epitt-PC kernel: [  291.906193] do_general_protection: 25 callbacks suppressed
Jul 20 11:20:41 epitt-PC kernel: [  291.906195] traps: EMT[2340] general protection ip:7fef19d53ccf sp:7fef4e037d10 error:0
Jul 20 11:20:41 epitt-PC kernel: [  291.906199]  in VBoxPciRawR3.so[7fef19d51000+b000]
Jul 20 11:20:42 epitt-PC kernel: [  292.226659] vboxpci 0000:11:00.0: freeing irq 20
Jul 20 11:20:42 epitt-PC kernel: [  292.226671] vboxpci 0000:11:00.0: vboxPciOsDevDeinit
Jul 20 11:20:42 epitt-PC kernel: [  292.227246] vboxpci: freeing IOMMU domain ffff949bd8b71488

```

My question is what can be general_protection caused by in this case? Google says that it CPU error because of wrong memory addressing... 
Any ideas or thoughts about it?

Thank you in advance, and sorry for a too general question ;)

---

### Post by slickymaster on 2017-07-20
*Thread moved to **Virtualisation**.*

---

