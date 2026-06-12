---
title: "Sonido trabado"
date: 2009-07-24
forum: Software
---

### Post by bloodytanga on 2009-07-24
Tengo un problema con el sonido. Me reproduce casi siempre bien pero a veces como que se  traba o hace ruidos tipo zumbidos.

---

### Post by milovan1971 on 2009-07-25
Tendrías que explicar un poco mejor el problema. Qué tarjeta tenés?
Si no sabés los datos de la tarjeta, escribí esto en la terminal:
```
lspci -vnn
```y copía acá el resultado de la sección "Multimedia audio controller" o algo por el estilo.
cheers.

---

### Post by bloodytanga on 2009-07-25
Mi tarjeta de sonido es la onboard de la placa Asus K8V-MX.
El audio me anda bien pero a veces cuando estoy escuchando música y me llega un mensaje en pidgin los parlantes empiezan a hacer como un zumbido corto. O si estoy escuchando música y en internet hay un video de youtube (sin que lo abra, solo está ahi) generalmente asa lo mismo del zumbido o sino se traba la canción y despues de un instantet vuelve a reproducirse.

---

### Post by MPx1 on 2009-07-28
a mi me pasa lo mismo, pero yo tengo una placa de sonido pci [viejita, ya]

te paso lo que me muestra la terminal:

00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e300 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e100 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e200 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at e400 [size=8]
	I/O ports at e500 [size=4]
	I/O ports at e600 [size=8]
	I/O ports at e700 [size=4]
	I/O ports at e800 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: medium devsel, IRQ 5
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

02:01.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
	Subsystem: Creative Labs Device [1102:100a]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:02.0 VGA compatible controller [0300]: nVidia Corporation NV18 [GeForce4 MX 4000] [10de:0185] (rev c1)
	Subsystem: XFX Pine Group Inc. Device [1682:201f]
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:04.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13f0:0200] (rev 31)
	Subsystem: Sundance Technology Inc / IC Plus Corp Device [13f0:0201]
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d100 [size=128]
	Memory at f5020000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at f5030000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: sundance
	Kernel modules: sundance

mpx@mpx-desktop:~$ su
Contraseña: 
root@mpx-desktop:/home/mpx# lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
	Subsystem: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570]
	Flags: bus master, fast devsel, latency 0
	Memory at f0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [e4] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 3.0
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] (rev 02)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Kernel modules: shpchp

00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e300 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e100 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e200 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02) (prog-if 20)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f6000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f4000000-f5ffffff
	Prefetchable memory behind bridge: e8000000-efffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 18
	I/O ports at e400 [size=8]
	I/O ports at e500 [size=4]
	I/O ports at e600 [size=8]
	I/O ports at e700 [size=4]
	I/O ports at e800 [size=16]
	Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
	Subsystem: Foxconn International, Inc. Device [105b:0c71]
	Flags: medium devsel, IRQ 5
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

02:01.0 Multimedia audio controller [0401]: Creative Labs CA0106 Soundblaster [1102:0007]
	Subsystem: Creative Labs Device [1102:100a]
	Flags: bus master, medium devsel, latency 32, IRQ 22
	I/O ports at d000 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:02.0 VGA compatible controller [0300]: nVidia Corporation NV18 [GeForce4 MX 4000] [10de:0185] (rev c1)
	Subsystem: XFX Pine Group Inc. Device [1682:201f]
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
	Memory at f4000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	[virtual] Expansion ROM at f5000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:04.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13f0:0200] (rev 31)
	Subsystem: Sundance Technology Inc / IC Plus Corp Device [13f0:0201]
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at d100 [size=128]
	Memory at f5020000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at f5030000 [disabled] [size=64K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: sundance
	Kernel modules: sundance

---

