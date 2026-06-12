---
title: "No IOMMU Groups even though VT-d is on and kvm-ok says acceleration can be used"
date: 2017-01-05
forum: Virtualisation
---

### Post by schattenphoenix on 2017-01-05
I've followed a guide for PCIe Passthrough on Ubuntu trying to eliminate the need of rebooting for games and - learning.
The guide i've followed is here: [https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/](https://www.pugetsystems.com/labs/articles/Multiheaded-NVIDIA-Gaming-using-Ubuntu-14-04-KVM-585/)
A question similar to mine has already been posted here: [https://ubuntuforums.org/showthread.php?t=2322179](https://ubuntuforums.org/showthread.php?t=2322179).

My problem is pretty much exactly what he had though the solutions suggested there dont quite cut it for me.
Ive set up everything according to this guide and checked "kvm-ok" which gives me this output:

```
root@Ubuntufon:/usr# kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used
```

Also i get this:
```
root@Ubuntufon:/usr# dmesg | grep -e DMAR -e IOMMU
[    0.000000] DMAR: IOMMU enabled
```

And 
```
find /sys/kernel/iommu_groups/ -type l
```
Gives me no output .

My GRUB_CMDLINE_LINUX_DEFAULT says
```
GRUB_CMDLINE_LINUX_DEFAULT="intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1"
```

cat on /proc/cmdline gives me
```
BOOT_IMAGE=/boot/vmlinuz-4.4.0-57-generic.efi.signed root=UUID=a166bf54-2eb9-4714-a13a-eaa355296c46 ro intel_iommu=on vfio_iommu_type1.allow_unsafe_interrupts=1
```

dmesg | grep pci-stub says
```
[    1.453818] pci-stub: add 10DE:1C03 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    1.454536] pci-stub 0000:01:00.0: claimed by stub
[    1.455385] pci-stub: add 10DE:10F1 sub=FFFFFFFF:FFFFFFFF cls=00000000/00000000
[    1.456022] pci-stub 0000:01:00.1: claimed by stub
```

Which shows me the graphics are claimed by pci-stub though
```
sudo lspci -s 01: -v
```
gives me
```
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c03 (rev a1) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 6163
    Flags: fast devsel, IRQ 16
    Memory at de000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    Expansion ROM at df000000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [250] Latency Tolerance Reporting
    Capabilities: [128] Power Budgeting <?>
    Capabilities: [420] Advanced Error Reporting
    Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
    Capabilities: [900] #19
    Kernel modules: nvidiafb, nouveau

01:00.1 Audio device: NVIDIA Corporation Device 10f1 (rev a1)
    Subsystem: eVga.com. Corp. Device 6163
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at df080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [78] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Kernel modules: snd_hda_intel
```

But I dont think this helps with the Problem (might be another though).
The Problem I currently have is, that I dont seem to have any IOMMU Groups.

This is on Ubuntu 16.04 LTS, I tryed the same on Kubuntu 16.10 before with the same results and thought it might be the cause for whatever weird reason but it does not seem so.

Any suggestions would be welcome and if you need more input, let me know!

EDIT: Photo of BIOS showing that virtualization is on
[IMG]https://i.imgsafe.org/ee93b8fbbd.jpg[/IMG]
Full Image:
[_[https://i.imgsafe.org/ee93d44902.jpg](https://i.imgsafe.org/ee93d44902.jpg)_]("https://i.imgsafe.org/ee93d44902.jpg")

---

### Post by KillerKelvUK on 2017-01-06
Hi, the photo you've shared showing virtualisation being enabled pertains only to Intel VT-x.  For PCI passthrough the CPU and motherboard need to also support Intel VT-d which is where you get your IOMMU separation.  Have you confirmed that your hardware supports both standards as on first glance your issue is that one or both factors don't support VT-d.  NOTE:  these options could be switched separately in the BIOS/UEFI i.e. on my mobo (ASRock Z97) the VT-x switch is in the CPU section and the VT-d switch is in the chipset section.

---

### Post by ODTech on 2017-01-19
The check you did for IOMMU is not accurate, rather check this way as per Alex Williamson instructions. The dev for redhat working on KVM.

```
dmesg | grep Virtual
```
You need to see an output like below, if you don't see it then IOMMU is not enabled.
```
[    0.428319] PCI-DMA: Intel(R) Virtualization Technology for Directed I/O
```

Most K series cpu's don't support Vt-d / IOMMU, since you are using a Z motherboard i'm going guess you have a K cpu. Check Intel's ARK to make sure.

---

