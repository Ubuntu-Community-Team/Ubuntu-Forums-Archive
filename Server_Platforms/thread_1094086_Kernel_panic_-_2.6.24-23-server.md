---
title: "Kernel panic - 2.6.24-23-server"
date: 2009-03-12
forum: Server Platforms
---

### Post by Scormen on 2009-03-12
Hi all,

I'm having since a hour a problem with my Ubuntu 8.04.2 amd64 server installation. On this server is a DHCP, webserver and proxy server installed.
When a client tries to connect to a external FTP server, the local server crashes with a "kernel panic - not syncing aiee".

I have already tried booting with "acpi=off", but that doesn't help.

The server is a Dell R300.

Here is the dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@crested) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 01:36:05 UTC 2009 (Ubuntu 2.6.24-23.48-server)
[    0.000000] Command line: root=/dev/md3 ro quiet splash acpi=off
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007faa0000 (usable)
[    0.000000]  BIOS-e820: 000000007faa0000 - 000000007fab6000 (reserved)
[    0.000000]  BIOS-e820: 000000007fab6000 - 000000007fad5c00 (ACPI data)
[    0.000000]  BIOS-e820: 000000007fad5c00 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 522912) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.5 present.
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007faa0000
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 522912) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007faa0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      160
[    0.000000]     0:      256 ->   522912
[    0.000000] On node 0 totalpages: 522816
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1324 pages reserved
[    0.000000]   DMA zone: 2620 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7093 pages used for memmap
[    0.000000]   DMA32 zone: 511723 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000] MPTABLE: OEM ID: DELL     MPTABLE: Product ID: PE 020F      MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #2
[    0.000000] Processor #3
[    0.000000] Processor #1
[    0.000000] I/O APIC #4 at 0xFEC00000.
[    0.000000] Setting APIC routing to flat
[    0.000000] Processors: 4
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 41952 bytes of per cpu data
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 514343
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: root=/dev/md3 ro quiet splash acpi=off
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC calibrated against PIT
[    0.000000] time.c: Detected 2833.371 MHz processor.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Checking aperture...
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2049440k/2091648k available (2526k kernel code, 41824k reserved, 1329k data, 328k init)
[    0.000000] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=4, Nodes=1
[    0.000000] Calibrating delay using timer specific routine.. 5669.91 BogoMIPS (lpj=28349570)
[    0.000000] Security Framework initialized
[    0.000000] SELinux:  Disabled at boot.
[    0.000000] AppArmor: AppArmor initialized
[    0.000000] Failure registering capabilities with primary security module.
[    0.000000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.000000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.000000] Mount-cache hash table entries: 256
[    0.000000] Initializing cgroup subsys ns
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 6144K
[    0.000000] CPU 0/0 -> Node 0
[    0.000000] using mwait in idle threads.
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 0
[    0.000000] CPU0: Thermal monitoring enabled (TM1)
[    0.000000] SMP alternatives: switching to UP code
[    0.000000] Early unpacking initramfs... done
[    0.000000] ExtINT not setup in hardware but reported by MP table
[    0.000000] Using local APIC timer interrupts.
[    0.000000] APIC timer calibration result 20833606
[    0.000000] Detected 20.833 MHz APIC timer.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 1/4 APIC 0x2
[    0.000000] Initializing CPU#1
[    0.000000] Calibrating delay using timer specific routine.. 5666.79 BogoMIPS (lpj=28333990)
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 6144K
[    0.000000] CPU 1/2 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 2
[    0.000000] CPU1: Thermal monitoring enabled (TM1)
[    0.000000] Intel(R) Xeon(R) CPU           X3363  @ 2.83GHz stepping 0a
[    0.000000] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 2/4 APIC 0x3
[    0.000000] Initializing CPU#2
[    0.000000] Calibrating delay using timer specific routine.. 5666.83 BogoMIPS (lpj=28334195)
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 6144K
[    0.000000] CPU 2/3 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 3
[    0.000000] CPU2: Thermal monitoring enabled (TM1)
[    0.000000] Intel(R) Xeon(R) CPU           X3363  @ 2.83GHz stepping 0a
[    0.000000] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.000000] SMP alternatives: switching to SMP code
[    0.000000] Booting processor 3/4 APIC 0x1
[    0.000000] Initializing CPU#3
[    0.000000] Calibrating delay using timer specific routine.. 5666.78 BogoMIPS (lpj=28333908)
[    0.000000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000000] CPU: L2 cache: 6144K
[    0.000000] CPU 3/1 -> Node 0
[    0.000000] CPU: Physical Processor ID: 0
[    0.000000] CPU: Processor Core ID: 1
[    0.000000] CPU3: Thermal monitoring enabled (TM1)
[    0.000000] Intel(R) Xeon(R) CPU           X3363  @ 2.83GHz stepping 0a
[    0.000000] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.000000] Brought up 4 CPUs
[    0.000000] CPU0 attaching sched-domain:
[    0.000000]  domain 0: span 00000000,00000009
[    0.000000]   groups: 00000000,00000001 00000000,00000008
[    0.000000]   domain 1: span 00000000,0000000f
[    0.000000]    groups: 00000000,00000009 00000000,00000006
[    0.000000]    domain 2: span 00000000,0000000f
[    0.000000]     groups: 00000000,0000000f
[    0.000000] CPU1 attaching sched-domain:
[    0.000000]  domain 0: span 00000000,00000006
[    0.000000]   groups: 00000000,00000002 00000000,00000004
[    0.000000]   domain 1: span 00000000,0000000f
[    0.000000]    groups: 00000000,00000006 00000000,00000009
[    0.000000]    domain 2: span 00000000,0000000f
[    0.000000]     groups: 00000000,0000000f
[    0.000000] CPU2 attaching sched-domain:
[    0.000000]  domain 0: span 00000000,00000006
[    0.000000]   groups: 00000000,00000004 00000000,00000002
[    0.000000]   domain 1: span 00000000,0000000f
[    0.000000]    groups: 00000000,00000006 00000000,00000009
[    0.000000]    domain 2: span 00000000,0000000f
[    0.000000]     groups: 00000000,0000000f
[    0.000000] CPU3 attaching sched-domain:
[    0.000000]  domain 0: span 00000000,00000009
[    0.000000]   groups: 00000000,00000008 00000000,00000001
[    0.000000]   domain 1: span 00000000,0000000f
[    0.000000]    groups: 00000000,00000009 00000000,00000006
[    0.000000]    domain 2: span 00000000,0000000f
[    0.000000]     groups: 00000000,0000000f
[    0.000000] net_namespace: 120 bytes
[    0.000000] Time: 13:33:17  Date: 03/12/09
[    0.000000] NET: Registered protocol family 16
[    0.000000] PCI: Using configuration type 1
[    0.000000] ACPI: Interpreter disabled.
[    0.000000] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.000000] pnp: PnP ACPI: disabled
[    0.000000] PCI: Probing PCI hardware
[    0.000000] PCI: Probing PCI hardware (bus 00)
[    0.000000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.000000] PCI quirk: region 0880-08bf claimed by ICH6 GPIO
[    0.000000] PCI: Transparent bridge - 0000:00:1e.0
[    0.000000] PCI: Using IRQ router default [8086/2916] at 0000:00:1f.0
[    0.000000] PCI->APIC IRQ transform: 0000:00:00.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:02.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:04.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:06.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:1c.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:1c.4[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:00:1c.5[B] -> IRQ 17
[    0.000000] PCI->APIC IRQ transform: 0000:00:1d.0[A] -> IRQ 21
[    0.000000] PCI->APIC IRQ transform: 0000:00:1d.1[B] -> IRQ 20
[    0.000000] PCI->APIC IRQ transform: 0000:00:1d.2[C] -> IRQ 21
[    0.000000] PCI->APIC IRQ transform: 0000:00:1d.7[A] -> IRQ 21
[    0.000000] PCI->APIC IRQ transform: 0000:00:1f.2[C] -> IRQ 23
[    0.000000] PCI->APIC IRQ transform: 0000:00:1f.5[D] -> IRQ 22
[    0.000000] PCI->APIC IRQ transform: 0000:05:00.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:07:00.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 16
[    0.000000] PCI->APIC IRQ transform: 0000:02:00.0[A] -> IRQ 17
[    0.000000] PCI->APIC IRQ transform: 0000:0a:07.0[A] -> IRQ 19
[    0.000000] NET: Registered protocol family 8
[    0.000000] NET: Registered protocol family 20
[    0.000000] NetLabel: Initializing
[    0.000000] NetLabel:  domain hash size = 128
[    0.000000] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.000000] NetLabel:  unlabeled traffic allowed by default
[    0.000000] PCI-GART: No AMD northbridge found.
[    0.000000] AppArmor: AppArmor Filesystem Enabled
[    0.000000] PCI: Bridge: 0000:00:02.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:03.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:04.0
[    0.000000]   IO window: e000-efff
[    0.000000]   MEM window: dfa00000-dfbfffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:05.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:06.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: dfc00000-dfcfffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:07.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:1c.0
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: disabled.
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:1c.4
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: dfd00000-dfdfffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:1c.5
[    0.000000]   IO window: disabled.
[    0.000000]   MEM window: dfe00000-dfefffff
[    0.000000]   PREFETCH window: disabled.
[    0.000000] PCI: Bridge: 0000:00:1e.0
[    0.000000]   IO window: d000-dfff
[    0.000000]   MEM window: dff00000-dfffffff
[    0.000000]   PREFETCH window: d0000000-d7ffffff
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.000000] NET: Registered protocol family 2
[    0.000000] Time: tsc clocksource has been installed.
[    0.000000] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.000000] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.000000] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.000000] TCP: Hash tables configured (established 262144 bind 65536)
[    0.000000] TCP reno registered
[    0.000000] checking if image is initramfs... it is
[    0.000000] Freeing initrd memory: 7613k freed
[    0.000000] audit: initializing netlink socket (disabled)
[    0.000000] audit(1236864796.689:1): initialized
[    0.000000] Total HugeTLB memory allocated, 0
[    0.000000] VFS: Disk quotas dquot_6.5.1
[    0.000000] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.000000] io scheduler noop registered
[    0.000000] io scheduler anticipatory registered
[    0.000000] io scheduler deadline registered (default)
[    0.000000] io scheduler cfq registered
[    0.000000] Boot video device is 0000:0a:07.0
[    0.000000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:02.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:03.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:03.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:04.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:05.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:06.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:07.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:07.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.000000] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.000000] assign_interrupt_mode Found MSI capability
[    0.000000] Allocate Port Service[0000:00:1c.5:pcie00]
[    0.000000] Real Time Clock Driver v1.12ac
[    0.000000] Linux agpgart interface v0.102
[    0.000000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.000000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.000000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.000000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.000000] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.000000] PNP: No PS/2 controller found. Probing ports directly.
[    0.000000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.000000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.000000] mice: PS/2 mouse device common for all mice
[    0.000000] cpuidle: using governor ladder
[    0.000000] cpuidle: using governor menu
[    0.000000] NET: Registered protocol family 1
[    0.000000] registered taskstats version 1
[    0.000000]   Magic number: 1:290:584
[    0.000000]   hash matches device ptyc2
[    0.000000] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[    0.000000] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[    0.000000] Freeing unused kernel memory: 328k freed
[    0.000000] Write protecting the kernel read-only data: 1044k
[    0.000000] fuse init (API version 7.9)
[    0.000000] thermal: Unknown symbol acpi_processor_set_thermal_limit
[    0.000000] md: linear personality registered for level -1
[    0.000000] md: multipath personality registered for level -4
[    0.000000] md: raid0 personality registered for level 0
[    0.000000] md: raid1 personality registered for level 1
[    0.000000] xor: automatically using best checksumming function: generic_sse
[    0.000000]    generic_sse: 10834.400 MB/sec
[    0.000000] xor: using function: generic_sse (10834.400 MB/sec)
[    0.000000] async_tx: api initialized (async)
[    0.000000] raid6: int64x1   2507 MB/s
[    0.000000] raid6: int64x2   3181 MB/s
[    0.000000] raid6: int64x4   3276 MB/s
[    0.000000] raid6: int64x8   2617 MB/s
[    0.000000] raid6: sse2x1    3845 MB/s
[    0.000000] raid6: sse2x2    7944 MB/s
[    0.000000] raid6: sse2x4    8807 MB/s
[    0.000000] raid6: using algorithm sse2x4 (8807 MB/s)
[    0.000000] md: raid6 personality registered for level 6
[    0.000000] md: raid5 personality registered for level 5
[    0.000000] md: raid4 personality registered for level 4
[    0.000000] md: raid10 personality registered for level 10
[    0.000000] SCSI subsystem initialized
[    0.000000] Fusion MPT base driver 3.04.06
[    0.000000] Copyright (c) 1999-2007 LSI Corporation
[    0.000000] Fusion MPT SAS Host driver 3.04.06
[    0.000000] mptbase: ioc0: Initiating bringup
[    0.000000] usbcore: registered new interface driver usbfs
[    0.000000] usbcore: registered new interface driver hub
[    0.000000] usbcore: registered new device driver usb
[    0.000000] libata version 3.00 loaded.
[    0.000000] USB Universal Host Controller Interface driver v3.0
[    0.000000] ioc0: LSISAS1068E B3: Capabilities={Initiator}
[    0.000000] PCI: Setting latency timer of device 0000:05:00.0 to 64
[    0.000000] scsi0 : ioc0: LSISAS1068E B3, FwRev=00192f00h, Ports=1, MaxQ=266, IRQ=16
[    0.000000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HE160HJ  0-24 PQ: 0 ANSI: 5
[    0.000000] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG HE160HJ  0-24 PQ: 0 ANSI: 5
[    0.000000] tg3.c:v3.86 (November 9, 2007)
[    0.000000] PCI: Setting latency timer of device 0000:07:00.0 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    0.000000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.000000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.000000] ehci_hcd 0000:00:1d.7: debug port 1
[    0.000000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    0.000000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xdf9ffc00
[    0.000000] Driver 'sd' needs updating - please use bus_type methods
[    0.000000] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[    0.000000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    0.000000] usb usb1: configuration #1 chosen from 1 choice
[    0.000000] hub 1-0:1.0: USB hub found
[    0.000000] hub 1-0:1.0: 6 ports detected
[    0.000000] eth0: Tigon3 [partno(BCM95722A2202G) rev a200 PHY(5722/5756)] (PCI Express) 10/100/1000Base-T Ethernet 00:10:18:32:1f:da
[    0.000000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[    0.000000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    0.000000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[    0.000000] eth1: Tigon3 [partno(BCM95722) rev a200 PHY(5722/5756)] (PCI Express) 10/100/1000Base-T Ethernet 00:22:19:aa:c6:3b
[    0.000000] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] WireSpeed[1] TSOcap[1]
[    0.000000] eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[    0.000000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 0:0:0:0: [sda] 312500000 512-byte hardware sectors (160000 MB)
[    0.000000] eth2: Tigon3 [partno(BCM95722) rev a200 PHY(5722/5756)] (PCI Express) 10/100/1000Base-T Ethernet 00:22:19:aa:c6:3c
[    0.000000] eth2: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] WireSpeed[1] TSOcap[1]
[    0.000000] eth2: dma_rwctrl[76180000] dma_mask[64-bit]
[    0.000000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    0.000000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.000000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000cc80
[    0.000000] usb usb2: configuration #1 chosen from 1 choice
[    0.000000] hub 2-0:1.0: USB hub found
[    0.000000] hub 2-0:1.0: 2 ports detected
[    0.000000] sd 0:0:0:0: [sda] Write Protect is off
[    0.000000] sd 0:0:0:0: [sda] Mode Sense: 73 00 00 08
[    0.000000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    0.000000] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.000000] sd 0:0:1:0: [sdb] 312500000 512-byte hardware sectors (160000 MB)
[    0.000000] sd 0:0:1:0: [sdb] Write Protect is off
[    0.000000] sd 0:0:1:0: [sdb] Mode Sense: 73 00 00 08
[    0.000000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000] sd 0:0:1:0: [sdb] 312500000 512-byte hardware sectors (160000 MB)
[    0.000000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    0.000000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.000000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000cca0
[    0.000000] usb usb3: configuration #1 chosen from 1 choice
[    0.000000] hub 3-0:1.0: USB hub found
[    0.000000] hub 3-0:1.0: 2 ports detected
[    0.000000] sd 0:0:1:0: [sdb] Write Protect is off
[    0.000000] sd 0:0:1:0: [sdb] Mode Sense: 73 00 00 08
[    0.000000] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.000000]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 sdb6 >
[    0.000000] sd 0:0:1:0: [sdb] Attached SCSI disk
[    0.000000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.000000] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.000000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    0.000000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.000000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.000000] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000ccc0
[    0.000000] usb usb4: configuration #1 chosen from 1 choice
[    0.000000] hub 4-0:1.0: USB hub found
[    0.000000] hub 4-0:1.0: 2 ports detected
[    0.000000] usb 1-5: new high speed USB device using ehci_hcd and address 2
[    0.000000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.000000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    0.000000] ata_piix 0000:00:1f.2: version 2.12
[    0.000000] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.000000] md: md0 stopped.
[    0.000000] usb 1-5: configuration #1 chosen from 1 choice
[    0.000000] hub 1-5:1.0: USB hub found
[    0.000000] hub 1-5:1.0: 2 ports detected
[    0.000000] md: bind<sdb2>
[    0.000000] md: md1 stopped.
[    0.000000] md: bind<sdb3>
[    0.000000] md: md2 stopped.
[    0.000000] md: bind<sdb5>
[    0.000000] md: md3 stopped.
[    0.000000] md: md0 stopped.
[    0.000000] md: unbind<sdb2>
[    0.000000] md: export_rdev(sdb2)
[    0.000000] md: bind<sdb2>
[    0.000000] md: bind<sda2>
[    0.000000] md0: setting max_sectors to 128, segment boundary to 32767
[    0.000000] raid0: looking at sda2
[    0.000000] raid0:   comparing sda2(489856) with sda2(489856)
[    0.000000] raid0:   END
[    0.000000] raid0:   ==> UNIQUE
[    0.000000] raid0: 1 zones
[    0.000000] raid0: looking at sdb2
[    0.000000] raid0:   comparing sdb2(489856) with sda2(489856)
[    0.000000] raid0:   EQUAL
[    0.000000] raid0: FINAL 1 zones
[    0.000000] raid0: done.
[    0.000000] raid0 : md_size is 979712 blocks.
[    0.000000] raid0 : conf->hash_spacing is 979712 blocks.
[    0.000000] raid0 : nb_zone is 1.
[    0.000000] raid0 : Allocating 8 bytes for hash.
[    0.000000] md: md1 stopped.
[    0.000000] md: unbind<sdb3>
[    0.000000] md: export_rdev(sdb3)
[    0.000000] md: bind<sdb3>
[    0.000000] md: bind<sda3>
[    0.000000] md1: setting max_sectors to 128, segment boundary to 32767
[    0.000000] raid0: looking at sda3
[    0.000000] raid0:   comparing sda3(1951808) with sda3(1951808)
[    0.000000] raid0:   END
[    0.000000] raid0:   ==> UNIQUE
[    0.000000] raid0: 1 zones
[    0.000000] raid0: looking at sdb3
[    0.000000] raid0:   comparing sdb3(1951808) with sda3(1951808)
[    0.000000] raid0:   EQUAL
[    0.000000] raid0: FINAL 1 zones
[    0.000000] raid0: done.
[    0.000000] raid0 : md_size is 3903616 blocks.
[    0.000000] raid0 : conf->hash_spacing is 3903616 blocks.
[    0.000000] raid0 : nb_zone is 1.
[    0.000000] raid0 : Allocating 8 bytes for hash.
[    0.000000] md: md2 stopped.
[    0.000000] md: unbind<sdb5>
[    0.000000] md: export_rdev(sdb5)
[    0.000000] md: bind<sdb5>
[    0.000000] md: bind<sda5>
[    0.000000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    0.000000] scsi1 : ata_piix
[    0.000000] scsi2 : ata_piix
[    0.000000] ata1: SATA max UDMA/133 cmd 0xcc20 ctl 0xcc10 bmdma 0xcc40 irq 23
[    0.000000] ata2: SATA max UDMA/133 cmd 0xcc28 ctl 0xcc14 bmdma 0xcc48 irq 23
[    0.000000] md2: setting max_sectors to 128, segment boundary to 32767
[    0.000000] raid0: looking at sda5
[    0.000000] raid0:   comparing sda5(489856) with sda5(489856)
[    0.000000] raid0:   END
[    0.000000] raid0:   ==> UNIQUE
[    0.000000] raid0: 1 zones
[    0.000000] raid0: looking at sdb5
[    0.000000] raid0:   comparing sdb5(489856) with sda5(489856)
[    0.000000] raid0:   EQUAL
[    0.000000] raid0: FINAL 1 zones
[    0.000000] raid0: done.
[    0.000000] raid0 : md_size is 979712 blocks.
[    0.000000] raid0 : conf->hash_spacing is 979712 blocks.
[    0.000000] raid0 : nb_zone is 1.
[    0.000000] raid0 : Allocating 8 bytes for hash.
[    0.000000] md: md3 stopped.
[    0.000000] md: bind<sdb6>
[    0.000000] md: bind<sda6>
[    0.000000] md3: setting max_sectors to 128, segment boundary to 32767
[    0.000000] raid0: looking at sda6
[    0.000000] raid0:   comparing sda6(153123392) with sda6(153123392)
[    0.000000] raid0:   END
[    0.000000] raid0:   ==> UNIQUE
[    0.000000] raid0: 1 zones
[    0.000000] raid0: looking at sdb6
[    0.000000] raid0:   comparing sdb6(153123392) with sda6(153123392)
[    0.000000] raid0:   EQUAL
[    0.000000] raid0: FINAL 1 zones
[    0.000000] raid0: done.
[    0.000000] raid0 : md_size is 306246784 blocks.
[    0.000000] raid0 : conf->hash_spacing is 306246784 blocks.
[    0.000000] raid0 : nb_zone is 1.
[    0.000000] raid0 : Allocating 8 bytes for hash.
[    0.000000] ata1.01: ATAPI: HL-DT-STCD-RW/DVD-ROM GCC-T20N, A107, max UDMA/33
[    0.000000] usb 1-5.2: new low speed USB device using ehci_hcd and address 3
[    0.000000] usb 1-5.2: configuration #1 chosen from 1 choice
[    0.000000] usbcore: registered new interface driver hiddev
[    0.000000] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.2/1-5.2:1.0/input/input1
[    0.000000] ata1.01: configured for UDMA/33
[    0.000000] input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1d.7-5.2
[    0.000000] usbcore: registered new interface driver usbhid
[    0.000000] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[    0.000000] scsi 1:0:1:0: CD-ROM            HL-DT-ST CDRW/DVD GCCT20N A107 PQ: 0 ANSI: 5
[    0.000000] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[    0.000000] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    0.000000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[    0.000000] scsi3 : ata_piix
[    0.000000] scsi4 : ata_piix
[    0.000000] ata3: SATA max UDMA/133 cmd 0xcc30 ctl 0xcc18 bmdma 0xcc60 irq 22
[    0.000000] ata4: SATA max UDMA/133 cmd 0xcc38 ctl 0xcc1c bmdma 0xcc68 irq 22
[    0.000000] Driver 'sr' needs updating - please use bus_type methods
[    0.000000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.000000] Uniform CD-ROM driver Revision: 3.20
[    0.000000] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    0.000000] Attempting manual resume
[    0.000000] swsusp: Resume From Partition 9:1
[    0.000000] PM: Checking swsusp image.
[    0.000000] PM: Resume from disk failed.
[    0.000000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    0.000000] EXT3-fs: write access will be enabled during recovery.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3-fs: recovery complete.
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.000000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    0.000000] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    0.000000] iTCO_vendor_support: vendor-support=0
[    0.000000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[    0.000000] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0860)
[    0.000000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    0.000000] input: PC Speaker as /devices/platform/pcspkr/input/input2
[    0.000000] NET: Registered protocol family 10
[    0.000000] lo: Disabled Privacy Extensions
[    0.000000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    0.000000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    0.000000] loop: module loaded
[    0.000000] lp: driver loaded but no devices found
[    0.000000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[    0.000000] tg3: eth0: Flow control is on for TX and on for RX.
[    0.000000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    0.000000] tg3: eth1: Link is up at 100 Mbps, full duplex.
[    0.000000] tg3: eth1: Flow control is on for TX and on for RX.
[    0.000000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[    0.000000] Adding 3903608k swap on /dev/md1.  Priority:-1 extents:1 across:3903608k
[    0.000000] EXT3 FS on md3, internal journal
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3 FS on sda1, internal journal
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3 FS on md0, internal journal
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] kjournald starting.  Commit interval 5 seconds
[    0.000000] EXT3 FS on md2, internal journal
[    0.000000] EXT3-fs: mounted filesystem with ordered data mode.
[    0.000000] eth1: no IPv6 routers present
[    0.000000] eth0: no IPv6 routers present
[    0.000000] ip_tables: (C) 2000-2006 Netfilter Core Team
[    0.000000] NET: Registered protocol family 17
[    0.000000] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[    0.000000] nf_nat_ftp: kernel >= 2.6.10 only uses 'ports' for conntrack modules
[    0.000000] IN=eth1 OUT= MAC=00:22:19:aa:c6:3b:00:1b:24:b1:e8:87:08:00 SRC=192.168.2.200 DST=192.168.2.1 LEN=64 TOS=0x10 PREC=0x00 TTL=64 ID=47218 DF PROTO=TCP SPT=41044 DPT=22 WINDOW=95 RES=0x00 ACK URGP=0 
[    0.000000] IN=eth1 OUT= MAC=00:22:19:aa:c6:3b:00:1b:24:b1:e8:87:08:00 SRC=192.168.2.200 DST=192.168.2.1 LEN=100 TOS=0x10 PREC=0x00 TTL=64 ID=47219 DF PROTO=TCP SPT=41044 DPT=22 WINDOW=95 RES=0x00 ACK PSH URGP=0 
[    0.000000] IN=eth1 OUT= MAC=00:22:19:aa:c6:3b:00:1b:24:b1:e8:87:08:00 SRC=192.168.2.200 DST=192.168.2.1 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=47220 DF PROTO=TCP SPT=41044 DPT=22 WINDOW=95 RES=0x00 ACK URGP=0 
[    0.000000] IN=eth1 OUT= MAC=00:22:19:aa:c6:3b:00:1b:24:b1:e8:87:08:00 SRC=192.168.2.200 DST=192.168.2.1 LEN=100 TOS=0x10 PREC=0x00 TTL=64 ID=47221 DF PROTO=TCP SPT=41044 DPT=22 WINDOW=95 RES=0x00 ACK PSH URGP=0 
[    0.000000] IN=eth1 OUT= MAC=00:22:19:aa:c6:3b:00:1b:24:b1:e8:87:08:00 SRC=192.168.2.200 DST=192.168.2.1 LEN=52 TOS=0x10 PREC=0x00 TTL=64 ID=47222 DF PROTO=TCP SPT=41044 DPT=22 WINDOW=95 RES=0x00 ACK URGP=0 
```

Any ideas?

Thanks.

---

### Post by ptn107 on 2009-03-12
Can you also confirm this on 2.6.24-22?

---

### Post by Scormen on 2009-03-13
I have installed "linux-image-2.6.24-22-server_2.6.24-22.44".
But... Just the same problem happend.

I don't have the time to clear this out, sorry. I will backup all my files and go for a reinstallation.

On this system I had installed:
- Apache, MySQL, PHP,...
- Postfix
- ProFTP
- Courier
- Squid
- Frox (FTP cache, after this, it went wrong. Deinstall didn't help)

On the previous installation (Ubuntu server 7.10) there was no problem. All packages were installed via apt-get.

But, thanks for your help.

---

### Post by Scormen on 2009-03-18
Hi all,

Like I said in my previous post, I have done a reinstallation of the system (Ubuntu server amd64 8.04.2).

But I get this problem again after a 20 min of working. I think I have found the culprit: lm-sensors.

I only installed these packages at this moment: apache, bind9, squid3 and lm-senors.

lm-sensors is the only one from the 4 installed programs that has something "to do" with the kernel.

Is it possible that lm-sensors the problem is?

I'm running this on a Dell R300.

---

### Post by lykwydchykyn on 2009-03-18
It's possible the kernel modules for the sensors are crashing the kernel, but I couldn't say for sure.

If removing lm-sensors doesn't fix it, I'd recommend going through the BIOS and disabling hardware you don't plan to use and features that seem potentially troublesome (like processor frequency scaling, etc).

I'd also recommend upgrading the BIOS to the latest if it isn't already.  You can do this through apt for some models, check here:
[http://linux.dell.com/wiki/index.php/Repository/firmware](http://linux.dell.com/wiki/index.php/Repository/firmware)

---

### Post by regala on 2009-03-18
> 

Any ideas?

Thanks.

Can you post the backtrace that is printed on the console when the kernel panics ? It would be more helpful than trying to guess what's gone berserk.

simply getting the backtrace (the list of symbols printed) not all the address stuff would be very welcome :)

-- 
Mathieu

---

