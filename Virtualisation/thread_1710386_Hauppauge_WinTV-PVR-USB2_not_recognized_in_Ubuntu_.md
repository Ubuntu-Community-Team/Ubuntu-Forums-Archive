---
title: "Hauppauge WinTV-PVR-USB2 not recognized in Ubuntu Guest"
date: 2011-03-19
forum: Virtualisation
---

### Post by charles.marker on 2011-03-19
I am running Ubuntu 10.10 with a KVM guest running mythbuntu 10.10.  I am trying to get USB passs through to work.  I have been able to successfully pass through a USB thumb drive and format/mount it in the guest.  It is not automatically mounted when I boot the guest.  I now am trying to do the same for a Hauppauge WinTV-PVR-USB2.  After adding the device with virt-manager and rebooting the guest when running lsusb I see an extra USB device but it has all zeros for the vendor and product ID's.  If I run lsusb on the host I see the device.  If I unplug the device and try to start the guest I get an message from virt-manager indicating that the device is missing.

I'm new to KVM/QEMU so I don't know what tools are available to debug something like this.  I have checked dmesg and /var/log/messages on the guest but don't see anything.  I also have checked /var/log/libvirt/qemu/vm1.log and don't see anything there either.  Thanks for any help.

---

### Post by Marco van Beek on 2011-04-14
I have a similar problem. I can attach a fingerprint reader on my laptop to my virtual Windows 7 machine, but even though virsh says it has been attached, I can't see my TomTom SatNav device. Both would seem to be USB2 devices, but my PCI to USB device in the VM is being reported as an Intel 82371SB, which I think might be USB1.1. That is the only thing I can think of that might be causing the problem.

---

