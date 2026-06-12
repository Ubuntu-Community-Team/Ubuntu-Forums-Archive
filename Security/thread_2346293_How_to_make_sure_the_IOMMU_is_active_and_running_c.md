---
title: "How to make sure the IOMMU is active and running correctly?"
date: 2016-12-13
forum: Security
---

### Post by Megadoomer on 2016-12-13
Hi everyone,

I have recently learned about a system component called the IOMMU (or "input–output memory management unit"), which apparently is able to restrict the memory access of devices, such as PCI and networking cards, for example. That way, these devices would not be able to simply read or corrupt all of the system memory in case of malfunction or maybe even backdoored firmware, because a device is only able to access a designated part of the system memory.

Now, I do have a motherboard that is apparently equipped with an IOMMU and also has it activated in the BIOS (Asus Crosshair IV). And, as far as I know, Linux has had kernel support of IOMMUs for quite a while.

How can I make sure that the IOMMU is working correctly (as I imagine this module can/should not be noticed in everyday use of the graphical interface)? Is it necessary to select certain installation options or can it be activated at any point? Must devices be entered manually or is it a completely automatic system? How can I configure the settings, if there are any?


Kind regards! :)

---

