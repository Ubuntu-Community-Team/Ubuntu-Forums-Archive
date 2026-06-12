---
title: "Textures not showing"
date: 2011-01-11
forum: Wine
---

### Post by Hmmster on 2011-01-11
Hello, 
So, when i try to run for example Perfect World in wine, i cannot see any characters, and some written letters, but i can see the entire world and the weapon they're holding.
When i start the SC2 demo installer, i cannot see anything in the menü, but i can still click on stuff and it works.

Does anyone know why these textures (don't know if that's the right word)
This used to be the case in WoW too, but i solved it by making it run in OpenGL. But how do i do this do SC2 & PW?

EDIT: Hmm, for a while after i added some new things in Winetricks and installed new GPU drivers i could actually see text in the SC2 Menu, i can't now anymore though :S
I did install it when i could see the text, and now i can't see my units, or any buildings in both SP and MP.

EDIT: A fact that i hope will help, this ONLY occurs when i have the  driver you get from System -> properties -> Additional driver  installed (ATI/AMD propietary graphics driver)
This sucks though, since everything lags without it :sad:

---

### Post by Hmmster on 2011-01-12
Ffs, bump

---

### Post by mIXpRo on 2011-01-12
what is your display controller ?
and what is the output of the terminal ? 
when you run : wine "path/the game.exe"

---

### Post by Hmmster on 2011-01-13
I do not know what "Display controller" means, sorry.
And sorry, but how do i run wine "path/the game.exe"?
hmmster@Rand0m:~$ wine "~/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe"
wine: cannot find '~/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe'

---

### Post by mIXpRo on 2011-01-13
write  the output of :
> 
lspci -v


and in terminal :
> 
wine /home/USER/.wine/drive_c/Program\ Files/StarCraft\ II/StarCraft\ II.exe


---

### Post by Hmmster on 2011-01-13
> 
hmmster@Rand0m:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: fast devsel
    Capabilities: <access denied>

00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fbb00000-fbbfffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
    Subsystem: Device 0043:0083
    Flags: fast devsel
    Capabilities: <access denied>

00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
    Flags: fast devsel

00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
    Flags: fast devsel

00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
    Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at fbafe000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8375
    Flags: bus master, fast devsel, latency 0, IRQ 52
    Memory at fbaf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: c0000000-c01fffff
    Prefetchable memory behind bridge: 00000000c0200000-00000000c03fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: c0400000-c05fffff
    Prefetchable memory behind bridge: 00000000c0600000-00000000c07fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0800000-c09fffff
    Prefetchable memory behind bridge: 00000000c0a00000-00000000c0bfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.6 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 7 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fbd00000-fbdfffff
    Prefetchable memory behind bridge: 00000000c0c00000-00000000c0dfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 06) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: fbc00000-fbcfffff
    Prefetchable memory behind bridge: 00000000faf00000-00000000faffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fbafd000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: fbe00000-fbefffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 06) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at 9c00 [size=8]
    I/O ports at 9880 [size=4]
    I/O ports at 9800 [size=8]
    I/O ports at 9480 [size=4]
    I/O ports at 9400 [size=16]
    I/O ports at 9080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: medium devsel, IRQ 15
    Memory at fbafc000 (64-bit, non-prefetchable) [size=256]
    I/O ports at ffe0 [size=32]
    Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 06) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 8383
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 21
    I/O ports at ac00 [size=8]
    I/O ports at a880 [size=4]
    I/O ports at a800 [size=8]
    I/O ports at a480 [size=4]
    I/O ports at a400 [size=16]
    I/O ports at a080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series] (prog-if 00 [VGA controller])
    Subsystem: Hightech Information System Ltd. Device 2288
    Flags: bus master, fast devsel, latency 0, IRQ 54
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fbbc0000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at b000 [size=256]
    Expansion ROM at fbba0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon

01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
    Subsystem: Hightech Information System Ltd. Device aa58
    Flags: bus master, fast devsel, latency 0, IRQ 53
    Memory at fbbfc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard
    Flags: bus master, fast devsel, latency 0, IRQ 51
    I/O ports at c800 [size=256]
    Memory at fafff000 (64-bit, prefetchable) [size=4K]
    Memory at faff8000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at fbcf0000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01 [AHCI 1.0])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fbdfe000 (32-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
    Subsystem: ASUSTeK Computer Inc. Device 824f
    Flags: bus master, fast devsel, latency 0, IRQ 19
    I/O ports at dc00 [size=8]
    I/O ports at d880 [size=4]
    I/O ports at d800 [size=8]
    I/O ports at d480 [size=4]
    I/O ports at d400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_jmicron
    Kernel modules: pata_jmicron

07:01.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
    Subsystem: Accton Technology Corporation EN-1207D Fast Ethernet Adapter
    Flags: bus master, medium devsel, latency 64, IRQ 16
    I/O ports at e800 [size=256]
    Memory at fbeffc00 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at fbec0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too

07:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0) (prog-if 10 [OHCI])
    Subsystem: ASUSTeK Computer Inc. M4A series motherboard
    Flags: bus master, medium devsel, latency 64, IRQ 19
    Memory at fbeff000 (32-bit, non-prefetchable) [size=2K]
    I/O ports at ec00 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci, ohci1394


And it still can't find /home/hmmster/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe
> 
hmmster@Rand0m:~$ wine /home/hmmster/.wine/drive_c/Program\ Files/StarCraft\ II/StarCraft\ II.exe 
wine: cannot find '/home/hmmster/.wine/drive_c/Program Files/StarCraft II/StarCraft II.exe'


---

### Post by mIXpRo on 2011-01-13
try installing these :
[libtxc-dxtn-dev]("http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn-dev.php")
[libtxc-dxtn0]("http://debian-multimedia.org/dists/unstable/main/binary-i386/package/libtxc-dxtn-dev.php")

from here :
[http://debian-multimedia.org/dists/unstable/main/binary-i386/](http://debian-multimedia.org/dists/unstable/main/binary-i386/)

if it doesn't help , you have to go to winehq.org .

---

### Post by Hmmster on 2011-01-13
All that did was make some letters dissapear too =/ (It may not have been because i installed it though, sometimes when i start it they dissapear)
And what am i supposed to do on winehq? Ask there?

EDIT: A fact that i hope will help, this ONLY occurs when i have the driver you get from System -> properties -> Additional driver installed (ATI/AMD propietary graphics driver)
This sucks though, since everything lags without it :(

---

### Post by Hmmster on 2011-01-13
Bump

---

### Post by Hmmster on 2011-01-14
Bump

---

