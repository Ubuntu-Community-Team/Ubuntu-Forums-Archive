---
title: "System hanging up... no clue what is going on... here is my log"
date: 2009-08-06
forum: Server Platforms
---

### Post by gilligan8 on 2009-08-06
Ok... I'm running 8.04 server and have had pretty much ZERO problems with it for a LONG time (uptime had to have been close to a year).  

Out of the blue I decided to check some disk usage on my raid 5 (software) and it seemed to be taking a while... I didn't think much of it as I knew it was a large directory.  Then the wife started complaining she couldn't save her photoshop file to the server and had to save it locally.  I thought it was just her pc or photoshop.  Then I looked back at my system and the du -hs was STILL going... well.. it was frozen.

I could launch another putty and get the MOTD but it would stop at the logging in.  I hooked up a keyboard and monitor to the box and it had some errors but wouldn't respond.  I hit CTR+ALT+DEL and it recognized I did that but wouldn't actually reboot.

I had to shut it down the hard way.

I bring it back up and everything seems ok except that my raid didn't come back up... ok, I'm a little nervous, that's a lot of data.  So I mdadm --assemble the array and everything looks fine.  I try to xfs_check and it complains that the logs aren't right and I should mount and then umount it.  So I did, then I hit xfs_check /dev/md0 again... it drops to the next line and there is no progress or data.  I looked at the HD lights and they were going crazy so I figured it was just the way xfs_check worked (maybe I forgot the --progress switch or something).  Well, after a while I look and no lights and the same errors (see below).  It was frozen again.

Restart it and run a memtest on it and everything looks fine.  I don't mess with the raid and it is still up and running.  Obviously the raid is the most important but I don't want to play with it and take the chance of corrupting anything.

Here is kern.log... any ideas... I got nothing (it looked like memory but that is checking out ok).

```
Aug  6 17:43:35 FileServer kernel: Inspecting /boot/System.map-2.6.24-24-server
Aug  6 17:43:35 FileServer kernel: Loaded 28777 symbols from /boot/System.map-2.6.24-24-server.
Aug  6 17:43:35 FileServer kernel: Symbols match kernel version 2.6.24.
Aug  6 17:43:35 FileServer kernel: Loaded 17660 symbols from 65 modules.
Aug  6 17:43:35 FileServer kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug  6 17:43:35 FileServer kernel: [    0.000000] Initializing cgroup subsys cpu
Aug  6 17:43:35 FileServer kernel: [    0.000000] Linux version 2.6.24-24-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Tue Jun 30 21:03:25 UTC 2009 (Ubuntu 2.6.24-24.55-server)
Aug  6 17:43:35 FileServer kernel: [    0.000000] BIOS-provided physical RAM map:
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fe70000 (usable)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 000000001fe70000 - 000000001fe72000 (ACPI NVS)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 000000001fe72000 - 000000001fe93000 (ACPI data)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 000000001fe93000 - 000000001ff00000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000fecf0000 - 00000000fecf1000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Aug  6 17:43:35 FileServer kernel: [    0.000000] 0MB HIGHMEM available.
Aug  6 17:43:35 FileServer kernel: [    0.000000] 510MB LOWMEM available.
Aug  6 17:43:35 FileServer kernel: [    0.000000] found SMP MP-table at 000fe710
Aug  6 17:43:35 FileServer kernel: [    0.000000] Entering add_active_range(0, 0, 130672) 0 entries of 256 used
Aug  6 17:43:35 FileServer kernel: [    0.000000] Zone PFN ranges:
Aug  6 17:43:35 FileServer kernel: [    0.000000]   DMA             0 ->     4096
Aug  6 17:43:35 FileServer kernel: [    0.000000]   Normal       4096 ->   130672
Aug  6 17:43:35 FileServer kernel: [    0.000000]   HighMem    130672 ->   130672
Aug  6 17:43:35 FileServer kernel: [    0.000000] Movable zone start PFN for each node
Aug  6 17:43:35 FileServer kernel: [    0.000000] early_node_map[1] active PFN ranges
Aug  6 17:43:35 FileServer kernel: [    0.000000]     0:        0 ->   130672
Aug  6 17:43:35 FileServer kernel: [    0.000000] On node 0 totalpages: 130672
Aug  6 17:43:35 FileServer kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Aug  6 17:43:35 FileServer kernel: [    0.000000]   DMA zone: 0 pages reserved
Aug  6 17:43:35 FileServer kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Aug  6 17:43:35 FileServer kernel: [    0.000000]   Normal zone: 988 pages used for memmap
Aug  6 17:43:35 FileServer kernel: [    0.000000]   Normal zone: 125588 pages, LIFO batch:31
Aug  6 17:43:35 FileServer kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Aug  6 17:43:35 FileServer kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Aug  6 17:43:35 FileServer kernel: [    0.000000] DMI 2.3 present.
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: RSDP signature @ 0xC00FEBA0 checksum 0
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: RSDP 000FEBA0, 0014 (r0 DELL  )
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: RSDT 000FD18C, 0038 (r1 DELL    GX270          7 ASL        61)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: FACP 000FD1C4, 0074 (r1 DELL    GX270          7 ASL        61)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: DSDT FFFD3216, 2795 (r1   DELL    dt_ex     1000 MSFT  100000D)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: FACS 1FE70000, 0040
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: SSDT FFFD5AE8, 00BA (r1   DELL    st_ex     1000 MSFT  100000D)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: APIC 000FD238, 006C (r1 DELL    GX270          7 ASL        61)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: BOOT 000FD2A4, 0028 (r1 DELL    GX270          7 ASL        61)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: ASF! 000FD2CC, 0067 (r16 DELL    GX270          7 ASL        61)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Aug  6 17:43:35 FileServer kernel: [    0.000000] Processor #0 15:2 APIC version 20
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Aug  6 17:43:35 FileServer kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: IRQ0 used by override.
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: IRQ2 used by override.
Aug  6 17:43:35 FileServer kernel: [    0.000000] ACPI: IRQ9 used by override.
Aug  6 17:43:35 FileServer kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Aug  6 17:43:35 FileServer kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Aug  6 17:43:35 FileServer kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1ff00000:ded00000)
Aug  6 17:43:35 FileServer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Aug  6 17:43:35 FileServer kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Aug  6 17:43:35 FileServer kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129652
Aug  6 17:43:35 FileServer kernel: [    0.000000] Kernel command line: root=UUID=ac5cd99f-1cd7-4b54-b6ad-15926b998e9f ro quiet splash
Aug  6 17:43:35 FileServer kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Aug  6 17:43:35 FileServer kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Aug  6 17:43:35 FileServer kernel: [    0.000000] Enabling fast FPU save and restore... done.
Aug  6 17:43:35 FileServer kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Aug  6 17:43:35 FileServer kernel: [    0.000000] Initializing CPU#0
Aug  6 17:43:35 FileServer kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Aug  6 17:43:35 FileServer kernel: [    0.000000] Detected 2992.873 MHz processor.
Aug  6 17:43:35 FileServer kernel: [   13.701655] Console: colour VGA+ 80x25
Aug  6 17:43:35 FileServer kernel: [   13.701659] console [tty0] enabled
Aug  6 17:43:35 FileServer kernel: [   13.701862] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Aug  6 17:43:35 FileServer kernel: [   13.702054] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Aug  6 17:43:35 FileServer kernel: [   13.710632] Memory: 505832k/522688k available (2258k kernel code, 16240k reserved, 1037k data, 384k init, 0k highmem)
Aug  6 17:43:35 FileServer kernel: [   13.710642] virtual kernel memory layout:
Aug  6 17:43:35 FileServer kernel: [   13.710643]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Aug  6 17:43:35 FileServer kernel: [   13.710644]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Aug  6 17:43:35 FileServer kernel: [   13.710645]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
Aug  6 17:43:35 FileServer kernel: [   13.710646]     lowmem  : 0xc0000000 - 0xdfe70000   ( 510 MB)
Aug  6 17:43:35 FileServer kernel: [   13.710647]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
Aug  6 17:43:35 FileServer kernel: [   13.710648]       .data : 0xc0334af9 - 0xc0437fe4   (1037 kB)
Aug  6 17:43:35 FileServer kernel: [   13.710649]       .text : 0xc0100000 - 0xc0334af9   (2258 kB)
Aug  6 17:43:35 FileServer kernel: [   13.710652] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Aug  6 17:43:35 FileServer kernel: [   13.710685] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Aug  6 17:43:35 FileServer kernel: [   13.860634] Calibrating delay using timer specific routine.. 5989.17 BogoMIPS (lpj=29945856)
Aug  6 17:43:35 FileServer kernel: [   13.860656] Security Framework initialized
Aug  6 17:43:35 FileServer kernel: [   13.860662] SELinux:  Disabled at boot.
Aug  6 17:43:35 FileServer kernel: [   13.860676] AppArmor: AppArmor initialized
Aug  6 17:43:35 FileServer kernel: [   13.860679] Failure registering capabilities with primary security module.
Aug  6 17:43:35 FileServer kernel: [   13.860687] Mount-cache hash table entries: 512
Aug  6 17:43:35 FileServer kernel: [   13.860801] Initializing cgroup subsys ns
Aug  6 17:43:35 FileServer kernel: [   13.860805] Initializing cgroup subsys cpuacct
Aug  6 17:43:35 FileServer kernel: [   13.860816] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
Aug  6 17:43:35 FileServer kernel: [   13.860828] CPU: Trace cache: 12K uops, L1 D cache: 8K
Aug  6 17:43:35 FileServer kernel: [   13.860831] CPU: L2 cache: 512K
Aug  6 17:43:35 FileServer kernel: [   13.860833] CPU: Hyper-Threading is disabled
Aug  6 17:43:35 FileServer kernel: [   13.860836] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043080 00004400 00000000 00000000 00000000
Aug  6 17:43:35 FileServer kernel: [   13.860846] Compat vDSO mapped to ffffe000.
Aug  6 17:43:35 FileServer kernel: [   13.860858] Checking 'hlt' instruction... OK.
Aug  6 17:43:35 FileServer kernel: [   13.900970] SMP alternatives: switching to UP code
Aug  6 17:43:35 FileServer kernel: [   13.902326] Freeing SMP alternatives: 12k freed
Aug  6 17:43:35 FileServer kernel: [   13.902442] Early unpacking initramfs... done
Aug  6 17:43:35 FileServer kernel: [   14.175630] ACPI: Core revision 20070126
Aug  6 17:43:35 FileServer kernel: [   14.187850] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Aug  6 17:43:35 FileServer kernel: [   14.211025] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
Aug  6 17:43:35 FileServer kernel: [   14.211056] Total of 1 processors activated (5989.17 BogoMIPS).
Aug  6 17:43:35 FileServer kernel: [   14.211182] ENABLING IO-APIC IRQs
Aug  6 17:43:35 FileServer kernel: [   14.211352] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Aug  6 17:43:35 FileServer kernel: [   14.430417] Brought up 1 CPUs
Aug  6 17:43:35 FileServer kernel: [   14.430435] CPU0 attaching sched-domain:
Aug  6 17:43:35 FileServer kernel: [   14.430438]  domain 0: span 01
Aug  6 17:43:35 FileServer kernel: [   14.430440]   groups: 01
Aug  6 17:43:35 FileServer kernel: [   14.430612] net_namespace: 64 bytes
Aug  6 17:43:35 FileServer kernel: [   14.430624] Booting paravirtualized kernel on bare hardware
Aug  6 17:43:35 FileServer kernel: [   14.431124] Time: 22:41:22  Date: 08/06/09
Aug  6 17:43:35 FileServer kernel: [   14.431149] NET: Registered protocol family 16
Aug  6 17:43:35 FileServer kernel: [   14.431354] EISA bus registered
Aug  6 17:43:35 FileServer kernel: [   14.431378] ACPI: bus type pci registered
Aug  6 17:43:35 FileServer kernel: [   14.431534] PCI: PCI BIOS revision 2.10 entry at 0xfbaaa, last bus=1
Aug  6 17:43:35 FileServer kernel: [   14.431536] PCI: Using configuration type 1
Aug  6 17:43:35 FileServer kernel: [   14.431554] Setting up standard PCI resources
Aug  6 17:43:35 FileServer kernel: [   14.437938] ACPI: EC: Look up EC in DSDT
Aug  6 17:43:35 FileServer kernel: [   14.463665] ACPI: Interpreter enabled
Aug  6 17:43:35 FileServer kernel: [   14.463669] ACPI: (supports S0 S1 S3 S4 S5)
Aug  6 17:43:35 FileServer kernel: [   14.463684] ACPI: Using IOAPIC for interrupt routing
Aug  6 17:43:35 FileServer kernel: [   14.488126] ACPI: PCI Root Bridge [PCI0] (0000:00)
Aug  6 17:43:35 FileServer kernel: [   14.488591] HPET at base address 0xfed00000
Aug  6 17:43:35 FileServer kernel: [   14.488598] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
Aug  6 17:43:35 FileServer kernel: [   14.488601] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
Aug  6 17:43:35 FileServer kernel: [   14.488909] PCI: Transparent bridge - 0000:00:1e.0
Aug  6 17:43:35 FileServer kernel: [   14.488930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Aug  6 17:43:35 FileServer kernel: [   14.489329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Aug  6 17:43:35 FileServer kernel: [   14.580102] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
Aug  6 17:43:35 FileServer kernel: [   14.580400] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 9 10 11 12 15)
Aug  6 17:43:35 FileServer kernel: [   14.580684] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
Aug  6 17:43:35 FileServer kernel: [   14.580968] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
Aug  6 17:43:35 FileServer kernel: [   14.581251] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  6 17:43:35 FileServer kernel: [   14.581537] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  6 17:43:35 FileServer kernel: [   14.581821] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
Aug  6 17:43:35 FileServer kernel: [   14.582106] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 9 10 11 12 15)
Aug  6 17:43:35 FileServer kernel: [   14.582321] Linux Plug and Play Support v0.97 (c) Adam Belay
Aug  6 17:43:35 FileServer kernel: [   14.582355] pnp: PnP ACPI init
Aug  6 17:43:35 FileServer kernel: [   14.582365] ACPI: bus type pnp registered
Aug  6 17:43:35 FileServer kernel: [   14.608027] pnp: PnP ACPI: found 10 devices
Aug  6 17:43:35 FileServer kernel: [   14.608030] ACPI: ACPI bus type pnp unregistered
Aug  6 17:43:35 FileServer kernel: [   14.608034] PnPBIOS: Disabled by ACPI PNP
Aug  6 17:43:35 FileServer kernel: [   14.608293] PCI: Using ACPI for IRQ routing
Aug  6 17:43:35 FileServer kernel: [   14.608297] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Aug  6 17:43:35 FileServer kernel: [   14.640300] NET: Registered protocol family 8
Aug  6 17:43:35 FileServer kernel: [   14.640303] NET: Registered protocol family 20
Aug  6 17:43:35 FileServer kernel: [   14.640338] NetLabel: Initializing
Aug  6 17:43:35 FileServer kernel: [   14.640340] NetLabel:  domain hash size = 128
Aug  6 17:43:35 FileServer kernel: [   14.640341] NetLabel:  protocols = UNLABELED CIPSOv4
Aug  6 17:43:35 FileServer kernel: [   14.640353] NetLabel:  unlabeled traffic allowed by default
Aug  6 17:43:35 FileServer kernel: [   14.640434] hpet clockevent registered
Aug  6 17:43:35 FileServer kernel: [   14.640439] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Aug  6 17:43:35 FileServer kernel: [   14.640443] hpet0: 3 64-bit timers, 14318180 Hz
Aug  6 17:43:35 FileServer kernel: [   14.641486] AppArmor: AppArmor Filesystem Enabled
Aug  6 17:43:35 FileServer kernel: [   14.650272] Time: tsc clocksource has been installed.
Aug  6 17:43:35 FileServer kernel: [   14.670311] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670314] system 00:00: iomem range 0x100000-0xffffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670317] system 00:00: iomem range 0x1000000-0x1fe6ffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670320] system 00:00: iomem range 0xc0000-0xfffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670323] system 00:00: iomem range 0xfec00000-0xfec0ffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670326] system 00:00: iomem range 0xfee00000-0xfee0ffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670329] system 00:00: iomem range 0xfed20000-0xfed8ffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670331] system 00:00: iomem range 0xfecf0000-0xfecf0fff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670334] system 00:00: iomem range 0xffb00000-0xffbfffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670337] system 00:00: iomem range 0xffc00000-0xffffffff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.670349] system 00:09: ioport range 0x800-0x85f has been reserved
Aug  6 17:43:35 FileServer kernel: [   14.670352] system 00:09: ioport range 0xc00-0xc7f has been reserved
Aug  6 17:43:35 FileServer kernel: [   14.670355] system 00:09: ioport range 0x860-0x8ff could not be reserved
Aug  6 17:43:35 FileServer kernel: [   14.700800] PCI: Bridge: 0000:00:1e.0
Aug  6 17:43:35 FileServer kernel: [   14.700805]   IO window: d000-dfff
Aug  6 17:43:35 FileServer kernel: [   14.700810]   MEM window: fe900000-feafffff
Aug  6 17:43:35 FileServer kernel: [   14.700814]   PREFETCH window: disabled.
Aug  6 17:43:35 FileServer kernel: [   14.700826] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Aug  6 17:43:35 FileServer kernel: [   14.700839] NET: Registered protocol family 2
Aug  6 17:43:35 FileServer kernel: [   14.800277] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Aug  6 17:43:35 FileServer kernel: [   14.800500] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Aug  6 17:43:35 FileServer kernel: [   14.800560] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Aug  6 17:43:35 FileServer kernel: [   14.800619] TCP: Hash tables configured (established 16384 bind 16384)
Aug  6 17:43:35 FileServer kernel: [   14.800621] TCP reno registered
Aug  6 17:43:35 FileServer kernel: [   14.830311] checking if image is initramfs... it is
Aug  6 17:43:35 FileServer kernel: [   15.150048] Switched to high resolution mode on CPU 0
Aug  6 17:43:35 FileServer kernel: [   15.363568] Freeing initrd memory: 7439k freed
Aug  6 17:43:35 FileServer kernel: [   15.363727] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
Aug  6 17:43:35 FileServer kernel: [   15.363729] Simple Boot Flag at 0x7a set to 0x1
Aug  6 17:43:35 FileServer kernel: [   15.364139] audit: initializing netlink socket (disabled)
Aug  6 17:43:35 FileServer kernel: [   15.364152] audit(1249598482.540:1): initialized
Aug  6 17:43:35 FileServer kernel: [   15.364303] Total HugeTLB memory allocated, 0
Aug  6 17:43:35 FileServer kernel: [   15.366206] VFS: Disk quotas dquot_6.5.1
Aug  6 17:43:35 FileServer kernel: [   15.366287] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Aug  6 17:43:35 FileServer kernel: [   15.366483] io scheduler noop registered
Aug  6 17:43:35 FileServer kernel: [   15.366486] io scheduler anticipatory registered
Aug  6 17:43:35 FileServer kernel: [   15.366488] io scheduler deadline registered (default)
Aug  6 17:43:35 FileServer kernel: [   15.366502] io scheduler cfq registered
Aug  6 17:43:35 FileServer kernel: [   15.366514] Boot video device is 0000:00:02.0
Aug  6 17:43:35 FileServer kernel: [   15.366856] isapnp: Scanning for PnP cards...
Aug  6 17:43:35 FileServer kernel: [   15.723412] isapnp: No Plug & Play device found
Aug  6 17:43:35 FileServer kernel: [   15.754265] Real Time Clock Driver v1.12ac
Aug  6 17:43:35 FileServer kernel: [   15.754351] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Aug  6 17:43:35 FileServer kernel: [   15.754460] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  6 17:43:35 FileServer kernel: [   15.755198] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Aug  6 17:43:35 FileServer kernel: [   15.755980] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Aug  6 17:43:35 FileServer kernel: [   15.756048] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Aug  6 17:43:35 FileServer kernel: [   15.756193] PNP: No PS/2 controller found. Probing ports directly.
Aug  6 17:43:35 FileServer kernel: [   15.758733] serio: i8042 KBD port at 0x60,0x64 irq 1
Aug  6 17:43:35 FileServer kernel: [   15.758738] serio: i8042 AUX port at 0x60,0x64 irq 12
Aug  6 17:43:35 FileServer kernel: [   15.770209] mice: PS/2 mouse device common for all mice
Aug  6 17:43:35 FileServer kernel: [   15.770332] EISA: Probing bus 0 at eisa.0
Aug  6 17:43:35 FileServer kernel: [   15.770367] EISA: Detected 0 cards.
Aug  6 17:43:35 FileServer kernel: [   15.770370] cpuidle: using governor ladder
Aug  6 17:43:35 FileServer kernel: [   15.770372] cpuidle: using governor menu
Aug  6 17:43:35 FileServer kernel: [   15.770459] NET: Registered protocol family 1
Aug  6 17:43:35 FileServer kernel: [   15.770488] Using IPI No-Shortcut mode
Aug  6 17:43:35 FileServer kernel: [   15.770517] registered taskstats version 1
Aug  6 17:43:35 FileServer kernel: [   15.770617]   Magic number: 5:928:703
Aug  6 17:43:35 FileServer kernel: [   15.770730] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Aug  6 17:43:35 FileServer kernel: [   15.771228] Freeing unused kernel memory: 384k freed
Aug  6 17:43:35 FileServer kernel: [   15.771265] Write protecting the kernel read-only data: 828k
Aug  6 17:43:35 FileServer kernel: [   15.938376] fuse init (API version 7.9)
Aug  6 17:43:35 FileServer kernel: [   15.956355] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
Aug  6 17:43:35 FileServer kernel: [   15.971210] md: linear personality registered for level -1
Aug  6 17:43:35 FileServer kernel: [   15.975086] md: multipath personality registered for level -4
Aug  6 17:43:35 FileServer kernel: [   15.978770] md: raid0 personality registered for level 0
Aug  6 17:43:35 FileServer kernel: [   15.983430] md: raid1 personality registered for level 1
Aug  6 17:43:35 FileServer kernel: [   15.987013] xor: automatically using best checksumming function: pIII_sse
Aug  6 17:43:35 FileServer kernel: [   16.029668]    pIII_sse  :  3830.800 MB/sec
Aug  6 17:43:35 FileServer kernel: [   16.029671] xor: using function: pIII_sse (3830.800 MB/sec)
Aug  6 17:43:35 FileServer kernel: [   16.030428] async_tx: api initialized (async)
Aug  6 17:43:35 FileServer kernel: [   16.199632] raid6: int32x1    747 MB/s
Aug  6 17:43:35 FileServer kernel: [   16.369570] raid6: int32x2    942 MB/s
Aug  6 17:43:35 FileServer kernel: [   16.539446] raid6: int32x4   1162 MB/s
Aug  6 17:43:35 FileServer kernel: [   16.709386] raid6: int32x8    696 MB/s
Aug  6 17:43:35 FileServer kernel: [   16.879315] raid6: mmxx1     2488 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.049225] raid6: mmxx2     3156 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.219148] raid6: sse1x1    1464 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.389070] raid6: sse1x2    2738 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.558999] raid6: sse2x1    2129 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.728922] raid6: sse2x2    3376 MB/s
Aug  6 17:43:35 FileServer kernel: [   17.728924] raid6: using algorithm sse2x2 (3376 MB/s)
Aug  6 17:43:35 FileServer kernel: [   17.728928] md: raid6 personality registered for level 6
Aug  6 17:43:35 FileServer kernel: [   17.728929] md: raid5 personality registered for level 5
Aug  6 17:43:35 FileServer kernel: [   17.728931] md: raid4 personality registered for level 4
Aug  6 17:43:35 FileServer kernel: [   17.752368] md: raid10 personality registered for level 10
Aug  6 17:43:35 FileServer kernel: [   18.128907] usbcore: registered new interface driver usbfs
Aug  6 17:43:35 FileServer kernel: [   18.128934] usbcore: registered new interface driver hub
Aug  6 17:43:35 FileServer kernel: [   18.136564] usbcore: registered new device driver usb
Aug  6 17:43:35 FileServer kernel: [   18.148482] USB Universal Host Controller Interface driver v3.0
Aug  6 17:43:35 FileServer kernel: [   18.148550] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
Aug  6 17:43:35 FileServer kernel: [   18.148562] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Aug  6 17:43:35 FileServer kernel: [   18.148565] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Aug  6 17:43:35 FileServer kernel: [   18.148859] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
Aug  6 17:43:35 FileServer kernel: [   18.148887] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000ff80
Aug  6 17:43:35 FileServer kernel: [   18.149024] usb usb1: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   18.149048] hub 1-0:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   18.149054] hub 1-0:1.0: 2 ports detected
Aug  6 17:43:35 FileServer kernel: [   18.186386] SCSI subsystem initialized
Aug  6 17:43:35 FileServer kernel: [   18.219192] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Aug  6 17:43:35 FileServer kernel: [   18.219196] Copyright (c) 1999-2006 Intel Corporation.
Aug  6 17:43:35 FileServer kernel: [   18.229056] libata version 3.00 loaded.
Aug  6 17:43:35 FileServer kernel: [   18.258822] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
Aug  6 17:43:35 FileServer kernel: [   18.258835] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Aug  6 17:43:35 FileServer kernel: [   18.258839] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Aug  6 17:43:35 FileServer kernel: [   18.258862] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
Aug  6 17:43:35 FileServer kernel: [   18.258887] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ff60
Aug  6 17:43:35 FileServer kernel: [   18.258995] usb usb2: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   18.259022] hub 2-0:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   18.259028] hub 2-0:1.0: 2 ports detected
Aug  6 17:43:35 FileServer kernel: [   18.312496] FDC 0 is a post-1991 82077
Aug  6 17:43:35 FileServer kernel: [   18.368785] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Aug  6 17:43:35 FileServer kernel: [   18.368798] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Aug  6 17:43:35 FileServer kernel: [   18.368802] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Aug  6 17:43:35 FileServer kernel: [   18.368826] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
Aug  6 17:43:35 FileServer kernel: [   18.368851] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000ff40
Aug  6 17:43:35 FileServer kernel: [   18.368969] usb usb3: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   18.368999] hub 3-0:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   18.369005] hub 3-0:1.0: 2 ports detected
Aug  6 17:43:35 FileServer kernel: [   18.478702] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 16
Aug  6 17:43:35 FileServer kernel: [   18.478715] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Aug  6 17:43:35 FileServer kernel: [   18.478719] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Aug  6 17:43:35 FileServer kernel: [   18.478742] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
Aug  6 17:43:35 FileServer kernel: [   18.478764] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000ff20
Aug  6 17:43:35 FileServer kernel: [   18.478875] usb usb4: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   18.478900] hub 4-0:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   18.478905] hub 4-0:1.0: 2 ports detected
Aug  6 17:43:35 FileServer kernel: [   18.538588] usb 1-1: new full speed USB device using uhci_hcd and address 2
Aug  6 17:43:35 FileServer kernel: [   18.588919] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
Aug  6 17:43:35 FileServer kernel: [   18.588934] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Aug  6 17:43:35 FileServer kernel: [   18.588937] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Aug  6 17:43:35 FileServer kernel: [   18.588971] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
Aug  6 17:43:35 FileServer kernel: [   18.592892] ehci_hcd 0000:00:1d.7: debug port 1
Aug  6 17:43:35 FileServer kernel: [   18.592898] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
Aug  6 17:43:35 FileServer kernel: [   18.592907] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xffa80800
Aug  6 17:43:35 FileServer kernel: [   18.678517] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Aug  6 17:43:35 FileServer kernel: [   18.678652] usb usb5: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   18.678678] hub 5-0:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   18.678684] hub 5-0:1.0: 8 ports detected
Aug  6 17:43:35 FileServer kernel: [   18.788683] ACPI: PCI Interrupt 0000:01:0c.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug  6 17:43:35 FileServer kernel: [   19.036875] e1000: 0000:01:0c.0: e1000_probe: (PCI:33MHz:32-bit) 00:0d:56:f1:2a:e8
Aug  6 17:43:35 FileServer kernel: [   19.118109] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Aug  6 17:43:35 FileServer kernel: [   19.118238] sata_via 0000:01:09.0: version 2.3
Aug  6 17:43:35 FileServer kernel: [   19.118257] ACPI: PCI Interrupt 0000:01:09.0[A] -> GSI 18 (level, low) -> IRQ 18
Aug  6 17:43:35 FileServer kernel: [   19.118339] sata_via 0000:01:09.0: routed to hard irq line 9
Aug  6 17:43:35 FileServer kernel: [   19.123125] scsi0 : sata_via
Aug  6 17:43:35 FileServer kernel: [   19.124244] scsi1 : sata_via
Aug  6 17:43:35 FileServer kernel: [   19.124315] scsi2 : sata_via
Aug  6 17:43:35 FileServer kernel: [   19.124346] ata1: SATA max UDMA/133 port i16@0xdd60 bmdma 0xdda0 irq 18
Aug  6 17:43:35 FileServer kernel: [   19.124349] ata2: SATA max UDMA/133 port i16@0xdd70 bmdma 0xdda8 irq 18
Aug  6 17:43:35 FileServer kernel: [   19.124351] ata3: PATA max UDMA/133 port i16@0xdd80 bmdma 0xddb0 irq 18
Aug  6 17:43:35 FileServer kernel: [   19.248253] usb 1-1: device not accepting address 2, error -71
Aug  6 17:43:35 FileServer kernel: [   19.588105] usb 5-1: new high speed USB device using ehci_hcd and address 2
Aug  6 17:43:35 FileServer kernel: [   19.608158] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug  6 17:43:35 FileServer kernel: [   19.636631] ata1.00: ATA-7: WDC WD5000AAJS-00TKA0, 12.01C01, max UDMA/133
Aug  6 17:43:35 FileServer kernel: [   19.636634] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
Aug  6 17:43:35 FileServer kernel: [   19.669265] ata1.00: configured for UDMA/133
Aug  6 17:43:35 FileServer kernel: [   19.746800] usb 5-1: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   19.747092] hub 5-1:1.0: USB hub found
Aug  6 17:43:35 FileServer kernel: [   19.747216] hub 5-1:1.0: 3 ports detected
Aug  6 17:43:35 FileServer kernel: [   20.097971] usb 5-1.2: new low speed USB device using ehci_hcd and address 3
Aug  6 17:43:35 FileServer kernel: [   20.157871] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Aug  6 17:43:35 FileServer kernel: [   20.184886] ata2.00: ATA-8: WDC WD5000AAJS-22YFA0, 12.01C02, max UDMA/133
Aug  6 17:43:35 FileServer kernel: [   20.184889] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
Aug  6 17:43:35 FileServer kernel: [   20.214488] usb 5-1.2: configuration #1 chosen from 1 choice
Aug  6 17:43:35 FileServer kernel: [   20.219150] ata2.00: configured for UDMA/133
Aug  6 17:43:35 FileServer kernel: [   20.235115] usbcore: registered new interface driver hiddev
Aug  6 17:43:35 FileServer kernel: [   20.238396] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/5-1.2/5-1.2:1.0/input/input1
Aug  6 17:43:35 FileServer kernel: [   20.257921] input,hidraw0: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-1.2
Aug  6 17:43:35 FileServer kernel: [   20.261178] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/5-1.2/5-1.2:1.1/input/input2
Aug  6 17:43:35 FileServer kernel: [   20.287844] input,hidraw1: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-1.2
Aug  6 17:43:35 FileServer kernel: [   20.287863] usbcore: registered new interface driver usbhid
Aug  6 17:43:35 FileServer kernel: [   20.287867] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug  6 17:43:35 FileServer kernel: [   20.389253] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 12.0 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   20.389682] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-2 12.0 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   20.393981] ata_piix 0000:00:1f.1: version 2.12
Aug  6 17:43:35 FileServer kernel: [   20.393999] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
Aug  6 17:43:35 FileServer kernel: [   20.394038] PCI: Setting latency timer of device 0000:00:1f.1 to 64
Aug  6 17:43:35 FileServer kernel: [   20.395786] scsi3 : ata_piix
Aug  6 17:43:35 FileServer kernel: [   20.396273] scsi4 : ata_piix
Aug  6 17:43:35 FileServer kernel: [   20.396318] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Aug  6 17:43:35 FileServer kernel: [   20.396321] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Aug  6 17:43:35 FileServer kernel: [   20.402905] Driver 'sd' needs updating - please use bus_type methods
Aug  6 17:43:35 FileServer kernel: [   20.402992] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   20.403006] sd 0:0:0:0: [sda] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   20.403009] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   20.403028] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   20.403077] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   20.403088] sd 0:0:0:0: [sda] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   20.403091] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   20.403110] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   20.403115]  sda: sda1
Aug  6 17:43:35 FileServer kernel: [   20.408433] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  6 17:43:35 FileServer kernel: [   20.408498] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   20.408512] sd 1:0:0:0: [sdb] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   20.408515] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   20.408534] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   20.408589] sd 1:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   20.408601] sd 1:0:0:0: [sdb] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   20.408603] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   20.408622] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   20.408625]  sdb: sdb1
Aug  6 17:43:35 FileServer kernel: [   20.413349] sd 1:0:0:0: [sdb] Attached SCSI disk
Aug  6 17:43:35 FileServer kernel: [   20.419839] sd 0:0:0:0: Attached scsi generic sg0 type 0
Aug  6 17:43:35 FileServer kernel: [   20.419861] sd 1:0:0:0: Attached scsi generic sg1 type 0
Aug  6 17:43:35 FileServer kernel: [   20.628118] ata4.00: ATA-6: ST380011A, 8.16, max UDMA/100
Aug  6 17:43:35 FileServer kernel: [   20.628123] ata4.00: 156250000 sectors, multi 8: LBA48 
Aug  6 17:43:35 FileServer kernel: [   20.668027] ata4.00: configured for UDMA/100
Aug  6 17:43:35 FileServer kernel: [   21.007745] ata5.00: ATAPI: HL-DT-STDVD-ROM GDR8162B, 0015, max UDMA/33
Aug  6 17:43:35 FileServer kernel: [   21.207585] ata5.00: configured for UDMA/33
Aug  6 17:43:35 FileServer kernel: [   21.207701] scsi 3:0:0:0: Direct-Access     ATA      ST380011A        8.16 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   21.208075] sd 3:0:0:0: [sdc] 156250000 512-byte hardware sectors (80000 MB)
Aug  6 17:43:35 FileServer kernel: [   21.208089] sd 3:0:0:0: [sdc] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.208092] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.208111] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.208163] sd 3:0:0:0: [sdc] 156250000 512-byte hardware sectors (80000 MB)
Aug  6 17:43:35 FileServer kernel: [   21.208174] sd 3:0:0:0: [sdc] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.208176] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.208194] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.208198]  sdc: sdc1 sdc2 sdc3
Aug  6 17:43:35 FileServer kernel: [   21.239675] sd 3:0:0:0: [sdc] Attached SCSI disk
Aug  6 17:43:35 FileServer kernel: [   21.239714] sd 3:0:0:0: Attached scsi generic sg2 type 0
Aug  6 17:43:35 FileServer kernel: [   21.246217] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVD-ROM GDR8162B 0015 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   21.246291] scsi 4:0:0:0: Attached scsi generic sg3 type 5
Aug  6 17:43:35 FileServer kernel: [   21.246314] ata_piix 0000:00:1f.2: MAP [ P0 -- P1 -- ]
Aug  6 17:43:35 FileServer kernel: [   21.246331] ACPI: PCI Interrupt 0000:00:1f.2[A] -> GSI 18 (level, low) -> IRQ 18
Aug  6 17:43:35 FileServer kernel: [   21.246367] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Aug  6 17:43:35 FileServer kernel: [   21.246761] scsi5 : ata_piix
Aug  6 17:43:35 FileServer kernel: [   21.246930] scsi6 : ata_piix
Aug  6 17:43:35 FileServer kernel: [   21.246966] ata6: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 18
Aug  6 17:43:35 FileServer kernel: [   21.246969] ata7: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 18
Aug  6 17:43:35 FileServer kernel: [   21.428888] ata6.00: ATA-8: WDC WD5000AAJS-22YFA0, 12.01C02, max UDMA/133
Aug  6 17:43:35 FileServer kernel: [   21.428893] ata6.00: 976773168 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  6 17:43:35 FileServer kernel: [   21.468649] ata6.00: configured for UDMA/133
Aug  6 17:43:35 FileServer kernel: [   21.652849] ata7.00: ATA-7: WDC WD5000AAJS-00TKA0, 12.01C01, max UDMA/133
Aug  6 17:43:35 FileServer kernel: [   21.652853] ata7.00: 976773168 sectors, multi 8: LBA48 NCQ (depth 0/32)
Aug  6 17:43:35 FileServer kernel: [   21.687987] ata7.00: configured for UDMA/133
Aug  6 17:43:35 FileServer kernel: [   21.688107] scsi 5:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-2 12.0 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   21.688494] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   21.688508] sd 5:0:0:0: [sdd] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.688511] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.688529] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.688581] sd 5:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   21.688592] sd 5:0:0:0: [sdd] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.688595] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.688613] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.688616]  sdd: sdd1
Aug  6 17:43:35 FileServer kernel: [   21.698780] sd 5:0:0:0: [sdd] Attached SCSI disk
Aug  6 17:43:35 FileServer kernel: [   21.698819] sd 5:0:0:0: Attached scsi generic sg4 type 0
Aug  6 17:43:35 FileServer kernel: [   21.699383] scsi 6:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 12.0 PQ: 0 ANSI: 5
Aug  6 17:43:35 FileServer kernel: [   21.699718] sd 6:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   21.699731] sd 6:0:0:0: [sde] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.699734] sd 6:0:0:0: [sde] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.699752] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.699800] sd 6:0:0:0: [sde] 976773168 512-byte hardware sectors (500108 MB)
Aug  6 17:43:35 FileServer kernel: [   21.699811] sd 6:0:0:0: [sde] Write Protect is off
Aug  6 17:43:35 FileServer kernel: [   21.699814] sd 6:0:0:0: [sde] Mode Sense: 00 3a 00 00
Aug  6 17:43:35 FileServer kernel: [   21.699832] sd 6:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  6 17:43:35 FileServer kernel: [   21.699836]  sde: sde1
Aug  6 17:43:35 FileServer kernel: [   21.708347] sd 6:0:0:0: [sde] Attached SCSI disk
Aug  6 17:43:35 FileServer kernel: [   21.708382] sd 6:0:0:0: Attached scsi generic sg5 type 0
Aug  6 17:43:35 FileServer kernel: [   21.732363] Driver 'sr' needs updating - please use bus_type methods
Aug  6 17:43:35 FileServer kernel: [   21.763344] sr0: scsi3-mmc drive: 20x/48x cd/rw xa/form2 cdda tray
Aug  6 17:43:35 FileServer kernel: [   21.763349] Uniform CD-ROM driver Revision: 3.20
Aug  6 17:43:35 FileServer kernel: [   21.763405] sr 4:0:0:0: Attached scsi CD-ROM sr0
Aug  6 17:43:35 FileServer kernel: [   27.364773] EXT3-fs: INFO: recovery required on readonly filesystem.
Aug  6 17:43:35 FileServer kernel: [   27.364778] EXT3-fs: write access will be enabled during recovery.
Aug  6 17:43:35 FileServer kernel: [   28.460039] kjournald starting.  Commit interval 5 seconds
Aug  6 17:43:35 FileServer kernel: [   28.460055] EXT3-fs: sdc2: orphan cleanup on readonly fs
Aug  6 17:43:35 FileServer kernel: [   28.476925] ext3_orphan_cleanup: deleting unreferenced inode 1697877
Aug  6 17:43:35 FileServer kernel: [   28.494821] ext3_orphan_cleanup: deleting unreferenced inode 1697875
Aug  6 17:43:35 FileServer kernel: [   28.506877] ext3_orphan_cleanup: deleting unreferenced inode 1698107
Aug  6 17:43:35 FileServer kernel: [   28.516060] ext3_orphan_cleanup: deleting unreferenced inode 1712298
Aug  6 17:43:35 FileServer kernel: [   28.526465] ext3_orphan_cleanup: deleting unreferenced inode 1712297
Aug  6 17:43:35 FileServer kernel: [   28.534595] ext3_orphan_cleanup: deleting unreferenced inode 1697871
Aug  6 17:43:35 FileServer kernel: [   28.552674] ext3_orphan_cleanup: deleting unreferenced inode 835760
Aug  6 17:43:35 FileServer kernel: [   28.560948] ext3_orphan_cleanup: deleting unreferenced inode 1696691
Aug  6 17:43:35 FileServer kernel: [   28.582213] ext3_orphan_cleanup: deleting unreferenced inode 41124
Aug  6 17:43:35 FileServer kernel: [   28.878821] ext3_orphan_cleanup: deleting unreferenced inode 655366
Aug  6 17:43:35 FileServer kernel: [   28.878830] ext3_orphan_cleanup: deleting unreferenced inode 655365
Aug  6 17:43:35 FileServer kernel: [   28.878836] ext3_orphan_cleanup: deleting unreferenced inode 655364
Aug  6 17:43:35 FileServer kernel: [   28.878841] ext3_orphan_cleanup: deleting unreferenced inode 655363
Aug  6 17:43:35 FileServer kernel: [   28.878846] ext3_orphan_cleanup: deleting unreferenced inode 655362
Aug  6 17:43:35 FileServer kernel: [   28.878850] EXT3-fs: sdc2: 14 orphan inodes deleted
Aug  6 17:43:35 FileServer kernel: [   28.878851] EXT3-fs: recovery complete.
Aug  6 17:43:35 FileServer kernel: [   28.895808] EXT3-fs: mounted filesystem with ordered data mode.
Aug  6 17:43:35 FileServer kernel: [   33.212217] input: PC Speaker as /devices/platform/pcspkr/input/input3
Aug  6 17:43:35 FileServer kernel: [   33.432087] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Aug  6 17:43:35 FileServer kernel: [   33.508240] Linux agpgart interface v0.102
Aug  6 17:43:35 FileServer kernel: [   33.592704] parport_pc 00:08: reported by Plug and Play ACPI
Aug  6 17:43:35 FileServer kernel: [   33.592755] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
Aug  6 17:43:35 FileServer kernel: [   33.626735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Aug  6 17:43:35 FileServer kernel: [   33.652138] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Aug  6 17:43:35 FileServer kernel: [   33.682037] input: Power Button (FF) as /devices/virtual/input/input4
Aug  6 17:43:35 FileServer kernel: [   33.719535] intel_rng: FWH not detected
Aug  6 17:43:35 FileServer kernel: [   33.727759] agpgart: Detected an Intel 865 Chipset.
Aug  6 17:43:35 FileServer kernel: [   33.727848] agpgart: Detected 892K stolen memory.
Aug  6 17:43:35 FileServer kernel: [   33.739556] agpgart: AGP aperture is 128M @ 0xe8000000
Aug  6 17:43:35 FileServer kernel: [   33.751928] ACPI: Power Button (FF) [PWRF]
Aug  6 17:43:35 FileServer kernel: [   33.751987] input: Power Button (CM) as /devices/virtual/input/input5
Aug  6 17:43:35 FileServer kernel: [   33.791949] ACPI: Power Button (CM) [VBTN]
Aug  6 17:43:35 FileServer kernel: [   33.951795] iTCO_vendor_support: vendor-support=0
Aug  6 17:43:35 FileServer kernel: [   34.051742] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Aug  6 17:43:35 FileServer kernel: [   34.051823] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
Aug  6 17:43:35 FileServer kernel: [   34.051869] iTCO_wdt: No card detected
Aug  6 17:43:35 FileServer kernel: [   34.665664] udev: renamed network interface eth0 to eth1
Aug  6 17:43:35 FileServer kernel: [   34.711775] e1000: eth1: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Aug  6 17:43:35 FileServer kernel: [   35.363314] NET: Registered protocol family 10
Aug  6 17:43:35 FileServer kernel: [   35.363566] lo: Disabled Privacy Extensions
Aug  6 17:43:35 FileServer kernel: [   36.073798] loop: module loaded
Aug  6 17:43:35 FileServer kernel: [   36.090207] lp0: using parport0 (interrupt-driven).
Aug  6 17:43:35 FileServer kernel: [   37.023671] Adding 875532k swap on /dev/sdc3.  Priority:-1 extents:1 across:875532k
Aug  6 17:43:35 FileServer kernel: [   38.279096] EXT3 FS on sdc2, internal journal
Aug  6 17:43:35 FileServer kernel: [   46.136340] eth1: no IPv6 routers present
Aug  6 17:43:35 FileServer kernel: [   92.901513] kjournald starting.  Commit interval 5 seconds
Aug  6 17:43:35 FileServer kernel: [   92.901713] EXT3 FS on sdc1, internal journal
Aug  6 17:43:35 FileServer kernel: [   92.901717] EXT3-fs: mounted filesystem with ordered data mode.
Aug  6 17:43:35 FileServer kernel: [   92.970335] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
Aug  6 17:43:35 FileServer kernel: [   92.972736] SGI XFS Quota Management subsystem
Aug  6 17:43:35 FileServer kernel: [   93.474989] ip_tables: (C) 2000-2006 Netfilter Core Team
Aug  6 17:43:35 FileServer kernel: [   95.289690] RPC: Registered udp transport module.
Aug  6 17:43:35 FileServer kernel: [   95.289694] RPC: Registered tcp transport module.
Aug  6 17:43:54 FileServer kernel: [  115.742223] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Aug  6 17:43:54 FileServer kernel: [  115.824984] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Aug  6 17:43:54 FileServer kernel: [  115.834505] NFSD: starting 90-second grace period
Aug  6 18:11:19 FileServer kernel: [ 1760.547499] md: md0 stopped.
Aug  6 18:11:19 FileServer kernel: [ 1760.551226] md: bind<sde1>
Aug  6 18:11:19 FileServer kernel: [ 1760.551508] md: bind<sdd1>
Aug  6 18:11:19 FileServer kernel: [ 1760.551757] md: bind<sda1>
Aug  6 18:11:19 FileServer kernel: [ 1760.551991] md: bind<sdb1>
Aug  6 18:11:19 FileServer kernel: [ 1760.626649] raid5: device sdb1 operational as raid disk 0
Aug  6 18:11:19 FileServer kernel: [ 1760.626655] raid5: device sda1 operational as raid disk 3
Aug  6 18:11:19 FileServer kernel: [ 1760.626657] raid5: device sdd1 operational as raid disk 2
Aug  6 18:11:19 FileServer kernel: [ 1760.626659] raid5: device sde1 operational as raid disk 1
Aug  6 18:11:19 FileServer kernel: [ 1760.627679] raid5: allocated 4211kB for md0
Aug  6 18:11:19 FileServer kernel: [ 1760.627684] raid5: raid level 5 set md0 active with 4 out of 4 devices, algorithm 2
Aug  6 18:11:19 FileServer kernel: [ 1760.627686] RAID5 conf printout:
Aug  6 18:11:19 FileServer kernel: [ 1760.627687]  --- rd:4 wd:4
Aug  6 18:11:19 FileServer kernel: [ 1760.627690]  disk 0, o:1, dev:sdb1
Aug  6 18:11:19 FileServer kernel: [ 1760.627692]  disk 1, o:1, dev:sde1
Aug  6 18:11:19 FileServer kernel: [ 1760.627693]  disk 2, o:1, dev:sdd1
Aug  6 18:11:19 FileServer kernel: [ 1760.627695]  disk 3, o:1, dev:sda1
Aug  6 18:13:17 FileServer kernel: [ 1877.745176] Filesystem "md0": Disabling barriers, not supported by the underlying device
Aug  6 18:13:17 FileServer kernel: [ 1877.745547] XFS mounting filesystem md0
Aug  6 18:13:17 FileServer kernel: [ 1877.840939] Starting XFS recovery on filesystem: md0 (logdev: internal)
Aug  6 18:13:18 FileServer kernel: [ 1879.104432] Ending XFS recovery on filesystem: md0 (logdev: internal)

```

[COLOR="Red"]This is where it starts to take a dump on me (I think).[/COLOR]

```

Aug  6 18:26:50 FileServer kernel: [ 2685.747564] SABnzbd.py invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
Aug  6 18:26:51 FileServer kernel: [ 2685.747571] Pid: 5795, comm: SABnzbd.py Not tainted 2.6.24-24-server #1
Aug  6 18:26:52 FileServer kernel: [ 2685.747591]  [oom_kill_process+0x10a/0x120] oom_kill_process+0x10a/0x120
Aug  6 18:26:52 FileServer kernel: [ 2685.747616]  [out_of_memory+0x167/0x1a0] out_of_memory+0x167/0x1a0
Aug  6 18:26:52 FileServer kernel: [ 2685.747638]  [nfs:__alloc_pages+0x34c/0x380] __alloc_pages+0x34c/0x380
Aug  6 18:26:52 FileServer kernel: [ 2685.747665]  [__do_page_cache_readahead+0x11d/0x240] __do_page_cache_readahead+0x11d/0x240
Aug  6 18:26:52 FileServer kernel: [ 2685.747669]  [sync_page+0x0/0x40] sync_page+0x0/0x40
Aug  6 18:26:52 FileServer kernel: [ 2685.747693]  [do_page_cache_readahead+0x4c/0x70] do_page_cache_readahead+0x4c/0x70
Aug  6 18:26:52 FileServer kernel: [ 2685.747705]  [xfs:filemap_fault+0x2f2/0x530] filemap_fault+0x2f2/0x420
Aug  6 18:26:52 FileServer kernel: [ 2685.747712]  [nfs:schedule+0x217/0x6b0] schedule+0x217/0x630
Aug  6 18:26:52 FileServer kernel: [ 2685.747737]  [__do_fault+0x83/0x4c0] __do_fault+0x83/0x4c0
Aug  6 18:26:52 FileServer kernel: [ 2685.747780]  [handle_mm_fault+0x21b/0xb80] handle_mm_fault+0x21b/0xb80
Aug  6 18:26:52 FileServer kernel: [ 2685.747792]  [<c012b180>] default_wake_function+0x0/0x10
Aug  6 18:26:52 FileServer kernel: [ 2685.747858]  [do_page_fault+0x143/0x900] do_page_fault+0x143/0x900
Aug  6 18:26:52 FileServer kernel: [ 2685.747865]  [nfs:dput+0x2c/0x490] dput+0x2c/0x100
Aug  6 18:26:52 FileServer kernel: [ 2685.747873]  [__fput+0x114/0x170] __fput+0x114/0x170
Aug  6 18:26:52 FileServer kernel: [ 2685.747883]  [nfs:mntput_no_expire+0x13/0x150] mntput_no_expire+0x13/0x70
Aug  6 18:26:52 FileServer kernel: [ 2685.747902]  [do_page_fault+0x0/0x900] do_page_fault+0x0/0x900
Aug  6 18:26:52 FileServer kernel: [ 2685.747907]  [error_code+0x72/0x78] error_code+0x72/0x78
Aug  6 18:26:52 FileServer kernel: [ 2685.747923]  [rt_mutex_slowlock+0x3f0/0x4b0] rt_mutex_slowlock+0x3f0/0x4b0
Aug  6 18:26:52 FileServer kernel: [ 2685.747939]  =======================
Aug  6 18:26:52 FileServer kernel: [ 2685.747941] Mem-info:
Aug  6 18:26:52 FileServer kernel: [ 2685.747942] DMA per-cpu:
Aug  6 18:26:52 FileServer kernel: [ 2685.747944] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
Aug  6 18:26:52 FileServer kernel: [ 2685.747946] Normal per-cpu:
Aug  6 18:26:52 FileServer kernel: [ 2685.747949] CPU    0: Hot: hi:  186, btch:  31 usd: 160   Cold: hi:   62, btch:  15 usd:  14
Aug  6 18:26:52 FileServer kernel: [ 2685.747952] Active:60199 inactive:60349 dirty:0 writeback:0 unstable:0
Aug  6 18:26:52 FileServer kernel: [ 2685.747953]  free:1194 slab:2402 mapped:498 pagetables:1235 bounce:0
Aug  6 18:26:52 FileServer kernel: [ 2685.747956] DMA free:2040kB min:88kB low:108kB high:132kB active:4972kB inactive:5076kB present:16256kB pages_scanned:21155 all_unreclaimable? yes
Aug  6 18:26:52 FileServer kernel: [ 2685.747958] lowmem_reserve[]: 0 490 490 490
Aug  6 18:26:52 FileServer kernel: [ 2685.747963] Normal free:2736kB min:2788kB low:3484kB high:4180kB active:235824kB inactive:236320kB present:502352kB pages_scanned:839128 all_unreclaimable? yes
Aug  6 18:26:52 FileServer kernel: [ 2685.747965] lowmem_reserve[]: 0 0 0 0
Aug  6 18:26:52 FileServer kernel: [ 2685.747969] DMA: 2*4kB 0*8kB 1*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 2040kB
Aug  6 18:26:52 FileServer kernel: [ 2685.747977] Normal: 6*4kB 4*8kB 2*16kB 4*32kB 1*64kB 1*128kB 1*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 2712kB
Aug  6 18:26:52 FileServer kernel: [ 2685.747986] Swap cache: add 437923, delete 437678, find 26040/55768, race 0+0
Aug  6 18:26:52 FileServer kernel: [ 2685.747988] Free swap  = 0kB
Aug  6 18:26:52 FileServer kernel: [ 2685.747989] Total swap = 875532kB
Aug  6 18:26:52 FileServer kernel: [ 2685.747990] Free swap:            0kB
Aug  6 18:26:52 FileServer kernel: [ 2685.751903] 130672 pages of RAM
Aug  6 18:26:52 FileServer kernel: [ 2685.751905] 0 pages of HIGHMEM
Aug  6 18:26:52 FileServer kernel: [ 2685.751906] 2196 reserved pages
Aug  6 18:26:52 FileServer kernel: [ 2685.751907] 4664 pages shared
Aug  6 18:26:52 FileServer kernel: [ 2685.751909] 245 pages swap cached
Aug  6 18:26:52 FileServer kernel: [ 2685.751910] 0 pages dirty
Aug  6 18:26:52 FileServer kernel: [ 2685.751911] 0 pages writeback
Aug  6 18:26:52 FileServer kernel: [ 2685.751912] 498 pages mapped
Aug  6 18:26:52 FileServer kernel: [ 2685.751913] 2402 pages slab
Aug  6 18:26:52 FileServer kernel: [ 2685.751915] 1235 pages pagetables
Aug  6 18:26:52 FileServer kernel: [ 2685.751917] Out of memory: kill process 5790 (SABnzbd.py) score 42837 or a child
Aug  6 18:26:52 FileServer kernel: [ 2685.752000] Killed process 5790 (SABnzbd.py)
```

---

### Post by gilligan8 on 2009-08-07
*bump for the day walkers* ;)

---

### Post by gilligan8 on 2009-08-08
*weekend bump*

I managed to crash it again... ran fine for a while then I did another xfs_check and watched the swap file slowly get eaten up till the system started throwing OOM errors and then grinded to a halt (well, for all intents and purposes).

---

### Post by ian dobson on 2009-08-09
Hi,

Try booting up in single user mode and run a file check on all your file systems. It might help if you can add extra memory to the box (atleast when you run the file checks).

It looks as if something is really eating your memory, xfs_check can use alot of memory so running is in single user mode will give it as much memory as possible. How large is your xfs filesystem (I see it's sitting on a md raid array).

Have a look here:- [http://fixunix.com/storage/202061-large-linux-xfs-volumes-xfs_check.html](http://fixunix.com/storage/202061-large-linux-xfs-volumes-xfs_check.html)

Or maybe here:- [http://www.nabble.com/xfs_check-td17494452.html](http://www.nabble.com/xfs_check-td17494452.html)
Regards
Ian Dobson

---

### Post by gilligan8 on 2009-08-10
Thanks for the reply Ian.

The thing is that this wasn't what caused the problem the first time... it's not JUST xfs_check... that is just a consistant way to make it happen.

The first time I just did a du -hs on a dir that had about 300gigs in it.

I know I don't have a lot of ram in the system (512mb) but this is a headless system in my home that doesn't see much of a load.  I download Torrents and News Group stuff with it, IRC , personal web server (apache2) and samba to my home network.  Should I just increase the swap file?

I feel like there may be a memory leak somewhere because a du -hs command SHOULDN'T lock up the system.  I did it later on the entire /home/ directory and it processed it no problems and reported 1.1T (this included said directory that locked up the system before.)  There would have been nothing else running that should have taken up that much more ram before.

On another note... should I not have picked XFS?  I thought I was doing good picking that fs?? :(

---

### Post by grantemsley on 2009-08-10
Have you run memtest86 on the system? Is there any chance your memory is (slightly) bad?

---

### Post by gilligan8 on 2009-08-10
Sorry... if I didn't mention that originally but that was my first thought also.

No errors passed MANY times (I left while it was running.)

---

### Post by gilligan8 on 2009-08-11
*bump*

---

### Post by ian dobson on 2009-08-12
Hi,

Sounds as if you have corruption in your xfs file system. maybe try running xfs_repair which does almost the same thing as xfs_check but uses alot less memory.

By the way oom-killer is a "process" that kills less important processes when memory gets very tight. 

Regards
Ian Dobson

---

### Post by gilligan8 on 2009-08-12
Will do... someone else yesterday (a disc golf buddy) suggested I might have a corrupt file causing the memory leak.

Will report back.

---

### Post by gilligan8 on 2009-08-12
Hmm... I ran it first with -nv and then with just -v.

The exit status was 0 on both and from what I read if there were errors the exit status would have been 1 with the -n.

Either way here is the results:

```
        XFS_REPAIR Summary    Wed Aug 12 10:27:19 2009

Phase           Start           End             Duration
Phase 1:        08/12 10:26:04  08/12 10:26:05  1 second
Phase 2:        08/12 10:26:05  08/12 10:26:16  11 seconds
Phase 3:        08/12 10:26:16  08/12 10:26:59  43 seconds
Phase 4:        08/12 10:26:59  08/12 10:27:02  3 seconds
Phase 5:        08/12 10:27:02  08/12 10:27:04  2 seconds
Phase 6:        08/12 10:27:04  08/12 10:27:04
Phase 7:        08/12 10:27:04  08/12 10:27:04

Total run time: 1 minute
done

```

---

