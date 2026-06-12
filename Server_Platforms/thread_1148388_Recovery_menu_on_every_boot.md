---
title: "Recovery menu on every boot"
date: 2009-05-04
forum: Server Platforms
---

### Post by infirmus on 2009-05-04
Is it normal behaviour that the recovery menu comes up on every boot? It is quite annoying as it prevents you from remotely rebooting the server.

I have to select "Resume normal boot" every time the server is restarted.

---

### Post by infirmus on 2009-05-05
Bump - is this normal behaviour?

---

### Post by cariboo on 2009-05-06
It sounds like you have recovery mode set as the default boot. You can edit /boot/grub/menu.lst to set which mode and kernel you want to boot. By default menu.lst is set to boot from the first kernel on the list. Look for this section:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

Change the zero to whichever kernel you want to boot from.

---

### Post by infirmus on 2009-05-09
> **cariboo907 said:**
> It sounds like you have recovery mode set as the default boot. You can edit /boot/grub/menu.lst to set which mode and kernel you want to boot. By default menu.lst is set to boot from the first kernel on the list. Look for this section:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0
```

Change the zero to whichever kernel you want to boot from.
Nope the menu.lst file is bog stock standard, default is 0 and the first kernel listed is not the recovery one.

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-server
uuid		0e4adf42-d13e-4475-ae79-1c2344e0b960
kernel		/vmlinuz-2.6.28-11-server root=/dev/mapper/single-rootfs ro quiet splash 
initrd		/initrd.img-2.6.28-11-server
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-server (recovery mode)
uuid		0e4adf42-d13e-4475-ae79-1c2344e0b960
kernel		/vmlinuz-2.6.28-11-server root=/dev/mapper/single-rootfs ro  single
initrd		/initrd.img-2.6.28-11-server

title		Ubuntu 9.04, memtest86+
uuid		0e4adf42-d13e-4475-ae79-1c2344e0b960
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by infirmus on 2009-05-11
dmesg output
```
[    0.000000] BIOS EBDA/lowmem at: 0009d800/0009d800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-server (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 02:45:36 UTC 2009 (Ubuntu 2.6.28-11.42-server)
[    0.000000] Command line: root=/dev/mapper/single-rootfs ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d800 (usable)
[    0.000000]  BIOS-e820: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dfb0000 (usable)
[    0.000000]  BIOS-e820: 000000007dfb0000 - 000000007dfc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dfc0000 - 000000007dff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dff0000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x7dfb0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d800 (usable)
[    0.000000]  modified: 000000000009d800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007dfb0000 (usable)
[    0.000000]  modified: 000000007dfb0000 - 000000007dfc0000 (ACPI data)
[    0.000000]  modified: 000000007dfc0000 - 000000007dff0000 (ACPI NVS)
[    0.000000]  modified: 000000007dff0000 - 000000007e000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-000000007dfb0000
[    0.000000]  0000000000 - 007de00000 page 2M
[    0.000000]  007de00000 - 007dfb0000 page 4k
[    0.000000] kernel direct mapping tables up to 7dfb0000 @ 10000-14000
[    0.000000] last_map_addr: 7dfb0000 end: 7dfb0000
[    0.000000] RAMDISK: 377d4000 - 37fef71f
[    0.000000] ACPI: RSDP 000FBA40, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7DFB0000, 003C (r1 100207 RSDT1125 20071002 MSFT       97)
[    0.000000] ACPI: FACP 7DFB0200, 0084 (r2 A M I  OEMFACP  12000601 MSFT       97)
[    0.000000] ACPI: DSDT 7DFB0450, 5B7A (r1  ASR32 ASR32164      164 INTL 20051117)
[    0.000000] ACPI: FACS 7DFC0000, 0040
[    0.000000] ACPI: APIC 7DFB0390, 0080 (r1 100207 APIC1125 20071002 MSFT       97)
[    0.000000] ACPI: MCFG 7DFB0410, 003C (r1 100207 OEMMCFG  20071002 MSFT       97)
[    0.000000] ACPI: OEMB 7DFC0040, 0071 (r1 100207 OEMB1125 20071002 MSFT       97)
[    0.000000] ACPI: NVHD 7DFC00C0, 0554 (r1 100207  NVHDCP  20071002 MSFT       97)
[    0.000000] ACPI: SSDT 7DFB5FD0, 0206 (r1 A M I  POWERNOW        1 AMD         1)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 007dfb0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]
[    0.000000]   #3 [00377d4000 - 0037fef71f]          RAMDISK ==> [00377d4000 - 0037fef71f]
[    0.000000]   #4 [000009d800 - 0000100000]    BIOS reserved ==> [000009d800 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007dfb0
[    0.000000] On node 0 totalpages: 515901
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2542 pages reserved
[    0.000000]   DMA zone: 1383 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6999 pages used for memmap
[    0.000000]   DMA32 zone: 504921 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e8000
[    0.000000] PM: Registered nosave memory: 00000000000e8000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:80c00000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 506304
[    0.000000] Kernel command line: root=/dev/mapper/single-rootfs ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2095.145 MHz processor.
[    0.010000] spurious 8259A interrupt: IRQ7.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try cgroup_disable=memory option if you don't want
[    0.010000] Scanning for low memory corruption every 60 seconds
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Node 0: aperture @ e244000000 size 32 MB
[    0.010000] Aperture beyond 4GB. Ignoring.
[    0.010000] Memory: 1992192k/2064064k available (4758k kernel code, 460k absent, 70696k reserved, 2542k data, 536k init)
[    0.010000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.010009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4190.29 BogoMIPS (lpj=20951450)
[    0.010030] Security Framework initialized
[    0.010037] SELinux:  Disabled at boot.
[    0.010053] AppArmor: AppArmor initialized
[    0.010061] Mount-cache hash table entries: 256
[    0.010206] Initializing cgroup subsys ns
[    0.010209] Initializing cgroup subsys cpuacct
[    0.010212] Initializing cgroup subsys memory
[    0.010216] Initializing cgroup subsys freezer
[    0.010228] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010230] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010231] tseg: 0000000000
[    0.010247] CPU: Physical Processor ID: 0
[    0.010248] CPU: Processor Core ID: 0
[    0.010251] using C1E aware idle routine
[    0.011810] ACPI: Core revision 20080926
[    0.013775] ACPI: Checking initramfs for custom DSDT
[    0.302191] Setting APIC routing to flat
[    0.302715] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1
[    0.402750] CPU0: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 01
[    0.410000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 4189.85 BogoMIPS (lpj=20949290)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.560218] CPU1: AMD Athlon(tm) X2 Dual Core Processor BE-2350 stepping 01
[    0.560232] Brought up 2 CPUs
[    0.560234] Total of 2 processors activated (8380.14 BogoMIPS).
[    0.560324] CPU0 attaching sched-domain:
[    0.560326]  domain 0: span 0-1 level CPU
[    0.560328]   groups: 0 1
[    0.560334] CPU1 attaching sched-domain:
[    0.560335]  domain 0: span 0-1 level CPU
[    0.560337]   groups: 1 0
[    0.560397] net_namespace: 1400 bytes
[    0.560397] Booting paravirtualized kernel on bare hardware
[    0.560397] Time: 13:15:31  Date: 05/04/09
[    0.560397] regulator: core version 0.5
[    0.560397] NET: Registered protocol family 16
[    0.560397] node 0 link 0: io port [1000, ffffff]
[    0.560397] node 0 link 0: io port [1000, 1fff]
[    0.560397] TOM: 0000000080000000 aka 2048M
[    0.560397] node 0 link 0: mmio [e0000000, efffffff]
[    0.560397] node 0 link 0: mmio [a0000, bffff]
[    0.560397] node 0 link 0: mmio [80000000, fe0bffff]
[    0.560397] bus: [00,07] on node 0 link 0
[    0.560397] bus: 00 index 0 io port: [0, ffff]
[    0.560397] bus: 00 index 1 mmio: [80000000, fcffffffff]
[    0.560397] bus: 00 index 2 mmio: [a0000, bffff]
[    0.560397] ACPI: bus type pci registered
[    0.560397] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.560397] PCI: Not using MMCONFIG.
[    0.560397] PCI: Using configuration type 1 for base access
[    0.560850] ACPI: EC: Look up EC in DSDT
[    0.574529] ACPI: Interpreter enabled
[    0.574532] ACPI: (supports S0 S1 S3 S4 S5)
[    0.574551] ACPI: Using IOAPIC for interrupt routing
[    0.574609] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.580178] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.593524] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.603062] ACPI: No dock devices found.
[    0.603130] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.603280] pci 0000:00:01.0: reg 10 io port: [0x1f00-0x1fff]
[    0.603315] pci 0000:00:01.1: reg 10 io port: [0xcc00-0xcc3f]
[    0.603324] pci 0000:00:01.1: reg 20 io port: [0x1d00-0x1d3f]
[    0.603328] pci 0000:00:01.1: reg 24 io port: [0x1e00-0x1e3f]
[    0.603338] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    0.603343] pci 0000:00:01.1: PME# disabled
[    0.603370] pci 0000:00:01.3: reg 10 32bit mmio: [0xfe980000-0xfe9fffff]
[    0.603451] pci 0000:00:06.0: reg 20 io port: [0xffa0-0xffaf]
[    0.603497] pci 0000:00:09.0: reg 10 io port: [0xf80-0xf87]
[    0.603500] pci 0000:00:09.0: reg 14 io port: [0xf00-0xf03]
[    0.603503] pci 0000:00:09.0: reg 18 io port: [0xe80-0xe87]
[    0.603506] pci 0000:00:09.0: reg 1c io port: [0xe00-0xe03]
[    0.603509] pci 0000:00:09.0: reg 20 io port: [0xbc00-0xbc0f]
[    0.603513] pci 0000:00:09.0: reg 24 32bit mmio: [0xfe97c000-0xfe97dfff]
[    0.603545] pci 0000:00:0a.0: reg 10 32bit mmio: [0xfe97b000-0xfe97bfff]
[    0.603548] pci 0000:00:0a.0: reg 14 io port: [0xb880-0xb887]
[    0.603552] pci 0000:00:0a.0: reg 18 32bit mmio: [0xfe97ac00-0xfe97acff]
[    0.603555] pci 0000:00:0a.0: reg 1c 32bit mmio: [0xfe97a800-0xfe97a80f]
[    0.603566] pci 0000:00:0a.0: supports D1 D2
[    0.603567] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603571] pci 0000:00:0a.0: PME# disabled
[    0.603594] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603596] pci 0000:00:0b.0: PME# disabled
[    0.603617] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603619] pci 0000:00:0c.0: PME# disabled
[    0.603640] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603642] pci 0000:00:0d.0: PME# disabled
[    0.603662] pci 0000:00:0e.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603665] pci 0000:00:0e.0: PME# disabled
[    0.603685] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603688] pci 0000:00:0f.0: PME# disabled
[    0.603710] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603712] pci 0000:00:10.0: PME# disabled
[    0.603733] pci 0000:00:11.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.603735] pci 0000:00:11.0: PME# disabled
[    0.603750] pci 0000:00:12.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.603755] pci 0000:00:12.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.603759] pci 0000:00:12.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.603764] pci 0000:00:12.0: reg 30 32bit mmio: [0xfe940000-0xfe95ffff]
[    0.603858] pci 0000:01:08.0: reg 10 32bit mmio: [0xfeaf0000-0xfeafffff]
[    0.603921] pci 0000:01:0a.0: reg 10 64bit mmio: [0xfeaefc00-0xfeaefc7f]
[    0.603930] pci 0000:01:0a.0: reg 18 64bit mmio: [0xfeae0000-0xfeae7fff]
[    0.603936] pci 0000:01:0a.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.603945] pci 0000:01:0a.0: reg 30 32bit mmio: [0xfea00000-0xfea7ffff]
[    0.603952] pci 0000:01:0a.0: supports D1 D2
[    0.603978] pci 0000:00:08.0: transparent bridge
[    0.603981] pci 0000:00:08.0: bridge io port: [0xd000-0xdfff]
[    0.603984] pci 0000:00:08.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.604054] pci 0000:03:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.604069] pci 0000:03:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.604083] pci 0000:03:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.604092] pci 0000:03:00.0: supports D1 D2
[    0.604094] pci 0000:03:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.604098] pci 0000:03:00.0: PME# disabled
[    0.604136] pci 0000:00:0c.0: bridge io port: [0xe000-0xefff]
[    0.604138] pci 0000:00:0c.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.604310] bus 00 -> node 0
[    0.604316] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.604738] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.604899] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.605012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.605125] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[    0.605239] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[    0.605353] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR15._PRT]
[    0.605466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR16._PRT]
[    0.605580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.618990] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *7 10 11 16 17 18 19)
[    0.619253] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.619519] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 *10 11 16 17 18 19)
[    0.619779] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.620065] ACPI: PCI Interrupt Link [LNEA] (IRQs 5 7 10 *11 16 17 18 19)
[    0.620331] ACPI: PCI Interrupt Link [LNEB] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.620592] ACPI: PCI Interrupt Link [LNEC] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.620853] ACPI: PCI Interrupt Link [LNED] (IRQs 5 7 10 11 16 17 18 19) *0, disabled.
[    0.621118] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.621378] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *0, disabled.
[    0.621643] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[    0.621902] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.622166] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.622429] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.622694] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[    0.622958] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *15
[    0.623261] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.623526] ACPI: PCI Interrupt Link [UB11] (IRQs 20 21 22 23) *11
[    0.623786] ACPI: PCI Interrupt Link [UB12] (IRQs 20 21 22 23) *0, disabled.
[    0.624054] ACPI: WMI: Mapper loaded
[    0.624135] SCSI subsystem initialized
[    0.624135] libata version 3.00 loaded.
[    0.624135] usbcore: registered new interface driver usbfs
[    0.624135] usbcore: registered new interface driver hub
[    0.624135] usbcore: registered new device driver usb
[    0.624135] PCI: Using ACPI for IRQ routing
[    0.660008] Bluetooth: Core ver 2.13
[    0.660024] NET: Registered protocol family 31
[    0.660024] Bluetooth: HCI device and connection manager initialized
[    0.660024] Bluetooth: HCI socket layer initialized
[    0.660024] NET: Registered protocol family 8
[    0.660024] NET: Registered protocol family 20
[    0.660031] NetLabel: Initializing
[    0.660032] NetLabel:  domain hash size = 128
[    0.660033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.660047] NetLabel:  unlabeled traffic allowed by default
[    0.660260] AppArmor: AppArmor Filesystem Enabled
[    0.690008] pnp: PnP ACPI init
[    0.690020] ACPI: bus type pnp registered
[    0.694794] pnp: PnP ACPI: found 12 devices
[    0.694796] ACPI: ACPI bus type pnp unregistered
[    0.694807] system 00:04: ioport range 0x4d0-0x4d1 has been reserved
[    0.694809] system 00:04: ioport range 0x800-0x80f has been reserved
[    0.694811] system 00:04: ioport range 0x1000-0x107f has been reserved
[    0.694814] system 00:04: ioport range 0x1080-0x10ff has been reserved
[    0.694816] system 00:04: ioport range 0x1400-0x147f has been reserved
[    0.694819] system 00:04: ioport range 0x1480-0x14ff has been reserved
[    0.694821] system 00:04: ioport range 0x1800-0x187f has been reserved
[    0.694824] system 00:04: ioport range 0x1880-0x18ff has been reserved
[    0.694826] system 00:04: ioport range 0x1c00-0x1c7f has been reserved
[    0.694828] system 00:04: ioport range 0x1c80-0x1cff has been reserved
[    0.694831] system 00:04: iomem range 0xfefe0000-0xfefe01ff has been reserved
[    0.694834] system 00:04: iomem range 0xfefe1000-0xfefe1fff has been reserved
[    0.694836] system 00:04: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.694841] system 00:06: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.694844] system 00:06: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.694849] system 00:09: ioport range 0x290-0x29f has been reserved
[    0.694854] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.694858] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.694861] system 00:0b: iomem range 0xc0000-0xcffff has been reserved
[    0.694863] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.694865] system 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[    0.694868] system 00:0b: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.699581] pci 0000:00:08.0: PCI bridge, secondary bus 0000:01
[    0.699583] pci 0000:00:08.0:   IO window: 0xd000-0xdfff
[    0.699587] pci 0000:00:08.0:   MEM window: 0xfea00000-0xfeafffff
[    0.699590] pci 0000:00:08.0:   PREFETCH window: 0x00000080000000-0x000000800fffff
[    0.699594] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.699596] pci 0000:00:0b.0:   IO window: disabled
[    0.699598] pci 0000:00:0b.0:   MEM window: disabled
[    0.699600] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.699603] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.699605] pci 0000:00:0c.0:   IO window: 0xe000-0xefff
[    0.699611] pci 0000:00:0c.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.699613] pci 0000:00:0c.0:   PREFETCH window: 0x00000080100000-0x000000801fffff
[    0.699616] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.699618] pci 0000:00:0d.0:   IO window: disabled
[    0.699620] pci 0000:00:0d.0:   MEM window: disabled
[    0.699622] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.699625] pci 0000:00:0e.0: PCI bridge, secondary bus 0000:05
[    0.699626] pci 0000:00:0e.0:   IO window: disabled
[    0.699628] pci 0000:00:0e.0:   MEM window: disabled
[    0.699630] pci 0000:00:0e.0:   PREFETCH window: disabled
[    0.699633] pci 0000:00:0f.0: PCI bridge, secondary bus 0000:06
[    0.699635] pci 0000:00:0f.0:   IO window: disabled
[    0.699637] pci 0000:00:0f.0:   MEM window: disabled
[    0.699639] pci 0000:00:0f.0:   PREFETCH window: disabled
[    0.699642] pci 0000:00:10.0: PCI bridge, secondary bus 0000:07
[    0.699643] pci 0000:00:10.0:   IO window: disabled
[    0.699645] pci 0000:00:10.0:   MEM window: disabled
[    0.699647] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.699650] pci 0000:00:11.0: PCI bridge, secondary bus 0000:08
[    0.699652] pci 0000:00:11.0:   IO window: disabled
[    0.699654] pci 0000:00:11.0:   MEM window: disabled
[    0.699656] pci 0000:00:11.0:   PREFETCH window: disabled
[    0.699663] pci 0000:00:08.0: setting latency timer to 64
[    0.699668] pci 0000:00:0b.0: setting latency timer to 64
[    0.699672] pci 0000:00:0c.0: setting latency timer to 64
[    0.699675] pci 0000:00:0d.0: setting latency timer to 64
[    0.699679] pci 0000:00:0e.0: setting latency timer to 64
[    0.699683] pci 0000:00:0f.0: setting latency timer to 64
[    0.699686] pci 0000:00:10.0: setting latency timer to 64
[    0.699690] pci 0000:00:11.0: setting latency timer to 64
[    0.699693] bus: 00 index 0 io port: [0x00-0xffff]
[    0.699695] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.699697] bus: 01 index 0 io port: [0xd000-0xdfff]
[    0.699699] bus: 01 index 1 mmio: [0xfea00000-0xfeafffff]
[    0.699701] bus: 01 index 2 mmio: [0x80000000-0x800fffff]
[    0.699702] bus: 01 index 3 io port: [0x00-0xffff]
[    0.699704] bus: 01 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.699706] bus: 02 index 0 mmio: [0x0-0x0]
[    0.699708] bus: 02 index 1 mmio: [0x0-0x0]
[    0.699709] bus: 02 index 2 mmio: [0x0-0x0]
[    0.699711] bus: 02 index 3 mmio: [0x0-0x0]
[    0.699712] bus: 03 index 0 io port: [0xe000-0xefff]
[    0.699714] bus: 03 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.699716] bus: 03 index 2 mmio: [0x80100000-0x801fffff]
[    0.699717] bus: 03 index 3 mmio: [0x0-0x0]
[    0.699719] bus: 04 index 0 mmio: [0x0-0x0]
[    0.699720] bus: 04 index 1 mmio: [0x0-0x0]
[    0.699722] bus: 04 index 2 mmio: [0x0-0x0]
[    0.699723] bus: 04 index 3 mmio: [0x0-0x0]
[    0.699725] bus: 05 index 0 mmio: [0x0-0x0]
[    0.699726] bus: 05 index 1 mmio: [0x0-0x0]
[    0.699728] bus: 05 index 2 mmio: [0x0-0x0]
[    0.699729] bus: 05 index 3 mmio: [0x0-0x0]
[    0.699731] bus: 06 index 0 mmio: [0x0-0x0]
[    0.699732] bus: 06 index 1 mmio: [0x0-0x0]
[    0.699734] bus: 06 index 2 mmio: [0x0-0x0]
[    0.699735] bus: 06 index 3 mmio: [0x0-0x0]
[    0.699737] bus: 07 index 0 mmio: [0x0-0x0]
[    0.699738] bus: 07 index 1 mmio: [0x0-0x0]
[    0.699739] bus: 07 index 2 mmio: [0x0-0x0]
[    0.699741] bus: 07 index 3 mmio: [0x0-0x0]
[    0.699743] bus: 08 index 0 mmio: [0x0-0x0]
[    0.699744] bus: 08 index 1 mmio: [0x0-0x0]
[    0.699746] bus: 08 index 2 mmio: [0x0-0x0]
[    0.699747] bus: 08 index 3 mmio: [0x0-0x0]
[    0.699758] NET: Registered protocol family 2
[    0.700021] Switched to high resolution mode on CPU 0
[    0.700183] Switched to high resolution mode on CPU 1
[    0.780070] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.780533] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.782483] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.782986] TCP: Hash tables configured (established 262144 bind 65536)
[    0.782989] TCP reno registered
[    0.810126] NET: Registered protocol family 1
[    0.810250] checking if image is initramfs... it is
[    1.393685] Freeing initrd memory: 8301k freed
[    1.398311] audit: initializing netlink socket (disabled)
[    1.398331] type=2000 audit(1241442931.390:1): initialized
[    1.406098] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.407234] VFS: Disk quotas dquot_6.5.1
[    1.407281] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.407841] fuse init (API version 7.10)
[    1.407915] msgmni has been set to 3908
[    1.408112] alg: No test for stdrng (krng)
[    1.408127] io scheduler noop registered
[    1.408129] io scheduler anticipatory registered
[    1.408131] io scheduler deadline registered (default)
[    1.408172] io scheduler cfq registered
[    1.408203] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.408265] pci 0000:00:08.0: Enabling HT MSI Mapping
[    1.408291] pci 0000:00:0a.0: Enabling HT MSI Mapping
[    1.408305] pci 0000:00:0b.0: Enabling HT MSI Mapping
[    1.408319] pci 0000:00:0c.0: Enabling HT MSI Mapping
[    1.408334] pci 0000:00:0d.0: Enabling HT MSI Mapping
[    1.408348] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.408363] pci 0000:00:0f.0: Enabling HT MSI Mapping
[    1.408377] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.408392] pci 0000:00:11.0: Enabling HT MSI Mapping
[    1.408406] pci 0000:00:12.0: Boot video device
[    1.414608] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.414629] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.414645] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    1.414651] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.414663] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.414695] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.414714] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.414725] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    1.414731] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.414741] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.414772] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.414791] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.414802] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X
[    1.414807] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.414817] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.414848] pcieport-driver 0000:00:0e.0: setting latency timer to 64
[    1.414867] pcieport-driver 0000:00:0e.0: found MSI capability
[    1.414877] pcieport-driver 0000:00:0e.0: irq 2300 for MSI/MSI-X
[    1.414883] pci_express 0000:00:0e.0:pcie00: allocate port service
[    1.414893] pci_express 0000:00:0e.0:pcie03: allocate port service
[    1.414924] pcieport-driver 0000:00:0f.0: setting latency timer to 64
[    1.414943] pcieport-driver 0000:00:0f.0: found MSI capability
[    1.414954] pcieport-driver 0000:00:0f.0: irq 2299 for MSI/MSI-X
[    1.414959] pci_express 0000:00:0f.0:pcie00: allocate port service
[    1.414970] pci_express 0000:00:0f.0:pcie03: allocate port service
[    1.415001] pcieport-driver 0000:00:10.0: setting latency timer to 64
[    1.415020] pcieport-driver 0000:00:10.0: found MSI capability
[    1.415030] pcieport-driver 0000:00:10.0: irq 2298 for MSI/MSI-X
[    1.415036] pci_express 0000:00:10.0:pcie00: allocate port service
[    1.415050] pci_express 0000:00:10.0:pcie03: allocate port service
[    1.415080] pcieport-driver 0000:00:11.0: setting latency timer to 64
[    1.415099] pcieport-driver 0000:00:11.0: found MSI capability
[    1.415110] pcieport-driver 0000:00:11.0: irq 2297 for MSI/MSI-X
[    1.415116] pci_express 0000:00:11.0:pcie00: allocate port service
[    1.415126] pci_express 0000:00:11.0:pcie03: allocate port service
[    1.415169] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.415178] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.415298] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.415300] ACPI: Power Button (FF) [PWRF]
[    1.415346] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.415348] ACPI: Power Button (CM) [PWRB]
[    1.415606] processor ACPI_CPU:00: registered as cooling_device0
[    1.415639] processor ACPI_CPU:01: registered as cooling_device1
[    1.491392] Linux agpgart interface v0.103
[    1.491403] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.492255] brd: module loaded
[    1.492536] loop: module loaded
[    1.492602] Fixed MDIO Bus: probed
[    1.492607] PPP generic driver version 2.4.2
[    1.492661] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.492688] Driver 'sd' needs updating - please use bus_type methods
[    1.492696] Driver 'sr' needs updating - please use bus_type methods
[    1.492731] ahci 0000:00:09.0: version 3.0
[    1.493173] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.493184] ahci 0000:00:09.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.493268] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.493271] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pmp pio 
[    1.493274] ahci 0000:00:09.0: setting latency timer to 64
[    1.493687] scsi0 : ahci
[    1.493856] scsi1 : ahci
[    1.493943] scsi2 : ahci
[    1.494046] scsi3 : ahci
[    1.494132] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.494135] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.494137] ata3: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.494140] ata4: SATA max UDMA/133 abar m8192@0xfe97c000 port 0xfe97c280 irq 23
[    2.420032] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.448752] ata1.00: ATA-8: ST31000333AS, CC1H, max UDMA/133
[    2.448754] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.490719] ata1.00: configured for UDMA/133
[    3.420025] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.440559] ata2.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    3.440561] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.442548] ata2.00: configured for UDMA/133
[    4.370024] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.371943] ata3.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    4.371945] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.373933] ata3.00: configured for UDMA/133
[    4.720024] ata4: SATA link down (SStatus 0 SControl 300)
[    4.720111] scsi 0:0:0:0: Direct-Access     ATA      ST31000333AS     CC1H PQ: 0 ANSI: 5
[    4.720196] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.720211] sd 0:0:0:0: [sda] Write Protect is off
[    4.720213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.720240] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.720310] sd 0:0:0:0: [sda] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.720322] sd 0:0:0:0: [sda] Write Protect is off
[    4.720324] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.720343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.720346]  sda: sda1 sda2
[    4.726062] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.726112] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.726163] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    4.726235] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.726247] sd 1:0:0:0: [sdb] Write Protect is off
[    4.726249] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.726268] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.726311] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.726323] sd 1:0:0:0: [sdb] Write Protect is off
[    4.726325] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.726344] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.726347]  sdb: sdb1
[    4.786593] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.786627] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.786676] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[    4.786745] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.786757] sd 2:0:0:0: [sdc] Write Protect is off
[    4.786759] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.786779] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.786818] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[    4.786830] sd 2:0:0:0: [sdc] Write Protect is off
[    4.786832] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.786856] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.786859]  sdc: sdc1
[    4.809565] sd 2:0:0:0: [sdc] Attached SCSI disk
[    4.809595] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.809700] sata_sil24 0000:01:0a.0: version 1.1
[    4.810141] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19
[    4.810152] sata_sil24 0000:01:0a.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, low) -> IRQ 19
[    4.810679] scsi4 : sata_sil24
[    4.810789] scsi5 : sata_sil24
[    4.810861] scsi6 : sata_sil24
[    4.810934] scsi7 : sata_sil24
[    4.810962] ata5: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae0000 irq 19
[    4.810966] ata6: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae2000 irq 19
[    4.810969] ata7: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae4000 irq 19
[    4.810972] ata8: SATA max UDMA/100 host m128@0xfeaefc00 port 0xfeae6000 irq 19
[    7.050036] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    7.058255] ata5.00: ATA-8: SAMSUNG HD501LJ, CR100-10, max UDMA7
[    7.058257] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    7.060261] ata5.00: configured for UDMA/100
[    9.300034] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    9.320583] ata6.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[    9.320585] ata6.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    9.322607] ata6.00: configured for UDMA/100
[   11.410030] ata7: SATA link down (SStatus 0 SControl 0)
[   13.500030] ata8: SATA link down (SStatus 0 SControl 0)
[   13.500116] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   13.500201] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   13.500216] sd 4:0:0:0: [sdd] Write Protect is off
[   13.500218] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   13.500241] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.500305] sd 4:0:0:0: [sdd] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   13.500316] sd 4:0:0:0: [sdd] Write Protect is off
[   13.500318] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   13.500338] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.500342]  sdd: sdd1
[   13.557456] sd 4:0:0:0: [sdd] Attached SCSI disk
[   13.557501] sd 4:0:0:0: Attached scsi generic sg3 type 0
[   13.557554] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   13.557619] sd 5:0:0:0: [sde] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   13.557632] sd 5:0:0:0: [sde] Write Protect is off
[   13.557634] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   13.557654] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.557697] sd 5:0:0:0: [sde] 976773168 512-byte hardware sectors: (500 GB/465 GiB)
[   13.557708] sd 5:0:0:0: [sde] Write Protect is off
[   13.557710] sd 5:0:0:0: [sde] Mode Sense: 00 3a 00 00
[   13.557730] sd 5:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.557733]  sde: sde1
[   13.595618] sd 5:0:0:0: [sde] Attached SCSI disk
[   13.595654] sd 5:0:0:0: Attached scsi generic sg4 type 0
[   13.595783] pata_amd 0000:00:06.0: version 0.3.10
[   13.595826] pata_amd 0000:00:06.0: setting latency timer to 64
[   13.595930] scsi8 : pata_amd
[   13.596010] scsi9 : pata_amd
[   13.597238] ata9: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   13.597241] ata10: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   13.770336] ata9.00: ATAPI: PIONEER DVD-RW  DVR-111, 1.29, max UDMA/66
[   13.770356] ata9: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:900:0x11)
[   13.810332] ata9.00: configured for UDMA/66
[   13.816878] ata10: port disabled. ignoring.
[   13.816906] isa bounce pool size: 16 pages
[   13.823489] scsi 8:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-111  1.29 PQ: 0 ANSI: 5
[   13.846726] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.846729] Uniform CD-ROM driver Revision: 3.20
[   13.846825] sr 8:0:0:0: Attached scsi CD-ROM sr0
[   13.846870] sr 8:0:0:0: Attached scsi generic sg5 type 5
[   13.847244] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   13.847260] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   13.847271] uhci_hcd: USB Universal Host Controller Interface driver
[   13.847307] usbcore: registered new interface driver libusual
[   13.847340] usbcore: registered new interface driver usbserial
[   13.847348] USB Serial support registered for generic
[   13.847357] usbcore: registered new interface driver usbserial_generic
[   13.847360] usbserial: USB Serial Driver core
[   13.847395] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   13.850157] serio: i8042 KBD port at 0x60,0x64 irq 1
[   13.850161] serio: i8042 AUX port at 0x60,0x64 irq 12
[   13.871296] mice: PS/2 mouse device common for all mice
[   13.961316] rtc_cmos 00:05: RTC can wake from S4
[   13.961354] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   13.961388] rtc0: alarms up to one year, y3k, 114 bytes nvram
[   13.961440] device-mapper: uevent: version 1.0.3
[   13.961544] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   13.961682] device-mapper: multipath: version 1.0.5 loaded
[   13.961685] device-mapper: multipath round-robin: version 1.0.0 loaded
[   13.961850] cpuidle: using governor ladder
[   13.961852] cpuidle: using governor menu
[   13.962249] TCP cubic registered
[   13.962317] NET: Registered protocol family 10
[   13.962687] lo: Disabled Privacy Extensions
[   13.962945] NET: Registered protocol family 17
[   13.962966] Bluetooth: L2CAP ver 2.11
[   13.962968] Bluetooth: L2CAP socket layer initialized
[   13.962970] Bluetooth: SCO (Voice Link) ver 0.6
[   13.962972] Bluetooth: SCO socket layer initialized
[   13.963022] Bluetooth: RFCOMM socket layer initialized
[   13.963028] Bluetooth: RFCOMM TTY layer initialized
[   13.963030] Bluetooth: RFCOMM ver 1.10
[   13.963080] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor BE-2350 processors (2 cpu cores) (version 2.20.00)
[   13.963139] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xc
[   13.963142] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[   13.963144] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[   13.963145] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[   13.963295] registered taskstats version 1
[   13.963455]   Magic number: 9:390:280
[   13.963490] tty tty17: hash matches
[   13.963566] rtc_cmos 00:05: setting system clock to 2009-05-04 13:15:44 UTC (1241442944)
[   13.963569] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   13.963570] EDD information not available.
[   13.963613] Freeing unused kernel memory: 536k freed
[   13.963891] Write protecting the kernel read-only data: 6708k
[   13.980430] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   14.101297] md: linear personality registered for level -1
[   14.103603] md: multipath personality registered for level -4
[   14.105607] md: raid0 personality registered for level 0
[   14.108647] md: raid1 personality registered for level 1
[   14.110563] xor: automatically using best checksumming function: generic_sse
[   14.151255]    generic_sse:  6266.800 MB/sec
[   14.151257] xor: using function: generic_sse (6266.800 MB/sec)
[   14.152442] async_tx: api initialized (async)
[   14.321272] raid6: int64x1   1741 MB/s
[   14.491274] raid6: int64x2   2389 MB/s
[   14.661282] raid6: int64x4   1883 MB/s
[   14.831292] raid6: int64x8   1781 MB/s
[   15.001267] raid6: sse2x1    2910 MB/s
[   15.171267] raid6: sse2x2    3904 MB/s
[   15.341265] raid6: sse2x4    4063 MB/s
[   15.341266] raid6: using algorithm sse2x4 (4063 MB/s)
[   15.341270] md: raid6 personality registered for level 6
[   15.341272] md: raid5 personality registered for level 5
[   15.341273] md: raid4 personality registered for level 4
[   15.347733] md: raid10 personality registered for level 10
[   15.452849] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   15.453312] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[   15.453325] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 22 (level, low) -> IRQ 22
[   15.453330] forcedeth 0000:00:0a.0: setting latency timer to 64
[   15.472844] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   15.474221] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 18
[   15.474237] r8169 0000:03:00.0: PCI INT A -> Link[LNEA] -> GSI 18 (level, low) -> IRQ 18
[   15.474255] r8169 0000:03:00.0: setting latency timer to 64
[   15.474346] r8169 0000:03:00.0: irq 2296 for MSI/MSI-X
[   15.474958] eth0: RTL8168b/8111b at 0xffffc2000004a000, 00:21:27:c9:d2:17, XID 38000000 IRQ 2296
[   15.477871] md: bind<sde1>
[   15.486542] md: bind<sdd1>
[   15.500125] md: bind<sdb1>
[   15.503282] md: bind<sdc1>
[   15.504374] md: md0: raid array is not clean -- starting background reconstruction
[   15.510583] raid5: device sdc1 operational as raid disk 1
[   15.510587] raid5: device sdb1 operational as raid disk 0
[   15.510589] raid5: device sdd1 operational as raid disk 2
[   15.510591] raid5: device sde1 operational as raid disk 3
[   15.511971] raid5: allocated 4288kB for md0
[   15.511974] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
[   15.511976] RAID5 conf printout:
[   15.511977]  --- rd:4 wd:4
[   15.511980]  disk 0, o:1, dev:sdb1
[   15.511982]  disk 1, o:1, dev:sdc1
[   15.511983]  disk 2, o:1, dev:sdd1
[   15.511985]  disk 3, o:1, dev:sde1
[   15.512672] md: resync of RAID array md0
[   15.512675] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[   15.512676] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[   15.512683] md: using 128k window, over a total of 488383488 blocks.
[   15.512685] md: resuming resync of md0 from checkpoint.
[   15.694559]  md0: unknown partition table
[   15.981115] forcedeth 0000:00:0a.0: ifname eth1, PHY OUI 0x732 @ 1, addr 00:19:66:51:e4:79
[   15.981120] forcedeth 0000:00:0a.0: highdma pwrctl mgmt timirq lnktim msi desc-v3
[   16.612304] PM: Starting manual resume from disk
[   16.612308] PM: Resume from partition 252:0
[   16.612309] PM: Checking hibernation image.
[   16.612591] PM: Resume from disk failed.
[   16.631738] kjournald starting.  Commit interval 5 seconds
[   16.631753] EXT3-fs: mounted filesystem with ordered data mode.
[   17.696086] udev: starting version 141
[   18.039098] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   18.157707] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   19.186614] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   19.505560] lp: driver loaded but no devices found
[   19.694801] Adding 1048568k swap on /dev/mapper/single-swap.  Priority:-1 extents:1 across:1048568k
[   20.025631] EXT3 FS on dm-1, internal journal
[   22.068024] kjournald starting.  Commit interval 5 seconds
[   22.068527] EXT3 FS on sda1, internal journal
[   22.068535] EXT3-fs: mounted filesystem with ordered data mode.
[   22.247168] kjournald starting.  Commit interval 5 seconds
[   22.287626] EXT3 FS on dm-3, internal journal
[   22.287634] EXT3-fs: mounted filesystem with ordered data mode.
[   22.316499] kjournald starting.  Commit interval 5 seconds
[   22.317538] EXT3 FS on dm-2, internal journal
[   22.317546] EXT3-fs: mounted filesystem with ordered data mode.
[   22.676212] type=1505 audit(1241442953.207:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2044
[   22.676367] type=1505 audit(1241442953.207:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2044
[   22.676418] type=1505 audit(1241442953.207:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2044
[   22.676465] type=1505 audit(1241442953.207:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2044
[   22.721033] type=1505 audit(1241442953.247:6): operation="profile_load" name="/usr/sbin/dhcpd3" name2="default" pid=2049
[   22.751803] type=1505 audit(1241442953.287:7): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2053
[   22.782706] type=1505 audit(1241442953.317:8): operation="profile_load" name="/usr/sbin/named" name2="default" pid=2057
[   22.814186] type=1505 audit(1241442953.347:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2061
[   22.933559] forcedeth 0000:00:0a.0: irq 2295 for MSI/MSI-X
[   23.223047] Bridge firewalling registered
[   23.236164] device eth0 entered promiscuous mode
[   23.242919] r8169: eth0: link up
[   23.242929] r8169: eth0: link up
[   23.258725] br0: port 1(eth0) entering learning state
[   23.337817] NET: Registered protocol family 24
[   24.191590] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.680016] eth0: no IPv6 routers present
[   33.791267] eth1: no IPv6 routers present
[   34.110014] br0: no IPv6 routers present
[   38.250016] br0: topology change detected, propagating
[   38.250024] br0: port 1(eth0) entering forwarding state
[   38.425772] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   38.426028] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   38.426030] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   38.426031] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   38.726646] RPC: Registered udp transport module.
[   38.726649] RPC: Registered tcp transport module.
[   38.801155] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   46.612184] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   46.618133] NFSD: starting 90-second grace period
[   47.565451] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
[  111.690845] Clocksource tsc unstable (delta = -215107045 ns)
```

---

### Post by colinrotherham on 2009-05-18
This is also affecting me.

I've just installed Ubuntu Server 9.04 with no modifications to menu.lst and I'm getting the same problem. Recovery menu at every boot.

---

### Post by infirmus on 2009-06-11
I have still got no idea what is causing this. Can someone please help.

---

### Post by infirmus on 2009-06-11
OK I found the problem I think.

It's because my kernel command line is (from /proc/cmdline)
```
root=/dev/mapper/single-rootfs ro quiet splash
```

and the code that runs the recovery menu is /etc/event.d/rc-default contains a line which says
```
if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
```

which puts the system into single user mode if "single" is found in the cmdline. If the system is in single user mode then the recovery mode comes up.

---

