---
title: "Server error after a power failure"
date: 2013-02-07
forum: Server Platforms
---

### Post by pojokan on 2013-02-07
I am a newbie, my server error after a power failure, I do not know what I should do :cry:. is there anything that can help me

My server config:

Ubuntu Linux 10.04.3
Apache version 2.2.14 
MySQL version 5.1.66 
2Gb RAM
Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz, 4 cores
451.79 GB total, 28.72 GB used
Server Use: Joomla Web Sites


Apache2 error.log
```
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Feb 07 17:55:38 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 07 17:57:12 2013] [error] [client 202.46.49.13] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/web1/public_html/configuration.php on line 53
[Thu Feb 07 17:57:45 2013] [error] [client 119.63.193.196] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/web1/public_html/configuration.php on line 53
[Thu Feb 07 18:23:45 2013] [error] [client 180.76.5.55] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Feb 07 19:15:27 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 07 19:58:50 2013] [error] [client 202.46.61.24] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 19:59:33 2013] [error] [client 119.63.193.131] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 20:27:23 2013] [error] [client 180.76.5.140] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 20:39:37 2013] [error] [client 180.76.6.26] PHP Parse error:  syntax error, unexpected T_STRING, expecting ',' or ';' in /home/web1/public_html/configuration.php on line 53
[Thu Feb 07 21:54:29 2013] [error] [client 202.46.55.33] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 21:55:02 2013] [error] [client 119.63.193.194] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 23:21:14 2013] [error] [client 180.76.5.170] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 23:52:23 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Feb 07 23:52:53 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Thu Feb 07 23:58:39 2013] [error] [client 202.46.55.29] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 23:59:21 2013] [error] [client 119.63.193.131] PHP Notice:  Undefined variable: countscript in /home/web2/public_html/plugins/content/plg_disqus_debate_echo.php on line 323
[Thu Feb 07 23:59:47 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Thu Feb 07 23:59:51 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Fri Feb 08 00:07:38 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Feb 08 00:07:44 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Fri Feb 08 00:50:15 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Feb 08 00:50:20 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Fri Feb 08 00:51:26 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Feb 08 00:51:55 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal operations
[Fri Feb 08 00:55:43 2013] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Fri Feb 08 00:55:49 2013] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.18 with Suhosin-Patch configured -- resuming normal
```

---

### Post by tgalati4 on 2013-02-07
```
dmesg | more
```
Page forward with spacebar, "q" to quit.  Look for hard disk read errors.

It looks like the power outage cause some disk errors in your Joomla PHP files.

Did you have an Unterruptable Power Supply (UPS) on this server?  If you are running a Joomla website, how can you be a newbie?

---

### Post by howefield on 2013-02-07
Thread moved to the "*Server Platforms*" forum.

---

### Post by pojokan on 2013-02-07
> **tgalati4 said:**
> ```
dmesg | more
```
Page forward with spacebar, "q" to quit.  Look for hard disk read errors.

It looks like the power outage cause some disk errors in your Joomla PHP files.

Did you have an Unterruptable Power Supply (UPS) on this server?  If you are running a Joomla website, how can you be a newbie?

like this ?
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-45-generic-pae (buildd@roseapple) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5.1) ) #102-Ubuntu SMP Wed Jan 2 22:10:16 UTC 2013 (Ubuntu
 2.6.32-45.102-generic-pae 2.6.32.60+drm33.26)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
[    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  BIOS-e820: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  BIOS-e820: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  BIOS-e820: 0000000040200000 - 000000007a30d000 (usable)
[    0.000000]  BIOS-e820: 000000007a30d000 - 000000007a35e000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007a35e000 - 000000007a377000 (reserved)
[    0.000000]  BIOS-e820: 000000007a377000 - 000000007a379000 (usable)
[    0.000000]  BIOS-e820: 000000007a379000 - 000000007a37a000 (reserved)
[    0.000000]  BIOS-e820: 000000007a37a000 - 000000007a388000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007a388000 - 000000007a3dd000 (reserved)
[    0.000000]  BIOS-e820: 000000007a3dd000 - 000000007a420000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007a420000 - 000000007a800000 (usable)
[    0.000000]  BIOS-e820: 000000007b000000 - 000000007f200000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.6 present.
[    0.000000] last_pfn = 0x7a800 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 07B000000 mask FFF000000 uncachable
[    0.000000]   2 base 07C000000 mask FFC000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009ac00 (usable)
[    0.000000]  modified: 000000000009ac00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  modified: 0000000020000000 - 0000000020200000 (reserved)
[    0.000000]  modified: 0000000020200000 - 0000000040000000 (usable)
[    0.000000]  modified: 0000000040000000 - 0000000040200000 (reserved)
[    0.000000]  modified: 0000000040200000 - 000000007a30d000 (usable)
[    0.000000]  modified: 000000007a30d000 - 000000007a35e000 (ACPI NVS)
[    0.000000]  modified: 000000007a35e000 - 000000007a377000 (reserved)
[    0.000000]  modified: 000000007a377000 - 000000007a379000 (usable)
[    0.000000]  modified: 000000007a379000 - 000000007a37a000 (reserved)
[    0.000000]  modified: 000000007a37a000 - 000000007a388000 (ACPI NVS)
[    0.000000]  modified: 000000007a388000 - 000000007a3dd000 (reserved)
[    0.000000]  modified: 000000007a3dd000 - 000000007a420000 (ACPI NVS)
[    0.000000]  modified: 000000007a420000 - 000000007a800000 (usable)
[    0.000000]  modified: 000000007b000000 - 000000007f200000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00e00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000379fe000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 0000200000 page 4k
[    0.000000]  0000200000 - 0037800000 page 2M
[    0.000000]  0037800000 - 00379fe000 page 4k
[    0.000000] kernel direct mapping tables up to 379fe000 @ 7000-d000
[    0.000000] RAMDISK: 17867000 - 1803fec1
[    0.000000] ACPI: RSDP 000f0430 00024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 7a356070 0005C (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 7a35ce08 000F4 (v04 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 7a356158 06CAA (v02 HPQOEM SLIC-CPC 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 7a37ff80 00040
[    0.000000] ACPI: APIC 7a35cf00 00072 (v03 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 7a35cf78 00102 (v01 HPQOEM SLIC-CPC 00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 7a35d080 0003C (v01 HPQOEM SLIC-CPC 01072009 MSFT 00000097)
[    0.000000] ACPI: SLIC 7a35d0c0 00176 (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: HPET 7a35d238 00038 (v01 HPQOEM SLIC-CPC 01072009 AMI. 00000004)
[    0.000000] ACPI: DBGP 7a35d270 00034 (v01 HPQOEM SLIC-CPC 01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1070MB HIGHMEM available.
[    0.000000] 889MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 379fe000
[    0.000000]   low ram: 0 - 379fe000
[    0.000000]   node 0 low ram: 00000000 - 379fe000
[    0.000000]   node 0 bootmap 00009000 - 0000ff40
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00379fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 0000941838]    TEXT DATA BSS ==> [0000100000 - 0000941838]
[    0.000000]   #4 [0017867000 - 001803fec1]          RAMDISK ==> [0017867000 - 001803fec1]
[    0.000000]   #5 [000009ac00 - 0000100000]    BIOS reserved ==> [000009ac00 - 0000100000]
[    0.000000]   #6 [0000942000 - 00009491c1]              BRK ==> [0000942000 - 00009491c1]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
[    0.000000] found SMP MP-table at [c00fcd80] fcd80
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000379fe
[    0.000000]   HighMem  0x000379fe -> 0x0007a800
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[7] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009a
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000]     0: 0x00020200 -> 0x00040000
[    0.000000]     0: 0x00040200 -> 0x0007a30d
[    0.000000]     0: 0x0007a377 -> 0x0007a379
[    0.000000]     0: 0x0007a420 -> 0x0007a800
[    0.000000] On node 0 totalpages: 500357
[    0.000000] free_area_init_node: node 0, pgdat c07e0e00, node_mem_map c1001000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3958 pages, LIFO batch:0
[    0.000000]   Normal zone: 1748 pages used for memmap
[    0.000000]   Normal zone: 221482 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2141 pages used for memmap
[    0.000000]   HighMem zone: 270996 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009a000 - 000000000009b000
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] Allocating PCI resources starting at 7f200000 (gap: 7f200000:7fb1c000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 15 pages/cpu @c2000000 s39512 r0 d21928 u524288
[    0.000000] pcpu-alloc: s39512 r0 d21928 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 496436
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-45-generic-pae root=UUID=864b045c-2169-4deb-931b-af00bca122c1 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 10035200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000379fe:0007a800)
[    0.000000] Memory: 1956984k/2007040k available (4856k kernel code, 43120k reserved, 2229k data, 684k init, 1092548k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xffa00000 - 0xffc00000   (2048 kB)
[    0.000000]     vmalloc : 0xf81fe000 - 0xff9fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf79fe000   ( 889 MB)
[    0.000000]       .init : 0xc07ec000 - 0xc0897000   ( 684 kB)
[    0.000000]       .data : 0xc05be01f - 0xc07eb788   (2229 kB)
[    0.000000]       .text : 0xc0100000 - 0xc05be01f   (4856 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 3093.224 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 6186.44 BogoMIPS (lpj=12372896)
[    0.000010] Security Framework initialized
[    0.000020] AppArmor: AppArmor initialized
[    0.000024] Mount-cache hash table entries: 512
[    0.000088] Initializing cgroup subsys ns
[    0.000090] Initializing cgroup subsys cpuacct
[    0.000093] Initializing cgroup subsys memory
[    0.000096] Initializing cgroup subsys devices
[    0.000098] Initializing cgroup subsys freezer
[    0.000099] Initializing cgroup subsys net_cls
[    0.000111] CPU: Physical Processor ID: 0
[    0.000112] CPU: Processor Core ID: 0
[    0.000115] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.000116] CPU: L2 cache: 256K
[    0.000117] CPU: L3 cache: 3072K
[    0.000120] mce: CPU supports 7 MCE banks
[    0.000128] CPU0: Thermal monitoring enabled (TM1)
[    0.000130] CPU 0 MCA banks CMCI:0 CMCI:1 CMCI:3 SHD:5 SHD:6
[    0.000136] using mwait in idle threads.
[    0.000139] Performance Events: Nehalem/Corei7 events, Intel PMU driver.
[    0.000142] ... version:                3
[    0.000143] ... bit width:              48
[    0.000144] ... generic registers:      4
[    0.000145] ... value mask:             0000ffffffffffff
[    0.000146] ... max period:             000000007fffffff
[    0.000147] ... fixed-purpose events:   3
[    0.000148] ... event mask:             000000070000000f
[    0.000151] Checking 'hlt' instruction... OK.
[    0.014531] ACPI: Core revision 20090903
[    0.020926] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.020928] ftrace: allocating 22480 entries in 44 pages
[    0.027460] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.027794] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.067472] CPU0: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz stepping 07
[    0.172407] Booting processor 1 APIC 0x2 ip 0x6000
[    0.182607] Initializing CPU#1
[    0.260328] CPU: Physical Processor ID: 0
[    0.260328] CPU: Processor Core ID: 1
[    0.260330] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.260331] CPU: L2 cache: 256K
[    0.260332] CPU: L3 cache: 3072K
[    0.260342] CPU1: Thermal monitoring enabled (TM1)
[    0.260343] CPU 1 MCA banks CMCI:0 CMCI:1 CMCI:3 SHD:5 SHD:6
[    0.260417] CPU1: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz stepping 07
[    0.260423] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280479] Booting processor 2 APIC 0x1 ip 0x6000
[    0.290685] Initializing CPU#2
[    0.368303] CPU: Physical Processor ID: 0
[    0.368304] CPU: Processor Core ID: 0
[    0.368306] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.368308] CPU: L2 cache: 256K
[    0.368309] CPU: L3 cache: 3072K
[    0.368320] CPU2: Thermal monitoring enabled (TM1)
[    0.368322] CPU 2 MCA banks SHD:0 SHD:1 SHD:3 SHD:5 SHD:6
[    0.368402] CPU2: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz stepping 07
[    0.368409] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.388465] Booting processor 3 APIC 0x3 ip 0x6000
[    0.398664] Initializing CPU#3
[    0.476277] CPU: Physical Processor ID: 0
[    0.476278] CPU: Processor Core ID: 1
[    0.476280] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.476281] CPU: L2 cache: 256K
[    0.476282] CPU: L3 cache: 3072K
[    0.476291] CPU3: Thermal monitoring enabled (TM1)
[    0.476293] CPU 3 MCA banks SHD:0 SHD:1 SHD:3 SHD:5 SHD:6
[    0.476377] CPU3: Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz stepping 07
[    0.476383] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.496396] Brought up 4 CPUs
[    0.496398] Total of 4 processors activated (24744.18 BogoMIPS).
[    0.498275] CPU0 attaching sched-domain:
[    0.498277]  domain 0: span 0,2 level SIBLING
[    0.498279]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[    0.498282]   domain 1: span 0-3 level MC
[    0.498283]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.498288] CPU1 attaching sched-domain:
[    0.498289]  domain 0: span 1,3 level SIBLING
[    0.498291]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[    0.498293]   domain 1: span 0-3 level MC
[    0.498295]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.498298] CPU2 attaching sched-domain:
[    0.498299]  domain 0: span 0,2 level SIBLING
[    0.498300]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[    0.498303]   domain 1: span 0-3 level MC
[    0.498304]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[    0.498307] CPU3 attaching sched-domain:
[    0.498308]  domain 0: span 1,3 level SIBLING
[    0.498309]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[    0.498312]   domain 1: span 0-3 level MC
[    0.498313]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[    0.498479] devtmpfs: initialized
[    0.498691] regulator: core version 0.5
[    0.498714] Time:  2:41:10  Date: 02/08/13
[    0.498737] NET: Registered protocol family 16
[    0.498796] Trying to unpack rootfs image as initramfs...
[    0.498800] EISA bus registered
[    0.498805] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.498806] ACPI: bus type pci registered
[    0.498845] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.498846] PCI: Not using MMCONFIG.
[    0.511207] PCI: Using configuration type 1 for base access
[    0.511785] bio: create slab <bio-0> at 0
[    0.512374] ACPI: EC: Look up EC in DSDT
[    0.513475] ACPI: Executed 1 blocks of module-level executable AML code
[    0.517018] ACPI: Interpreter enabled
[    0.517021] ACPI: (supports S0 S3 S4 S5)
[    0.517032] ACPI: Using IOAPIC for interrupt routing
[    0.517063] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.517163] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.517164] PCI: Using MMCONFIG for extended config space
[    0.517327] ACPI: BIOS _OSI(Linux) query ignored
[    0.521002] ACPI: No dock devices found.
[    0.521243] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.521316] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.521318] pci 0000:00:01.0: PME# disabled
[    0.521342] pci 0000:00:02.0: reg 10 64bit mmio: [0xfe000000-0xfe3fffff]
[    0.521347] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.521350] pci 0000:00:02.0: reg 20 io port: [0xf000-0xf03f]
[    0.521420] pci 0000:00:16.0: reg 10 64bit mmio: [0xfe508000-0xfe50800f]
[    0.521477] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.521481] pci 0000:00:16.0: PME# disabled
[    0.521536] pci 0000:00:1a.0: reg 10 32bit mmio: [0xfe507000-0xfe5073ff]
[    0.521604] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.521607] pci 0000:00:1a.0: PME# disabled
[    0.521645] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe500000-0xfe503fff]
[    0.521697] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.521700] pci 0000:00:1b.0: PME# disabled
[    0.521780] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.521784] pci 0000:00:1c.0: PME# disabled
[    0.521867] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.521870] pci 0000:00:1c.1: PME# disabled
[    0.521952] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.521956] pci 0000:00:1c.2: PME# disabled
[    0.522039] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.522043] pci 0000:00:1c.3: PME# disabled
[    0.522125] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.522129] pci 0000:00:1c.4: PME# disabled
[    0.522211] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.522215] pci 0000:00:1c.5: PME# disabled
[    0.522265] pci 0000:00:1d.0: reg 10 32bit mmio: [0xfe506000-0xfe5063ff]
[    0.522334] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.522337] pci 0000:00:1d.0: PME# disabled
[    0.522477] pci 0000:00:1f.2: reg 10 io port: [0xf0b0-0xf0b7]
[    0.522482] pci 0000:00:1f.2: reg 14 io port: [0xf0a0-0xf0a3]
[    0.522487] pci 0000:00:1f.2: reg 18 io port: [0xf090-0xf097]
[    0.522492] pci 0000:00:1f.2: reg 1c io port: [0xf080-0xf083]
[    0.522497] pci 0000:00:1f.2: reg 20 io port: [0xf060-0xf07f]
[    0.522502] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe505000-0xfe5057ff]
[    0.522542] pci 0000:00:1f.2: PME# supported from D3hot
[    0.522545] pci 0000:00:1f.2: PME# disabled
[    0.522571] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe504000-0xfe5040ff]
[    0.522584] pci 0000:00:1f.3: reg 20 io port: [0xf040-0xf05f]
[    0.522793] pci 0000:05:00.0: reg 10 32bit mmio: [0xfe400000-0xfe40ffff]
[    0.522949] pci 0000:00:1c.3: bridge 32bit mmio: [0xfe400000-0xfe4fffff]
[    0.523006] pci 0000:06:00.0: reg 10 io port: [0xe000-0xe0ff]
[    0.523028] pci 0000:06:00.0: reg 18 64bit mmio pref: [0xd0004000-0xd0004fff]
[    0.523044] pci 0000:06:00.0: reg 20 64bit mmio pref: [0xd0000000-0xd0003fff]
[    0.523128] pci 0000:06:00.0: supports D1 D2
[    0.523129] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.523134] pci 0000:06:00.0: PME# disabled
[    0.523192] pci 0000:00:1c.4: bridge io port: [0xe000-0xefff]
[    0.523200] pci 0000:00:1c.4: bridge 64bit mmio pref: [0xd0000000-0xd00fffff]
[    0.523269] pci_bus 0000:00: on NUMA node 0
[    0.523271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.523369] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.523402] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.523435] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.523468] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.523500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
[    0.523539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX5._PRT]
[    0.523574] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.526742] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10)
[    0.526817] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.526892] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.526965] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.527039] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.527114] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.527188] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.527261] ACPI: PCI Interrupt Link [LNKH] (IRQs *11 12 14 15)
[    0.527328] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.527334] vgaarb: loaded
[    0.527399] SCSI subsystem initialized
[    0.527474] libata version 3.00 loaded.
[    0.527522] usbcore: registered new interface driver usbfs
[    0.527528] usbcore: registered new interface driver hub
[    0.527547] usbcore: registered new device driver usb
[    0.527619] ACPI: WMI: Mapper loaded
[    0.527620] PCI: Using ACPI for IRQ routing
[    0.527738] NetLabel: Initializing
[    0.527739] NetLabel:  domain hash size = 128
[    0.527740] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.527747] NetLabel:  unlabeled traffic allowed by default
[    0.527772] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.527776] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.529792] Switching to clocksource tsc
[    0.531108] AppArmor: AppArmor Filesystem Enabled
[    0.531115] pnp: PnP ACPI init
[    0.531120] ACPI: bus type pnp registered
[    0.532271] pnp: PnP ACPI: found 11 devices
[    0.532273] ACPI: ACPI bus type pnp unregistered
[    0.532275] PnPBIOS: Disabled by ACPI PNP
[    0.532281] system 00:01: iomem range 0xfed10000-0xfed19fff has been reserved
[    0.532283] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.532285] system 00:01: iomem range 0xfed90000-0xfed93fff has been reserved
[    0.532286] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.532288] system 00:01: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.532291] system 00:02: ioport range 0x200-0x201 has been reserved
[    0.532295] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.532299] system 00:08: ioport range 0x400-0x453 has been reserved
[    0.532300] system 00:08: ioport range 0x458-0x47f has been reserved
[    0.532302] system 00:08: ioport range 0x1180-0x119f has been reserved
[    0.532303] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.532305] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.532306] system 00:08: iomem range 0xfec00000-0xfecfffff could not be reserved
[    0.532308] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.532310] system 00:08: iomem range 0xff000000-0xffffffff has been reserved
[    0.532313] system 00:09: ioport range 0x454-0x457 has been reserved
[    0.566947] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.566949] pci 0000:00:01.0:   IO window: disabled
[    0.566951] pci 0000:00:01.0:   MEM window: disabled
[    0.566952] pci 0000:00:01.0:   PREFETCH window: disabled
[    0.566955] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.566956] pci 0000:00:1c.0:   IO window: disabled
[    0.566960] pci 0000:00:1c.0:   MEM window: disabled
[    0.566964] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.566969] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:03
[    0.566970] pci 0000:00:1c.1:   IO window: disabled
[    0.566975] pci 0000:00:1c.1:   MEM window: disabled
[    0.566978] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.566984] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:04
[    0.566985] pci 0000:00:1c.2:   IO window: disabled
[    0.566989] pci 0000:00:1c.2:   MEM window: disabled
[    0.566993] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.566998] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:05
[    0.566999] pci 0000:00:1c.3:   IO window: disabled
[    0.567004] pci 0000:00:1c.3:   MEM window: 0xfe400000-0xfe4fffff
[    0.567007] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.567013] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.567016] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.567020] pci 0000:00:1c.4:   MEM window: disabled
[    0.567024] pci 0000:00:1c.4:   PREFETCH window: 0x000000d0000000-0x000000d00fffff
[    0.567030] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:07
[    0.567031] pci 0000:00:1c.5:   IO window: disabled
[    0.567035] pci 0000:00:1c.5:   MEM window: disabled
[    0.567039] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.567053]   alloc irq_desc for 16 on node -1
[    0.567055]   alloc kstat_irqs on node -1
[    0.567058] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.567061] pci 0000:00:01.0: setting latency timer to 64
[    0.567069]   alloc irq_desc for 17 on node -1
[    0.567070]   alloc kstat_irqs on node -1
[    0.567072] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.567075] pci 0000:00:1c.0: setting latency timer to 64
[    0.567083] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.567087] pci 0000:00:1c.1: setting latency timer to 64
[    0.567094]   alloc irq_desc for 18 on node -1
[    0.567095]   alloc kstat_irqs on node -1
[    0.567097] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.567101] pci 0000:00:1c.2: setting latency timer to 64
[    0.567108]   alloc irq_desc for 19 on node -1
[    0.567109]   alloc kstat_irqs on node -1
[    0.567111] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.567115] pci 0000:00:1c.3: setting latency timer to 64
[    0.567123] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.567126] pci 0000:00:1c.4: setting latency timer to 64
[    0.567134] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.567138] pci 0000:00:1c.5: setting latency timer to 64
[    0.567142] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.567143] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.567145] pci_bus 0000:05: resource 1 mem: [0xfe400000-0xfe4fffff]
[    0.567147] pci_bus 0000:06: resource 0 io:  [0xe000-0xefff]
[    0.567148] pci_bus 0000:06: resource 2 pref mem [0xd0000000-0xd00fffff]
[    0.567170] NET: Registered protocol family 2
[    0.567219] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.567350] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.567544] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.567638] TCP: Hash tables configured (established 131072 bind 65536)
[    0.567640] TCP reno registered
[    0.567679] NET: Registered protocol family 1
[    0.567774] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
[    0.567814] pci 0000:00:02.0: Boot video device
[    0.567824] pci 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.692244] pci 0000:00:1a.0: PCI INT A disabled
[    0.692262]   alloc irq_desc for 23 on node -1
[    0.692263]   alloc kstat_irqs on node -1
[    0.692267] pci 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.820214] pci 0000:00:1d.0: PCI INT A disabled
[    0.820389] cpufreq-nforce2: No nForce2 chipset.
[    0.820404] Scanning for low memory corruption every 60 seconds
[    0.820464] audit: initializing netlink socket (disabled)
[    0.820471] type=2000 audit(1360291270.000:1): initialized
[    0.826235] highmem bounce pool size: 64 pages
[    0.826238] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.826997] VFS: Disk quotas dquot_6.5.2
[    0.827027] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.827323] fuse init (API version 7.13)
[    0.827366] msgmni has been set to 1690
[    0.827505] alg: No test for stdrng (krng)
[    0.827534] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.827536] io scheduler noop registered
[    0.827537] io scheduler anticipatory registered
[    0.827538] io scheduler deadline registered
[    0.827559] io scheduler cfq registered (default)
[    0.827632]   alloc irq_desc for 24 on node -1
[    0.827633]   alloc kstat_irqs on node -1
[    0.827638] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.827641] pcieport 0000:00:01.0: setting latency timer to 64
[    0.827716]   alloc irq_desc for 25 on node -1
[    0.827717]   alloc kstat_irqs on node -1
[    0.827723] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.827730] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.827821]   alloc irq_desc for 26 on node -1
[    0.827821]   alloc kstat_irqs on node -1
[    0.827827] pcieport 0000:00:1c.1: irq 26 for MSI/MSI-X
[    0.827835] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.827925]   alloc irq_desc for 27 on node -1
[    0.827926]   alloc kstat_irqs on node -1
[    0.827932] pcieport 0000:00:1c.2: irq 27 for MSI/MSI-X
[    0.827940] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.828029]   alloc irq_desc for 28 on node -1
[    0.828030]   alloc kstat_irqs on node -1
[    0.828036] pcieport 0000:00:1c.3: irq 28 for MSI/MSI-X
[    0.828043] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.828133]   alloc irq_desc for 29 on node -1
[    0.828134]   alloc kstat_irqs on node -1
[    0.828140] pcieport 0000:00:1c.4: irq 29 for MSI/MSI-X
[    0.828147] pcieport 0000:00:1c.4: setting latency timer to 64
[    0.828241]   alloc irq_desc for 30 on node -1
[    0.828242]   alloc kstat_irqs on node -1
[    0.828248] pcieport 0000:00:1c.5: irq 30 for MSI/MSI-X
[    0.828256] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.828308] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.828325] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.828379] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.828385] ACPI: Power Button [PWRB]
[    0.828408] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.828410] ACPI: Power Button [PWRF]
[    0.828822] ACPI: SSDT 7a37ec18 0038C (v01    AMI      IST 00000001 MSFT 03000001)
[    0.829003] ACPI: SSDT 7a37fe18 00084 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.829364] Monitor-Mwait will be used to enter C-3 state
[    0.829390] processor LNXCPU:00: registered as cooling_device0
[    0.836556] processor LNXCPU:01: registered as cooling_device1
[    0.836951] processor LNXCPU:02: registered as cooling_device2
[    0.841208] Freeing initrd memory: 8035k freed
[    0.842174] processor LNXCPU:03: registered as cooling_device3
[    0.843105] isapnp: Scanning for PnP cards...
[    0.843806] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.844530] brd: module loaded
[    0.844760] loop: module loaded
[    0.844808] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.845026] Fixed MDIO Bus: probed
[    0.845046] PPP generic driver version 2.4.2
[    0.845061] tun: Universal TUN/TAP device driver, 1.6
[    0.845063] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.845103] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.845114] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.845124] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.845127] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    0.845145] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.845168] ehci_hcd 0000:00:1a.0: debug port 2
[    0.849044] ehci_hcd 0000:00:1a.0: cache line size of 32 is not supported
[    0.849063] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xfe507000
[    0.864186] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.864241] usb usb1: configuration #1 chosen from 1 choice
[    0.864256] hub 1-0:1.0: USB hub found
[    0.864260] hub 1-0:1.0: 2 ports detected
[    0.864287] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.864295] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.864298] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    0.864314] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.864334] ehci_hcd 0000:00:1d.0: debug port 2
[    0.868205] ehci_hcd 0000:00:1d.0: cache line size of 32 is not supported
[    0.868214] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xfe506000
[    0.880182] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.880224] usb usb2: configuration #1 chosen from 1 choice
[    0.880237] hub 2-0:1.0: USB hub found
[    0.880242] hub 2-0:1.0: 2 ports detected
[    0.880267] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.880274] uhci_hcd: USB Universal Host Controller Interface driver
[    0.880312] PNP: No PS/2 controller found. Probing ports directly.
[    0.880659] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.880663] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.880710] mice: PS/2 mouse device common for all mice
[    0.880765] rtc_cmos 00:04: RTC can wake from S4
[    0.880782] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.880806] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.880857] device-mapper: uevent: version 1.0.3
[    0.880913] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.880978] device-mapper: multipath: version 1.1.0 loaded
[    0.880980] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.881038] EISA: Probing bus 0 at eisa.0
[    0.881061] EISA: Detected 0 cards.
[    0.881198] cpuidle: using governor ladder
[    0.881282] cpuidle: using governor menu
[    0.881471] TCP cubic registered
[    0.881549] NET: Registered protocol family 10
[    0.881899] NET: Registered protocol family 17
[    0.882525] Using IPI No-Shortcut mode
[    0.882576] PM: Resume from disk failed.
[    0.882587] registered taskstats version 1
[    0.882949]   Magic number: 1:915:661
[    0.882953] block ram14: hash matches
[    0.882996] rtc_cmos 00:04: setting system clock to 2013-02-08 02:41:11 UTC (1360291271)
[    0.882998] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.882999] EDD information not available.
[    1.176237] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.196511] isapnp: No Plug & Play device found
[    1.196525] Freeing unused kernel memory: 684k freed
[    1.196678] Write protecting the kernel text: 4860k
[    1.196724] Write protecting the kernel read-only data: 1888k
[    1.207555] udev: starting version 151
[    1.211645] md: linear personality registered for level -1
[    1.227137] ahci 0000:00:1f.2: version 3.0
[    1.227153] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.227188]   alloc irq_desc for 31 on node -1
[    1.227190]   alloc kstat_irqs on node -1
[    1.227199] ahci 0000:00:1f.2: irq 31 for MSI/MSI-X
[    1.231125] md: multipath personality registered for level -4
[    1.231304] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.231326] r8169 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.231363] r8169 0000:06:00.0: setting latency timer to 64
[    1.231369] r8169 0000:06:00.0: unknown MAC, using family default
[    1.231417]   alloc irq_desc for 32 on node -1
[    1.231418]   alloc kstat_irqs on node -1
[    1.231432] r8169 0000:06:00.0: irq 32 for MSI/MSI-X
[    1.231928] eth0: RTL8168b/8111b at 0xf82ac000, e0:69:95:9e:2f:9b, XID 0c200000 IRQ 32
[    1.239328] md: raid0 personality registered for level 0
[    1.240126] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 3 Gbps 0x13 impl SATA mode
[    1.240130] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst
[    1.240136] ahci 0000:00:1f.2: setting latency timer to 64
[    1.250424] md: raid1 personality registered for level 1
[    1.252093] async_tx: api initialized (async)
[    1.252692] xor: automatically using best checksumming function: pIII_sse
[    1.256151] scsi0 : ahci
[    1.256238] scsi1 : ahci
[    1.256284] scsi2 : ahci
[    1.256328] scsi3 : ahci
[    1.256374] scsi4 : ahci
[    1.256493] ata1: SATA max UDMA/133 abar m2048@0xfe505000 port 0xfe505100 irq 31
[    1.256497] ata2: SATA max UDMA/133 abar m2048@0xfe505000 port 0xfe505180 irq 31
[    1.256498] ata3: DUMMY
[    1.256500] ata4: DUMMY
[    1.256502] ata5: SATA max UDMA/133 abar m2048@0xfe505000 port 0xfe505300 irq 31
[    1.272087]    pIII_sse  : 11365.000 MB/sec
[    1.272089] xor: using function: pIII_sse (11365.000 MB/sec)
[    1.308553] usb 1-1: configuration #1 chosen from 1 choice
[    1.308651] hub 1-1:1.0: USB hub found
[    1.308753] hub 1-1:1.0: 4 ports detected
[    1.372079] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.477846] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.477848] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.477866] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.478745] ata1.00: ATA-8: ST3500418AS, HP40, max UDMA/100
[    1.478748] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.479063] ata2.00: ATA-8: ST500DM002-1BD142, KC44, max UDMA/133
[    1.479065] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.479834] ata1.00: configured for UDMA/100
[    1.480534] ata2.00: configured for UDMA/133
[    1.481980] ata5.00: ATAPI: hp      DVD-RAM GH60L, RD05, max UDMA/100
[    1.486921] ata5.00: configured for UDMA/100
[    1.493911] scsi 0:0:0:0: Direct-Access     ATA      ST3500418AS      HP40 PQ: 0 ANSI: 5
[    1.493999] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.494004] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.494059] sd 0:0:0:0: [sda] Write Protect is off
[    1.494061] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.494077] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.494090] scsi 1:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 KC44 PQ: 0 ANSI: 5
[    1.494174]  sda:
[    1.494180] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.494236] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.494238] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    1.494278] sd 1:0:0:0: [sdb] Write Protect is off
[    1.494280] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.494300] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.494397]  sdb:
[    1.502312] usb 2-1: configuration #1 chosen from 1 choice
[    1.502513] hub 2-1:1.0: USB hub found
[    1.502584] hub 2-1:1.0: 6 ports detected
[    1.508108]  sda1 sda2 <
[    1.513205] scsi 4:0:0:0: CD-ROM            hp       DVD-RAM GH60L    RD05 PQ: 0 ANSI: 5
[    1.513541]  sdb1
[    1.513749] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.529525]  sda5 >
[    1.529757] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.534455] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.534460] Uniform CD-ROM driver Revision: 3.20
[    1.534544] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.534580] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    1.577950] usb 1-1.1: new low speed USB device using ehci_hcd and address 3
[    1.603354] raid6: int32x1   1461 MB/s
[    1.632922] mdadm: sending ioctl 1261 to a partition!
[    1.632925] mdadm: sending ioctl 1261 to a partition!
[    1.640444] mdadm: sending ioctl 1261 to a partition!
[    1.640446] mdadm: sending ioctl 1261 to a partition!
[    1.641136] mdadm: sending ioctl 1261 to a partition!
[    1.641137] mdadm: sending ioctl 1261 to a partition!
[    1.641525] mdadm: sending ioctl 1261 to a partition!
[    1.641526] mdadm: sending ioctl 1261 to a partition!
[    1.641558] mdadm: sending ioctl 1261 to a partition!
[    1.641559] mdadm: sending ioctl 1261 to a partition!
[    1.642985] md: bind<sdb1>
[    1.646570] md: bind<sda1>
[    1.647879] raid1: raid set md1 active with 2 out of 2 mirrors
[    1.647895] md1: detected capacity change from 0 to 492833996800
[    1.648605]  md1: unknown partition table
[    1.671334] raid6: int32x2   1421 MB/s
[    1.677220] usb 1-1.1: configuration #1 chosen from 1 choice
[    1.683806] usbcore: registered new interface driver hiddev
[    1.687045] input: Dell Dell QuietKey Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input3
[    1.687107] generic-usb 0003:413C:2106.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell QuietKey Keyboard] on usb-0000:00:1a.0-1.1/input0
[    1.687127] usbcore: registered new interface driver usbhid
[    1.687130] usbhid: v2.6:USB HID core driver
[    1.739335] raid6: int32x4   1139 MB/s
[    1.777930] usb 2-1.2: new low speed USB device using ehci_hcd and address 3
[    1.807314] raid6: int32x8    973 MB/s
[    1.873697] usb 2-1.2: configuration #1 chosen from 1 choice
[    1.875286] raid6: mmxx1     4831 MB/s
[    1.876854] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input4
[    1.876917] generic-usb 0003:0458:003A.0002: input,hidraw1: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:1d.0-1.2/input0
[    1.943274] raid6: mmxx2     5384 MB/s
[    1.949890] usb 2-1.4: new high speed USB device using ehci_hcd and address 4
[    2.011259] raid6: sse1x1    4147 MB/s
[    2.056903] usb 2-1.4: configuration #1 chosen from 1 choice
[    2.065126] Initializing USB Mass Storage driver...
[    2.065198] scsi5 : SCSI emulation for USB Mass Storage devices
[    2.065250] usb-storage: device found at 4
[    2.065252] usb-storage: waiting for device to settle before scanning
[    2.065257] usbcore: registered new interface driver usb-storage
[    2.065259] USB Mass Storage support registered.
[    2.079255] raid6: sse1x2    5040 MB/s
[    2.147237] raid6: sse2x1    8302 MB/s
[    2.215232] raid6: sse2x2   10222 MB/s
[    2.215233] raid6: using algorithm sse2x2 (10222 MB/s)
[    2.218399] md: raid6 personality registered for level 6
[    2.218400] md: raid5 personality registered for level 5
[    2.218401] md: raid4 personality registered for level 4
[    2.222584] md: raid10 personality registered for level 10
[    2.333843] EXT4-fs (md1): mounted filesystem with ordered data mode
[    7.061534] usb-storage: device scan complete
[    7.063665] scsi 5:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    7.064015] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    7.068090] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    9.456957] udev: starting version 151
[    9.465775] Adding 7101432k swap on /dev/sda5.  Priority:-1 extents:1 across:7101432k
[    9.500679] __ratelimit: 24 callbacks suppressed
[    9.500681] mdadm: sending ioctl 1261 to a partition!
[    9.500683] mdadm: sending ioctl 1261 to a partition!
[    9.675039] lp: driver loaded but no devices found
[    9.705199] vga16fb: initializing
[    9.705202] vga16fb: mapped to 0xc00a0000
[    9.705240] fb0: VGA16 VGA frame buffer device
[    9.783346] type=1505 audit(1360291280.155:2):  operation="profile_load" pid=605 name="/sbin/dhclient3"
[    9.783449] type=1505 audit(1360291280.155:3):  operation="profile_replace" pid=589 name="/sbin/dhclient3"
[    9.783761] type=1505 audit(1360291280.155:4):  operation="profile_load" pid=605 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.783973] type=1505 audit(1360291280.155:5):  operation="profile_replace" pid=589 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.784017] type=1505 audit(1360291280.155:6):  operation="profile_load" pid=605 name="/usr/lib/connman/scripts/dhclient-script"
[    9.784332] type=1505 audit(1360291280.155:7):  operation="profile_replace" pid=589 name="/usr/lib/connman/scripts/dhclient-script"
[    9.801207] r8169: eth0: link up
[    9.801211] r8169: eth0: link up
[    9.817718] mdadm: sending ioctl 1261 to a partition!
[    9.817720] mdadm: sending ioctl 1261 to a partition!
[    9.824113] Console: switching to colour frame buffer device 80x30
[    9.850899] mdadm: sending ioctl 1261 to a partition!
[    9.850902] mdadm: sending ioctl 1261 to a partition!
[    9.851779] mdadm: sending ioctl 1261 to a partition!
[    9.851782] mdadm: sending ioctl 1261 to a partition!
[    9.852455] mdadm: sending ioctl 1261 to a partition!
[    9.852457] mdadm: sending ioctl 1261 to a partition!
[   10.155981] type=1505 audit(1360291280.655:8):  operation="profile_load" pid=940 name="/usr/share/gdm/guest-session/Xsession"
[   10.156111] type=1505 audit(1360291280.655:9):  operation="profile_replace" pid=941 name="/sbin/dhclient3"
[   10.156623] type=1505 audit(1360291280.655:10):  operation="profile_replace" pid=941 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.156918] type=1505 audit(1360291280.655:11):  operation="profile_replace" pid=941 name="/usr/lib/connman/scripts/dhclient-script"
[   10.225398]   alloc irq_desc for 22 on node -1
[   10.225400]   alloc kstat_irqs on node -1
[   10.225406] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.225455] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.430175] hda_codec: ALC662 rev1: BIOS auto-probing.
[   10.431745] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.221822] ppdev: user-space parallel port driver
[   11.660674] CPU0 attaching NULL sched-domain.
[   11.660678] CPU1 attaching NULL sched-domain.
[   11.660679] CPU2 attaching NULL sched-domain.
[   11.660680] CPU3 attaching NULL sched-domain.
[   11.685479] CPU0 attaching sched-domain:
[   11.685481]  domain 0: span 0,2 level SIBLING
[   11.685483]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   11.685486]   domain 1: span 0-3 level MC
[   11.685488]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   11.685492] CPU1 attaching sched-domain:
[   11.685493]  domain 0: span 1,3 level SIBLING
[   11.685494]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   11.685497]   domain 1: span 0-3 level MC
[   11.685498]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   11.685502] CPU2 attaching sched-domain:
[   11.685503]  domain 0: span 0,2 level SIBLING
[   11.685504]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   11.685507]   domain 1: span 0-3 level MC
[   11.685508]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   11.685511] CPU3 attaching sched-domain:
[   11.685512]  domain 0: span 1,3 level SIBLING
[   11.685513]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   11.685516]   domain 1: span 0-3 level MC
[   11.685517]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   16.537727] CPU0 attaching NULL sched-domain.
[   16.537731] CPU1 attaching NULL sched-domain.
[   16.537733] CPU2 attaching NULL sched-domain.
[   16.537735] CPU3 attaching NULL sched-domain.
[   16.562706] CPU0 attaching sched-domain:
[   16.562709]  domain 0: span 0,2 level SIBLING
[   16.562711]   groups: 0 (cpu_power = 589) 2 (cpu_power = 589)
[   16.562716]   domain 1: span 0-3 level MC
[   16.562718]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   16.562723] CPU1 attaching sched-domain:
[   16.562725]  domain 0: span 1,3 level SIBLING
[   16.562727]   groups: 1 (cpu_power = 589) 3 (cpu_power = 589)
[   16.562731]   domain 1: span 0-3 level MC
[   16.562733]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   16.562737] CPU2 attaching sched-domain:
[   16.562739]  domain 0: span 0,2 level SIBLING
[   16.562741]   groups: 2 (cpu_power = 589) 0 (cpu_power = 589)
[   16.562745]   domain 1: span 0-3 level MC
[   16.562746]    groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
[   16.562751] CPU3 attaching sched-domain:
[   16.562752]  domain 0: span 1,3 level SIBLING
[   16.562754]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
[   16.562758]   domain 1: span 0-3 level MC
[   16.562760]    groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
[   20.056442] eth0: no IPv6 routers present
[ 1141.595638] __ratelimit: 18 callbacks suppressed
[ 1141.595642] mdadm: sending ioctl 1261 to a partition!
[ 1141.595645] mdadm: sending ioctl 1261 to a partition!
[ 1157.930421] mdadm: sending ioctl 1261 to a partition!
[ 1157.930426] mdadm: sending ioctl 1261 to a partition!

```

then what should I do?

I have ups but is under repair,I am newbie in ubuntu, I just asked to keep these servers after the administrator get out of here

---

### Post by tgalati4 on 2013-02-08
Although this looks troubling:

[ 1141.595638] __ratelimit: 18 callbacks suppressed
[ 1141.595642] mdadm: sending ioctl 1261 to a partition!
[ 1141.595645] mdadm: sending ioctl 1261 to a partition!

A quick search shows that it is simply flush buffer commands that are suppressed in newer kernels.

I don't see any hardware issues, so let's assume that you have some file corruption.

What is causing these?

[Fri Feb 08 00:07:38 2013] [notice] caught SIGTERM, shutting down

SIGTERM is a normal termination signal usually sent by another process to shut down gracefully.  So we need to find out what process is sending this signal to kill the Apache server.  Is it the PHP interpreter or something else?

When you rebooted the server manually, what messages come up regarding the starting of your web services?  Do all of the services come up normally?  Does the mysql database start normally?  Check more of the log files in /var/log to determine what is going on.

---

### Post by pojokan on 2013-02-18
problem solved

in this case there is an error in the Comments starting with '#' are deprecated in / etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0 should be on line 1 ';' instead of '#'

then the joomla configuration.php less signs' before;

:KS tgalati4, thank you for your attention to me that this was a newbie

---

### Post by tgalati4 on 2013-02-18
Sounds like something got updated, but there was no restart until the power outage.  The updated code runs and crashes--this is called regression.  Changes to interpretation of configuration files will cause breakage, which makes me think that some updates were applied, but not rebooted in a controlled manner.  Otherwise you would have these problems at a time other than a power outage.

---

### Post by SeijiSensei on 2013-02-18
> ```
Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini
```

Not to mention this seems like an especially stupid regression.  Why would you deprecate the use of the hash sign to denote comments in configuration files?  I find the [ISC]("http://www.isc.org/") style with lots and lots of semicolons (see BIND and DHCPD for examples) annoying.  I keep putting hash marks in BIND zone files and keeping the zone from loading.  Gee, fellas, you could accept both "#" and ";" as comment delimiters, instead of deprecating "#".  Guess I need to go read the rationale for this decision by the developers at php.net.

There's a bug report filed for this: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/573436](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/573436).  It dates back to 2010.  Someone running 12.04 reported it as late as last October.

To see if you have any configuration files that need to have the "#" changed to ";", use this:
```

cd /etc/php5/apache2/conf.d
sudo grep '#' *

```
If no files are listed, you've found all the problems.

**Update:** There's no official justification I can find.  I did come across some folks talking about this on [reddit]("http://www.reddit.com/r/PHP/comments/18dgn3/why_are_hash_comments_deprecated/").  One said that the standard style for .ini files is the semicolon.  I don't think any of them had an idea why the change was made.  It happened in [5.3](http://php.net/manual/en/migration53.deprecated.php).

---

### Post by tgalati4 on 2013-02-18
This change has burned me as well, but it didn't occur to me from reading the original post.  I was thrown off by "power outage" and thinking of all of the bad things that can happen with a sudden loss of power.  Misreading comments is not one of them!

---

