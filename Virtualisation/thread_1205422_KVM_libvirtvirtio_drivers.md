---
title: "KVM libvirt/virtio drivers"
date: 2009-07-06
forum: Virtualisation
---

### Post by freakalad on 2009-07-06
The driver-support for KVM clients seem incomplete.

I recently upgraded to Jaunty, and many of the clients, especially the windows ones, are acting strange (keep disappearing from catalogue, etc), and they look for new drives, which should not be happening, since hardware should be abstracted. One driver 2003 DOES prompt for, is some generic "PCI Device" (whatever that means...). 
This seems a libvirt issue

On GNU-Linux/Ubuntu clients, a fresh basic Jaunty NBR client in this case, I tried checking what was set under System > Administration > Drivers. All was set, except for some Cirrus Logic framebuffer driver.
I did a `sudo dpkg-reconfigure xserver-xorg` & variations thereof & set rendering mote to kernel framebuffer, & by a long process of elimination, figured our that specific version of the FrameBuffered Cirrus Logic abstracted driver was blacklisted, which I then un-blacklisted:
finding commenting out the line "blacklist cirrusfb" from /etc/modprobe.d/blacklist*

So:
* where can I find working 32- & 64-bit drivers for my clients? windoze, ubuntu/generic gnu/linux, bsd/unix, others
* will loading these "special" drivers set my clients to be paravirt'ed clients? (there's not an awful lot of info on this subject out there, btw)
* if cirrus is the default "enhanced" driver for KVM clients, why is it blacklisted?
* can I use drivers provided to VirtualBox as generic/abstracted drivers for my KVM guests/clients too? Especially the 3D graphics (I think, these in turn, are Wine driver)
* do I need to load new drivers into clients every time a new KVM or libvirt comes out?

- J

---

