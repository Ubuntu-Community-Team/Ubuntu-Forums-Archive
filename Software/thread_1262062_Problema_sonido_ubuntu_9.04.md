---
title: "Problema sonido ubuntu 9.04"
date: 2009-09-04
forum: Software
---

### Post by emasg on 2009-09-04
Hola a todos, hace un tiempo me instalé ubuntu 9.04 en mi pc. Si bien soy nuevo en linux pude arreglarme solo para la mayoría de las cosas. Lo único que no logré solucionar todavía es el tema del sonido.
Tengo una placa de sonido pci encore no se cuanto, y otra encore de entrada de tv.
El problema en sí es muy raro. Por ejemplo, en el tvtime funciona perfecto el sonido, sale por los dos parlantes y se escucha muy bien.
Para la música uso Rhythmbox, y se escucha por un solo parlante.
Y para lo que es video (cualquier formato, hasta los de flash) no se escucha.
Ya revisé todo el tema de los volúmenes con el alsamixer y etc.
En varios foros ví que podía ser ese el problema, pero no se soluciona.
Otro problema es que tengo que deshabilitar el sonido de los juegos para poder jugarlos porque se entrecorta y el juego se pone lento (hasta el counter 1.6 por wine).

esta es la salida de lspci -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device 818e
    Flags: bus master, medium devsel, latency 32
    Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
    Capabilities: [c0] AGP version 3.5
    Kernel driver in use: agpgart-sis
    Kernel modules: sis-agp

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
    Flags: bus master, 66MHz, fast devsel, latency 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: cef00000-cfffffff
    Prefetchable memory behind bridge: d0000000-dfffffff
    Kernel modules: shpchp

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
    Flags: bus master, medium devsel, latency 0

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01) (prog-if 80 [Master])
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 128, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ffa0 [size=16]
    Capabilities: [58] Power Management version 2
    Kernel driver in use: pata_sis

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
    Subsystem: ASUSTeK Computer Inc. Device 810f
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at d800 [size=256]
    I/O ports at d400 [size=128]
    Capabilities: [48] Power Management version 2
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at ceefc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 64, IRQ 21
    Memory at ceefd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f) (prog-if 10)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 64, IRQ 22
    Memory at ceefe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 64, IRQ 23
    Memory at ceeff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: ehci_hcd

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, medium devsel, latency 64, IRQ 19
    I/O ports at d000 [size=256]
    Memory at ceefb000 (32-bit, non-prefetchable) [size=4K]
    Expansion ROM at ceec0000 [disabled] [size=128K]
    Capabilities: [40] Power Management version 2
    Kernel driver in use: sis900
    Kernel modules: sis900

00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01) (prog-if 85)
    Subsystem: ASUSTeK Computer Inc. Device 810e
    Flags: bus master, 66MHz, medium devsel, latency 128, IRQ 17
    I/O ports at c800 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c000 [size=8]
    I/O ports at b800 [size=4]
    I/O ports at b400 [size=16]
    I/O ports at <unassigned>
    Kernel driver in use: sata_sis

00:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
    Subsystem: VIA Technologies Inc. Device 2403
    Flags: bus master, medium devsel, latency 64, IRQ 19
    I/O ports at b000 [size=32]
    I/O ports at a800 [size=128]
    Capabilities: [80] Power Management version 1
    Kernel driver in use: ICE1724
    Kernel modules: snd-ice1724

00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
    Subsystem: Device 1a7f:2008
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at ceefac00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [40] Power Management version 1
    Kernel driver in use: saa7134
    Kernel modules: saa7134

00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
    Flags: bus master, medium devsel, latency 64, IRQ 18
    I/O ports at a400 [size=256]
    Memory at ceefa800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp

01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)
    Subsystem: XFX Pine Group Inc. Device 1219
    Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
    Memory at cf000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    [virtual] Expansion ROM at cefe0000 [disabled] [size=128K]
    Capabilities: [60] Power Management version 2
    Capabilities: [44] AGP version 3.0
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafb

esta es la salida de asoundconf list:
Names of available sound cards:
SI7012
SAA7134
ICE1724

Hay alguna aplicación que sea como un asistente para configurar el sonido?
espero respuesta, desde ya muchas gracias :)

---

### Post by emasg on 2009-09-09
Hola Foro!
ya habia iniciado este thread pero me lo movieron y no lo puedo encontrar.
Soy practicamente nuevo en linux, aunque me manejo bien y pude hacer que casi todo funcione como lo esperaba, el problema que persiste es el del sonido.
Tengo una placa de sonido encore no se cuanto pci y una de entrada de tv tambien encore.
Cuando uso el tvtime el sonido anda perfecto, el unico problema es que lo cierro y se sigue escuchando como si estaria abierto, pero bueno, silencio la entrada de linea y listo.
Cuando escucho musica por rhythmbox tengo el problema de que el sonido sale por un solo parlante pero en mono. digamos, se escucha todo, pero en un solo parlante.
Y en youtube y en otros videos anda solamente algunas veces, a veces directamente no arranca y tengo que reiniciar la pc.
En los juegos tambien tengo problemas, inclusive con el cs 6 emulado, si le pongo sonido se escucha entrecortado y el juego, cualquiera sea, se vuelve lentisimo.

dejo la salida de lspci:
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:08.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
00:09.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600] (rev a1)

Aclaracion: tengo windows xp en la misma pc y el sonido funciona bien.
Alguna idea?

---

### Post by emasg on 2009-09-09
buenisimo!

---

