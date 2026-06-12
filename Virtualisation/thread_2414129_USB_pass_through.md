---
title: "USB pass through"
date: 2019-03-06
forum: Virtualisation
---

### Post by jmoellers on 2019-03-06
Hi,
I'm running a 64-bit Kubuntu 16.04 host. Attached is an Auerswald PBX through USB. It works mostly fine physically, but one of the tools, COMlist, used to list incoming and outgoing calls, will not start up, it hangs in a futex call, so I tried running it from a Kubuntu 12.04 32-bit VM, where it used to work.
Unfortunately, the VM does not see the PBX, no matter whether I use the USB Bus/Device numbers or the USB Vendor/Product IDs.
The qemu invocation does list the USB Bus/Device number (ps) but the VM doesn't see it. No mention in the syslog of the guest.

---

