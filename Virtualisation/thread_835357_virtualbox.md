---
title: "virtualbox"
date: 2008-06-20
forum: Virtualisation
---

### Post by Doby on 2008-06-20
I recently installed the new updates for ubuntu 7.10 and now I can not use my virtualbox xp, or install a new xp in virtualbox I get this error and do not know how to correct the issue.


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 please help me.

---

### Post by dnns123 on 2008-06-20
type "sudo /etc/init.d/vboxdrv start"
wait for the "user@user:~$" to show again, it'll say when its done

---

### Post by Doby on 2008-06-20
I did that and I get this

 
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

---

### Post by Doby on 2008-06-20
and this is what i get when I run dmesg

624)
[    0.000000] ACPI: SSDT 7F684F93, 04E6 (r1 HPQOEM SLIC-MPC     3000 INTL 20050624)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] Built 1 zonelists.  Total pages: 517779
[    0.000000] Kernel command line: root=UUID=94b33fce-ab70-4447-8bef-3c84b557b666 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1729.222 MHz processor.
[   31.654272] Console: colour VGA+ 80x25
[   31.654558] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   31.654944] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   31.769541] Memory: 2058040k/2087424k available (2016k kernel code, 28068k reserved, 919k data, 364k init, 1169920k highmem)
[   31.769552] virtual kernel memory layout:
[   31.769553]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   31.769554]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   31.769556]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   31.769557]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   31.769558]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   31.769560]       .data : 0xc02f8036 - 0xc03dde84   ( 919 kB)
[   31.769561]       .text : 0xc0100000 - 0xc02f8036   (2016 kB)
[   31.769564] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   31.769604] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   31.769749] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   31.769754] hpet0: 3 64-bit timers, 14318180 Hz
[   31.850742] Calibrating delay using timer specific routine.. 3461.96 BogoMIPS (lpj=6923922)
[   31.850767] Security Framework v1.0.0 initialized
[   31.850775] SELinux:  Disabled at boot.
[   31.850789] Mount-cache hash table entries: 512
[   31.850924] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 0000c109 00000000 00000000
[   31.850933] monitor/mwait feature present.
[   31.850934] using mwait in idle threads.
[   31.850939] CPU: L1 I cache: 32K, L1 D cache: 32K
[   31.850942] CPU: L2 cache: 1024K
[   31.850945] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0000c109 00000000 00000000
[   31.850956] Compat vDSO mapped to ffffe000.
[   31.850969] Checking 'hlt' instruction... OK.
[   31.866858] SMP alternatives: switching to UP code
[   31.867068] Freeing SMP alternatives: 11k freed
[   31.867345] Early unpacking initramfs... done
[   32.203312] ACPI: Core revision 20070126
[   32.203387] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   32.253558] CPU0: Intel(R) Celeron(R) M CPU        430  @ 1.73GHz stepping 08
[   32.253584] Total of 1 processors activated (3461.96 BogoMIPS).
[   32.253780] ENABLING IO-APIC IRQs
[   32.253986] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   32.430529] Brought up 1 CPUs
[   32.430635] Booting paravirtualized kernel on bare hardware
[   32.430721] Time: 14:35:14  Date: 05/20/108
[   32.430741] NET: Registered protocol family 16
[   32.430821] EISA bus registered
[   32.430826] ACPI: bus type pci registered
[   32.430968] PCI: PCI BIOS revision 2.10 entry at 0xfd733, last bus=8
[   32.430970] PCI: Using configuration type 1
[   32.430972] Setting up standard PCI resources
[   32.435284] ACPI: EC: Look up EC in DSDT
[   32.435901] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   32.446199] ACPI: System BIOS is requesting _OSI(Linux)
[   32.446202] ACPI: Please test with "acpi_osi=!Linux"
[   32.446203] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   32.446850] ACPI: Interpreter enabled
[   32.446853] ACPI: (supports S0 S3 S4 S5)
[   32.446869] ACPI: Using IOAPIC for interrupt routing
[   32.456357] ACPI: EC: GPE=0x17, ports=0x66, 0x62
[   32.456409] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   32.456423] PCI: Probing PCI hardware (bus 00)
[   32.457168] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   32.457172] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   32.458006] PCI: Firmware left 0000:08:08.0 e100 interrupts enabled, disabling
[   32.458428] PCI: Transparent bridge - 0000:00:1e.0
[   32.458532] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   32.458849] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   32.458979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   32.459107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   32.459247] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   32.462010] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   32.462117] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   32.462217] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   32.462316] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   32.462414] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   32.462541] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   32.462641] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   32.462740] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   32.462855] Linux Plug and Play Support v0.97 (c) Adam Belay
[   32.462866] pnp: PnP ACPI init
[   32.462873] ACPI: bus type pnp registered
[   32.465572] pnp: PnP ACPI: found 11 devices
[   32.465574] ACPI: ACPI bus type pnp unregistered
[   32.465578] PnPBIOS: Disabled by ACPI PNP
[   32.465623] PCI: Using ACPI for IRQ routing
[   32.465626] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   32.495728] NET: Registered protocol family 8
[   32.495730] NET: Registered protocol family 20
[   32.495786] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   32.495789] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   32.495793] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   32.495796] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   32.495804] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   32.495807] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   32.498467] Time: tsc clocksource has been installed.
[   32.498482] Switched to high resolution mode on CPU 0
[   32.526079] PCI: Bridge: 0000:00:1c.0
[   32.526082]   IO window: 2000-2fff
[   32.526089]   MEM window: d2000000-d3ffffff
[   32.526094]   PREFETCH window: d0000000-d1ffffff
[   32.526100] PCI: Bridge: 0000:00:1c.2
[   32.526102]   IO window: disabled.
[   32.526107]   MEM window: disabled.
[   32.526111]   PREFETCH window: disabled.
[   32.526117] PCI: Bridge: 0000:00:1c.3
[   32.526119]   IO window: disabled.
[   32.526125]   MEM window: d4000000-d40fffff
[   32.526129]   PREFETCH window: disabled.
[   32.526136] PCI: Bridge: 0000:00:1e.0
[   32.526140]   IO window: 3000-3fff
[   32.526146]   MEM window: d4100000-d41fffff
[   32.526150]   PREFETCH window: disabled.
[   32.526181] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   32.526188] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   32.526212] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 17
[   32.526218] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   32.526241] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   32.526247] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   32.526261] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   32.526273] NET: Registered protocol family 2
[   32.562447] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   32.562522] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   32.563603] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   32.563992] TCP: Hash tables configured (established 131072 bind 65536)
[   32.563995] TCP reno registered
[   32.574562] checking if image is initramfs... it is
[   33.237272] Freeing initrd memory: 7051k freed
[   33.237397] Simple Boot Flag at 0x36 set to 0x1
[   33.237731] audit: initializing netlink socket (disabled)
[   33.237743] audit(1213972514.052:1): initialized
[   33.237810] highmem bounce pool size: 64 pages
[   33.239586] VFS: Disk quotas dquot_6.5.1
[   33.239633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   33.239722] io scheduler noop registered
[   33.239724] io scheduler anticipatory registered
[   33.239726] io scheduler deadline registered
[   33.239740] io scheduler cfq registered (default)
[   33.239754] Boot video device is 0000:00:02.0
[   33.239921] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   33.239981] assign_interrupt_mode Found MSI capability
[   33.239984] Allocate Port Service[0000:00:1c.0:pcie00]
[   33.240013] Allocate Port Service[0000:00:1c.0:pcie02]
[   33.240114] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   33.240171] assign_interrupt_mode Found MSI capability
[   33.240174] Allocate Port Service[0000:00:1c.2:pcie00]
[   33.240201] Allocate Port Service[0000:00:1c.2:pcie02]
[   33.240296] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   33.240354] assign_interrupt_mode Found MSI capability
[   33.240356] Allocate Port Service[0000:00:1c.3:pcie00]
[   33.240386] Allocate Port Service[0000:00:1c.3:pcie02]
[   33.240538] isapnp: Scanning for PnP cards...
[   33.594799] isapnp: No Plug & Play device found
[   33.620252] Real Time Clock Driver v1.12ac
[   33.620469] hpet_resources: 0xfed00000 is busy
[   33.620496] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   33.621699] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   33.621883] input: Macintosh mouse button emulation as /class/input/input0
[   33.621955] PNP: PS/2 Controller [PNP0303:KBD0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   33.623023] i8042.c: Detected active multiplexing controller, rev 1.1.
[   33.623103] serio: i8042 KBD port at 0x60,0x64 irq 1
[   33.623108] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   33.623111] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   33.623113] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   33.623116] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   33.623314] mice: PS/2 mouse device common for all mice
[   33.623519] EISA: Probing bus 0 at eisa.0
[   33.623527] Cannot allocate resource for EISA slot 1
[   33.623530] Cannot allocate resource for EISA slot 2
[   33.623533] Cannot allocate resource for EISA slot 3
[   33.623554] EISA: Detected 0 cards.
[   33.623648] TCP cubic registered
[   33.623662] NET: Registered protocol family 1
[   33.623686] Using IPI No-Shortcut mode
[   33.623857]   Magic number: 12:17:587
[   33.623937]   hash matches device ptyc5
[   33.624187] Freeing unused kernel memory: 364k freed
[   33.698894] input: AT Translated Set 2 keyboard as /class/input/input1
[   34.824978] AppArmor: AppArmor initialized<5>audit(1213972515.552:2):  type=1505 info="AppArmor initialized" pid=1236
[   34.830777] fuse init (API version 7.8)
[   34.836152] Failure registering capabilities with primary security module.
[   34.850110] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   34.850125] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[    2.908000] Marking TSC unstable due to: possible TSC halt in C2.
[    2.912000] Time: hpet clocksource has been installed.
[    2.912000] ACPI: Thermal Zone [TZS0] (72 C)
[    2.916000] ACPI: Thermal Zone [TZS1] (72 C)
[    3.388000] usbcore: registered new interface driver usbfs
[    3.388000] usbcore: registered new interface driver hub
[    3.388000] usbcore: registered new device driver usb
[    3.388000] USB Universal Host Controller Interface driver v3.0
[    3.388000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    3.388000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.388000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.388000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.388000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    3.388000] usb usb1: configuration #1 chosen from 1 choice
[    3.388000] hub 1-0:1.0: USB hub found
[    3.388000] hub 1-0:1.0: 2 ports detected
[    3.492000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    3.492000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.492000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.492000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.492000] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[    3.492000] usb usb2: configuration #1 chosen from 1 choice
[    3.492000] hub 2-0:1.0: USB hub found
[    3.492000] hub 2-0:1.0: 2 ports detected
[    3.504000] SCSI subsystem initialized
[    3.520000] libata version 2.21 loaded.
[    3.536000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[    3.536000] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.596000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 20
[    3.596000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.596000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.596000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.596000] uhci_hcd 0000:00:1d.2: irq 20, io base 0x00001860
[    3.596000] usb usb3: configuration #1 chosen from 1 choice
[    3.596000] hub 3-0:1.0: USB hub found
[    3.596000] hub 3-0:1.0: 2 ports detected
[    3.700000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 21
[    3.700000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.700000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.700000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.700000] uhci_hcd 0000:00:1d.3: irq 21, io base 0x00001880
[    3.700000] usb usb4: configuration #1 chosen from 1 choice
[    3.700000] hub 4-0:1.0: USB hub found
[    3.700000] hub 4-0:1.0: 2 ports detected
[    3.732000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[    3.804000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    3.804000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.804000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.804000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.804000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.804000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.804000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd4544000
[    3.848000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.848000] usb usb5: configuration #1 chosen from 1 choice
[    3.848000] hub 5-0:1.0: USB hub found
[    3.848000] hub 5-0:1.0: 8 ports detected
[    3.952000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ 22
[    3.980000] e100: eth0: e100_probe: addr 0xd4100000, irq 22, MAC addr 00:16:D3:11:FA:CD
[    3.980000] ACPI: PCI Interrupt 0000:08:09.0[A] -> GSI 16 (level, low) -> IRQ 21
[    4.000000] Clocksource tsc unstable (delta = -83892344 ns)
[    4.048000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[d4101000-d41017ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.052000] ata_piix 0000:00:1f.1: version 2.11
[    4.052000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[    4.052000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.052000] scsi0 : ata_piix
[    4.052000] scsi1 : ata_piix
[    4.052000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.052000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.260000] usb 1-1: device not accepting address 2, error -71
[    4.372000] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[    4.544000] ata1.00: configured for MWDMA2
[    4.544000] ata2: port disabled. ignoring.
[    4.548000] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
[    4.548000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    4.548000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    4.704000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 20 (level, low) -> IRQ 22
[    4.704000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.704000] scsi2 : ata_piix
[    4.704000] scsi3 : ata_piix
[    4.704000] ata3: SATA max UDMA/133 cmd 0x000118d0 ctl 0x000118c6 bmdma 0x000118b0 irq 22
[    4.704000] ata4: SATA max UDMA/133 cmd 0x000118c8 ctl 0x000118c2 bmdma 0x000118b8 irq 22
[    4.868000] ata3.00: ATA-8: FUJITSU MHY2250BH, 0000000B, max UDMA/100
[    4.868000] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.884000] ata3.00: configured for UDMA/100
[    5.048000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHY2250B 0000 PQ: 0 ANSI: 5
[    5.072000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.072000] Uniform CD-ROM driver Revision: 3.20
[    5.072000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.076000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.076000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.088000] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.088000] sd 2:0:0:0: [sda] Write Protect is off
[    5.088000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.088000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.088000] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.088000] sd 2:0:0:0: [sda] Write Protect is off
[    5.088000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.088000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.088000]  sda: sda1 sda2 < sda5 >
[    5.144000] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.164000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[    5.288000] Attempting manual resume
[    5.288000] swsusp: Resume From Partition 8:5
[    5.288000] PM: Checking swsusp image.
[    5.288000] PM: Resume from disk failed.
[    5.304000] kjournald starting.  Commit interval 5 seconds
[    5.304000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.324000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[06e40a00c98b5042]
[    5.336000] usb 1-1: configuration #1 chosen from 1 choice
[    5.344000] hub 1-1:1.0: USB hub found
[    5.344000] hub 1-1:1.0: 3 ports detected
[    5.692000] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    5.868000] usb 3-2: configuration #1 chosen from 1 choice
[    6.076000] usb 1-1.1: new full speed USB device using uhci_hcd and address 5
[    6.212000] usb 1-1.1: configuration #1 chosen from 1 choice
[    6.424000] usb 1-1.3: new low speed USB device using uhci_hcd and address 6
[    6.560000] usb 1-1.3: configuration #1 chosen from 1 choice
[   14.292000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.296000] agpgart: Detected an Intel 945GM Chipset.
[   14.296000] agpgart: Detected 7932K stolen memory.
[   14.312000] agpgart: AGP aperture is 256M @ 0xc0000000
[   14.380000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.432000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.116000] iTCO_vendor_support: vendor-support=0
[   15.300000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   15.300000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   15.300000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.356000] intel_rng: FWH not detected
[   15.792000] sdhci: Secure Digital Host Controller Interface driver
[   15.792000] sdhci: Copyright(c) Pierre Ossman
[   15.792000] sdhci: SDHCI controller found at 0000:08:09.1 [1180:0822] (rev 19)
[   15.792000] ACPI: PCI Interrupt 0000:08:09.1[B] -> GSI 18 (level, low) -> IRQ 17
[   15.792000] mmc0: SDHCI at 0xd4101800 irq 17 DMA
[   16.168000] ieee80211_crypt: registered algorithm 'NULL'
[   16.200000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.200000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.264000] Bluetooth: Core ver 2.11
[   16.264000] NET: Registered protocol family 31
[   16.264000] Bluetooth: HCI device and connection manager initialized
[   16.264000] Bluetooth: HCI socket layer initialized
[   16.300000] Bluetooth: HCI USB driver ver 2.9
[   16.300000] usbcore: registered new interface driver hci_usb
[   16.304000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   16.332000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   16.476000] usbcore: registered new interface driver hiddev
[   16.480000] input: Dell Dell USB Keyboard as /class/input/input3
[   16.480000] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1
[   16.484000] input: Dell Dell USB Keyboard as /class/input/input4
[   16.484000] input: USB HID v1.10 Device [Dell Dell USB Keyboard] on usb-0000:00:1d.0-1.1
[   16.500000] input: Logitech Optical USB Mouse as /class/input/input5
[   16.500000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1.3
[   16.500000] usbcore: registered new interface driver usbhid
[   16.500000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   16.532000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp
[   16.532000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.532000] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   16.532000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   16.532000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.588000] usbcore: registered new interface driver xpad
[   16.588000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   16.664000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 23
[   16.664000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   17.672000] lp: driver loaded but no devices found
[   17.740000] Adding 6048432k swap on /dev/sda5.  Priority:-1 extents:1 across:6048432k
[   18.172000] EXT3 FS on sda1, internal journal
[   18.756000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   20.668000] NET: Registered protocol family 17
[   22.688000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.688000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   22.700000] No dock devices found.
[   22.728000] ACPI: AC Adapter [ADP1] (on-line)
[   22.788000] ACPI: Battery Slot [BAT0] (battery present)
[   22.940000] input: Power Button (FF) as /class/input/input6
[   22.944000] ACPI: Power Button (FF) [PWRF]
[   22.984000] input: Lid Switch as /class/input/input7
[   22.988000] ACPI: Lid Switch [LID0]
[   23.032000] input: Sleep Button (CM) as /class/input/input8
[   23.036000] ACPI: Sleep Button (CM) [SLPB]
[   23.080000] input: Power Button (CM) as /class/input/input9
[   23.080000] ACPI: Power Button (CM) [PWRB]
[   24.440000] Failure registering capabilities with primary security module.
[   24.784000] ppdev: user-space parallel port driver
[   25.152000] audit(1213972538.378:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5110 profile="/usr/sbin/cupsd"
[   25.192000] apm: BIOS not found.
[   25.448000] NET: Registered protocol family 10
[   25.448000] lo: Disabled Privacy Extensions
[   25.448000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.448000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.540000] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   25.600000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   25.620000] NFSD: starting 90-second grace period
[   32.112000] hypervisor: module license 'unspecified' taints kernel.
[   32.116000] [ 5275] Device /dev/hypervisor registered with 10.63
[   32.120000] [ 5275] parallels Hypervisor 2.2-2226 initialized.
[   32.176000] vm_main: no version for "appIncCounter" found: kernel tainted.
[   32.184000] [ 5288] Device /dev/vm-main registered with 10.62
[   32.184000] [ 5288] Parallels Workstation 2.2-2226 Main module initialized.
[   32.964000] device vnic0 entered promiscuous mode
[   32.964000] audit(1213972546.378:4): dev=vnic0 prom=256 old_prom=0 auid=4294967295
[   34.144000] Bluetooth: L2CAP ver 2.8
[   34.144000] Bluetooth: L2CAP socket layer initialized
[   34.236000] Bluetooth: RFCOMM socket layer initialized
[   34.236000] Bluetooth: RFCOMM TTY layer initialized
[   34.236000] Bluetooth: RFCOMM ver 1.8
[   34.788000] APIC error on CPU0: 00(40)
[   38.152000] [drm] Initialized drm 1.1.0 20060810
[   38.156000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 21
[   38.156000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   46.816000] vnic0: no IPv6 routers present
[   51.772000] UDF-fs: No VRS found
[   68.068000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   78.844000] eth1: no IPv6 routers present
[  101.152000] eth1: no IPv6 routers present

---

### Post by NikoC on 2008-06-20
Perhaps a solution for your problem is offered [here]("http://ubuntuforums.org/showthread.php?t=737305")?

Cheers.

---

### Post by Doby on 2008-06-20
Nope, I am running gutsy still but I still tried it and still got the same error, the modprobe was not found.

---

### Post by Doby on 2008-06-20
I'm sorry its my "FATAL: Module vboxdrv not found"

---

### Post by philinux on 2008-06-20
Does vboxdrv file exist?

You could try booting with the previous kernel if a new kernel was part of your upgrades.

You could mark virtualbox for reinstall.

---

### Post by Doby on 2008-06-20
I already tried that too.  I am know upgrading to 8.04lts

---

### Post by jonthysell on 2008-06-20
I'm having the same problem on Gutsy, the auto-update said I needed a system reset, I assume it updated my kernel because now I'm .15 and the vboxdrv module is for .14.

Is there a .15 update for the vboxdrv in the works, or am I rolling back to the earlier kernel? Or just updating to Hardy?

---

### Post by Doby on 2008-06-20
I just updated to hardy and I still have the same problem but I'm going to try the link earlier in this post to see if that will fix the problem.

---

### Post by Doby on 2008-06-20
OK. I fixed the issue, and here is what I did.

First I upgraded to 8.04lts through the update manager(took about 2 hours for full upgrade).
Then after the restart I ran this in terminal

sudo /etc/init.d/vboxdrv start
sudo /etc/init.d/vboxdrv setup
sudo /etc/init.d/vboxdrv setup
aptitude install virtualbox-ose-modules-generic


Yes I ran the second line twice for some reason everyone else did it twice and it worked for them but not if they ran it once.  and after the last line you should restart virtual box, then you should be good.

I hope this helps anyone else out cause it was really shi**y that I lost my windows machine at work and not at home seems I only use windows for work.LOL.  Anyways good luck.  And thanks to everyone that helped me along too.

Long live Linuix

---

