---
title: "Intel VT-d (IOMMU): Gave up waiting for root device"
date: 2013-01-23
forum: Server Platforms
---

### Post by kaboon on 2013-01-23
On my [Intel SR2600URBRPR]("http://ark.intel.com/products/48665/Intel-Server-System-SR2600URBRPR"), I would like to passthrough a PCI-E graphics card to a KVM guest. As this requires Intel VT-d, I configured the following options in the BIOS:
```

Intel VT for Directed I/O   [Enabled]
  Interrupt Remapping       [Enabled]
  Coherency Support         [Disabled]
  ATS Support               [Enabled]
  Pass-through DMA Support  [Enabled]

```
When I try to boot up my freshly installed Ubuntu 12.10 with intel_iommu=on, it gives me tons of DMAR/DRHD errors:
```

...
DMAR:[DMA Write] Request device [05:01.0] fault addr ffbfe000
DMAR:[fault reason 02] Present bit in context entry is clear
DRHD: handling fault status reg 602
...

```
It then finally fails, because it can't find the boot device: "Gave up waiting for root device"
When I do a `ls /dev`, I can see sda, but sda1 (which is configured as the root) is missing...

I am using a Adaptec RAID controller ([Adaptec RAID 3405]("https://www.adaptec.com/en-us/products/controllers/hardware/sas/value/sas-3405/")) which is basically a PCI card connected to the disks (where the root of this Ubuntu server is). Could that be a problem?

With intel_iommu=off everything works (except the passthrough of the graphics card of course).

---

### Post by kaboon on 2013-01-24
In the meantime I also tried Debian and CentOS (just to make sure it is not some weird kernel bug): Same behavior... :(
Any ideas?

---

