---
title: "dmesg analysis"
date: 2008-07-29
forum: Server Platforms
---

### Post by Linux-Leach on 2008-07-29
I normally wouldn't do this, but having checked the output of my server's dmesg during a recent re-boot, I wanted to try.  I noticed a number of messages that could represent problems.  Therefore, I am appending a subset of my dmesg output.  If someone could take a quick scan and tell me if any of these deserve corrective action (and guide me to what that might be) I'd appreciate it.  Thanks in advance.

...
NUMA: Using 30 for the hash shift.
Using node hash shift of 30
...
Nvidia board detected. Ignoring ACPI timer override.
If you got timer trouble try acpi_use_timer_override
ACPI: PM-Timer IO Port: 0x8008
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
...
Setting APIC routing to flat
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at c2000000 (gap: c0000000:20000000)
...
PID hash table entries: 4096 (order: 12, 32768 bytes)
TSC calibrated against PM_TIMER
Marking TSC unstable due to TSCs unsynchronized
...
CPU 0: aperture @ 0 size 32 MB
No AGP bridge found
Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup
This costs you 64 MB of RAM
Mapping aperture over 65536 KB of RAM @ 4000000
...
SMP alternatives: switching to UP code
ACPI: Core revision 20070126
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Using local APIC timer interrupts.
APIC timer calibration result 12557791
...
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
...
PCI-DMA: Disabling AGP.
PCI-DMA: aperture base @ 4000000 size 65536 KB
PCI-DMA: using GART IOMMU.
PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
system 00:00: iomem range 0xfefff000-0xfeffffff has been reserved
system 00:02: ioport range 0x8000-0x807f has been reserved
system 00:02: ioport range 0x8080-0x80ff has been reserved
system 00:02: ioport range 0x8400-0x847f has been reserved
...
PCI: Bridge: 0000:00:09.0
  IO window: 2000-2fff
  MEM window: dd100000-deffffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:0d.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:0e.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Setting latency timer of device 0000:00:09.0 to 64
PCI: Setting latency timer of device 0000:00:0d.0 to 64
PCI: Setting latency timer of device 0000:00:0e.0 to 64
PCI: Bridge: 0000:08:0a.0
  IO window: 3000-4fff
  MEM window: df300000-df3fffff
  PREFETCH window: disabled.
PCI: Bridge: 0000:08:0b.0
  IO window: disabled.
  MEM window: df400000-df4fffff
  PREFETCH window: c2000000-c20fffff
...
Boot video device is 0000:01:06.0
PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:08:0a.0 subordinate bus.
AMD8131 rev 12 detected, disabling PCI-X MMRBC
PCI: MSI quirk detected. PCI_BUS_FLAGS_NO_MSI set for 0000:08:0b.0 subordinate bus.
AMD8131 rev 12 detected, disabling PCI-X MMRBC
PCI: Setting latency timer of device 0000:00:0d.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:0d.0:pcie00]
PCI: Setting latency timer of device 0000:00:0e.0 to 64
assign_interrupt_mode Found MSI capability
...
Probing IDE interface ide0...
hdb: LITE-ON CD-ROM LTN-5291S, ATAPI CD/DVD-ROM drive
hda: HDS728080PLAT20, ATA DISK drive
hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hda: UDMA/133 mode selected
hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hdb: UDMA/33 mode selected
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
...
ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ffb00000-0x00000000ffffffff - kernel bug?
...
CFI: Found no ck804xrom @ffc00000 device at location zero
...
cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
...
PCI: cache line size of 64 is not supported by device 0000:00:02.1
...
Driver 'sd' needs updating - please use bus_type methods
...

Daniel

---

### Post by jazzgossen on 2008-07-30
I don't see anything very alarming, but this message:

Your BIOS doesn't leave a aperture memory hole
Please enable the IOMMU option in the BIOS setup

should be relatively easy to fix in the BIOS. Enter BIOS (probably by pressing Del when booting your computer) and look for a "memory hole" option in the video/AGP setup section, and enable it. 

Although unless you have very little RAM, you probably won't notice any difference.

---

### Post by terciof on 2008-08-24
Hi All!

I had installed a Ubuntu Server 8.04 in a Dell Server machine(I don't remember which model specifically), and everything, except USB external driver is working.

I did configure every service that I need, unless my external driver that we use to create backup copies.

Attached my dmesg and lspci.

Seems to be a problem on CK804 chipset driver.

Expressive entries come:

```


dmesg:

[   26.851061] ck804xrom ck804xrom_init_one(): Unable to register resource 0x00000000ffb00000-0x00000000ffffffff - kernel bug?
[   26.871884] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1440
[   26.871903] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1400
[   26.981350] CFI: Found no ck804xrom @ffc00000 device at location zero
[   27.069153] JEDEC: Found no ck804xrom @ffc00000 device at location zero

...

[   27.127696] JEDEC: Found no ck804xrom @fff00000 device at location zero
[   27.127720] CFI: Found no ck804xrom @fff00000 device at location zero
[   27.127769] Found: SST 49LF080A
[   27.127776] ck804xrom @fff00000: Found 1 x8 devices at 0x0 in 8-bit bank
[   27.141760] input: Power Button (FF) as /devices/virtual/input/input4
[   27.143387] number of JEDEC chips: 1
[   27.143392] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.

...

[12406.907940] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: couldn't find an input interrupt endpoint
[12436.909560] usb 1-6: new high speed USB device using ehci_hcd and address 5
[12437.061805] usb 1-6: configuration #1 chosen from 1 choice
[12437.109430] usbcore: registered new interface driver libusual
[12437.121155] Initializing USB Mass Storage driver...
[12437.121527] scsi4 : SCSI emulation for USB Mass Storage devices
[12437.121857] usbcore: registered new interface driver usb-storage
[12437.121861] USB Mass Storage support registered.
[12437.122408] usb-storage: device found at 5
[12437.122410] usb-storage: waiting for device to settle before scanning
[12442.103123] usb-storage: device scan complete
[12442.105088] scsi 4:0:0:0: Direct-Access     SAMSUNG  S0MUJ50Q202207   CR10 PQ: 0 ANSI: 2 CCS
[12442.116685] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[12442.119554] sd 4:0:0:0: [sdb] Write Protect is off
[12442.119559] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12442.119563] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12442.123691] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[12442.126546] sd 4:0:0:0: [sdb] Write Protect is off
[12442.126551] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[12442.126554] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[12442.126614]  sdb: sdb1
[12442.174683] sd 4:0:0:0: [sdb] Attached SCSI disk
[12442.174725] sd 4:0:0:0: Attached scsi generic sg2 type 0
[12469.239730] kjournald starting.  Commit interval 5 seconds
[12469.239750] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[12469.242330] EXT3 FS on sdb1, internal journal
[12469.242336] EXT3-fs: mounted filesystem with ordered data mode.
[12501.886591] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12512.143491] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12517.406765] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12517.526604] usb 1-6: device descriptor read/64, error -71
[12517.756306] usb 1-6: device descriptor read/64, error -71
[12517.986014] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12518.105855] usb 1-6: device descriptor read/64, error -71
[12518.335557] usb 1-6: device descriptor read/64, error -71
[12518.565266] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12518.984730] usb 1-6: device not accepting address 5, error -71
[12519.104578] usb 1-6: reset high speed USB device using ehci_hcd and address 5
[12519.524042] usb 1-6: device not accepting address 5, error -71
[12519.524109] sd 4:0:0:0: Device offlined - not ready after error recovery
[12519.524117] sd 4:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK

uname -a:

Linux service.cosa.local 2.6.24-19-server #1 SMP Wed Jun 18 15:18:00 UTC 2008 i686 GNU/Linux

lscpi:

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express

cpuinfo:

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : Dual-Core AMD Opteron(tm) Processor 1212
stepping        : 3
cpu MHz         : 2009.264
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips        : 4020.41
clflush size    : 64

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 67
model name      : Dual-Core AMD Opteron(tm) Processor 1212
stepping        : 3
cpu MHz         : 2009.264
cache size      : 1024 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy ts fid vid ttp tm stc
bogomips        : 4018.55
clflush size    : 64

meminfo:

MemTotal:      1034152 kB
MemFree:        536892 kB
Buffers:         99224 kB
Cached:         273548 kB
SwapCached:          0 kB
Active:         175712 kB
Inactive:       220840 kB
HighTotal:      129984 kB
HighFree:          260 kB
LowTotal:       904168 kB
LowFree:        536632 kB
SwapTotal:      497972 kB
SwapFree:       497972 kB
Dirty:              28 kB
Writeback:           0 kB
AnonPages:       23916 kB
Mapped:           5420 kB
Slab:            91708 kB
SReclaimable:    81256 kB
SUnreclaim:      10452 kB
PageTables:        396 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1015048 kB
Committed_AS:    63960 kB
VmallocTotal:   118776 kB
VmallocUsed:      7964 kB
VmallocChunk:   110480 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB



```

I saw some news about machines with more than 4GB RAM, not my case.

May I fill a bug report?

Thanks!

Tercio

---

### Post by terciof on 2008-08-24
I know that this is weird, but, I did a restart, the same messages, but now I can mount the external driver.

Well, the same messages still apply.

Now I have this on my dmesg when I try a fsck.ext3 -nvtt /dev/sdb1

```

[  145.636055] kjournald starting.  Commit interval 5 seconds
[  145.637796] EXT3-fs warning: mounting fs with errors, running e2fsck is recommended
[  145.639643] EXT3 FS on sdb1, internal journal
[  145.639648] EXT3-fs: recovery complete.
[  145.639652] EXT3-fs: mounted filesystem with ordered data mode.
[ 1406.808475] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1406.808482] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current]
[ 1406.808486] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1406.808491] end_request: I/O error, dev sdb, sector 601748279
[ 1406.808495] Buffer I/O error on device sdb1, logical block 300874108
[ 1406.808539] Buffer I/O error on device sdb1, logical block 300874109
[ 1406.808567] Buffer I/O error on device sdb1, logical block 300874110
[ 1406.808595] Buffer I/O error on device sdb1, logical block 300874111
[ 1413.037606] sd 4:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1413.037611] sd 4:0:0:0: [sdb] Sense Key : Medium Error [current]
[ 1413.037614] sd 4:0:0:0: [sdb] Add. Sense: Unrecovered read error
[ 1413.037618] end_request: I/O error, dev sdb, sector 601748279
[ 1413.037620] Buffer I/O error on device sdb1, logical block 300874108
[ 1413.037649] Buffer I/O error on device sdb1, logical block 300874109
[ 1413.037677] Buffer I/O error on device sdb1, logical block 300874110
[ 1413.037704] Buffer I/O error on device sdb1, logical block 300874111


```

Regards,

---

