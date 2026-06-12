---
title: "KVM PCI Passthrough Windows can't start device"
date: 2011-10-19
forum: Virtualisation
---

### Post by felixjai on 2011-10-19
Hi,

I have qemu-kvm-14.0 on ubuntu 11.10 oneiric on a Lenovo T400 laptop. I'm trying to pci passthrough the intel wireless 5100 card (minipci) to a Windows XP or 7 guest VM. 

I've compiled all the necessary kernel. My windows guest VM (both xp and 7) are able to detect the wireless card in Windows Device Manager, but after installing the latest intel drivers, the windows guests say it can't start the device (code 10).

Then as a test, I've tried using a ubuntu 11.10 as the guest VM and attach the same wireless card. the ubuntu guest VM is able to detect and use the wireless card correctly with pci passthrough.

Has anyone experienced this problem with pci passthrough using in Windows guests? I've also tried attach other pci devices from the host, such as a built-in card reader. Same error reported in the windows guests.

Any help is appreciated. Thanks!

---

### Post by felixjai on 2011-10-21
anyone?

---

