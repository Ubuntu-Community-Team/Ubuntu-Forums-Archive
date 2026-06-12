---
title: "QEMU-KVM Video Out Options"
date: 2019-08-04
forum: Virtualisation
---

### Post by cruzer001 on 2019-08-04
First off let me say that this is a home user setup and not a production machine, I'm just looking for what's best for me.

There are choices offered for video out.  Right now I have QXL running with 64M of vram (seems to be enough), but what about the other options?  "VGA, Virto, VMVGA, Xen"  Would I be better off using something else?

---

### Post by Dennis N on 2019-08-04
I set it to virtio. Its the only video option that offered 3D acceleration to be selected.

---

### Post by cruzer001 on 2019-08-04
Hi Dennis N :)

Although I do not currently run virtual 3D, this is _very_ good to know for future use.

Gnome-desktop (not ubuntu-gnome) is the most resource hungry desktop I currently have running in a VM (3D not required).

---

### Post by cruzer001 on 2019-08-05
RedHat adds a little to this

[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/chap-kvm_para_virtualized_virtio_drivers#sect-KVM_Para_virtualized_virtio_Drivers-Using_KVM_virtio_drivers_for_existing_devices](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/virtualization_deployment_and_administration_guide/chap-kvm_para_virtualized_virtio_drivers#sect-KVM_Para_virtualized_virtio_Drivers-Using_KVM_virtio_drivers_for_existing_devices)

---

### Post by Dennis N on 2019-08-05
```
RedHat adds a little to this
```

Yes, that's referring to the "Virtual Disk" type selection, where one if them is also labeled Virtio (I'm using that). Previous posts referred to Virtio Video option. Virt Manager GUI allows switching Virtual Disk type after installing, so you don't need to use terminal as discussed in the article if you use Virt Manager.  

My Virt Manager settings panel has Virtual Disk options (Disk bus) as:

Virtio
SATA
SCSI
USB

I once did some timings of startup. Virtio was the fastest, but SATA was close. IDE is slow. I installed using UEFI, although there may be no obvious reason* to do that with just one OS on the disk. I once checked the speed, and UEFI may take 1 or 2 seconds longer. 

One OS installer, Manjaro, would not install to VM with Virtio disk, so used SATA instead.

*some non-obvious reasons to use UEFI can be found: [TianoCore]("https://www.tianocore.org/")

---

### Post by cruzer001 on 2019-08-05
> My Virt Manager settings panel has Virtual Disk options (Disk bus) as:

Virtio
SATA
SCSI
USB
I pondered over that setting when I ran across it, thinking it should be sata.  I left it at default.

---

