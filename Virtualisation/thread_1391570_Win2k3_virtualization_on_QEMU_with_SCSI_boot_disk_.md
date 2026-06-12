---
title: "Win2k3 virtualization on QEMU with SCSI boot disk fails"
date: 2010-01-26
forum: Virtualisation
---

### Post by ravindra.rajaram on 2010-01-26
I'm trying to install Win2k3 on QEMU (don't have KVM :(), with an emulated (single) SCSI hard disk. The installation starts up fine, but after the first re-boot, I just see a "trap 00000006 exception" and nothing happens after that!
I removed the SCSI disk (virtual) and then the VM boots up fine with the ISO image.
I cannot get any concrete information on if QEMU supports SCSI emulation.
Any help ?

Oh and I'm trying all this on a Ubuntu 9.10 server, managing using virsh.

-RR

---

### Post by Seq on 2010-01-26
> **ravindra.rajaram said:**
> I'm trying to install Win2k3 on QEMU (don't have KVM :(), with an emulated (single) SCSI hard disk. The installation starts up fine, but after the first re-boot, I just see a "trap 00000006 exception" and nothing happens after that!
I removed the SCSI disk (virtual) and then the VM boots up fine with the ISO image.
I cannot get any concrete information on if QEMU supports SCSI emulation.
Any help ?

Oh and I'm trying all this on a Ubuntu 9.10 server, managing using virsh.

-RR

I'd point more toward a scsi driver issue with win2k3. I'm running virtio now with kvm, but I had previously used scsi with linux guests without issue.

---

### Post by ravindra.rajaram on 2010-01-27
I can try the virtio option, but I'm not sure if that will help the issue at hand. The windows image that I'm trying to create, is expected to be deployed on a cloud environment based on Eucalyptus.
Research suggests a SCSI HD with atleast two partitions is required for the HD to work with Eucalyptus. I'll however try the virtio option and report back!

---

### Post by Seq on 2010-01-27
> **ravindra.rajaram said:**
> I can try the virtio option, but I'm not sure if that will help the issue at hand. The windows image that I'm trying to create, is expected to be deployed on a cloud environment based on Eucalyptus.
Research suggests a SCSI HD with atleast two partitions is required for the HD to work with Eucalyptus. I'll however try the virtio option and report back!

virtio would require a driver as well. I haven't really virtualized Windows on qemu or kvm. There appears to be some drivers available.

[http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers]("http://www.linux-kvm.com/content/tip-how-setup-windows-guest-paravirtual-network-drivers")

---

