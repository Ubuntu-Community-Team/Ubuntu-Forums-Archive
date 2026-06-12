---
title: "Virtual Box Question"
date: 2018-11-04
forum: Virtualisation
---

### Post by khreha on 2018-11-04
I'm trying to install Lubuntu 18.10 into the latest version of Oracle VirtualBox 5.5.20.

Unlike Ubuntu 18.10, Lubuntu doesn't appear to offer a "direct path" to installing it into Virtual Box ?? Instead, it only boots into the Live system desktop, and apparently (?????) this is the ONLY way is to install it ??  (ie: via the desktop that boots up in the Live version of Lubuntu vs. giving you the option to install it or run it live as Ubuntu does ????)

So here's my question:
If I try to install it via the desktop "install icon" will Lubuntu install inside the VirtualBox ??  Or will it attempt to install itself onto my hard drive as if I booted the Live version from a USB drive or DVD ??  (If that makes sense ??)

---

### Post by TheFu on 2018-11-05
Any installation running inside **any** virtual machine be that virtualbox, KVM, ESXi, or VMware will install to the storage setup for that specific virtual machine.  It cannot see the physical disks, unless you go out of your way to enable PCI passthrough (which isn't trivial).

Hope that answers the question.

---

