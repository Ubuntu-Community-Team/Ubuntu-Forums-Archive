---
title: "KVM-QEMU No access to usb devices"
date: 2010-02-02
forum: Virtualisation
---

### Post by tkarkache on 2010-02-02
Good Day,

I am hoping someone can shed some light on an issue I can seem to find a resolution too. 
When starting my vm guest using virt-manager gui I can't access my usb device even though it is defined in the guest xml file. 
I have tried adding myself to group KVM and libvirt. Add udev rules etc..

I am running Ubuntu 9.10 x64. KVM-QEMU-0.11.0. 

If I start the vm from the command line using qemu-kvm -usb -usbdevice xx:xx etc, I can get the device working.

Running from the command is feasible, however I don't know the syntax for using the virtio drivers for disk and nic using bridge networking. If some knows of a good guide that would awesome thanks.

---

