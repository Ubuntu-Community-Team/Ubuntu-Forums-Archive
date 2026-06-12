---
title: "QEMU GPU Passthrough - No output to monitor"
date: 2016-08-23
forum: Virtualisation
---

### Post by rimorobi on 2016-08-23
Hello!

I tried to make the QEmu - GPU Passthrough thing work, but with no success. I followed the tutorial on the Arch Wiki. Everything worked until I installed Windows and I wanted to add the isolated Gpu to the VM. Then no output was sent to the connected HDMI monitor. 

My comp is az Acer V5-591G Notebook with i7-6700HQ and GTX950M and Intel HD530 Intergrated Graphics. 

I think the problem is that the intergrated card handles the HDMI slot, because when I start ubuntu, it indentifies the connected display and sets up the screen mirroring. If I disabled the display in the settings, it didnt help.

Could it be the problem that the Nvidia card has no access to the HDMI slot, so it doesn't see the display? If I connect a vnc to the VM, then I can see that windows starts up correctly.

Thanks for any help!

---

### Post by KillerKelvUK on 2016-08-23
Hi, so you are thinking correctly.  HDMI ports are directly linked to a specific GFX card and cannot work with any other GFX cards, so a HDMI out on your motherboard is only paired to the integrated graphics.  For GPU passthrough you need to us the HDMI slot on the GPU you are passing through.

---

### Post by rimorobi on 2016-08-23
So I have no chance to use the Nvidia card for passthrough, even if I install the driver on the Windows guest?

---

### Post by KillerKelvUK on 2016-08-24
Technically you have several options available depending upon your hardware and proficiency in linux...
[LIST]
[*]Primary vga assignment; this is where you attempt to pass through the gfx card your virtual host (physical PC) assigns as its primary GFX card when it boots up, the one that displays your BIOS/UEFI screen etc.  Passing through the primary GFX card in all circumstances is extremely troublesome due to how the host has to bind to that card as part of the boot process.  When your host has integrated gfx e.g. Intel iGP this is even worse and to my knowledge not possible outside of the Intel GVP project which is still in development ([https://01.org/igvt-g](https://01.org/igvt-g)).  If your host doesn't have integrated gfx but instead requires a gfx card in one of the PCI slots then it is possible to pass this through, the downside however is that you have to sacrifice host GFX i.e. you will have no video output at all and be relegated to managing the host via SSH etc.  This kind of passthrough whilst possible is more complicated and troublesome than the alternative (below), requiring a functional UEFI/OVMF chain, disabling the framebuffer, dumping the VBIOS on the primary card plus all the other passthrough steps as you've probably been following.
[*]Secondary vga assignment; this is where you have 2x gfx cards in your host e.g. for me I have my Intel iGP which is my primary and an nVidia PCI card as my secondary...so to be clear my host PC boots and uses the Intel iGP gfx for output to my monitors and my nVidia card is not used at all by my OS (blacklisted and stubbed to vfio-pci).  As a result the secondary gfx card is much more accessible to kvm/qemu as it isn't tied into the vga arbitration process the host goes through on boot, this method of passthrough is what you will mostly read about and is much easier to achieve.
[/LIST]

So to answer your question, its difficult to say what will/wont work for you based on your posting so far.  I'd suggest you need to review the options you have in the UEFI on the laptop to see if there is a way to stop it grabbing the connected display on the HDMI port, it would also be of use to see the output of 'sudo lspci -v'.

---

### Post by rimorobi on 2016-08-24
I'll look around see if I can somehow disable the intel card of taking ownership in handling the HDMI output

The output of sudo lspci -v:

```

00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 07)
	Subsystem: Acer Incorporated [ALI] Skylake Host Bridge/DRAM Registers
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=10 <?>


00:01.0 PCI bridge: Intel Corporation Sky Lake PCIe Controller (x16) (rev 07) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 122
	Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: 93000000-93ffffff
	Prefetchable memory behind bridge: 0000000080000000-0000000091ffffff
	Capabilities: [88] Subsystem: Acer Incorporated [ALI] Skylake PCIe Controller (x16)
	Capabilities: [80] Power Management version 3
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [a0] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [140] Root Complex Link
	Capabilities: [d94] #19
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:02.0 VGA compatible controller: Intel Corporation Skylake Integrated Graphics (rev 06) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Skylake Integrated Graphics
	Flags: bus master, fast devsel, latency 0, IRQ 128
	Memory at 92000000 (64-bit, non-prefetchable) [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 5000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [40] Vendor Specific Information: Len=0c <?>
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [100] #1b
	Capabilities: [200] Address Translation Service (ATS)
	Capabilities: [300] #13
	Kernel driver in use: i915_bpo
	Kernel modules: i915_bpo


00:14.0 USB controller: Intel Corporation Sunrise Point-H USB 3.0 xHCI Controller (rev 31) (prog-if 30 [XHCI])
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H USB 3.0 xHCI Controller
	Flags: bus master, medium devsel, latency 0, IRQ 125
	Memory at 94300000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [70] Power Management version 2
	Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
	Kernel driver in use: xhci_hcd


00:14.2 Signal processing controller: Intel Corporation Sunrise Point-H Thermal subsystem (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H Thermal subsystem
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 9432a000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-


00:15.0 Signal processing controller: Intel Corporation Sunrise Point-H LPSS I2C Controller #0 (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H Serial IO I2C Controller
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at 9432b000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Vendor Specific Information: Len=14 <?>
	Kernel driver in use: intel-lpss
	Kernel modules: intel_lpss_pci


00:16.0 Communication controller: Intel Corporation Sunrise Point-H CSME HECI #1 (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H CSME HECI
	Flags: bus master, fast devsel, latency 0, IRQ 129
	Memory at 9432c000 (64-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei_me
	Kernel modules: mei_me


00:17.0 SATA controller: Intel Corporation Sunrise Point-H SATA Controller [AHCI mode] (rev 31) (prog-if 01 [AHCI 1.0])
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H SATA Controller [AHCI mode]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 126
	Memory at 94328000 (32-bit, non-prefetchable) [size=8K]
	Memory at 9432f000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 5080 [size=8]
	I/O ports at 5088 [size=4]
	I/O ports at 5060 [size=32]
	Memory at 9432d000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Kernel driver in use: ahci
	Kernel modules: ahci


00:1c.0 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #3 (rev f1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 123
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: 94000000-941fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Sunrise Point-H PCI Express Root Port
	Capabilities: [a0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Access Control Services
	Capabilities: [200] L1 PM Substates
	Capabilities: [220] #19
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1c.3 PCI bridge: Intel Corporation Sunrise Point-H PCI Express Root Port #4 (rev f1) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0, IRQ 124
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 94200000-942fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Acer Incorporated [ALI] Sunrise Point-H PCI Express Root Port
	Capabilities: [a0] Power Management version 3
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Access Control Services
	Capabilities: [200] L1 PM Substates
	Capabilities: [220] #19
	Kernel driver in use: pcieport
	Kernel modules: shpchp


00:1f.0 ISA bridge: Intel Corporation Sunrise Point-H LPC Controller (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H LPC Controller
	Flags: bus master, medium devsel, latency 0


00:1f.2 Memory controller: Intel Corporation Sunrise Point-H PMC (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H PMC
	Flags: bus master, fast devsel, latency 0
	Memory at 94324000 (32-bit, non-prefetchable) [size=16K]


00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H HD Audio
	Flags: bus master, fast devsel, latency 32, IRQ 138
	Memory at 94320000 (64-bit, non-prefetchable) [size=16K]
	Memory at 94310000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 3
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel


00:1f.4 SMBus: Intel Corporation Sunrise Point-H SMBus (rev 31)
	Subsystem: Acer Incorporated [ALI] Sunrise Point-H SMBus
	Flags: medium devsel, IRQ 11
	Memory at 9432e000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 5040 [size=32]
	Kernel modules: i2c_i801


01:00.0 3D controller: NVIDIA Corporation GM107M [GeForce GTX 950M] (rev a2)
	Subsystem: Acer Incorporated [ALI] GM107M [GeForce GTX 950M]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 93000000 (32-bit, non-prefetchable) [size=16M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	Memory at 90000000 (64-bit, prefetchable) [size=32M]
	I/O ports at 4000 [disabled] [size=128]
	Expansion ROM at <ignored> [disabled]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [250] Latency Tolerance Reporting
	Capabilities: [258] L1 PM Substates
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>
	Capabilities: [900] #19
	Kernel driver in use: vfio-pci
	Kernel modules: nvidiafb, nouveau


07:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
	Subsystem: Foxconn International, Inc. QCA6174 802.11ac Wireless Network Adapter
	Flags: bus master, fast devsel, latency 0, IRQ 130
	Memory at 94000000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=8/8 Maskable+ 64bit-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [148] Virtual Channel
	Capabilities: [168] Device Serial Number 00-00-00-00-00-00-00-00
	Capabilities: [178] Latency Tolerance Reporting
	Capabilities: [180] L1 PM Substates
	Kernel driver in use: ath10k_pci
	Kernel modules: ath10k_pci


08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
	Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
	Flags: bus master, fast devsel, latency 0, IRQ 127
	I/O ports at 3000 [size=256]
	Memory at 94204000 (64-bit, non-prefetchable) [size=4K]
	Memory at 94200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
	Capabilities: [170] Latency Tolerance Reporting
	Capabilities: [178] L1 PM Substates
	Kernel driver in use: r8169
	Kernel modules: r8169

```

---

### Post by KillerKelvUK on 2016-08-24
Is the nvidia device at 01:00.0 in its own IOMMU group?

Looks like the laptop has a vga (dsub) output, the passthrough gfx aren't being routed to that port are they?

---

### Post by rimorobi on 2016-08-24
No, the VGA is in the IOMMU group with the 
```

00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07)

```

pci bridge.

I'll check out if the VGA connect if any output appears

---

### Post by KillerKelvUK on 2016-08-24
> **rimorobi said:**
> No, the VGA is in the IOMMU group with the 
```

00:01.0 PCI bridge [0604]: Intel Corporation Sky Lake PCIe Controller (x16) [8086:1901] (rev 07)

```

pci bridge.

I'll check out if the VGA connect if any output appears

The controller in the group shouldn't be a problem, i have the same so recommend you disregard.

```

dmesg | grep vgaarb
[    0.272139] vgaarb: setting as boot device: PCI:0000:00:02.0  <----my on chip VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
[    0.272141] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.272147] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none  <---- my secondary VGA compatible controller: NVIDIA Corporation GM204 [GeForce GTX 970] (rev a1)
[    0.272151] vgaarb: loaded
[    0.272153] vgaarb: bridge control possible 0000:01:00.0
[    0.272155] vgaarb: no bridge control possible 0000:00:02.0
[    1.613174] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    3.430200] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=io+mem:owns=none

```

How does your config compare to the above?

---

### Post by rimorobi on 2016-08-24
Thats what I got from the command. Interestingly there is nothing about the 01:00.0 device (the nvidia card)

```

[    0.250023] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.250024] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.250027] vgaarb: loaded
[    0.250027] vgaarb: bridge control possible 0000:00:02.0
[    0.990962] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem

```

---

