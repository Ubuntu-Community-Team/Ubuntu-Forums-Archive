---
title: "detecting multiple CPUs"
date: 2007-05-18
forum: Server Platforms
---

### Post by tr333 on 2007-05-18
I have a server machine that contains two P3 CPUs.  How can I find out if ubuntu has detected and is using both CPUs?

---

### Post by fyl2u on 2007-05-18
I just read a thread in one of the other Ubuntu Forum's rooms about this...

[http://ubuntuforums.org/showthread.php?t=447288](http://ubuntuforums.org/showthread.php?t=447288)

---

### Post by tr333 on 2007-05-18
it seems as though its not detecting the other CPU.  How can i get ubuntu to detect and use the other CPU?

---

### Post by craigp84 on 2007-05-18
Hi tr333,

Do a:

```
cat /proc/cpuinfo
```

And:

```
uname -a
```

Then paste the results of both here.

Thanks,

Craig

---

### Post by tr333 on 2007-05-18
```
tom@wirelessduck:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 845.652
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1692.59
clflush size    : 32
```

```
tom@wirelessduck:~$ uname -a
Linux wirelessduck 2.6.20-15-server #2 SMP Sun Apr 15 07:41:34 UTC 2007 i686 GNU/Linux
```

---

### Post by tr333 on 2007-05-18
edit: duplicate post

---

### Post by craigp84 on 2007-05-18
Hmmm...

If you've physically verified the CPUs are there, and you see them listed by the BIOS at POST time, then post your "dmesg" output.

Failing that, you're looking at this really being a 1 CPU box, not a 2 CPU as previously though, or the second CPU being dead, unseated, or otherwise unusable.

It's extraordinarily rare for a CPU to fail under normal operating conditions. Try reseating the CPU, and look for signs of a thermal-induced death.

Hope this helps,

-c

---

### Post by tr333 on 2007-05-18
```
tom@wirelessduck:~$ dmesg
[    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f400 end: 000000000009f400 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f400 size: 0000000000000c00 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000018000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000fc00 end: 000000003ffffc00 type: 3
[    0.000000] copy_e820_map() start: 000000003ffffc00 size: 0000000000000400 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003ffffc00 (ACPI data)
[    0.000000]  BIOS-e820: 000000003ffffc00 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6ab0
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.1 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6ac0
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040001  LTP 0x00000000) @ 0x3fffd7f1
[    0.000000] ACPI: FADT (v001 Intel  L440GX   0x06040001 INT  0x000f4242) @ 0x3ffffb32
[    0.000000] ACPI: MADT (v001 Intel  N440BX   0x06040001  TNI 0x00000000) @ 0x3ffffba6
[    0.000000] ACPI: DSDT (v001  Intel  L440GX0 0x06040001 MSFT 0x0100000b) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0xc08
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:8 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Detected 845.652 MHz processor.
[   51.411128] Built 1 zonelists.  Total pages: 260081
[   51.411137] Kernel command line: root=UUID=60a045f0-1373-442d-9ce1-8270dcc9dafb ro quiet splash
[   51.411616] mapped APIC to ffffd000 (fee00000)
[   51.411624] mapped IOAPIC to ffffc000 (fec00000)
[   51.411633] Enabling fast FPU save and restore... done.
[   51.411639] Enabling unmasked SIMD FPU exception support... done.
[   51.411663] Initializing CPU#0
[   51.411769] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   51.413839] Console: colour VGA+ 80x25
[   51.416368] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   51.420148] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   51.527769] Memory: 1028408k/1048512k available (2020k kernel code, 19332k reserved, 893k data, 328k init, 131008k highmem)
[   51.527800] virtual kernel memory layout:
[   51.527804]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
[   51.527807]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   51.527811]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
[   51.527815]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   51.527818]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
[   51.527822]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
[   51.527825]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
[   51.527834] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   51.671582] Calibrating delay using timer specific routine.. 1692.59 BogoMIPS (lpj=8462999)
[   51.671711] Security Framework v1.0.0 initialized
[   51.671744] SELinux:  Disabled at boot.
[   51.671791] Mount-cache hash table entries: 512
[   51.672205] CPU: After generic identify, caps: 0387fbff 00000000 00000000 00000000 00000000 00000000 00000000
[   51.672240] CPU: L1 I cache: 16K, L1 D cache: 16K
[   51.672247] CPU: L2 cache: 256K
[   51.672254] CPU serial number disabled.
[   51.672261] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
[   51.672291] Compat vDSO mapped to ffffe000.
[   51.672311] Remapping vsyscall page to ffffe000
[   51.672338] Checking 'hlt' instruction... OK.
[   51.711780] SMP alternatives: switching to UP code
[   51.712196] Freeing SMP alternatives: 11k freed
[   51.712659] Early unpacking initramfs... done
[   52.405580] ACPI: Core revision 20060707
[   52.409849] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   52.412598] CPU0: Intel Pentium III (Coppermine) stepping 03
[   52.412658] Total of 1 processors activated (1692.59 BogoMIPS).
[   52.413688] ENABLING IO-APIC IRQs
[   52.414057] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   52.630972] Brought up 1 CPUs
[   52.631609] Booting paravirtualized kernel on bare hardware
[   52.631759] Time:  7:37:18  Date: 04/15/107
[   52.631835] NET: Registered protocol family 16
[   52.632073] EISA bus registered
[   52.632085] ACPI: bus type pci registered
[   52.648778] PCI: PCI BIOS revision 2.10 entry at 0xfdab0, last bus=2
[   52.648785] PCI: Using configuration type 1
[   52.648790] Setting up standard PCI resources
[   52.656800] ACPI: Interpreter enabled
[   52.656809] ACPI: Using IOAPIC for interrupt routing
[   52.657838] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   52.657857] PCI: Probing PCI hardware (bus 00)
[   52.658040] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   52.659177] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[   52.659181] * this clock source is slow. Consider trying other clock sources
[   52.659241] PCI quirk: region 0c00-0c3f claimed by PIIX4 ACPI
[   52.659250] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[   52.659260] PIIX4 devres B PIO at 0cb8-0cbf
[   52.659267] PIIX4 devres C PIO at 0ca0-0ca3
[   52.659333] Boot video device is 0000:00:14.0
[   52.659581] PCI: Firmware left 0000:02:04.0 e100 interrupts enabled, disabling
[   52.659707] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   52.666456] ACPI: PCI Interrupt Link [PRQ0] (IRQs 3 4 5 7 10 11 12 15) *0, disabled.
[   52.667201] ACPI: PCI Interrupt Link [PRQ1] (IRQs 3 4 5 7 10 11 12 15) *0, disabled.
[   52.667960] ACPI: PCI Interrupt Link [PRQ2] (IRQs 3 4 5 7 10 *11 12 15)
[   52.668725] ACPI: PCI Interrupt Link [PRQ3] (IRQs 3 4 5 7 10 *11 12 15), disabled.
[   52.669476] ACPI: PCI Interrupt Link [PRQ4] (IRQs 3 4 *5 7 10 11 12 15)
[   52.670221] ACPI: PCI Interrupt Link [PRQ5] (IRQs 3 4 5 7 *10 11 12 15), disabled.
[   52.671044] ACPI: PCI Interrupt Link [PRQ6] (IRQs 3 4 5 7 10 11 12 15) *0, disabled.
[   52.671782] ACPI: PCI Interrupt Link [PRQ7] (IRQs 3 4 5 7 10 11 12 15) *0, disabled.
[   52.672234] Linux Plug and Play Support v0.97 (c) Adam Belay
[   52.672280] pnp: PnP ACPI init
[   52.677806] pnp: PnP ACPI: found 12 devices
[   52.677819] PnPBIOS: Disabled by ACPI PNP
[   52.677964] PCI: Using ACPI for IRQ routing
[   52.677973] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   52.681547] NET: Registered protocol family 8
[   52.681553] NET: Registered protocol family 20
[   52.681574] NetLabel: Initializing
[   52.681579] NetLabel:  domain hash size = 128
[   52.681584] NetLabel:  protocols = UNLABELED CIPSOv4
[   52.681618] NetLabel:  unlabeled traffic allowed by default
[   52.681994] pnp: 00:01: ioport range 0xc00-0xc3f could not be reserved
[   52.682002] pnp: 00:01: ioport range 0xca0-0xca7 has been reserved
[   52.682010] pnp: 00:01: ioport range 0xcb0-0xcbf has been reserved
[   52.682017] pnp: 00:01: ioport range 0xcc0-0xccf has been reserved
[   52.682025] pnp: 00:01: ioport range 0x1040-0x104f has been reserved
[   52.682829] PCI: Bridge: 0000:01:0f.0
[   52.682836]   IO window: 3000-3fff
[   52.682846]   MEM window: f4100000-f42fffff
[   52.682854]   PREFETCH window: 50000000-500fffff
[   52.682862] PCI: Bridge: 0000:00:01.0
[   52.682868]   IO window: 3000-3fff
[   52.682875]   MEM window: f4100000-f42fffff
[   52.682883]   PREFETCH window: 50000000-500fffff
[   52.682968] NET: Registered protocol family 2
[   52.750972] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   52.751487] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   52.756648] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   52.759455] TCP: Hash tables configured (established 131072 bind 65536)
[   52.759466] TCP reno registered
[   52.781141] checking if image is initramfs... it is
[   54.105585] Freeing initrd memory: 6611k freed
[   54.106643] audit: initializing netlink socket (disabled)
[   54.106676] audit(1179214640.540:1): initialized
[   54.106824] highmem bounce pool size: 64 pages
[   54.107015] VFS: Disk quotas dquot_6.5.1
[   54.107073] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   54.107203] io scheduler noop registered
[   54.107212] io scheduler anticipatory registered
[   54.107217] io scheduler deadline registered (default)
[   54.107246] io scheduler cfq registered
[   54.107829] isapnp: Scanning for PnP cards...
[   54.464911] isapnp: No Plug & Play device found
[   54.551347] Real Time Clock Driver v1.12ac
[   54.551475] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   54.551687] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.552109] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.553649] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   54.554238] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   54.554767] mice: PS/2 mouse device common for all mice
[   54.556210] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   54.556817] input: Macintosh mouse button emulation as /class/input/input0
[   54.556904] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   54.556915] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   54.557363] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[   54.561688] serio: i8042 KBD port at 0x60,0x64 irq 1
[   54.561707] serio: i8042 AUX port at 0x60,0x64 irq 12
[   54.562057] EISA: Probing bus 0 at eisa.0
[   54.562076] Cannot allocate resource for EISA slot 1
[   54.562083] Cannot allocate resource for EISA slot 2
[   54.562090] Cannot allocate resource for EISA slot 3
[   54.562134] EISA: Detected 0 cards.
[   54.592322] TCP cubic registered
[   54.592342] NET: Registered protocol family 1
[   54.592396] Using IPI No-Shortcut mode
[   54.592543] ACPI: (supports S0 S1 S4 S5)
[   54.592638]   Magic number: 7:441:622
[   54.592734]   hash matches device ptybf
[   54.593880] Freeing unused kernel memory: 328k freed
[   54.599402] Time: tsc clocksource has been installed.
[   54.607614] input: AT Translated Set 2 keyboard as /class/input/input1
[   55.015820] Capability LSM initialized
[   55.122219] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   56.508210] SCSI subsystem initialized
[   56.521820] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 16
[   56.658719] usbcore: registered new interface driver usbfs
[   56.658774] usbcore: registered new interface driver hub
[   56.658832] usbcore: registered new device driver usb
[   56.662780] USB Universal Host Controller Interface driver v3.0
[   56.941836] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   56.941846] e100: Copyright(c) 1999-2006 Intel Corporation
[   56.945825] Floppy drive(s): fd0 is 1.44M
[   56.995160] FDC 0 is a National Semiconductor PC87306
[   71.535539] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   71.535546]         <Adaptec 2902/04/10/15/20C/30C SCSI adapter>
[   71.535550]         aic7850: Single Channel A, SCSI Id=7, 3/253 SCBs
[   71.535554] 
[   71.536411] ACPI: PCI Interrupt 0000:00:0c.0[A] -> GSI 19 (level, low) -> IRQ 17
[   71.748948] scsi 0:0:0:0: Sequential-Access SONY     SDT-9000         0601 PQ: 0 ANSI: 2
[   71.748993]  target0:0:0: Beginning Domain Validation
[   71.756138]  target0:0:0: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 15)
[   71.763823]  target0:0:0: Domain Validation skipping write tests
[   71.763830]  target0:0:0: Ending Domain Validation
[   86.753167] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   86.753173]         <Adaptec aic7896/97 Ultra2 SCSI adapter>
[   86.753177]         aic7896/97: Ultra2 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   86.753181] 
[   86.754067] ACPI: PCI Interrupt 0000:00:0c.1[A] -> GSI 19 (level, low) -> IRQ 17
[  101.960801] scsi2 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[  101.960807]         <Adaptec aic7896/97 Ultra2 SCSI adapter>
[  101.960811]         aic7896/97: Ultra2 Wide Channel B, SCSI Id=7, 32/253 SCBs
[  101.960816] 
[  101.965227] ACPI: PCI Interrupt 0000:00:12.2[D] -> GSI 21 (level, low) -> IRQ 18
[  101.965258] uhci_hcd 0000:00:12.2: UHCI Host Controller
[  101.965520] uhci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[  101.965576] uhci_hcd 0000:00:12.2: irq 18, io base 0x00002c00
[  101.965851] usb usb1: configuration #1 chosen from 1 choice
[  101.965921] hub 1-0:1.0: USB hub found
[  101.965943] hub 1-0:1.0: 2 ports detected
[  102.000739] st: Version 20061107, fixed bufsize 32768, s/g segs 256
[  102.001190] st 0:0:0:0: Attached scsi tape st0
[  102.001197] st 0:0:0:0: st0: try direct i/o: yes (alignment 512 B)
[  102.027268] st 0:0:0:0: Attached scsi generic sg0 type 1
[  102.085176] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 19
[  102.108432] e100: eth0: e100_probe: addr 0xf4200000, irq 19, MAC addr 00:D0:B7:16:26:81
[  102.108905] PIIX4: IDE controller at PCI slot 0000:00:12.1
[  102.108929] PIIX4: chipset revision 1
[  102.108935] PIIX4: not 100% native mode: will probe irqs later
[  102.108951]     ide0: BM-DMA at 0x2c20-0x2c27, BIOS settings: hda:DMA, hdb:DMA
[  102.108976]     ide1: BM-DMA at 0x2c28-0x2c2f, BIOS settings: hdc:DMA, hdd:pio
[  102.108997] Probing IDE interface ide0...
[  102.420631] hda: WDC WD1600BB-56RDA0, ATA DISK drive
[  102.720382] hdb: WDC WD1600BB-56RDA0, ATA DISK drive
[  102.780415] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[  102.780570] Probing IDE interface ide1...
[  103.569693] hdc: SONY CD-ROM CDU523 1, ATAPI CD/DVD-ROM drive
[  103.929552] ide1 at 0x170-0x177,0x376 on irq 15
[  103.960425] libata version 2.20 loaded.
[  104.009631] hda: max request size: 512KiB
[  104.042417] hda: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(33)
[  104.042557] hda: cache flushes supported
[  104.042654]  hda: hda1 hda2 < hda5 >
[  104.079901] hdb: max request size: 512KiB
[  104.104906] hdb: 312581808 sectors (160041 MB) w/2048KiB Cache, CHS=19457/255/63, UDMA(33)
[  104.105031] hdb: cache flushes supported
[  104.105097]  hdb: unknown partition table
[  104.162815] hdc: ATAPI 52X CD-ROM drive, 128kB Cache, UDMA(33)
[  104.162874] Uniform CD-ROM driver Revision: 3.20
[  104.770719] Attempting manual resume
[  104.770729] swsusp: Resume From Partition 3:5
[  104.770734] PM: Checking swsusp image.
[  104.771113] PM: Resume from disk failed.
[  104.835000] kjournald starting.  Commit interval 5 seconds
[  104.835029] EXT3-fs: mounted filesystem with ordered data mode.
[  109.315024] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[  110.763820] NET: Registered protocol family 10
[  110.764044] lo: Disabled Privacy Extensions
[  111.761200] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  111.768348] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  112.882342] Linux agpgart interface v0.102 (c) Dave Jones
[  113.128574] agpgart: Detected an Intel 440GX Chipset.
[  113.133768] agpgart: AGP aperture is 64M @ 0xf8000000
[  113.209311] piix4_smbus 0000:00:12.3: Found 0000:00:12.3 device
[  113.734178] input: PC Speaker as /class/input/input2
[  113.876001] parport: PnPBIOS parport detected.
[  113.876107] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  114.568172] lp0: using parport0 (interrupt-driven).
[  114.877515] Adding 3028212k swap on /dev/disk/by-uuid/0159f9f2-be64-4f29-a14c-63cae76ad113.  Priority:-1 extents:1 across:3028212k
[  115.067825] EXT3 FS on hda1, internal journal
[  119.995022] ppdev: user-space parallel port driver
[  121.544856] eth0: no IPv6 routers present
[  138.657159] ip_tables: (C) 2000-2006 Netfilter Core Team
[245314.740418] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[245314.872337] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[245314.872404] NFSD: starting 90-second grace period
[245672.937895] nfsd: last server has exited
[245672.937906] nfsd: unexporting all filesystems
[245672.938731] RPC: failed to contact portmap (errno -5).
[245674.111100] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[245674.111164] NFSD: starting 90-second grace period
[274398.146205] ADDRCONF(NETDEV_UP): eth0: link is not ready
[274398.152816] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[274399.075264] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[274409.723175] eth0: no IPv6 routers present
[277025.784796] nfsd: last server has exited
[277025.784808] nfsd: unexporting all filesystems
[277025.786388] RPC: failed to contact portmap (errno -5).
[280185.893800] fuse init (API version 7.8)
```

i looked inside the box and i can see two cpu heatsinks, so i'm guessing that i do have two cpus.

EDIT: no idea how to operate the bios on this box (its a SCSI system). don't want to touch incase i bork anything.

---

### Post by craigp84 on 2007-05-18
Your box is dual processer capable, but the second CPU is not connected.

As above this is either because it's dead (allowed to overheat?) or because it's become unseated, or, because it's not there :-)

Remove the heatsinks, have a look.

-c

---

### Post by Uluen on 2007-05-19
> **tr333 said:**
> 
i looked inside the box and i can see two cpu heatsinks, so i'm guessing that i do have two cpus.

EDIT: no idea how to operate the bios on this box (its a SCSI system). don't want to touch incase i bork anything.

Is the two heatsinks identical? One could just be a VRM.
Did you try installing a SMP kernel?

---

### Post by tr333 on 2007-05-19
> **Uluen said:**
> Is the two heatsinks identical? One could just be a VRM.
Did you try installing a SMP kernel?

"uname -v" shows "#2 SMP Sun Apr 15 07:41:34 UTC 2007"

havent got to opening the box yet.

---

### Post by tr333 on 2007-05-19
after opening the box, i can't actually look at any CPUs.  The CPU enclosure seems to be a card coming off the motherboard about 13cm long and about 6 cm high, with a large heatsink/fan on one side of it.  I can't seem to get this card off the motherboard.  The only evidence I have of multiple cpus in this box is from the previous owner who told me it was dual-cpu.

---

### Post by craigp84 on 2007-05-19
Since when was a VRM huge and in requirement of a CPU sized heatsink?

But that's a good point, if you are going to add a second CPU, make sure you have a VRM for it too.

-c

---

