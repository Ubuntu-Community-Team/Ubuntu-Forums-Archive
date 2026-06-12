---
title: "CDROM in KVM Guest"
date: 2020-11-22
forum: Virtualisation
---

### Post by Quarkrad on 2020-11-22
Is it the case that one cannot have a cdrom in a kvm guest as per the host machine?  I can add sata cdrom device as a storage medium used in the install process but this is not the same as putting a cd/dvd in the host machine and it appearing on the kvm guest as per a usb stick.

---

### Post by wildmanne39 on 2020-11-22
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by TheFu on 2020-11-22
> **Quarkrad said:**
> Is it the case that one cannot have a cdrom in a kvm guest as per the host machine?  I can add sata cdrom device as a storage medium used in the install process but this is not the same as putting a cd/dvd in the host machine and it appearing on the kvm guest as per a usb stick.

No. You can add a virtual CD (an ISO file) to the VM, setup the virtual controller - sata or IDE or SCSI - and go.
If you want to passthru a physical device, then that passthru has to follow the requirements like passing through any non-USB physical device.  This is non-trivial.  IOMMU must be enabled in the host kernel for starters.  The VM must have exclusive access to the hardware controller and to the storage device.
[https://unix.stackexchange.com/questions/409616/ubuntu-16-04-host-windows-10-guest-cannot-passthrough-mount-an-audio-cdrom](https://unix.stackexchange.com/questions/409616/ubuntu-16-04-host-windows-10-guest-cannot-passthrough-mount-an-audio-cdrom)

Or do I completely miss the question?

---

### Post by Quarkrad on 2020-11-23
Thank you - you interpreted my question correctly; my error for not making the question clear enough.

---

### Post by TheFu on 2020-11-23
> **Quarkrad said:**
> Thank you - you interpreted my question correctly; my error for not making the question clear enough.

Passing through non-usb devices is sully more hassle than it is worth.  If you have the CD, jst use dd to clone it nto an ISO file and use that in the VM GUI config.
or
you can pt the ISO on any linux system, mount it using the **mount -o loop** technique. If the mount s on a different system, use nfs to share it.  very easy between linux/Unix systems.  Any network protocol works for VMs just like for physical installs.

---

