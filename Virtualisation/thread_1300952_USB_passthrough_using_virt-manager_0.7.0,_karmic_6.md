---
title: "USB passthrough using virt-manager 0.7.0, karmic 64"
date: 2009-10-25
forum: Virtualisation
---

### Post by johntnn on 2009-10-25
Trying to get USB passthrough working with a kvm virtual machine for a USB scanner.  I upgraded to karmic beta to get the latest virt-manager 0.7.0, with support for adding a physical device.  I'm now able to add the scanner as a new physical device through the virt-manager interface, but nothing happens.  Anyone had success with adding a device in virt-manager?

---

### Post by mkutsevol on 2009-10-25
Couple days ago I've had the same problem, spent several hours to make it work!
The thing is apparmor. You should go to /etc/apparmor.d/abstractions/libvirt-qemu and uncomment some lines there, read the comments in the file.
and check if you have hald installed. virsh (libvirt) relies on it to get host hardware list.
"virsh nodedev-list" has to list host's hardware.

---

### Post by johntnn on 2009-10-26
Thanks a bunch!  Yes, nodedev-list shows hardware with proper IDs.  As for Apparmor, I looked at it and sure enough, looks like that might be doing it.  Restarted my host and voila!  

Thanks again.  :p

---

