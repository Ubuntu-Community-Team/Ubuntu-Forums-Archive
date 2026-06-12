---
title: "KVM VGA pass-through not working for integrated AMD Ryzen 4900H Graphics"
date: 2022-07-12
forum: Virtualisation
---

### Post by Nunnsby on 2022-07-12
Running a headless server on a mini PC, with only one Graphics Card, the integrated board, a Ryzen 4900H. The card appears at group 6, but with a load of other devices too. 
I have loaded the vfio-pci driver and am using iommu.

Getting the following error when trying to start a VM: 

```

Error starting domain: internal error: qemu unexpectedly closed the monitor: 2022-07-12T22:08:31.781466Z qemu-system-x86_64: -device vfio-pci,host=0000:06:00.0,id=hostdev0,bus=pci.7,addr=0x0: vfio 0000:06:00.0: group 7 is not viable
Please ensure all devices within the iommu_group are bound to their vfio bus driver.

```

I suspect for some reason something else is grabbing the device/devices. A lot of articles here and elsewhere talk about Nvidia Drivers, so I am wondering if this is specific to to my AMD setup.

I currently have the following configuration in place:

/etc/default/grub

```

GRUB_CMDLINE_LINUX_DEFAULT="amd_iommu=on iommu=pt vm.ignore_msrs=1 vfio-pci.ids=1002:1636,1002:1637,1022:15df,1022:1639,1022:15e2,1022:15e3,1022:15e4"

```

lspci -nnv

```

00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Root Complex [1022:1630]
        Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir Root Complex [1022:1630]
        Flags: fast devsel

00:00.2 IOMMU [0806]: Advanced Micro Devices, Inc. [AMD] Renoir IOMMU [1022:1631]
        Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir IOMMU [1022:1631]
        Flags: bus master, fast devsel, latency 0, IRQ 25
        Capabilities: <access denied>

00:01.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
        Flags: fast devsel

00:01.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge [1022:1634] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 26
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: [disabled]
        Memory behind bridge: fcf00000-fcffffff [size=1M]
        Prefetchable memory behind bridge: [disabled]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:01.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge [1022:1634] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000f000-0000ffff [size=4K]
        Memory behind bridge: fce00000-fcefffff [size=1M]
        Prefetchable memory behind bridge: [disabled]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
        Flags: fast devsel

00:02.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge [1022:1634] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: [disabled]
        Memory behind bridge: [disabled]
        Prefetchable memory behind bridge: 00000000e0300000-00000000e04fffff [size=2M]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:02.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge [1022:1634] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 29
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: [disabled]
        Memory behind bridge: fc900000-fcbfffff [size=3M]
        Prefetchable memory behind bridge: [disabled]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:02.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe GPP Bridge [1022:1634] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: [disabled]
        Memory behind bridge: fcd00000-fcdfffff [size=1M]
        Prefetchable memory behind bridge: [disabled]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:08.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge [1022:1632]
        Flags: fast devsel

00:08.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus [1022:1635] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 31
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 0000e000-0000efff [size=4K]
        Memory behind bridge: fc400000-fc8fffff [size=5M]
        Prefetchable memory behind bridge: 00000000d0000000-00000000e01fffff [size=258M]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:08.2 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus [1022:1635] (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        I/O behind bridge: [disabled]
        Memory behind bridge: fcc00000-fccfffff [size=1M]
        Prefetchable memory behind bridge: [disabled]
        Capabilities: <access denied>
        Kernel driver in use: pcieport

00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b] (rev 51)
        Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:790b]
        Flags: 66MHz, medium devsel
        Kernel driver in use: piix4_smbus
        Kernel modules: i2c_piix4, sp5100_tco

00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e] (rev 51)
        Subsystem: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:790e]
        Flags: bus master, 66MHz, medium devsel, latency 0

00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 0 [1022:1448]
        Flags: fast devsel

00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 1 [1022:1449]
        Flags: fast devsel

00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 2 [1022:144a]
        Flags: fast devsel

00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 3 [1022:144b]
        Flags: fast devsel
        Kernel driver in use: k10temp
        Kernel modules: k10temp

00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 4 [1022:144c]
        Flags: fast devsel

00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 5 [1022:144d]
        Flags: fast devsel

00:18.6 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 6 [1022:144e]
        Flags: fast devsel

00:18.7 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Renoir Device 24: Function 7 [1022:144f]
        Flags: fast devsel

01:00.0 Non-Volatile memory controller [0108]: Kingston Technology Company, Inc. Device [2646:500d] (rev 01) (prog-if 02 [NVM Express])
        Subsystem: Kingston Technology Company, Inc. Device [2646:500d]
        Flags: bus master, fast devsel, latency 0, IRQ 36, NUMA node 0
        Memory at fcf00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: nvme
        Kernel modules: nvme

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
        DeviceName: Onboard LAN Brodcom
        Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:0123]
        Flags: bus master, fast devsel, latency 0, IRQ 24
        I/O ports at f000 [size=256]
        Memory at fce04000 (64-bit, non-prefetchable) [size=4K]
        Memory at fce00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

03:00.0 Network controller [0280]: MEDIATEK Corp. Device [14c3:0608]
        Subsystem: MEDIATEK Corp. Device [14c3:0608]
        Flags: fast devsel, IRQ 255
        Memory at e0300000 (64-bit, prefetchable) [disabled] [size=1M]
        Memory at e0400000 (64-bit, prefetchable) [disabled] [size=16K]
        Memory at e0404000 (64-bit, prefetchable) [disabled] [size=4K]
        Capabilities: <access denied>

04:00.0 Ethernet controller [0200]: Intel Corporation Device [8086:15f3] (rev 01)
        Subsystem: Intel Corporation Device [8086:0000]
        Flags: bus master, fast devsel, latency 0, IRQ 35
        Memory at fca00000 (32-bit, non-prefetchable) [size=1M]
        Memory at fcb00000 (32-bit, non-prefetchable) [size=16K]
        Expansion ROM at fc900000 [disabled] [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: igc
        Kernel modules: igc

05:00.0 USB controller [0c03]: VIA Technologies, Inc. VL805 USB 3.0 Host Controller [1106:3483] (rev 01) (prog-if 30 [XHCI])
        Subsystem: VIA Technologies, Inc. VL805 USB 3.0 Host Controller [1106:3483]
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at fcd00000 (64-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: xhci_hcd

06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Renoir [1002:1636] (rev f0) (prog-if 00 [VGA controller])
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Renoir [1002:0123]
        Flags: bus master, fast devsel, latency 0, IRQ 255
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at e0000000 (64-bit, prefetchable) [size=2M]
        I/O ports at e000 [disabled] [size=256]
        Memory at fc800000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci
        Kernel modules: amdgpu

06:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:1637]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:1637]
        Flags: fast devsel, IRQ 255
        Memory at fc8c8000 (32-bit, non-prefetchable) [disabled] [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci
        Kernel modules: snd_hda_intel

06:00.2 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor [1022:15df]
        Subsystem: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor [1022:15df]
        Flags: fast devsel, IRQ 255
        Memory at fc700000 (32-bit, non-prefetchable) [disabled] [size=1M]
        Memory at fc8ce000 (32-bit, non-prefetchable) [disabled] [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci

06:00.3 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1 [1022:1639] (prog-if 30 [XHCI])
        Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1 [1022:1639]
        Flags: fast devsel, IRQ 25
        Memory at fc600000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci

06:00.4 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1 [1022:1639] (prog-if 30 [XHCI])
        Subsystem: Advanced Micro Devices, Inc. [AMD] Renoir USB 3.1 [1022:1639]
        Flags: fast devsel, IRQ 25
        Memory at fc500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci

06:00.5 Multimedia controller [0480]: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor [1022:15e2] (rev 01)
        Subsystem: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor [1022:15e2]
        Flags: fast devsel, IRQ 255
        Memory at fc880000 (32-bit, non-prefetchable) [disabled] [size=256K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci
        Kernel modules: snd_pci_acp3x, snd_rn_pci_acp3x

06:00.6 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller [1022:15e3]
        DeviceName: HD Audio Controller
        Subsystem: Realtek Semiconductor Co., Ltd. Family 17h (Models 10h-1fh) HD Audio Controller [10ec:0000]
        Flags: fast devsel, IRQ 255
        Memory at fc8c0000 (32-bit, non-prefetchable) [disabled] [size=32K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci
        Kernel modules: snd_hda_intel

06:00.7 Signal processing controller [1180]: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/Renoir Sensor Fusion Hub [1022:15e4]
        Subsystem: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/Renoir Sensor Fusion Hub [1022:15e4]
        Flags: fast devsel, IRQ 255
        Memory at fc400000 (32-bit, non-prefetchable) [disabled] [size=1M]
        Memory at fc8cc000 (32-bit, non-prefetchable) [disabled] [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: vfio-pci

07:00.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 81) (prog-if 01 [AHCI 1.0])
        Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901]
        Flags: bus master, fast devsel, latency 0, IRQ 39
        Memory at fcc01000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

07:00.1 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901] (rev 81) (prog-if 01 [AHCI 1.0])
        Subsystem: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7901]
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at fcc00000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: ahci
        Kernel modules: ahci

```

dmesg | grep -i -e amd-vi -e dmar

```

[    0.156479] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR0, rdevid:160
[    0.156480] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR1, rdevid:160
[    0.156482] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR2, rdevid:160
[    0.156483] AMD-Vi: ivrs, add hid:AMDI0020, uid:\_SB.FUR3, rdevid:160
[    0.605950] pci 0000:00:00.2: AMD-Vi: IOMMU performance counters supported
[    0.606797] pci 0000:00:00.2: AMD-Vi: Found IOMMU cap 0x40
[    0.606799] pci 0000:00:00.2: AMD-Vi: Extended features (0x206d73ef22254ade):
[    0.606802] AMD-Vi: Interrupt remapping enabled
[    0.606803] AMD-Vi: Virtual APIC enabled
[    0.606804] AMD-Vi: X2APIC enabled
[    0.606949] AMD-Vi: Lazy IO/TLB flushing enabled
[    1.606348] AMD-Vi: AMD IOMMUv2 driver by Joerg Roedel <jroedel@suse.de>

```

---

### Post by Tadaen_Sylvermane on 2022-07-12
I've always understood you can't pass through the integrated. Need a discreet card.

---

### Post by Nunnsby on 2022-07-13
So I have two Mini PC's. The one is an Older Intel NUC, and the Integrated card on that one was in it's own "Group", and I was able to pass through that card fine, but, it was alone. This card, as you can see, shares the "Group" with a lot of other devices, so I'm thinking it is the other devices that are somehow being grabbed and causing the issue. But good to bear in mind that is might not actually be possible on this integrated board.

---

