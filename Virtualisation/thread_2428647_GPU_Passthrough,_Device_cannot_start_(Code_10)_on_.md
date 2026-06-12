---
title: "GPU Passthrough, Device cannot start (Code 10) on Guest"
date: 2019-10-07
forum: Virtualisation
---

### Post by estov on 2019-10-07
Hey there,

I've got a fresh install of Ubuntu on my notebook and I'd like to get Windows 7 (64bit) running as a VM with the kvm / QEMU / GPU passthrough technology. I got everything running but unfortunately Windows 7 doesn't recognize my GPU properly, in the device manager it shows a VGA card with the error message: "Device cannot start (Code 10)." It's strange though that the guest properly recognizes the audio chip of my GPU. 


I have 2 graphic cards on my computer (Intels Integrated graphics card and a GeForce GTX 1060):
```
 
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:591b] (rev 04)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] [10de:1c20] (rev a1)
```

Distribution I am running:
```

Ubuntu 18.04.3 LTS
```

Kernel version:
```
 5.0.0-31-generic

```

I followed several tutorials (mainly Arch Wiki) to setup the passthrough technology. Here my settings
1. Enabling IOMMU
- Kernel parameters for booting:
```
$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-5.0.0-31-generic root=UUID=a5c08679-4ccc-442e-a4b9-cc36649adc06 ro quiet splash intel_iommu=on iommu=pt kvm_amd.npt=1 vt.handoff=1

```
- IOMMU groups
```
 
IOMMU Group 0:
    00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers [8086:5910] (rev 05)
IOMMU Group 1:
[B]    00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) [8086:1901] (rev 05)
    01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] [10de:1c20] (rev a1)
    01:00.1 Audio device [0403]: NVIDIA Corporation GP106 High Definition Audio Controller [10de:10f1] (rev a1)[/B]
IOMMU Group 10:
    02:00.0 Network controller [0280]: Intel Corporation Dual Band Wireless-AC 3168NGW [Stone Peak] [8086:24fb] (rev 10)
IOMMU Group 11:
    03:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2500 Gigabit Ethernet Controller [1969:e0b1] (rev 10)
IOMMU Group 12:
    04:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1142 USB 3.1 Host Controller [1b21:1242]
IOMMU Group 2:
    00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:591b] (rev 04)
IOMMU Group 3:
    00:14.0 USB controller [0c03]: Intel Corporation 100 Series/C230 Series Chipset Family USB 3.0 xHCI Controller [8086:a12f] (rev 31)
    00:14.2 Signal processing controller [1180]: Intel Corporation 100 Series/C230 Series Chipset Family Thermal Subsystem [8086:a131] (rev 31)
IOMMU Group 4:
    00:16.0 Communication controller [0780]: Intel Corporation 100 Series/C230 Series Chipset Family MEI Controller #1 [8086:a13a] (rev 31)
IOMMU Group 5:
    00:17.0 SATA controller [0106]: Intel Corporation HM170/QM170 Chipset SATA Controller [AHCI Mode] [8086:a103] (rev 31)
IOMMU Group 6:
    00:1c.0 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #1 [8086:a110] (rev f1)
IOMMU Group 7:
    00:1c.3 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #4 [8086:a113] (rev f1)
IOMMU Group 8:
    00:1c.4 PCI bridge [0604]: Intel Corporation 100 Series/C230 Series Chipset Family PCI Express Root Port #5 [8086:a114] (rev f1)
IOMMU Group 9:
    00:1f.0 ISA bridge [0601]: Intel Corporation HM175 Chipset LPC/eSPI Controller [8086:a152] (rev 31)
    00:1f.2 Memory controller [0580]: Intel Corporation 100 Series/C230 Series Chipset Family Power Management Controller [8086:a121] (rev 31)
    00:1f.3 Audio device [0403]: Intel Corporation CM238 HD Audio Controller [8086:a171] (rev 31)
    00:1f.4 SMBus [0c05]: Intel Corporation 100 Series/C230 Series Chipset Family SMBus [8086:a123] (rev 31)

```

2. Isolation of the GPU with the vfio kernel module
- Kernel driver in use:
```
 01:00.0 VGA compatible controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] (rev a1)
    **Kernel driver in use: vfio-pci**
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GP106 High Definition Audio Controller (rev a1)
    **Kernel driver in use: vfio-pci**
    Kernel modules: snd_hda_intel

```

3. Setting up qemu
In the /etc/libvirt/qemu.conf file I uncommented:
```

nvram = [
   "/usr/share/OVMF/OVMF_CODE.fd:/usr/share/OVMF/OVMF_VARS.fd",
   "/usr/share/OVMF/OVMF_CODE.secboot.fd:/usr/share/OVMF/OVMF_VARS.fd",
   "/usr/share/AAVMF/AAVMF_CODE.fd:/usr/share/AAVMF/AAVMF_VARS.fd",
   "/usr/share/AAVMF/AAVMF32_CODE.fd:/usr/share/AAVMF/AAVMF32_VARS.fd"
]

```
4. Using virt-manager to setup guest (Windows 7 64 bit).
Nothing fancy /standard procedure. As Firmware I used UEFI, I tried both available chipsets (i440FX and Q35) and I checked "Copy host CPU configuration". After the installation of the guest I added the graphics card with the audio (2 pci devices) as hardware.


What could I have missed here ?
I also tested Arch Linux as a guest system and it seemed that it  properly recognized my GPU (lspci delivered NVIDIA GPU), so it might  be an issue with Windows 7 ?

Any help is very appreciated. Thanks in advance !

---

