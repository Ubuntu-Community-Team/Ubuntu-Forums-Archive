---
title: "A veces al iniciar no tengo sonido y no puedo apagar"
date: 2010-05-18
forum: Software
---

### Post by Fisaulerod on 2010-05-18
Hola. El domingo instalé Ubuntu 10.04 y todo funciona bien excepto que a veces al iniciar no carga el sonido y no puedo apagar el sistema. Si presiono apagar sólo se va a la pantalla de login (como si hubiera puesto cerrar sesión) y ahí si pongo apagar no pasa nada, teniendo que apagar el computador a la mala.
Esto ocurre a veces y siempre las dos cosas simultaneas. ¿Qué puede ser? Nunca me ha pasado en las versiones anteriores de Ubuntu.
Gracias de antemano.

---

### Post by Carlos C on 2010-05-19
¿Obtienes algún resultado cuando corres el comando "dmesg"?

---

### Post by Fisaulerod on 2010-05-19
> **Carlos C said:**
> ¿Obtienes algún resultado cuando corres el comando "dmesg"?

Afortunadamente por ahora no me ha pasado el problema. Cuando pase (espero que no vuelva a ocurrir), veré que ocurre con ese comando. Gracias.

---

### Post by Emejota on 2010-05-22
Tengo ese mismo problema, con el mismo ubuntu

La primera vez me pasó tras instalar el dos box y jugar a un juego. Lo desinstalé pensando que sería eso, pero ahora me ha vuelto a pasar. Esta vez lo único raro que he visto que ha pasado es que encendí el ordenador estando los auriculares conectados.
No hay sonido y no puedo apagar ni reiniciar, cuando lo intento lo que hace es un cambio de usuario :confused:

Tendré que apagar el ordenador a lo bestia, pero...

Bueno, he ejecutado ese comando, dmesg, (sólo había que poner eso, verdad?? sin nada de sudo... es que no tengo ni papa) y sí me salen muchas cosas.

---

### Post by Fisaulerod on 2010-05-22
> **Fisaulerod said:**
> Afortunadamente por ahora no me ha pasado el problema. Cuando pase (espero que no vuelva a ocurrir), veré que ocurre con ese comando. Gracias.

Ahora me acaba de pasar. No ocurrió nada al hacer dmesg. Me salé esto (no veo todo porqué la terminal se acaba):

```
[    0.196055] ACPI: Interpreter enabled
[    0.196062] ACPI: (supports S0 S3 S4 S5)
[    0.196084] ACPI: Using IOAPIC for interrupt routing
[    0.201678] ACPI: EC: GPE = 0x10, I/O: command/status = 0x66, data = 0x62
[    0.202013] ACPI: No dock devices found.
[    0.202130] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.202317] pci 0000:00:01.0: reg 10 io port: [0x1d00-0x1dff]
[    0.202358] pci 0000:00:01.1: reg 10 io port: [0x3080-0x30bf]
[    0.202370] pci 0000:00:01.1: reg 20 io port: [0x3040-0x307f]
[    0.202375] pci 0000:00:01.1: reg 24 io port: [0x3000-0x303f]
[    0.202395] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.202401] pci 0000:00:01.1: PME# disabled
[    0.202459] pci 0000:00:01.3: reg 10 32bit mmio: [0xf4200000-0xf427ffff]
[    0.202541] pci 0000:00:02.0: reg 10 32bit mmio: [0xf4486000-0xf4486fff]
[    0.202565] pci 0000:00:02.0: supports D1 D2
[    0.202568] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202571] pci 0000:00:02.0: PME# disabled
[    0.202596] pci 0000:00:02.1: reg 10 32bit mmio: [0xf4489000-0xf44890ff]
[    0.202624] pci 0000:00:02.1: supports D1 D2
[    0.202627] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202630] pci 0000:00:02.1: PME# disabled
[    0.202658] pci 0000:00:04.0: reg 10 32bit mmio: [0xf4487000-0xf4487fff]
[    0.202682] pci 0000:00:04.0: supports D1 D2
[    0.202685] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202688] pci 0000:00:04.0: PME# disabled
[    0.202713] pci 0000:00:04.1: reg 10 32bit mmio: [0xf4489400-0xf44894ff]
[    0.202741] pci 0000:00:04.1: supports D1 D2
[    0.202744] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.202747] pci 0000:00:04.1: PME# disabled
[    0.202783] pci 0000:00:06.0: reg 20 io port: [0x30c0-0x30cf]
[    0.202823] pci 0000:00:07.0: reg 10 32bit mmio: [0xf4480000-0xf4483fff]
[    0.202851] pci 0000:00:07.0: PME# supported from D3hot D3cold
[    0.202855] pci 0000:00:07.0: PME# disabled
[    0.202923] pci 0000:00:09.0: reg 10 io port: [0x30f0-0x30f7]
[    0.202928] pci 0000:00:09.0: reg 14 io port: [0x30e4-0x30e7]
[    0.202932] pci 0000:00:09.0: reg 18 io port: [0x30e8-0x30ef]
[    0.202936] pci 0000:00:09.0: reg 1c io port: [0x30e0-0x30e3]
[    0.202941] pci 0000:00:09.0: reg 20 io port: [0x30d0-0x30df]
[    0.202945] pci 0000:00:09.0: reg 24 32bit mmio: [0xf4484000-0xf4485fff]
[    0.202998] pci 0000:00:0a.0: reg 10 32bit mmio: [0xf4488000-0xf4488fff]
[    0.203003] pci 0000:00:0a.0: reg 14 io port: [0x30f8-0x30ff]
[    0.203007] pci 0000:00:0a.0: reg 18 32bit mmio: [0xf4489c00-0xf4489cff]
[    0.203012] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xf4489800-0xf448980f]
[    0.203037] pci 0000:00:0a.0: supports D1 D2
[    0.203039] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203044] pci 0000:00:0a.0: PME# disabled
[    0.203088] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203091] pci 0000:00:0c.0: PME# disabled
[    0.203133] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203136] pci 0000:00:0e.0: PME# disabled
[    0.203159] pci 0000:00:12.0: reg 10 32bit mmio: [0xf3000000-0xf3ffffff]
[    0.203165] pci 0000:00:12.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.203172] pci 0000:00:12.0: reg 1c 64bit mmio: [0xf2000000-0xf2ffffff]
[    0.203178] pci 0000:00:12.0: reg 30 32bit mmio pref: [0x000000-0x01ffff]
[    0.203303] pci 0000:01:09.0: reg 10 32bit mmio: [0xf4100000-0xf41007ff]
[    0.203337] pci 0000:01:09.0: supports D1 D2
[    0.203340] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203344] pci 0000:01:09.0: PME# disabled
[    0.203370] pci 0000:01:09.1: reg 10 32bit mmio: [0xf4100800-0xf41008ff]
[    0.203404] pci 0000:01:09.1: supports D1 D2
[    0.203406] pci 0000:01:09.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203410] pci 0000:01:09.1: PME# disabled
[    0.203437] pci 0000:01:09.2: reg 10 32bit mmio: [0xf4100c00-0xf4100cff]
[    0.203470] pci 0000:01:09.2: supports D1 D2
[    0.203473] pci 0000:01:09.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203477] pci 0000:01:09.2: PME# disabled
[    0.203503] pci 0000:01:09.3: reg 10 32bit mmio: [0xf4101000-0xf41010ff]
[    0.203537] pci 0000:01:09.3: supports D1 D2
[    0.203539] pci 0000:01:09.3: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203543] pci 0000:01:09.3: PME# disabled
[    0.203570] pci 0000:01:09.4: reg 10 32bit mmio: [0xf4101400-0xf41014ff]
[    0.203603] pci 0000:01:09.4: supports D1 D2
[    0.203606] pci 0000:01:09.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.203610] pci 0000:01:09.4: PME# disabled
[    0.203639] pci 0000:00:08.0: transparent bridge
[    0.203644] pci 0000:00:08.0: bridge 32bit mmio: [0xf4100000-0xf41fffff]
[    0.203683] pci 0000:00:0c.0: bridge io port: [0x00-0xfff]
[    0.203686] pci 0000:00:0c.0: bridge 32bit mmio: [0x000000-0x0fffff]
[    0.203691] pci 0000:00:0c.0: bridge 64bit mmio pref: [0x000000-0x0fffff]
[    0.203728] pci 0000:07:00.0: reg 10 64bit mmio: [0xf4000000-0xf400ffff]
[    0.203818] pci 0000:00:0e.0: bridge 32bit mmio: [0xf4000000-0xf40fffff]
[    0.203828] pci_bus 0000:00: on NUMA node 0
[    0.203832] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.203924] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    0.203946] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR1._PRT]
[    0.203982] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.XVR3._PRT]
[    0.232891] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 *10 11 14 15)
[    0.233079] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 *11 14 15)
[    0.233267] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.233455] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
[    0.233640] ACPI: PCI Interrupt Link [LK1E] (IRQs 16 17 18 19 20) *0, disabled.
[    0.233827] ACPI: PCI Interrupt Link [LK2E] (IRQs 16 17 18 19 20) *0, disabled.
[    0.234011] ACPI: PCI Interrupt Link [LK3E] (IRQs 16 17 18 19 20) *10
[    0.234196] ACPI: PCI Interrupt Link [LK4E] (IRQs 16 17 18 19 20) *0, disabled.
[    0.234380] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20) *10
[    0.234566] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20) *11
[    0.234751] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20) *10
[    0.234935] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20) *11
[    0.235119] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20) *10
[    0.235307] ACPI: PCI Interrupt Link [LGPU] (IRQs 21 22 23) *10
[    0.235492] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20) *0, disabled.
[    0.235680] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20) *5
[    0.235865] ACPI: PCI Interrupt Link [Z002] (IRQs 16 17 18 19 20) *7
[    0.236073] ACPI: PCI Interrupt Link [Z003] (IRQs 16 17 18 19 20) *11
[    0.236261] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20) *11
[    0.236398] vgaarb: device added: PCI:0000:00:12.0,decodes=io+mem,owns=io+mem,locks=none
[    0.236409] vgaarb: loaded
[    0.236548] SCSI subsystem initialized
[    0.236666] libata version 3.00 loaded.
[    0.236747] usbcore: registered new interface driver usbfs
[    0.236761] usbcore: registered new interface driver hub
[    0.236792] usbcore: registered new device driver usb
[    0.237033] ACPI: WMI: Mapper loaded
[    0.237036] PCI: Using ACPI for IRQ routing
[    0.237043] pci 0000:00:0c.0: BAR 13: can't allocate resource
[    0.237047] pci 0000:00:0c.0: BAR 14: can't allocate resource
[    0.237050] pci 0000:00:0c.0: BAR 15: can't allocate resource
[    0.237251] NetLabel: Initializing
[    0.237253] NetLabel:  domain hash size = 128
[    0.237255] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.237271] NetLabel:  unlabeled traffic allowed by default
[    0.237319] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.237326] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.244006] Switching to clocksource hpet
[    0.246031] AppArmor: AppArmor Filesystem Enabled
[    0.246056] pnp: PnP ACPI init
[    0.246077] ACPI: bus type pnp registered
[    0.249147] pnp: PnP ACPI: found 13 devices
[    0.249149] ACPI: ACPI bus type pnp unregistered
[    0.249153] PnPBIOS: Disabled by ACPI PNP
[    0.249167] system 00:02: iomem range 0xe0000000-0xefffffff has been reserved
[    0.249175] system 00:03: ioport range 0x1000-0x107f has been reserved
[    0.249178] system 00:03: ioport range 0x1080-0x10ff has been reserved
[    0.249182] system 00:03: ioport range 0x1400-0x147f has been reserved
[    0.249185] system 00:03: ioport range 0x1480-0x14ff has been reserved
[    0.249188] system 00:03: ioport range 0x1800-0x187f has been reserved
[    0.249192] system 00:03: ioport range 0x1880-0x18ff has been reserved
[    0.249195] system 00:03: ioport range 0x3040-0x307f has been reserved
[    0.249199] system 00:03: ioport range 0x3000-0x303f has been reserved
[    0.249205] system 00:04: ioport range 0x360-0x361 has been reserved
[    0.249209] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.249213] system 00:04: ioport range 0xfe00-0xfe00 has been reserved
[    0.249222] system 00:0b: iomem range 0xffc00000-0xffffffff could not be reserved
[    0.249226] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.249230] system 00:0b: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.249234] system 00:0b: iomem range 0xfed00000-0xfed00fff has been reserved
[    0.249237] system 00:0b: iomem range 0xfec80000-0xfec80fff has been reserved
[    0.249241] system 00:0b: iomem range 0xfef00000-0xfef00fff has been reserved
[    0.283984] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.283986] pci 0000:00:08.0:   IO window: disabled
[    0.283991] pci 0000:00:08.0:   MEM window: 0xf4100000-0xf41fffff
[    0.284007] pci 0000:00:08.0:   PREFETCH window: disabled
[    0.284012] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.284014] pci 0000:00:0c.0:   IO window: disabled
[    0.284018] pci 0000:00:0c.0:   MEM window: disabled
[    0.284020] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.284024] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:07
[    0.284027] pci 0000:00:0e.0:   IO window: disabled
[    0.284030] pci 0000:00:0e.0:   MEM window: 0xf4000000-0xf40fffff
[    0.284033] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.284043] pci 0000:00:08.0: setting latency timer to 64
[    0.284049] pci 0000:00:0c.0: setting latency timer to 64
[    0.284055] pci 0000:00:0e.0: setting latency timer to 64
[    0.284060] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.284063] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.284066] pci_bus 0000:01: resource 1 mem: [0xf4100000-0xf41fffff]
[    0.284069] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.284072] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.284075] pci_bus 0000:03: resource 0 mem: [0x0-0xfff]
[    0.284078] pci_bus 0000:03: resource 1 mem: [0x0-0xfffff]
[    0.284081] pci_bus 0000:03: resource 2 mem: [0x0-0xfffff]
[    0.284084] pci_bus 0000:07: resource 1 mem: [0xf4000000-0xf40fffff]
[    0.284129] NET: Registered protocol family 2
[    0.284236] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.284611] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.285575] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.286033] TCP: Hash tables configured (established 131072 bind 65536)
[    0.286037] TCP reno registered
[    0.286148] NET: Registered protocol family 1
[    0.286320] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286375] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286435] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286502] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286572] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286648] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.286656] pci 0000:00:12.0: Boot video device
[    0.286708] Simple Boot Flag at 0x36 set to 0x1
[    0.286910] cpufreq-nforce2: No nForce2 chipset.
[    0.286940] Scanning for low memory corruption every 60 seconds
[    0.287089] audit: initializing netlink socket (disabled)
[    0.287101] type=2000 audit(1274566004.285:1): initialized
[    0.297869] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.299473] VFS: Disk quotas dquot_6.5.2
[    0.299542] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.300202] fuse init (API version 7.13)
[    0.300295] msgmni has been set to 1480
[    0.300561] alg: No test for stdrng (krng)
[    0.300630] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.300634] io scheduler noop registered
[    0.300637] io scheduler anticipatory registered
[    0.300639] io scheduler deadline registered
[    0.300683] io scheduler cfq registered (default)
[    0.300847]   alloc irq_desc for 24 on node -1
[    0.300850]   alloc kstat_irqs on node -1
[    0.300863] pcieport 0000:00:0c.0: irq 24 for MSI/MSI-X
[    0.300871] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.300958]   alloc irq_desc for 25 on node -1
[    0.300961]   alloc kstat_irqs on node -1
[    0.300966] pcieport 0000:00:0e.0: irq 25 for MSI/MSI-X
[    0.300972] pcieport 0000:00:0e.0: setting latency timer to 64
[    0.301035] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.301065] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.301482] ACPI: AC Adapter [ACAD] (on-line)
[    0.301555] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.301561] ACPI: Power Button [PWRB]
[    0.301630] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.301867] ACPI: Lid Switch [LID]
[    0.301919] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.301923] ACPI: Sleep Button [SLPB]
[    0.301970] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.301973] ACPI: Power Button [PWRF]
[    0.302261] ACPI: processor limited to max C-state 1
[    0.302291] processor LNXCPU:00: registered as cooling_device0
[    0.302327] processor LNXCPU:01: registered as cooling_device1
[    0.305166] thermal LNXTHERM:01: registered as thermal_zone0
[    0.305175] ACPI: Thermal Zone [THRM] (37 C)
[    0.306990] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.308385] brd: module loaded
[    0.308886] loop: module loaded
[    0.308997] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.309244] pata_acpi 0000:00:06.0: setting latency timer to 64
[    0.309630] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 20
[    0.309636]   alloc irq_desc for 20 on node -1
[    0.309639]   alloc kstat_irqs on node -1
[    0.309651] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    0.309681] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.309689] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.310021] Fixed MDIO Bus: probed
[    0.310057] PPP generic driver version 2.4.2
[    0.310118] tun: Universal TUN/TAP device driver, 1.6
[    0.310120] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.310218] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.310578] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 19
[    0.310582]   alloc irq_desc for 19 on node -1
[    0.310584]   alloc kstat_irqs on node -1
[    0.310593] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 19 (level, low) -> IRQ 19
[    0.310614] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.310617] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.310672] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.310699] ehci_hcd 0000:00:02.1: debug port 1
[    0.310707] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.310730] ehci_hcd 0000:00:02.1: irq 19, io mem 0xf4489000
[    0.310861] ACPI: Battery Slot [BAT1] (battery absent)
[    0.310874] isapnp: Scanning for PnP cards...
[    0.359752] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.359868] usb usb1: configuration #1 chosen from 1 choice
[    0.359901] hub 1-0:1.0: USB hub found
[    0.359912] hub 1-0:1.0: 4 ports detected
[    0.360336] ACPI: PCI Interrupt Link [Z003] enabled at IRQ 18
[    0.360340]   alloc irq_desc for 18 on node -1
[    0.360343]   alloc kstat_irqs on node -1
[    0.360353] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z003] -> GSI 18 (level, low) -> IRQ 18
[    0.360371] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.360374] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.360419] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.360448] ehci_hcd 0000:00:04.1: debug port 1
[    0.360456] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.360478] ehci_hcd 0000:00:04.1: irq 18, io mem 0xf4489400
[    0.400172] Freeing initrd memory: 7771k freed
[    0.403901] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.404032] usb usb2: configuration #1 chosen from 1 choice
[    0.404067] hub 2-0:1.0: USB hub found
[    0.404078] hub 2-0:1.0: 4 ports detected
[    0.404160] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.404613] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 17
[    0.404619]   alloc irq_desc for 17 on node -1
[    0.404622]   alloc kstat_irqs on node -1
[    0.404632] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 17 (level, low) -> IRQ 17
[    0.404654] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.404657] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.404722] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.404758] ohci_hcd 0000:00:02.0: irq 17, io mem 0xf4486000
[    0.493679] usb usb3: configuration #1 chosen from 1 choice
[    0.493709] hub 3-0:1.0: USB hub found
[    0.493720] hub 3-0:1.0: 4 ports detected
[    0.494106] ACPI: PCI Interrupt Link [Z002] enabled at IRQ 16
[    0.494110]   alloc irq_desc for 16 on node -1
[    0.494112]   alloc kstat_irqs on node -1
[    0.494120] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z002] -> GSI 16 (level, low) -> IRQ 16
[    0.494134] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.494137] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.494182] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.494210] ohci_hcd 0000:00:04.0: irq 16, io mem 0xf4487000
[    0.554093] usb usb4: configuration #1 chosen from 1 choice
[    0.554127] hub 4-0:1.0: USB hub found
[    0.554138] hub 4-0:1.0: 4 ports detected
[    0.554195] uhci_hcd: USB Universal Host Controller Interface driver
[    0.554297] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.558250] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.559528] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.559538] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.559569] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.559597] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.559620] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.559752] mice: PS/2 mouse device common for all mice
[    0.559922] rtc_cmos 00:07: RTC can wake from S4
[    0.559966] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.560020] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.560137] device-mapper: uevent: version 1.0.3
[    0.560274] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.560355] device-mapper: multipath: version 1.1.0 loaded
[    0.560358] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.560492] EISA: Probing bus 0 at eisa.0
[    0.560498] Cannot allocate resource for EISA slot 1
[    0.560504] Cannot allocate resource for EISA slot 3
[    0.560521] EISA: Detected 0 cards.
[    0.560603] cpuidle: using governor ladder
[    0.560606] cpuidle: using governor menu
[    0.561084] TCP cubic registered
[    0.561261] NET: Registered protocol family 10
[    0.561766] lo: Disabled Privacy Extensions
[    0.562116] NET: Registered protocol family 17
[    0.562158] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-57 processors (2 cpu cores) (version 2.20.00)
[    0.562207] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x13
[    0.562210] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x14
[    0.562214] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x15
[    0.562217] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1a
[    0.562265] Using IPI No-Shortcut mode
[    0.562369] PM: Resume from disk failed.
[    0.562384] registered taskstats version 1
[    0.562755]   Magic number: 10:47:149
[    0.562778] bdi 1:1: hash matches
[    0.562889] rtc_cmos 00:07: setting system clock to 2010-05-22 22:06:45 UTC (1274566005)
[    0.562894] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.562897] EDD information not available.
[    0.588247] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.666732] isapnp: No Plug & Play device found
[    0.666758] Freeing unused kernel memory: 656k freed
[    0.667339] Write protecting the kernel text: 4676k
[    0.667381] Write protecting the kernel read-only data: 1840k
[    0.688673] udev: starting version 151
[    0.799729] ahci 0000:00:09.0: version 3.0
[    0.799750] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 20 (level, low) -> IRQ 20
[    0.799798]   alloc irq_desc for 26 on node -1
[    0.799801]   alloc kstat_irqs on node -1
[    0.799811] ahci 0000:00:09.0: irq 26 for MSI/MSI-X
[    0.799818] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    0.799892] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    0.799896] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio slum part 
[    0.799901] ahci 0000:00:09.0: setting latency timer to 64
[    0.824513] scsi0 : ahci
[    0.844349] scsi1 : ahci
[    0.850690] scsi2 : ahci
[    0.852808] scsi3 : ahci
[    0.852986] ata1: SATA max UDMA/133 abar m8192@0xf4484000 port 0xf4484100 irq 26
[    0.852991] ata2: SATA max UDMA/133 abar m8192@0xf4484000 port 0xf4484180 irq 26
[    0.852995] ata3: SATA max UDMA/133 abar m8192@0xf4484000 port 0xf4484200 irq 26
[    0.852999] ata4: SATA max UDMA/133 abar m8192@0xf4484000 port 0xf4484280 irq 26
[    0.853294] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    0.853677] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    0.853683] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    0.853689] forcedeth 0000:00:0a.0: setting latency timer to 64
[    0.984035] usb 3-3: new low speed USB device using ohci_hcd and address 2
[    1.172041] ata2: SATA link down (SStatus 0 SControl 300)
[    1.172052] ata3: SATA link down (SStatus 0 SControl 300)
[    1.172072] ata4: SATA link down (SStatus 0 SControl 300)
[    1.195748] usb 3-3: configuration #1 chosen from 1 choice
[    1.308036] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.336037] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.373309] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:0a:c6:6a
[    1.373314] forcedeth 0000:00:0a.0: highdma pwrctl mgmt gbit lnktim msi desc-v3
[    1.373366] pata_amd 0000:00:06.0: version 0.4.1
[    1.373416] pata_amd 0000:00:06.0: setting latency timer to 64
[    1.373533] scsi4 : pata_amd
[    1.373622] scsi5 : pata_amd
[    1.374103] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x30c0 irq 14
[    1.374107] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x30c8 irq 15
[    1.384815] ata1.00: ATA-7: WDC WD1600BEVS-22RST0, 04.01G04, max UDMA/133
[    1.384820] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.385650] ata1.00: configured for UDMA/133
[    1.385790] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-2 04.0 PQ: 0 ANSI: 5
[    1.386032] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.386087] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.386189] sd 0:0:0:0: [sda] Write Protect is off
[    1.386193] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.386220] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.386404]  sda: sda1 sda3 < sda5 sda6 >
[    1.412394] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.449732] usb 2-2: configuration #1 chosen from 1 choice
[    1.536319] ata5.00: ATAPI: Optiarc DVD RW AD-7530B, NX09, max UDMA/33
[    1.536350] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c700) ACPI=0x701f (60:600:0x13)
[    1.552262] ata5.00: configured for UDMA/33
[    1.554150] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7530B  NX09 PQ: 0 ANSI: 5
[    1.563982] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.563987] Uniform CD-ROM driver Revision: 3.20
[    1.564146] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.564225] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.564333] ata6: port disabled. ignoring.
[    1.569554] usbcore: registered new interface driver hiddev
[    1.574584] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 10
[    1.574602] ohci1394 0000:01:09.0: PCI INT A -> Link[LNK1] -> GSI 10 (level, low) -> IRQ 10
[    1.578061] input: USB Optical Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.0/input/input6
[    1.578228] generic-usb 0003:1BCF:0007.0001: input,hiddev96,hidraw0: USB HID v1.10 Mouse [USB Optical Mouse] on usb-0000:00:02.0-3/input0
[    1.578262] usbcore: registered new interface driver usbhid
[    1.578266] usbhid: v2.6:USB HID core driver
[    1.630052] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[f4100000-f41007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.920659] EXT4-fs (sda6): mounted filesystem with ordered data mode
[    2.904342] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00241b004a51ad00]
[   17.964705] Adding 1445840k swap on /dev/sda5.  Priority:-1 extents:1 across:1445840k 
[   17.983864] udev: starting version 151
[   18.059280] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[   18.059305] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[   18.074304] vga16fb: initializing
[   18.074310] vga16fb: mapped to 0xc00a0000
[   18.074393] fb0: VGA16 VGA frame buffer device
[   18.096905] lp: driver loaded but no devices found
[   18.224269] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   18.242589] Linux agpgart interface v0.103
[   18.245735] acpi device:08: registered as cooling_device2
[   18.246005] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input7
[   18.246066] ACPI: Video Device [IGPU] (multi-head: yes  rom: no  post: no)
[   18.305076] sdhci: Secure Digital Host Controller Interface driver
[   18.305079] sdhci: Copyright(c) Pierre Ossman
[   18.306728] sdhci-pci 0000:01:09.1: SDHCI controller found [1180:0822] (rev 22)
[   18.307077] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 11
[   18.307092] sdhci-pci 0000:01:09.1: PCI INT B -> Link[LNK2] -> GSI 11 (level, low) -> IRQ 11
[   18.307125] sdhci-pci 0000:01:09.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   18.307178] Registered led device: mmc0::
[   18.307226] mmc0: SDHCI controller on PCI [0000:01:09.1] using DMA
[   18.307616] ricoh-mmc: Ricoh MMC Controller disabling driver
[   18.307618] ricoh-mmc: Copyright(c) Philip Langdale
[   18.313198] ricoh-mmc: Ricoh MMC controller found at 0000:01:09.2 [1180:0843] (rev 12)
[   18.313223] ricoh-mmc: Controller is now disabled.
[   18.315596] cfg80211: Calling CRDA to update world regulatory domain
[   18.323563] Linux video capture interface: v2.00
[   18.328150] uvcvideo: Found UVC 1.00 device Acer CrystalEye webcam (064e:a101)
[   18.347805] input: Acer CrystalEye webcam as /devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input8
[   18.347912] usbcore: registered new interface driver uvcvideo
[   18.348162] USB Video Class driver (v0.1.0)
[   18.390300] cfg80211: World regulatory domain updated:
[   18.390305] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.390309] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.390312] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.390316] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.390318] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.390321] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.424117] nvidia: module license 'NVIDIA' taints kernel.
[   18.424122] Disabling lock debugging due to kernel taint
[   18.425235] type=1505 audit(1274580423.362:2):  operation="profile_load" pid=631 name="/sbin/dhclient3"
[   18.425539] type=1505 audit(1274580423.362:3):  operation="profile_load" pid=631 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   18.425710] type=1505 audit(1274580423.362:4):  operation="profile_load" pid=631 name="/usr/lib/connman/scripts/dhclient-script"
[   19.038163] Synaptics Touchpad, model: 1, fw: 6.5, id: 0x81a0b1, caps: 0xa04711/0xa04000
[   19.076681] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input9
[   19.136177]   alloc irq_desc for 27 on node -1
[   19.136181]   alloc kstat_irqs on node -1
[   19.136193] forcedeth 0000:00:0a.0: irq 27 for MSI/MSI-X
[   19.136397] eth0: no link during initialization.
[   19.137149] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.785938] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 19
[   19.785945] ath5k 0000:07:00.0: PCI INT A -> Link[LK3E] -> GSI 19 (level, low) -> IRQ 19
[   19.785955] ath5k 0000:07:00.0: setting latency timer to 64
[   19.786003] ath5k 0000:07:00.0: registered as 'phy0'
[   19.857774] acer-wmi: Acer Laptop ACPI-WMI Extras
[   19.858097] acer-wmi: Brightness must be controlled by generic video driver
[   19.879689] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 23
[   19.879697]   alloc irq_desc for 23 on node -1
[   19.879699]   alloc kstat_irqs on node -1
[   19.879711] nvidia 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 23 (level, low) -> IRQ 23
[   19.879719] nvidia 0000:00:12.0: setting latency timer to 64
[   19.879724] vgaarb: device changed decodes: PCI:0000:00:12.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.881026] NVRM: loading NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11 21:41:46 PST 2010
[   19.946711] Console: switching to colour frame buffer device 80x30
[   20.127400] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 18
[   20.127408] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 18 (level, low) -> IRQ 18
[   20.127413] hda_intel: Disable MSI for Nvidia chipset
[   20.127453] HDA Intel 0000:00:07.0: setting latency timer to 64
[   20.281791] ath: EEPROM regdomain: 0x65
[   20.281795] ath: EEPROM indicates we should expect a direct regpair map
[   20.281801] ath: Country alpha2 being used: 00
[   20.281803] ath: Regpair used: 0x65
[   20.290039] phy0: Selected rate control algorithm 'minstrel'
[   20.290932] Registered led device: ath5k-phy0::rx
[   20.291000] Registered led device: ath5k-phy0::tx
[   20.291005] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   20.374975] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.064728] hda_codec: ALC268: BIOS auto-probing.
[   23.168137] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input10
[   48.976340] wlan0: direct probe to AP 00:21:91:4a:83:6a (try 1)
[   48.976365] wlan0: deauthenticating from 00:21:91:4a:83:6a by local choice (reason=3)
[   48.976424] wlan0: direct probe to AP 00:21:91:4a:83:6a (try 1)
[   48.978879] wlan0: direct probe responded
[   48.978886] wlan0: authenticate with AP 00:21:91:4a:83:6a (try 1)
[   48.983240] wlan0: authenticated
[   48.983271] wlan0: associate with AP 00:21:91:4a:83:6a (try 1)
[   48.987208] wlan0: RX AssocResp from 00:21:91:4a:83:6a (capab=0x411 status=0 aid=4)
[   48.987213] wlan0: associated
[   48.987959] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   59.189029] wlan0: no IPv6 routers present

```

Supongo que es un bug. También en el foro general de ubuntu forums hay personas con este problema pero no hay ninguna solución. Bueno, tampoco pescaron mucho el tema xD.

Edit: Por cierto, para no apagar a la mala, es mejor irse a la terminal y poner:
```
sudo shutdown -h now
```

Además el bug esta reportado en [https://bugs.launchpad.net/ubuntu/+bug/576235]("https://bugs.launchpad.net/ubuntu/+bug/576235"). A los que le afecta este problema por favor que se logueen en el launchpad y pongan que les afecta el problema.

---

