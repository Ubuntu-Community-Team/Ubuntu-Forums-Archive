---
title: "KVM PCI passthrough without using pci address"
date: 2012-04-16
forum: Virtualisation
---

### Post by pootle42 on 2012-04-16
I'm passing through a couple of PCI devices to a guest VM (host is 12.04, guest is freebsd) using pci address OK, but this is slightly fragile in that changing bios settings can change the PCI addresses.

Is there any way to use vendor / product id with a pci device as can be done with USB?

I have tried the usb style syntax, but that just fails
```
[Mon, 16 Apr 2012 10:11:00 virt-install 2370] ERROR (cli:439) Did not find a matching node device for '0x10ec:0x8168'

```

I did find a reference to doing this[ here]("http://www.linux-archive.org/fedora-linux-management-tools/255205-virt-install-support-host-device-assignment.html"):
```
I'd strongly recommend virt-install only use managed=yes, and don't make
the use pick PCI ids off the list, rather present them with the human
readable vendor and product names.
```
but I can't find out the syntax to do this - all the docs on virt-install have the same few (addressed based) examples as do all the tutorials I've found.

---

