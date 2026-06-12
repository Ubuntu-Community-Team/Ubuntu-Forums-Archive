---
title: "GPU Passthrough: Blank Screen on Intel Integrated Graphics, Tux on Nvidia"
date: 2017-07-12
forum: Virtualisation
---

### Post by ysng on 2017-07-12
Hi all,

I have referred to many GPU passthrough guides but mainly based on [this site]("https://forum.level1techs.com/t/play-games-in-windows-on-linux-pci-passthrough-quick-guide/108981") since the progress I got is the furthest.

My setup is as follows:
-HP Envy 700-070d
-Intel(R) Core(TM) i5-4570 CPU @ 3.20GHz-Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
-NVIDIA GeForce GTX 770
-Linux 16.04 LTS x86_64 Kernel: 4.8.17
-One monitor is connected to the motherboard DVI port, the other connected to NVIDIA DVI port

What I want to achieve is to host Linux on Intel Integrated Graphics and a Windows VM on my Nvidia card.
However, I am stuck with a blank monitor on the iGPU whereas a purple screen with Tux logos on the Nvidia monitor.
I tried reconfiguring with both gdm and lightdm. But both ended up on the same blank screen despite a short Ubuntu loading screen on gdm.

After applying the ASC patch, this is my current IOMMU grouping:
```
IOMMU Group 0 00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
IOMMU Group 10 00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 04)
IOMMU Group 11 00:1f.0 ISA bridge [0601]: Intel Corporation Z87 Express LPC Controller [8086:8c44] (rev 04)
IOMMU Group 11 00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 04)
IOMMU Group 11 00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 04)
[B]IOMMU Group 12 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 770] [10de:1184] (rev a1)
IOMMU Group 12 01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)[/B]
IOMMU Group 13 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
IOMMU Group 14 04:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]
IOMMU Group 1 00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
**IOMMU Group 2 00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)**
IOMMU Group 3 00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 04)
IOMMU Group 4 00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
IOMMU Group 5 00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 04)
IOMMU Group 6 00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 04)
IOMMU Group 7 00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d4)
IOMMU Group 8 00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d4)
IOMMU Group 9 00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d4)

```

Unlike the guide, I have to blacklist nouveau in */etc/modprobe.d/blacklist.conf* as such:
```

blacklist nouveau
blacklist nvidiafb

```

This is what I managed to get after blacklisting nouveau:
```
 *-display       description: VGA compatible controller
       product: GK104 [GeForce GTX 770]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       **configuration: driver=vfio-pci latency=0**
       resources: irq:255 memory:f6000000-f6ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:c0000-dffff
  *-display
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       **configuration: driver=i915 latency=0**
       resources: irq:33 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)

```

And the kernel information on the GPUs are as follows:
```

00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
        DeviceName:  Onboard IGD
        Subsystem: Hewlett-Packard Company Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
        **Kernel driver in use: i915**
        Kernel modules: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 770] (rev a1)
        Subsystem: CardExpert Technology GK104 [GeForce GTX 770]
        **Kernel driver in use: vfio-pci**
        Kernel modules: nvidiafb, nouveau
01:00.1 Audio device: NVIDIA Corporation GK104 HDMI Audio Controller (rev a1)
        Subsystem: CardExpert Technology GK104 HDMI Audio Controller
        **Kernel driver in use: vfio-pci**
        Kernel modules: snd_hda_intel

```

The respective GPUs seem to be correctly claimed but I have no idea why there is no display on the iGPU monitor.
And for your information, there's display when I physically remove the NVIDIA card from the motherboard. :mad::mad:
I have also tried updating Intel graphics drivers and using *nomodeset *on grub.
On bios, Virtualization Technology is enabled and Intel VGA Controller is set as the Primary VGA device.

Any suggestion or advice is appreciated!!

---

