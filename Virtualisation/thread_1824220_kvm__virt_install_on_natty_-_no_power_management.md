---
title: "kvm / virt install on natty - no power management?"
date: 2011-08-13
forum: Virtualisation
---

### Post by pootle42 on 2011-08-13
I've just rebuilt my home server with natty server (no graphical console), and updated the kernel to 2.6.39 (to get IOMMU working properly). I'm using KVM

If I use virt-install to create new VMs, they appear to be setup without apic (even though it is in the xml file), and I cannot shut them down from command line on the host or from virtual machine manager.

With an old VM I imported though, shutdown works fine, the only difference in the XML I can see is that the old one has only acpi defined and uses pc-12 architecure, whereas the new ones have acpi, apic and pae as use pc-14 architecture.

Anyone know how I can fix this?

---

