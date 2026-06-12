---
title: "KVM and PCI passthrough"
date: 2008-11-07
forum: Virtualisation
---

### Post by geraldbrandt on 2008-11-07
Hi,

I saw that KVM allows PCI passthrough on VT-d systems with the comand:

-pcidevice host=bus:dev.func

Does 8.10 support this, or will it be an upgrade?  I rather use Ubuntu and it's supported virtualization than have to go and hunt down a good Xen distro.

Gerald

---

### Post by Lampi on 2008-12-03
Looking at the release date of [KVM-79]("http://www.linux-kvm.com/") (first kvm with pci card handling) I don't think it's included in Ibex.

The relevant patch you might want to try can be found in the [Linux Kernel Mailing List]("http://lkml.org/lkml/2008/9/23/175")

Maybe it's better to wait for an upgrade anyway or change to xen, meaning get back to Hardy 8.04.1

---

