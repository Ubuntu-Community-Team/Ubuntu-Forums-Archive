---
title: "ethtool"
date: 2010-07-31
forum: Server Platforms
---

### Post by youngros on 2010-07-31
Following a tutorial on setting up a server using wemin and run into a couple of things. I am aware when I run ethtool I should get a whole list of settings but I don't.

If I run ethtool eth0 I get the following

> Settings for eth0:
        Current message level: 0x00000007 (7)
        Link detected: yesand for sudo dhclient eth0

> Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/00:0c:29:77:aa:a9
Sending on   LPF/eth0/00:0c:29:77:aa:a9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.16 from 192.168.1.1
DHCPREQUEST of 192.168.1.16 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.16 from 192.168.1.1
bound to 192.168.1.16 -- renewal in 123357 seconds.and lspci -k

> 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
        Kernel modules: shpchp
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
        Kernel driver in use: ata_piix
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
        Kernel modules: i2c-piix4
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
        Kernel driver in use: mptspi
        Kernel modules: mptspi
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
        Kernel driver in use: pcieport
        Kernel modules: shpchp
02:00.0 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB
        Kernel driver in use: uhci_hcd
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
        Kernel driver in use: pcnet32
        Kernel modules: pcnet32
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
        Kernel driver in use: ENS1371
        Kernel modules: snd-ens1371
02:03.0 USB Controller: VMware USB2 EHCI Controller
        Kernel driver in use: ehci_hcd



---

### Post by koenn on 2010-07-31
> **youngros said:**
> Following a tutorial on setting up a server using wemin and run into a couple of things.


these things happen.

---

