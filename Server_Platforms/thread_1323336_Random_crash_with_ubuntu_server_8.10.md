---
title: "Random crash with ubuntu server 8.10"
date: 2009-11-11
forum: Server Platforms
---

### Post by antip_petrovitch on 2009-11-11
I have a computer that runs ubuntu server 8.10 and it started crashing recently. This is what happens :

The computer runs for several hours (maybe even days) and then suddenly it stops, I can't ping it, keyboard is dead, nothing. When I reboot it and look in the logs (syslog) I can't find anything to point me in a direction, everything looks normal (to me at least, I'm not a pro).

There is maybe one thing though, I noticed that the crashes happen after I plug and mount an external USB harddrive (LaCie), but I'm not sure if there is really a connection between this and the crashes.

I'm kind of lost here, if someone could give me a direction where to look, or a possible cause for the problem it would be greatly appreciated. Thanks!


Here is a part of the syslog,  I assume it froze between 2:39 and 6:32.
> 
Nov 10 02:05:00 home -- MARK --
Nov 10 02:09:01 home /USR/SBIN/CRON[20452]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 02:17:01 home /USR/SBIN/CRON[20459]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 02:39:01 home /USR/SBIN/CRON[20462]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 03:05:00 home -- MARK --
Nov 10 03:09:01 home /USR/SBIN/CRON[20469]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 03:17:01 home /USR/SBIN/CRON[20476]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 03:39:01 home /USR/SBIN/CRON[20479]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 04:05:00 home -- MARK --
Nov 10 04:09:01 home /USR/SBIN/CRON[20486]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 04:17:01 home /USR/SBIN/CRON[20493]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 04:39:01 home /USR/SBIN/CRON[20496]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 05:05:00 home -- MARK --
Nov 10 05:09:01 home /USR/SBIN/CRON[20503]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 05:17:01 home /USR/SBIN/CRON[20510]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 05:39:01 home /USR/SBIN/CRON[20521]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 06:05:00 home -- MARK --
Nov 10 06:09:01 home /USR/SBIN/CRON[20541]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 10 06:17:01 home /USR/SBIN/CRON[20552]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 10 06:25:01 home /USR/SBIN/CRON[20560]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Nov 10 06:39:01 home /USR/SBIN/CRON[20586]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 11 02:17:01 home /USR/SBIN/CRON[26122]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 02:39:01 home /USR/SBIN/CRON[26125]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 11 06:32:43 home syslogd 1.5.0#1ubuntu1: restart.
Nov 11 06:32:43 home kernel: Inspecting /boot/System.map-2.6.24-24-server
Nov 11 06:32:43 home kernel: Loaded 28777 symbols from /boot/System.map-2.6.24-24-server.
Nov 11 06:32:43 home kernel: Symbols match kernel version 2.6.24.
Nov 11 06:32:43 home kernel: Loaded 11548 symbols from 47 modules.
Nov 11 06:32:43 home kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 11 06:32:43 home kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 11 06:32:43 home kernel: [    0.000000] Linux version 2.6.24-24-server (buildd@palmer) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Tue Jul 7 20:21:17 UTC 2009 (Ubuntu 2.6.24-24.56-server)
Nov 11 06:32:43 home kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
Nov 11 06:32:43 home kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Nov 11 06:32:43 home kernel: [    0.000000] 0MB HIGHMEM available.
Nov 11 06:32:43 home kernel: [    0.000000] 479MB LOWMEM available.
Nov 11 06:32:43 home kernel: [    0.000000] found SMP MP-table at 000f5000
Nov 11 06:32:43 home kernel: [    0.000000] Entering add_active_range(0, 0, 122864) 0 entries of 256 used
Nov 11 06:32:43 home kernel: [    0.000000] Zone PFN ranges:
Nov 11 06:32:43 home kernel: [    0.000000]   DMA             0 ->     4096
Nov 11 06:32:43 home kernel: [    0.000000]   Normal       4096 ->   122864
Nov 11 06:32:43 home kernel: [    0.000000]   HighMem    122864 ->   122864
Nov 11 06:32:43 home kernel: [    0.000000] Movable zone start PFN for each node
Nov 11 06:32:43 home kernel: [    0.000000] early_node_map[1] active PFN ranges
Nov 11 06:32:43 home kernel: [    0.000000]     0:        0 ->   122864
Nov 11 06:32:43 home kernel: [    0.000000] On node 0 totalpages: 122864
Nov 11 06:32:43 home kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Nov 11 06:32:43 home kernel: [    0.000000]   DMA zone: 0 pages reserved
Nov 11 06:32:43 home kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Nov 11 06:32:43 home kernel: [    0.000000]   Normal zone: 927 pages used for memmap
Nov 11 06:32:43 home kernel: [    0.000000]   Normal zone: 117841 pages, LIFO batch:31
Nov 11 06:32:43 home kernel: [    0.000000]   HighMem zone: 0 pages used for memmap
Nov 11 06:32:43 home kernel: [    0.000000]   Movable zone: 0 pages used for memmap
Nov 11 06:32:43 home kernel: [    0.000000] DMI 2.3 present.
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F68A0 checksum 0
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: RSDP 000F68A0, 0014 (r0 GBT   )
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: RSDT 1DFF3000, 002C (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: FACP 1DFF3040, 0074 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: DSDT 1DFF30C0, 3883 (r1 GBT    AWRDACPI     1000 MSFT  100000C)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: FACS 1DFF0000, 0040
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: APIC 1DFF6980, 0068 (r1 GBT    AWRDACPI 42302E31 AWRD  1010101)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 11 06:32:43 home kernel: [    0.000000] Processor #0 15:2 APIC version 20
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Nov 11 06:32:43 home kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 20, address 0xfec00000, GSI 0-23
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: IRQ0 used by override.
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: IRQ2 used by override.
Nov 11 06:32:43 home kernel: [    0.000000] ACPI: IRQ9 used by override.
Nov 11 06:32:43 home kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 11 06:32:43 home kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 11 06:32:43 home kernel: [    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
Nov 11 06:32:43 home kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Nov 11 06:32:43 home kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Nov 11 06:32:43 home kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121905
Nov 11 06:32:43 home kernel: [    0.000000] Kernel command line: root=UUID=dff48eea-542c-4ff7-99cb-a3549801bd4f ro quiet splash
Nov 11 06:32:43 home kernel: [    0.000000] mapped APIC to ffffb000 (fee00000)
Nov 11 06:32:43 home kernel: [    0.000000] mapped IOAPIC to ffffa000 (fec00000)
Nov 11 06:32:43 home kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 11 06:32:43 home kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 11 06:32:43 home kernel: [    0.000000] Initializing CPU#0
Nov 11 06:32:43 home kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Nov 11 06:32:43 home kernel: [    0.000000] Detected 2525.012 MHz processor.
Nov 11 06:32:43 home kernel: [   12.692155] Console: colour VGA+ 80x25
Nov 11 06:32:43 home kernel: [   12.692161] console [tty0] enabled
Nov 11 06:32:43 home kernel: [   12.692589] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 11 06:32:43 home kernel: [   12.693321] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 11 06:32:43 home kernel: [   12.705006] Memory: 475244k/491456k available (2258k kernel code, 15688k reserved, 1037k data, 384k init, 0k highmem)
Nov 11 06:32:43 home kernel: [   12.705020] virtual kernel memory layout:
Nov 11 06:32:43 home kernel: [   12.705021]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Nov 11 06:32:43 home kernel: [   12.705022]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Nov 11 06:32:43 home kernel: [   12.705023]     vmalloc : 0xde800000 - 0xffbfe000   ( 531 MB)
Nov 11 06:32:43 home kernel: [   12.705025]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
Nov 11 06:32:43 home kernel: [   12.705026]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
Nov 11 06:32:43 home kernel: [   12.705027]       .data : 0xc0334b09 - 0xc0437fe4   (1037 kB)
Nov 11 06:32:43 home kernel: [   12.705028]       .text : 0xc0100000 - 0xc0334b09   (2258 kB)
Nov 11 06:32:43 home kernel: [   12.705031] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Nov 11 06:32:43 home kernel: [   12.705082] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Nov 11 06:32:43 home kernel: [   12.854899] Calibrating delay using timer specific routine.. 5053.01 BogoMIPS (lpj=25265094)
Nov 11 06:32:43 home kernel: [   12.854940] Security Framework initialized
Nov 11 06:32:43 home kernel: [   12.854951] SELinux:  Disabled at boot.
Nov 11 06:32:43 home kernel: [   12.854971] AppArmor: AppArmor initialized
Nov 11 06:32:43 home kernel: [   12.854977] Failure registering capabilities with primary security module.
Nov 11 06:32:43 home kernel: [   12.854992] Mount-cache hash table entries: 512
Nov 11 06:32:43 home kernel: [   12.855195] Initializing cgroup subsys ns
Nov 11 06:32:43 home kernel: [   12.855205] Initializing cgroup subsys cpuacct
Nov 11 06:32:43 home kernel: [   12.855225] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000 00000000
Nov 11 06:32:43 home kernel: [   12.855241] CPU: Trace cache: 12K uops, L1 D cache: 8K
Nov 11 06:32:43 home kernel: [   12.855244] CPU: L2 cache: 128K
Nov 11 06:32:43 home kernel: [   12.855247] CPU: Hyper-Threading is disabled
Nov 11 06:32:43 home kernel: [   12.855252] CPU: After all inits, caps: bfebfbff 00000000 00000000 00043080 00004400 00000000 00000000 00000000
Nov 11 06:32:43 home kernel: [   12.855268] Compat vDSO mapped to ffffe000.
Nov 11 06:32:43 home kernel: [   12.855289] Checking 'hlt' instruction... OK.
Nov 11 06:32:43 home kernel: [   12.895373] SMP alternatives: switching to UP code
Nov 11 06:32:43 home kernel: [   12.897430] Freeing SMP alternatives: 12k freed
Nov 11 06:32:43 home kernel: [   12.897608] Early unpacking initramfs... done
Nov 11 06:32:43 home kernel: [   13.261178] ACPI: Core revision 20070126
Nov 11 06:32:43 home kernel: [   13.261259] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Nov 11 06:32:43 home kernel: [   13.267303] CPU0: Intel(R) Celeron(R) CPU 2.50GHz stepping 09
Nov 11 06:32:43 home kernel: [   13.267348] Total of 1 processors activated (5053.01 BogoMIPS).
Nov 11 06:32:43 home kernel: [   13.267461] ENABLING IO-APIC IRQs
Nov 11 06:32:43 home kernel: [   13.267649] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 11 06:32:43 home kernel: [   13.484164] Brought up 1 CPUs
Nov 11 06:32:43 home kernel: [   13.484196] CPU0 attaching sched-domain:
Nov 11 06:32:43 home kernel: [   13.484202]  domain 0: span 01
Nov 11 06:32:43 home kernel: [   13.484204]   groups: 01
Nov 11 06:32:43 home kernel: [   13.484672] net_namespace: 64 bytes
Nov 11 06:32:43 home kernel: [   13.484690] Booting paravirtualized kernel on bare hardware
Nov 11 06:32:43 home kernel: [   13.485498] Time: 11:32:11  Date: 11/11/09
Nov 11 06:32:43 home kernel: [   13.485561] NET: Registered protocol family 16
Nov 11 06:32:43 home kernel: [   13.486439] EISA bus registered
Nov 11 06:32:43 home kernel: [   13.486486] ACPI: bus type pci registered
Nov 11 06:32:43 home kernel: [   13.498622] PCI: PCI BIOS revision 2.10 entry at 0xfa850, last bus=1
Nov 11 06:32:43 home kernel: [   13.498627] PCI: Using configuration type 1
Nov 11 06:32:43 home kernel: [   13.498648] Setting up standard PCI resources
Nov 11 06:32:43 home kernel: [   13.502495] ACPI: EC: Look up EC in DSDT
Nov 11 06:32:43 home kernel: [   13.506911] ACPI: Interpreter enabled
Nov 11 06:32:43 home kernel: [   13.506920] ACPI: (supports S0 S1 S4 S5)
Nov 11 06:32:43 home kernel: [   13.506943] ACPI: Using IOAPIC for interrupt routing
Nov 11 06:32:43 home kernel: [   13.516595] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 11 06:32:43 home kernel: [   13.516949] Enabling SiS 96x SMBus.
Nov 11 06:32:43 home kernel: [   13.517669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Nov 11 06:32:43 home kernel: [   13.537624] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Nov 11 06:32:43 home kernel: [   13.537793] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 11 06:32:43 home kernel: [   13.537946] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 11 06:32:43 home kernel: [   13.538103] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 11 06:32:43 home kernel: [   13.538255] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Nov 11 06:32:43 home kernel: [   13.538413] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
Nov 11 06:32:43 home kernel: [   13.538573] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Nov 11 06:32:43 home kernel: [   13.538729] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Nov 11 06:32:43 home kernel: [   13.539131] Linux Plug and Play Support v0.97 (c) Adam Belay
Nov 11 06:32:43 home kernel: [   13.539258] pnp: PnP ACPI init
Nov 11 06:32:43 home kernel: [   13.539285] ACPI: bus type pnp registered
Nov 11 06:32:43 home kernel: [   13.543598] pnp: PnP ACPI: found 9 devices
Nov 11 06:32:43 home kernel: [   13.543604] ACPI: ACPI bus type pnp unregistered
Nov 11 06:32:43 home kernel: [   13.543611] PnPBIOS: Disabled by ACPI PNP
Nov 11 06:32:43 home kernel: [   13.544683] PCI: Using ACPI for IRQ routing
Nov 11 06:32:43 home kernel: [   13.544691] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Nov 11 06:32:43 home kernel: [   13.583962] NET: Registered protocol family 8
Nov 11 06:32:43 home kernel: [   13.583968] NET: Registered protocol family 20
Nov 11 06:32:43 home kernel: [   13.584119] NetLabel: Initializing
Nov 11 06:32:43 home kernel: [   13.584125] NetLabel:  domain hash size = 128
Nov 11 06:32:43 home kernel: [   13.584126] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 11 06:32:43 home kernel: [   13.584155] NetLabel:  unlabeled traffic allowed by default
Nov 11 06:32:43 home kernel: [   13.584245] AppArmor: AppArmor Filesystem Enabled
Nov 11 06:32:43 home kernel: [   13.593894] Time: tsc clocksource has been installed.
Nov 11 06:32:43 home kernel: [   13.614045] system 00:00: iomem range 0xf0000-0xf3fff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614051] system 00:00: iomem range 0xf4000-0xf7fff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614054] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614057] system 00:00: iomem range 0xfc000-0xfffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614060] system 00:00: iomem range 0x1dff0000-0x1dffffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614065] system 00:00: iomem range 0xffff0000-0xffffffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614068] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614071] system 00:00: iomem range 0x100000-0x1dfeffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614074] system 00:00: iomem range 0xffee0000-0xffefffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614077] system 00:00: iomem range 0xfffe0000-0xfffeffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614080] system 00:00: iomem range 0xfec00000-0xfec00fff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614083] system 00:00: iomem range 0xfee00000-0xfeefffff could not be reserved
Nov 11 06:32:43 home kernel: [   13.614096] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Nov 11 06:32:43 home kernel: [   13.614099] system 00:02: ioport range 0x290-0x29f has been reserved
Nov 11 06:32:43 home kernel: [   13.614102] system 00:02: ioport range 0x800-0x805 has been reserved
Nov 11 06:32:43 home kernel: [   13.645787] PCI: Bridge: 0000:00:01.0
Nov 11 06:32:43 home kernel: [   13.645795]   IO window: d000-dfff
Nov 11 06:32:43 home kernel: [   13.645803]   MEM window: ed000000-ed0fffff
Nov 11 06:32:43 home kernel: [   13.645808]   PREFETCH window: e0000000-e7ffffff
Nov 11 06:32:43 home kernel: [   13.645848] NET: Registered protocol family 2
Nov 11 06:32:43 home kernel: [   13.743815] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Nov 11 06:32:43 home kernel: [   13.744155] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Nov 11 06:32:43 home kernel: [   13.744296] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Nov 11 06:32:43 home kernel: [   13.744518] TCP: Hash tables configured (established 16384 bind 16384)
Nov 11 06:32:43 home kernel: [   13.744525] TCP reno registered
Nov 11 06:32:43 home kernel: [   13.773885] checking if image is initramfs... it is
Nov 11 06:32:43 home kernel: [   14.153148] Switched to high resolution mode on CPU 0
Nov 11 06:32:43 home kernel: [   14.432102] Freeing initrd memory: 7145k freed
Nov 11 06:32:43 home kernel: [   14.434054] audit: initializing netlink socket (disabled)
Nov 11 06:32:43 home kernel: [   14.434081] audit(1257939131.620:1): initialized
Nov 11 06:32:43 home kernel: [   14.434357] Total HugeTLB memory allocated, 0
Nov 11 06:32:43 home kernel: [   14.440500] VFS: Disk quotas dquot_6.5.1
Nov 11 06:32:43 home kernel: [   14.440735] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 11 06:32:43 home kernel: [   14.441307] io scheduler noop registered
Nov 11 06:32:43 home kernel: [   14.441314] io scheduler anticipatory registered
Nov 11 06:32:43 home kernel: [   14.441317] io scheduler deadline registered (default)
Nov 11 06:32:43 home kernel: [   14.441354] io scheduler cfq registered
Nov 11 06:32:43 home kernel: [   14.441420] Boot video device is 0000:01:00.0
Nov 11 06:32:43 home kernel: [   14.442449] isapnp: Scanning for PnP cards...
Nov 11 06:32:43 home kernel: [   14.798627] isapnp: No Plug & Play device found
Nov 11 06:32:43 home kernel: [   14.983659] Real Time Clock Driver v1.12ac
Nov 11 06:32:43 home kernel: [   14.983975] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Nov 11 06:32:43 home kernel: [   14.988498] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Nov 11 06:32:43 home kernel: [   14.988704] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Nov 11 06:32:43 home kernel: [   14.989037] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Nov 11 06:32:43 home kernel: [   14.989043] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Nov 11 06:32:43 home kernel: [   14.989363] serio: i8042 KBD port at 0x60,0x64 irq 1
Nov 11 06:32:43 home kernel: [   14.992584] mice: PS/2 mouse device common for all mice
Nov 11 06:32:43 home kernel: [   14.993061] EISA: Probing bus 0 at eisa.0
Nov 11 06:32:43 home kernel: [   14.993074] Cannot allocate resource for EISA slot 1
Nov 11 06:32:43 home kernel: [   14.993104] EISA: Detected 0 cards.
Nov 11 06:32:43 home kernel: [   14.993109] cpuidle: using governor ladder
Nov 11 06:32:43 home kernel: [   14.993112] cpuidle: using governor menu
Nov 11 06:32:43 home kernel: [   14.993274] NET: Registered protocol family 1
Nov 11 06:32:43 home kernel: [   14.993333] Using IPI No-Shortcut mode
Nov 11 06:32:43 home kernel: [   14.993409] registered taskstats version 1
Nov 11 06:32:43 home kernel: [   14.993536]   Magic number: 1:500:529
Nov 11 06:32:43 home kernel: [   14.993707] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Nov 11 06:32:43 home kernel: [   14.995231] Freeing unused kernel memory: 384k freed
Nov 11 06:32:43 home kernel: [   14.995290] Write protecting the kernel read-only data: 828k
Nov 11 06:32:43 home kernel: [   15.011463] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Nov 11 06:32:43 home kernel: [   15.332810] fuse init (API version 7.9)
Nov 11 06:32:43 home kernel: [   15.372273] ACPI Exception (processor_core-0824): AE_NOT_FOUND, Processor Device is not present [20070126]
Nov 11 06:32:43 home kernel: [   16.170912] SCSI subsystem initialized
Nov 11 06:32:43 home kernel: [   16.247581] libata version 3.00 loaded.
Nov 11 06:32:43 home kernel: [   16.251746] usbcore: registered new interface driver usbfs
Nov 11 06:32:43 home kernel: [   16.251798] usbcore: registered new interface driver hub
Nov 11 06:32:43 home kernel: [   16.263927] usbcore: registered new device driver usb
Nov 11 06:32:43 home kernel: [   16.265779] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Nov 11 06:32:43 home kernel: [   16.265849] 8139cp 0000:00:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
Nov 11 06:32:43 home kernel: [   16.265909] 8139cp 0000:00:0f.0: Try the "8139too" driver instead.
Nov 11 06:32:43 home kernel: [   16.271917] 8139too Fast Ethernet driver 0.9.28
Nov 11 06:32:43 home kernel: [   16.272036] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 16 (level, low) -> IRQ 16
Nov 11 06:32:43 home kernel: [   16.272767] eth0: RealTek RTL8139 at 0xec00, 00:0f:ea:77:da:20, IRQ 16
Nov 11 06:32:43 home kernel: [   16.272773] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
Nov 11 06:32:43 home kernel: [   16.308703] pata_sis 0000:00:02.5: version 0.5.2
Nov 11 06:32:43 home kernel: [   16.320716] scsi0 : pata_sis
Nov 11 06:32:43 home kernel: [   16.330524] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 11 06:32:43 home kernel: [   16.340645] scsi1 : pata_sis
Nov 11 06:32:43 home kernel: [   16.341578] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
Nov 11 06:32:43 home kernel: [   16.341584] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
Nov 11 06:32:43 home kernel: [   16.402673] Floppy drive(s): fd0 is 1.44M
Nov 11 06:32:43 home kernel: [   16.423926] FDC 0 is a post-1991 82077
Nov 11 06:32:43 home kernel: [   16.550176] ata1.00: HPA unlocked: 320170943 -> 320173056, native 320173056
Nov 11 06:32:43 home kernel: [   16.550186] ata1.00: ATA-7: Maxtor 6B160P0, BAH41B70, max UDMA/133
Nov 11 06:32:43 home kernel: [   16.550189] ata1.00: 320173056 sectors, multi 16: LBA48 
Nov 11 06:32:43 home kernel: [   16.550208] ata1.00: limited to UDMA/33 due to 40-wire cable
Nov 11 06:32:43 home kernel: [   16.591718] ata1.00: configured for UDMA/33
Nov 11 06:32:43 home kernel: [   16.929916] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A103, max UDMA/33
Nov 11 06:32:43 home kernel: [   17.129449] ata2.00: configured for UDMA/33
Nov 11 06:32:43 home kernel: [   17.129692] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6B160P0   BAH4 PQ: 0 ANSI: 5
Nov 11 06:32:43 home kernel: [   17.134235] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A103 PQ: 0 ANSI: 5
Nov 11 06:32:43 home kernel: [   17.134704] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 17
Nov 11 06:32:43 home kernel: [   17.134732] ohci_hcd 0000:00:03.0: OHCI Host Controller
Nov 11 06:32:43 home kernel: [   17.135349] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
Nov 11 06:32:43 home kernel: [   17.135388] ohci_hcd 0000:00:03.0: irq 17, io mem 0xed103000
Nov 11 06:32:43 home kernel: [   17.191345] usb usb1: configuration #1 chosen from 1 choice
Nov 11 06:32:43 home kernel: [   17.191413] hub 1-0:1.0: USB hub found
Nov 11 06:32:43 home kernel: [   17.191435] hub 1-0:1.0: 3 ports detected
Nov 11 06:32:43 home kernel: [   17.299175] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 18
Nov 11 06:32:43 home kernel: [   17.299200] ohci_hcd 0000:00:03.1: OHCI Host Controller
Nov 11 06:32:43 home kernel: [   17.299270] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
Nov 11 06:32:43 home kernel: [   17.299301] ohci_hcd 0000:00:03.1: irq 18, io mem 0xed100000
Nov 11 06:32:43 home kernel: [   17.361063] usb usb2: configuration #1 chosen from 1 choice
Nov 11 06:32:43 home kernel: [   17.361130] hub 2-0:1.0: USB hub found
Nov 11 06:32:43 home kernel: [   17.361149] hub 2-0:1.0: 3 ports detected
Nov 11 06:32:43 home kernel: [   17.469410] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 19
Nov 11 06:32:43 home kernel: [   17.469436] ehci_hcd 0000:00:03.3: EHCI Host Controller
Nov 11 06:32:43 home kernel: [   17.469514] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
Nov 11 06:32:43 home kernel: [   17.469575] PCI: cache line size of 128 is not supported by device 0000:00:03.3
Nov 11 06:32:43 home kernel: [   17.469592] ehci_hcd 0000:00:03.3: irq 19, io mem 0xed101000
Nov 11 06:32:43 home kernel: [   17.488690] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Nov 11 06:32:43 home kernel: [   17.488900] usb usb3: configuration #1 chosen from 1 choice
Nov 11 06:32:43 home kernel: [   17.488964] hub 3-0:1.0: USB hub found
Nov 11 06:32:43 home kernel: [   17.488981] hub 3-0:1.0: 6 ports detected
Nov 11 06:32:43 home kernel: [   17.607749] Driver 'sd' needs updating - please use bus_type methods
Nov 11 06:32:43 home kernel: [   17.608722] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Nov 11 06:32:43 home kernel: [   17.608765] sd 0:0:0:0: [sda] Write Protect is off
Nov 11 06:32:43 home kernel: [   17.608770] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 11 06:32:43 home kernel: [   17.608825] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 06:32:43 home kernel: [   17.608970] sd 0:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
Nov 11 06:32:43 home kernel: [   17.609006] sd 0:0:0:0: [sda] Write Protect is off
Nov 11 06:32:43 home kernel: [   17.609010] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Nov 11 06:32:43 home kernel: [   17.609467] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 11 06:32:43 home kernel: [   17.609479]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Nov 11 06:32:43 home kernel: [   17.633927]  sda1 sda2 sda3
Nov 11 06:32:43 home kernel: [   17.648482] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 11 06:32:43 home kernel: [   17.665550] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 11 06:32:43 home kernel: [   17.665598] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 11 06:32:43 home kernel: [   17.674781] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Nov 11 06:32:43 home kernel: [   17.674790] Uniform CD-ROM driver Revision: 3.20
Nov 11 06:32:43 home kernel: [   17.674883] sr 1:0:0:0: Attached scsi CD-ROM sr0
Nov 11 06:32:43 home kernel: [   22.144854] Attempting manual resume
Nov 11 06:32:43 home kernel: [   22.144861] swsusp: Resume From Partition 8:2
Nov 11 06:32:43 home kernel: [   22.144863] PM: Checking swsusp image.
Nov 11 06:32:43 home kernel: [   22.145193] PM: Resume from disk failed.
Nov 11 06:32:43 home kernel: [   22.159663] JFS: nTxBlock = 3772, nTxLock = 30183
Nov 11 06:32:43 home kernel: [   27.355568] input: PC Speaker as /devices/platform/pcspkr/input/input2
Nov 11 06:32:43 home kernel: [   27.545146] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 11 06:32:43 home kernel: [   27.585147] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 11 06:32:43 home kernel: [   27.653508] Linux agpgart interface v0.102
Nov 11 06:32:43 home kernel: [   27.699798] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x1400
Nov 11 06:32:43 home kernel: [   27.764936] agpgart: Detected SiS chipset - id:1633
Nov 11 06:32:43 home kernel: [   27.770482] agpgart: AGP aperture is 64M @ 0xe8000000
Nov 11 06:32:43 home kernel: [   27.846055] input: Power Button (FF) as /devices/virtual/input/input3
Nov 11 06:32:43 home kernel: [   27.914623] ACPI: Power Button (FF) [PWRF]
Nov 11 06:32:43 home kernel: [   27.914758] input: Power Button (CM) as /devices/virtual/input/input4
Nov 11 06:32:43 home kernel: [   27.984551] ACPI: Power Button (CM) [PWRB]
Nov 11 06:32:43 home kernel: [   28.612853] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Nov 11 06:32:43 home kernel: [   29.599968] NET: Registered protocol family 10
Nov 11 06:32:43 home kernel: [   29.600358] lo: Disabled Privacy Extensions
Nov 11 06:32:43 home kernel: [   31.130838] loop: module loaded
Nov 11 06:32:43 home kernel: [   31.211083] lp: driver loaded but no devices found
Nov 11 06:32:43 home kernel: [   31.602179] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
Nov 11 06:32:43 home kernel: [   40.567367] eth0: no IPv6 routers present
Nov 11 06:32:43 home kernel: [   43.080272] ip_tables: (C) 2000-2006 Netfilter Core Team


lspci
> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


---

### Post by mrsteveman1 on 2009-11-11
Can you see the console screen when this happens? Does it give a kernel panic or just freeze?

---

### Post by antip_petrovitch on 2009-11-11
Yes I can see it if I turn off the powersaving, there is no kernel panic, just the cursor that "blinks" and nothing responding. It just happened again but this time without the external harddisk.

> Nov 11 20:39:01 home /USR/SBIN/CRON[7235]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 
rm)
Nov 11 20:52:43 home -- MARK --
Nov 11 21:09:01 home /USR/SBIN/CRON[7242]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 
rm)
Nov 11 21:17:01 home /USR/SBIN/CRON[7249]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 11 22:02:18 home syslogd 1.5.0#1ubuntu1: restart.
Nov 11 22:02:18 home kernel: Inspecting /boot/System.map-2.6.24-24-server
Nov 11 22:02:18 home kernel: Loaded 28777 symbols from /boot/System.map-2.6.24-24-server.


Can this be a hardware problem?

---

### Post by mrsteveman1 on 2009-11-11
The first step is to figure out the cause, try to trigger it somehow. Any idea when this started? Anything changed? Kernel upgrade maybe?

Is there any reason you are sticking with 8.10?

---

### Post by antip_petrovitch on 2009-11-11
The only reason I'm using 8.10 is because of the long time support. I will try to stop all services (apache, mysql, etc) and see if it crashes, maybe also monitor the temperature, we'll see.

I'm wondering if the fact that there is no error in syslog indicates something ? Like a hardware failure or something like that.

Anyway thanks for the replies, I will update soon.

---

### Post by mrsteveman1 on 2009-11-12
Actually you're using 8.04 from the looks of your kernel version, but yea its LTS.

Got any weird add-in cards? Maybe a PCI disk controller card? Is your CPU fan going bad or just not moving?

Hard freeze is hard to diagnose though, i've seen it happen before but i don't recall the cause.

---

