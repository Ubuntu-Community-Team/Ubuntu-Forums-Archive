---
title: "Automount flash drive"
date: 2010-08-10
forum: Server Platforms
---

### Post by jeffbarish on 2010-08-10
I am trying to get Ubuntu Server to automount a USB flash drive when I plug it into a USB port.  I installed usbmount, but I have not been able to detect its purpose.  The flash drive does not automount when I plug it in or when I reboot with it already plugged in.  Do I need usbmount?

I suspect that I need to create a udev rule.  If so, I figured that I could copy the appropriate rule from a machine running Ubuntu desktop (where automount already works).  However, I don't see such a rule on that machine.  How does Ubuntu desktop implement automount?  If I do need a rule for udev, does anyone, perchance, have such a rule for an arbitrary flash drive?

By the way, I am able to mount the flash drive manually using mount.  My only issue is getting the flash drive to mount automatically.

---

