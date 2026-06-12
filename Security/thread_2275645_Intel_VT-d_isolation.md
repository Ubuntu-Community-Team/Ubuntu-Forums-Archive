---
title: "Intel VT-d isolation"
date: 2015-04-27
forum: Security
---

### Post by amp819 on 2015-04-27
Does anyone know what sort of isolation/security capabilites to expect from Ubuntu's IOMMU drivers and Intel VT-d on a non-virtualized machine? From what I've read about VT-d, it should theoretically prevent a malcious device from performing a DMA attack, but it doesn't seem to be doing anything at all beyond sending "Intel-IOMMU: enabled" to dmesg. I'm FTracing the iommu* functions from boot and I have DMA-capable devices plugged in, so shouldn't I expect some kind of activity? Certainly possible that I have something misconfigured. I'm running Ubuntu 14.04 on a Intel(R) Core(TM) i5-4670, VT-d is enabled in BIOS, and intel_iommu=on in the kernel boot parameters. 

I haven't been able to find much info on the use of IOMMUs in Ubuntu for non-virtualization purposes, so any general pointers in that direction would be much appreciated.

---

