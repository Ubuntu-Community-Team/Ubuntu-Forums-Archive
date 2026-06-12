---
title: "Ubuntu server 12.04.02LTS amd64 does not route after libc6-dev update"
date: 2013-04-10
forum: Server Platforms
---

### Post by duesentriebchen on 2013-04-10
Hy there :)

I have a Ubuntu server 12.04.02LTS amd64 box configured as a primary firewall and router.

I have these network devices installed.

eth0 -> WAN
eth1 -> LAN, prerouting to the DMZ -> Web-, FTP-, Mailserver
eth2 -> LAN, Kubuntu client
wlan0 -> LAN, Mobile devices

Everything was working fine, until yesterday morning.
I did an update and following packets where **installed**.
```
[COLOR=#000000]linux-headers-3.2.0-40:amd64
[/COLOR][COLOR=#000000]linux-headers-3.2.0-40-generic:amd64
[/COLOR][COLOR=#000000]linux-image-3.2.0-40-generic:amd64[/COLOR][COLOR=#000000]
[/COLOR]
```[COLOR=#000000]

Following packets where **updated**.
[/COLOR]```
[COLOR=#000000]linux-generic:amd64 3.2.0.39.47 -> 3.2.0.40.48
[/COLOR][COLOR=#000000]linux-headers-generic:amd64 3.2.0.39.47 -> 3.2.0.40.48
[/COLOR][COLOR=#000000]linux-image-generic:amd64 3.2.0.39.47 -> 3.2.0.40.48
[/COLOR][COLOR=#000000]linux-libc-dev:amd64 3.2.0-39.62 -> 3.2.0-40.64[/COLOR]
```[COLOR=#000000]

Since these updates, my router does not route traffic to the WAN.
The "funny" thing is, that i can communicate from the LAN on eth2 to the DMZ on eth1 without any problems, except for encrypted connections via SSL or TSL(SSL/TSL [/COLOR][COLOR=#000000]shutdowns and failures)[/COLOR][COLOR=#000000].
I also can do a ping from the LAN to the WAN successfully.
When i try to do an update on the client on eth2, the GPG keys get an awnser, but the connection via http fails, same on eth1 for the DMZ.
The router itself establishes connections on eth0 to the WAN.

De facto i can not establish connections from the LAN via router to the WAN since yesterday morning.

The iptables-rules have not been changed since yesterday morning, so i can confirm that these where working until the updates where installed.

Is it possible that the libc-dev libaries collide with the iptables-rules/libaries?

I do not know how to figure this one out...

[/COLOR]

---

### Post by duesentriebchen on 2013-04-11
Nobody.... :(

hanging and waiting for help...

---

### Post by steeldriver on 2013-04-11
> **duesentriebchen said:**
> [COLOR=#000000]
I also can do a ping from the LAN to the WAN successfully.
When i try to do an update on the client on eth2, the GPG keys get an awnser, but the connection via http fails, same on eth1 for the DMZ.
The router itself establishes connections on eth0 to the WAN.
[/COLOR]

Are you sure it's a routing issue not a name resolution issue? can you ping external hosts via IP?

---

### Post by duesentriebchen on 2013-04-12
Hy steeldriver :)

Thank you for your reply!

Yes i can ping external addresses from the LAN like ```
ping -c 5 google.com
```

The name resolution is done and the ping is successfull.

Today i did a look in the ```
/var/log/syslog
```

After the new Kernel was installed there is shown a section that refers to the routing table. I can not remember the exact output at the moment. I will post it when i am at home in 2 hours.

The curious thing is, that the server in the DMZ -served by iptables prerouting and forwarding from the router- is not affected with this issue.

Only the LAN (including the WLAN) can not access the WAN but i am able to connect from the LAN to the server in the DMZ....

[COLOR=#000000][B]_EDIT_

[/B]1.)Here you find the syslog entry form the ROUTER, when the update was made. I tried to mark out some entries.

[/COLOR]```
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Initializing cgroup subsys cpusetApr  9 06:36:22 myfirstex kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Linux version 3.2.0-40-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #64-Ubuntu SMP Mon Mar 25 21:22:10 UTC 20$
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-40-generic root=UUID=6dd667a3-845b-4550-b578-367976a91955 ro splash quiet vt.handoff=7
Apr  9 06:36:22 myfirstex kernel: [    0.000000] KERNEL supported cpus:
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   Intel GenuineIntel
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   AMD AuthenticAMD
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   Centaur CentaurHauls
Apr  9 06:36:22 myfirstex kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000000e2000 - 0000000000100000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000d7f90000 (usable)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000d7f9e000 - 00000000d7fa0000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000d7fa0000 - 00000000d7fae000 (ACPI data)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000d7fae000 - 00000000d7fe0000 (ACPI NVS)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000d7fe0000 - 00000000d8000000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 00000000ffa00000 - 0000000100000000 (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001a0000000 (usable)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  9 06:36:22 myfirstex kernel: [    0.000000] SMBIOS 2.6 present.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] DMI: HP ProLiant MicroServer, BIOS O41     07/29/2011
Apr  9 06:36:22 myfirstex kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] No AGP bridge found
Apr  9 06:36:22 myfirstex kernel: [    0.000000] last_pfn = 0x1a0000 max_arch_pfn = 0x400000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] MTRR default type: uncachable
Apr  9 06:36:22 myfirstex kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   00000-9FFFF write-back
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   A0000-EFFFF uncachable
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   F0000-FFFFF write-protect
Apr  9 06:36:22 myfirstex kernel: [    0.000000] MTRR variable ranges enabled:
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   2 base 0000C0000000 mask FFFFE0000000 write-back
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   3 disabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   4 disabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   5 disabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   6 disabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   7 disabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000] TOM2: 00000001a0000000 aka 6656M
Apr  9 06:36:22 myfirstex kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  9 06:36:22 myfirstex kernel: [    0.000000] e820 update range: 00000000e0000000 - 0000000100000000 (usable) ==> (reserved)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] last_pfn = 0xd7f90 max_arch_pfn = 0x400000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Apr  9 06:36:22 myfirstex kernel: [    0.000000] initial memory mapped : 0 - 20000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Using GB pages for direct mapping
Apr  9 06:36:22 myfirstex kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000d7f90000
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  0000000000 - 00c0000000 page 1G
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  00c0000000 - 00d7e00000 page 2M
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  00d7e00000 - 00d7f90000 page 4k
Apr  9 06:36:22 myfirstex kernel: [    0.000000] kernel direct mapping tables up to d7f90000 @ 1fffd000-20000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] init_memory_mapping: 0000000100000000-00000001a0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  0100000000 - 0180000000 page 1G
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  0180000000 - 01a0000000 page 2M
Apr  9 06:36:22 myfirstex kernel: [    0.000000] kernel direct mapping tables up to 1a0000000 @ d7f8e000-d7f90000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] RAMDISK: 35e3e000 - 36f17000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: RSDP 00000000000f8f50 00024 (v02 HP    )
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: XSDT 00000000d7fa0100 0007C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: FACP 00000000d7fa0290 000F4 (v03 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: DSDT 00000000d7fa0620 06947 (v01 HP     ProLiant 00000006 INTL 20051117)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: FACS 00000000d7fae000 00040
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: APIC 00000000d7fa0390 00072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: MCFG 00000000d7fa0410 0003C (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: SPMI 00000000d7fa0450 00041 (v05 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: OEMB 00000000d7fae040 00072 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: HPET 00000000d7fab4e0 00038 (v01 HP     ProLiant 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: EINJ 00000000d7fab520 00130 (v01  AMIER AMI_EINJ 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: BERT 00000000d7fab6b0 00030 (v01  AMIER AMI_BERT 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: ERST 00000000d7fab6e0 001B0 (v01  AMIER AMI_ERST 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: HEST 00000000d7fab890 000A8 (v01  AMIER ABC_HEST 20110729 HP   00000097)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: SSDT 00000000d7fab940 00458 (v01 HP     ProLiant 00000001 AMD  00000001)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Apr  9 06:36:22 myfirstex kernel: [    0.000000] No NUMA configuration found
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Faking a node at 0000000000000000-00000001a0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Initmem setup node 0 0000000000000000-00000001a0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   NODE_DATA [000000019fffb000 - 000000019fffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.000000]  [ffffea0000000000-ffffea00067fffff] PMD -> [ffff880199800000-ffff88019f5fffff] on node 0
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Zone PFN ranges:
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   Normal   0x00100000 -> 0x001a0000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Movable zone start PFN for each node
Apr  9 06:36:22 myfirstex kernel: [    0.000000] early_node_map[3] active PFN ranges
Apr  9 06:36:22 myfirstex kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Apr  9 06:36:22 myfirstex kernel: [    0.000000]     0: 0x00000100 -> 0x000d7f90
Apr  9 06:36:22 myfirstex kernel: [    0.000000]     0: 0x00100000 -> 0x001a0000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] On node 0 totalpages: 1539870
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA zone: 5 pages reserved
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA zone: 3913 pages, LIFO batch:0
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA32 zone: 16320 pages used for memmap
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   DMA32 zone: 864208 pages, LIFO batch:31
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   Normal zone: 10240 pages used for memmap
Apr  9 06:36:22 myfirstex kernel: [    0.000000]   Normal zone: 645120 pages, LIFO batch:31
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  9 06:36:22 myfirstex kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 33, address 0xfec00000, GSI 0-23
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  9 06:36:22 myfirstex kernel: [    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr  9 06:36:22 myfirstex kernel: [    0.000000] nr_irqs_gsi: 40
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e2000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000000e2000 - 0000000000100000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d7f90000 - 00000000d7f9e000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d7f9e000 - 00000000d7fa0000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fa0000 - 00000000d7fae000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fae000 - 00000000d7fe0000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d7fe0000 - 00000000d8000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000d8000000 - 00000000e0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000ffa00000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000ffa00000 - 0000000100000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Allocating PCI resources starting at f0000000 (gap: f0000000:fa00000)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  9 06:36:22 myfirstex kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88019fc00000 s83136 r8192 d23360 u524288
Apr  9 06:36:22 myfirstex kernel: [    0.000000] pcpu-alloc: s83136 r8192 d23360 u524288 alloc=1*2097152
Apr  9 06:36:22 myfirstex kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1513241
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Policy zone: Normal
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-40-generic root=UUID=6dd667a3-845b-4550-b578-367976a91955 ro splash quiet vt.handoff=7
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Checking aperture...
Apr  9 06:36:22 myfirstex kernel: [    0.000000] No AGP bridge found
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Node 0: aperture @ cc000000 size 32 MB
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr  9 06:36:22 myfirstex kernel: [    0.000000] This costs you 64 MB of RAM
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ cc000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] PM: Registered nosave memory: 00000000cc000000 - 00000000d0000000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Memory: 5898108k/6815744k available (6574k kernel code, 656264k absent, 261372k reserved, 6629k data, 920k init)
Apr  9 06:36:22 myfirstex kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Hierarchical RCU implementation.
Apr  9 06:36:22 myfirstex kernel: [    0.000000]        RCU dyntick-idle grace-period acceleration is enabled.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] NR_IRQS:16640 nr_irqs:712 16
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Extended CMOS year: 2000
Apr  9 06:36:22 myfirstex kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr  9 06:36:22 myfirstex kernel: [    0.000000] vt handoff: transparent VT on vt#7
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Console: colour dummy device 80x25
Apr  9 06:36:22 myfirstex kernel: [    0.000000] console [tty0] enabled
Apr  9 06:36:22 myfirstex kernel: [    0.000000] allocated 49283072 bytes of page_cgroup
Apr  9 06:36:22 myfirstex kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  9 06:36:22 myfirstex kernel: [    0.000000] hpet clockevent registered
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Fast TSC calibration failed
Apr  9 06:36:22 myfirstex kernel: [    0.000000] TSC: PIT calibration matches HPET. 2 loops
Apr  9 06:36:22 myfirstex kernel: [    0.000000] Detected 1497.517 MHz processor.
Apr  9 06:36:22 myfirstex kernel: [    0.012005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2995.03 BogoMIPS (lpj=5990068)
Apr  9 06:36:22 myfirstex kernel: [    0.012012] pid_max: default: 32768 minimum: 301
Apr  9 06:36:22 myfirstex kernel: [    0.012047] Security Framework initialized
Apr  9 06:36:22 myfirstex kernel: [    0.012068] AppArmor: AppArmor initialized
Apr  9 06:36:22 myfirstex kernel: [    0.012071] Yama: becoming mindful.
Apr  9 06:36:22 myfirstex kernel: [    0.013032] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.017928] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.020134] Mount-cache hash table entries: 256
Apr  9 06:36:22 myfirstex kernel: [    0.020319] Initializing cgroup subsys cpuacct
Apr  9 06:36:22 myfirstex kernel: [    0.020327] Initializing cgroup subsys memory
Apr  9 06:36:22 myfirstex kernel: [    0.020340] Initializing cgroup subsys devices
Apr  9 06:36:22 myfirstex kernel: [    0.020344] Initializing cgroup subsys freezer
Apr  9 06:36:22 myfirstex kernel: [    0.020346] Initializing cgroup subsys blkio
Apr  9 06:36:22 myfirstex kernel: [    0.020356] Initializing cgroup subsys perf_event
Apr  9 06:36:22 myfirstex kernel: [    0.020394] tseg: 0000000000
Apr  9 06:36:22 myfirstex kernel: [    0.020414] CPU: Physical Processor ID: 0
Apr  9 06:36:22 myfirstex kernel: [    0.020416] CPU: Processor Core ID: 0
Apr  9 06:36:22 myfirstex kernel: [    0.020420] mce: CPU supports 6 MCE banks
Apr  9 06:36:22 myfirstex kernel: [    0.020432] using AMD E400 aware idle routine
Apr  9 06:36:22 myfirstex kernel: [    0.022610] ACPI: Core revision 20110623
Apr  9 06:36:22 myfirstex kernel: [    0.028015] ftrace: allocating 26565 entries in 105 pages
Apr  9 06:36:22 myfirstex kernel: [    0.032462] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  9 06:36:22 myfirstex kernel: [    0.075036] CPU0: AMD Turion(tm) II Neo N40L Dual-Core Processor stepping 03
Apr  9 06:36:22 myfirstex kernel: [    0.076004] Performance Events: AMD PMU driver.
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... version:                0
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... bit width:              48
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... generic registers:      4
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... value mask:             0000ffffffffffff
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... max period:             00007fffffffffff
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... fixed-purpose events:   0
Apr  9 06:36:22 myfirstex kernel: [    0.076004] ... event mask:             000000000000000f
Apr  9 06:36:22 myfirstex kernel: [    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
Apr  9 06:36:22 myfirstex kernel: [    0.076004] Booting Node   0, Processors  #1
Apr  9 06:36:22 myfirstex kernel: [    0.076004] smpboot cpu 1: start_ip = 99000
Apr  9 06:36:22 myfirstex kernel: [    0.168015] NMI watchdog enabled, takes one hw-pmu counter.
Apr  9 06:36:22 myfirstex kernel: [    0.168044] Brought up 2 CPUs
Apr  9 06:36:22 myfirstex kernel: [    0.168048] Total of 2 processors activated (6006.77 BogoMIPS).
Apr  9 06:36:22 myfirstex kernel: [    0.168044] System has AMD C1E enabled
Apr  9 06:36:22 myfirstex kernel: [    0.168060] Switch to broadcast mode on CPU1
Apr  9 06:36:22 myfirstex kernel: [    0.168853] Switch to broadcast mode on CPU0
Apr  9 06:36:22 myfirstex kernel: [    0.168853] devtmpfs: initialized
Apr  9 06:36:22 myfirstex kernel: [    0.170632] EVM: security.selinux
Apr  9 06:36:22 myfirstex kernel: [    0.170634] EVM: security.SMACK64
Apr  9 06:36:22 myfirstex kernel: [    0.170636] EVM: security.capability
Apr  9 06:36:22 myfirstex kernel: [    0.170763] PM: Registering ACPI NVS region at d7fae000 (204800 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.170763] print_constraints: dummy:
Apr  9 06:36:22 myfirstex kernel: [    0.170763] RTC time:  4:36:09, date: 04/09/13
Apr  9 06:36:22 myfirstex kernel: [    0.170763] NET: Registered protocol family 16
Apr  9 06:36:22 myfirstex kernel: [    0.173232] Trying to unpack rootfs image as initramfs...
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: io port [1000, ffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] TOM: 00000000e0000000 aka 3584M
Apr  9 06:36:22 myfirstex kernel: [    0.173232] Fam 10h mmconf [mem 0xe0000000-0xefffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: mmio [a0000, bffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: mmio [e0000000, f7ffffff] ==> [f0000000, f7ffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: mmio [f8000000, fe4fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: mmio [fe500000, fe6fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] node 0 link 0: mmio [fe700000, ffdfffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] TOM2: 00000001a0000000 aka 6656M
Apr  9 06:36:22 myfirstex kernel: [    0.173232] bus: [00, 1f] on node 0 link 0
Apr  9 06:36:22 myfirstex kernel: [    0.173232] bus: 00 index 0 [io  0x0000-0xffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] bus: 00 index 1 [mem 0x000a0000-0x000bffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] bus: 00 index 2 [mem 0xf0000000-0xffffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] bus: 00 index 3 [mem 0x1a0000000-0xfcffffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.173232] Extended Config Space enabled on 1 nodes
Apr  9 06:36:22 myfirstex kernel: [    0.173232] ACPI: bus type pci registered
Apr  9 06:36:22 myfirstex kernel: [    0.173232] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr  9 06:36:22 myfirstex kernel: [    0.173232] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Apr  9 06:36:22 myfirstex kernel: [    0.207498] PCI: Using configuration type 1 for base access
Apr  9 06:36:22 myfirstex kernel: [    0.212012] bio: create slab <bio-0> at 0
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: Added _OSI(Module Device)
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: Added _OSI(Processor Device)
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: Added _OSI(Processor Aggregator Device)
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: EC: Look up EC in DSDT
Apr  9 06:36:22 myfirstex kernel: [    0.212012] ACPI: Executed 2 blocks of module-level executable AML code
Apr  9 06:36:22 myfirstex kernel: [    0.214364] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Apr  9 06:36:22 myfirstex kernel: [    0.248119] ACPI: OEMN 00000000d7faaeb0 00624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 06:36:22 myfirstex kernel: [    0.248439] ACPI: Dynamic OEM Table Load:
Apr  9 06:36:22 myfirstex kernel: [    0.248444] ACPI: OEMN           (null) 00624 (v01 AMD    NAHP     00000001 INTL 20051117)
Apr  9 06:36:22 myfirstex kernel: [    0.280205] \_SB_:_OSC evaluation returned wrong type
Apr  9 06:36:22 myfirstex kernel: [    0.280210] _OSC request data:1 17
Apr  9 06:36:22 myfirstex kernel: [    0.280427] ACPI: Interpreter enabled
Apr  9 06:36:22 myfirstex kernel: [    0.280432] ACPI: (supports S0 S4 S5)
Apr  9 06:36:22 myfirstex kernel: [    0.280456] ACPI: Using IOAPIC for interrupt routing
Apr  9 06:36:22 myfirstex kernel: [    0.285695] ACPI: No dock devices found.
Apr  9 06:36:22 myfirstex kernel: [    0.285740] HEST: Table parsing has been initialized.
Apr  9 06:36:22 myfirstex kernel: [    0.285745] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr  9 06:36:22 myfirstex kernel: [    0.286592] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  9 06:36:22 myfirstex kernel: [    0.287274] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Apr  9 06:36:22 myfirstex kernel: [    0.287278] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287282] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287286] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287290] pci_root PNP0A08:00: host bridge window [mem 0xd8000000-0xdfffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287294] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xfebfffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287297] pci_root PNP0A08:00: host bridge window [mem 0xd8000000-0xdfffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287301] pci_root PNP0A08:00: host bridge window [mem 0xf0000000-0xffffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287307] pci_root PNP0A08:00: host bridge window expanded to [mem 0xd8000000-0xdfffffff]; [mem 0xd8000000-0xdfffffff] ignored
Apr  9 06:36:22 myfirstex kernel: [    0.287312] pci_root PNP0A08:00: host bridge window expanded to [mem 0xf0000000-0xffffffff]; [mem 0xf0000000-0xffffffff] ignored
Apr  9 06:36:22 myfirstex kernel: [    0.287320] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000d0000-0x000dffff] (conflicts with Adapter ROM [mem 0x000cf000-0x000d19ff])
Apr  9 06:36:22 myfirstex kernel: [    0.287339] pci 0000:00:00.0: [1022:9601] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.287408] pci 0000:00:01.0: [103c:9602] type 1 class 0x000604
Apr  9 06:36:22 myfirstex kernel: [    0.287454] pci 0000:00:02.0: [1022:9603] type 1 class 0x000604
Apr  9 06:36:22 myfirstex kernel: [    0.287500] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.287505] pci 0000:00:02.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.287528] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
Apr  9 06:36:22 myfirstex kernel: [    0.287573] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.287577] pci 0000:00:04.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.287599] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
Apr  9 06:36:22 myfirstex kernel: [    0.287643] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.287647] pci 0000:00:06.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.287685] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
Apr  9 06:36:22 myfirstex kernel: [    0.287708] pci 0000:00:11.0: reg 10: [io  0xc000-0xc007]
Apr  9 06:36:22 myfirstex kernel: [    0.287720] pci 0000:00:11.0: reg 14: [io  0xb000-0xb003]
Apr  9 06:36:22 myfirstex kernel: [    0.287731] pci 0000:00:11.0: reg 18: [io  0xa000-0xa007]
Apr  9 06:36:22 myfirstex kernel: [    0.287742] pci 0000:00:11.0: reg 1c: [io  0x9000-0x9003]
Apr  9 06:36:22 myfirstex kernel: [    0.287754] pci 0000:00:11.0: reg 20: [io  0x8000-0x800f]
Apr  9 06:36:22 myfirstex kernel: [    0.287765] pci 0000:00:11.0: reg 24: [mem 0xfe4ffc00-0xfe4fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.287839] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.287854] pci 0000:00:12.0: reg 10: [mem 0xfe4fe000-0xfe4fefff]
Apr  9 06:36:22 myfirstex kernel: [    0.287929] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.287950] pci 0000:00:12.2: reg 10: [mem 0xfe4ff800-0xfe4ff8ff]
Apr  9 06:36:22 myfirstex kernel: [    0.288048] pci 0000:00:12.2: supports D1 D2
Apr  9 06:36:22 myfirstex kernel: [    0.288051] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr  9 06:36:22 myfirstex kernel: [    0.288056] pci 0000:00:12.2: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.288080] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.288095] pci 0000:00:13.0: reg 10: [mem 0xfe4fd000-0xfe4fdfff]
Apr  9 06:36:22 myfirstex kernel: [    0.288170] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.288191] pci 0000:00:13.2: reg 10: [mem 0xfe4ff400-0xfe4ff4ff]
Apr  9 06:36:22 myfirstex kernel: [    0.288277] pci 0000:00:13.2: supports D1 D2
Apr  9 06:36:22 myfirstex kernel: [    0.288280] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr  9 06:36:22 myfirstex kernel: [    0.288286] pci 0000:00:13.2: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.288309] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
Apr  9 06:36:22 myfirstex kernel: [    0.288387] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
Apr  9 06:36:22 myfirstex kernel: [    0.288402] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
Apr  9 06:36:22 myfirstex kernel: [    0.288413] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
Apr  9 06:36:22 myfirstex kernel: [    0.288425] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
Apr  9 06:36:22 myfirstex kernel: [    0.288436] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
Apr  9 06:36:22 myfirstex kernel: [    0.288447] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
Apr  9 06:36:22 myfirstex kernel: [    0.288489] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
Apr  9 06:36:22 myfirstex kernel: [    0.288570] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
Apr  9 06:36:22 myfirstex kernel: [    0.288620] pci 0000:00:16.0: [1002:4397] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.288636] pci 0000:00:16.0: reg 10: [mem 0xfe4fc000-0xfe4fcfff]
Apr  9 06:36:22 myfirstex kernel: [    0.288711] pci 0000:00:16.2: [1002:4396] type 0 class 0x000c03
Apr  9 06:36:22 myfirstex kernel: [    0.288732] pci 0000:00:16.2: reg 10: [mem 0xfe4ff000-0xfe4ff0ff]
Apr  9 06:36:22 myfirstex kernel: [    0.288817] pci 0000:00:16.2: supports D1 D2
Apr  9 06:36:22 myfirstex kernel: [    0.288820] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr  9 06:36:22 myfirstex kernel: [    0.288826] pci 0000:00:16.2: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.288848] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.288872] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.288891] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.288911] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.288940] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
Apr  9 06:36:22 myfirstex kernel: [    0.288997] pci 0000:01:05.0: [1002:9712] type 0 class 0x000300
Apr  9 06:36:22 myfirstex kernel: [    0.289009] pci 0000:01:05.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
Apr  9 06:36:22 myfirstex kernel: [    0.289016] pci 0000:01:05.0: reg 14: [io  0xd000-0xd0ff]
Apr  9 06:36:22 myfirstex kernel: [    0.289022] pci 0000:01:05.0: reg 18: [mem 0xfe6f0000-0xfe6fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289036] pci 0000:01:05.0: reg 24: [mem 0xfe500000-0xfe5fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289059] pci 0000:01:05.0: supports D1 D2
Apr  9 06:36:22 myfirstex kernel: [    0.289101] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr  9 06:36:22 myfirstex kernel: [    0.289107] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Apr  9 06:36:22 myfirstex kernel: [    0.289111] pci 0000:00:01.0:   bridge window [mem 0xfe500000-0xfe6fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289117] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 06:36:22 myfirstex kernel: [    0.289162] pci 0000:02:00.0: [8086:105e] type 0 class 0x000200
Apr  9 06:36:22 myfirstex kernel: [    0.289178] pci 0000:02:00.0: reg 10: [mem 0xfe7e0000-0xfe7fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289189] pci 0000:02:00.0: reg 14: [mem 0xfe7c0000-0xfe7dffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289200] pci 0000:02:00.0: reg 18: [io  0xe800-0xe81f]
Apr  9 06:36:22 myfirstex kernel: [    0.289233] pci 0000:02:00.0: reg 30: [mem 0xfe7a0000-0xfe7bffff pref]
Apr  9 06:36:22 myfirstex kernel: [    0.289277] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.289283] pci 0000:02:00.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.289314] pci 0000:02:00.1: [8086:105e] type 0 class 0x000200
Apr  9 06:36:22 myfirstex kernel: [    0.289329] pci 0000:02:00.1: reg 10: [mem 0xfe780000-0xfe79ffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289340] pci 0000:02:00.1: reg 14: [mem 0xfe760000-0xfe77ffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289351] pci 0000:02:00.1: reg 18: [io  0xe400-0xe41f]
Apr  9 06:36:22 myfirstex kernel: [    0.289384] pci 0000:02:00.1: reg 30: [mem 0xfe740000-0xfe75ffff pref]
Apr  9 06:36:22 myfirstex kernel: [    0.289428] pci 0000:02:00.1: PME# supported from D0 D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.289433] pci 0000:02:00.1: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.289455] pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Apr  9 06:36:22 myfirstex kernel: [    0.289467] pci 0000:00:02.0: PCI bridge to [bus 02-02]
Apr  9 06:36:22 myfirstex kernel: [    0.289473] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Apr  9 06:36:22 myfirstex kernel: [    0.289477] pci 0000:00:02.0:   bridge window [mem 0xfe700000-0xfe7fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.289524] pci 0000:03:00.0: [168c:0030] type 0 class 0x000280
Apr  9 06:36:22 myfirstex kernel: [    0.289544] pci 0000:03:00.0: reg 10: [mem 0xfe8e0000-0xfe8fffff 64bit]
Apr  9 06:36:22 myfirstex kernel: [    0.289586] pci 0000:03:00.0: reg 30: [mem 0xfe8d0000-0xfe8dffff pref]
Apr  9 06:36:22 myfirstex kernel: [    0.289631] pci 0000:03:00.0: supports D1
Apr  9 06:36:22 myfirstex kernel: [    0.289633] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
Apr  9 06:36:22 myfirstex kernel: [    0.289639] pci 0000:03:00.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.296063] pci 0000:00:04.0: PCI bridge to [bus 03-03]
Apr  9 06:36:22 myfirstex kernel: [    0.296074] pci 0000:00:04.0:   bridge window [mem 0xfe800000-0xfe8fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.296135] pci 0000:04:00.0: [14e4:165b] type 0 class 0x000200
Apr  9 06:36:22 myfirstex kernel: [    0.296158] pci 0000:04:00.0: reg 10: [mem 0xfe9f0000-0xfe9fffff 64bit]
Apr  9 06:36:22 myfirstex kernel: [    0.296274] pci 0000:04:00.0: PME# supported from D3hot D3cold
Apr  9 06:36:22 myfirstex kernel: [    0.296281] pci 0000:04:00.0: PME# disabled
Apr  9 06:36:22 myfirstex kernel: [    0.304069] pci 0000:00:06.0: PCI bridge to [bus 04-04]
Apr  9 06:36:22 myfirstex kernel: [    0.304079] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.304154] pci 0000:00:14.4: PCI bridge to [bus 05-05] (subtractive decode)
Apr  9 06:36:22 myfirstex kernel: [    0.304165] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Apr  9 06:36:22 myfirstex kernel: [    0.304169] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr  9 06:36:22 myfirstex kernel: [    0.304172] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr  9 06:36:22 myfirstex kernel: [    0.304176] pci 0000:00:14.4:   bridge window [mem 0xd8000000-0xdfffffff] (subtractive decode)
Apr  9 06:36:22 myfirstex kernel: [    0.304180] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xffffffff] (subtractive decode)
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex kernel: [    0.304205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  9 06:36:22 myfirstex kernel: [    0.304473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Apr  9 06:36:22 myfirstex kernel: [    0.304521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
Apr  9 06:36:22 myfirstex kernel: [    0.304572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
Apr  9 06:36:22 myfirstex kernel: [    0.304610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT][/COLOR]
Apr  9 06:36:22 myfirstex kernel: [    0.304879]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Apr  9 06:36:22 myfirstex kernel: [    0.305115]  pci0000:00: ACPI _OSC control (0x1d) granted
Apr  9 06:36:22 myfirstex kernel: [    0.313944] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314027] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314107] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314184] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314245] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314293] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314341] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314389] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr  9 06:36:22 myfirstex kernel: [    0.314549] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
Apr  9 06:36:22 myfirstex kernel: [    0.314555] vgaarb: loaded
Apr  9 06:36:22 myfirstex kernel: [    0.314557] vgaarb: bridge control possible 0000:01:05.0
Apr  9 06:36:22 myfirstex kernel: [    0.314697] i2c-core: driver [aat2870] using legacy suspend method
Apr  9 06:36:22 myfirstex kernel: [    0.314700] i2c-core: driver [aat2870] using legacy resume method
Apr  9 06:36:22 myfirstex kernel: [    0.314793] SCSI subsystem initialized
Apr  9 06:36:22 myfirstex kernel: [    0.316019] libata version 3.00 loaded.
Apr  9 06:36:22 myfirstex kernel: [    0.316019] usbcore: registered new interface driver usbfs
Apr  9 06:36:22 myfirstex kernel: [    0.316019] usbcore: registered new interface driver hub
Apr  9 06:36:22 myfirstex kernel: [    0.316019] usbcore: registered new device driver usb
Apr  9 06:36:22 myfirstex kernel: [    0.316019] PCI: Using ACPI for IRQ routing
Apr  9 06:36:22 myfirstex kernel: [    0.324204] PCI: pci_cache_line_size set to 64 bytes
Apr  9 06:36:22 myfirstex kernel: [    0.324302] reserve RAM buffer: 000000000009e800 - 000000000009ffff
Apr  9 06:36:22 myfirstex kernel: [    0.324306] reserve RAM buffer: 00000000d7f90000 - 00000000d7ffffff
Apr  9 06:36:22 myfirstex kernel: [    0.324435] NetLabel: Initializing
Apr  9 06:36:22 myfirstex kernel: [    0.324438] NetLabel:  domain hash size = 128
Apr  9 06:36:22 myfirstex kernel: [    0.324441] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  9 06:36:22 myfirstex kernel: [    0.324456] NetLabel:  unlabeled traffic allowed by default
Apr  9 06:36:22 myfirstex kernel: [    0.324521] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr  9 06:36:22 myfirstex kernel: [    0.324527] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr  9 06:36:22 myfirstex kernel: [    0.326580] Switching to clocksource hpet
Apr  9 06:36:22 myfirstex kernel: [    0.337006] AppArmor: AppArmor Filesystem Enabled
Apr  9 06:36:22 myfirstex kernel: [    0.337049] pnp: PnP ACPI init
Apr  9 06:36:22 myfirstex kernel: [    0.337074] ACPI: bus type pnp registered
Apr  9 06:36:22 myfirstex kernel: [    0.337486] pnp 00:00: [bus 00-ff]
Apr  9 06:36:22 myfirstex kernel: [    0.337490] pnp 00:00: [io  0x0cf8-0x0cff]
Apr  9 06:36:22 myfirstex kernel: [    0.337494] pnp 00:00: [io  0x0000-0x0cf7 window]
Apr  9 06:36:22 myfirstex kernel: [    0.337497] pnp 00:00: [io  0x0d00-0xffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337501] pnp 00:00: [mem 0x000a0000-0x000bffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337504] pnp 00:00: [mem 0x000d0000-0x000dffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337507] pnp 00:00: [mem 0xd8000000-0xdfffffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337511] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337514] pnp 00:00: [mem 0xd8000000-0xdfffffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337518] pnp 00:00: [mem 0xf0000000-0xffffffff window]
Apr  9 06:36:22 myfirstex kernel: [    0.337605] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.337742] pnp 00:01: [mem 0x00000000-0xffffffffffffffff disabled]
Apr  9 06:36:22 myfirstex kernel: [    0.337745] pnp 00:01: [mem 0xd8000000-0xdfffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.337820] system 00:01: [mem 0xd8000000-0xdfffffff] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.337826] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.337900] pnp 00:02: [dma 4]
Apr  9 06:36:22 myfirstex kernel: [    0.337903] pnp 00:02: [io  0x0000-0x000f]
Apr  9 06:36:22 myfirstex kernel: [    0.337906] pnp 00:02: [io  0x0081-0x0083]
Apr  9 06:36:22 myfirstex kernel: [    0.337909] pnp 00:02: [io  0x0087]
Apr  9 06:36:22 myfirstex kernel: [    0.337912] pnp 00:02: [io  0x0089-0x008b]
Apr  9 06:36:22 myfirstex kernel: [    0.337915] pnp 00:02: [io  0x008f]
Apr  9 06:36:22 myfirstex kernel: [    0.337918] pnp 00:02: [io  0x00c0-0x00df]
Apr  9 06:36:22 myfirstex kernel: [    0.337957] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.337971] pnp 00:03: [io  0x0070-0x0071]
Apr  9 06:36:22 myfirstex kernel: [    0.337989] pnp 00:03: [irq 8]
Apr  9 06:36:22 myfirstex kernel: [    0.338024] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.338077] pnp 00:04: [io  0x0061]
Apr  9 06:36:22 myfirstex kernel: [    0.338117] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.338128] pnp 00:05: [io  0x00f0-0x00ff]
Apr  9 06:36:22 myfirstex kernel: [    0.338135] pnp 00:05: [irq 13]
Apr  9 06:36:22 myfirstex kernel: [    0.338174] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.338207] pnp 00:06: [mem 0xfed00000-0xfed003ff]
Apr  9 06:36:22 myfirstex kernel: [    0.338244] pnp 00:06: Plug and Play ACPI device, IDs PNP0103 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.338347] pnp 00:07: [io  0x0060]
Apr  9 06:36:22 myfirstex kernel: [    0.338353] pnp 00:07: [io  0x0064]
Apr  9 06:36:22 myfirstex kernel: [    0.338356] pnp 00:07: [mem 0xfec00000-0xfec00fff]
Apr  9 06:36:22 myfirstex kernel: [    0.338359] pnp 00:07: [mem 0xfee00000-0xfee00fff]
Apr  9 06:36:22 myfirstex kernel: [    0.338426] system 00:07: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338431] system 00:07: [mem 0xfee00000-0xfee00fff] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338436] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.338612] pnp 00:08: [io  0x0010-0x001f]
Apr  9 06:36:22 myfirstex kernel: [    0.338615] pnp 00:08: [io  0x0022-0x003f]
Apr  9 06:36:22 myfirstex kernel: [    0.338618] pnp 00:08: [io  0x0062-0x0063]
Apr  9 06:36:22 myfirstex kernel: [    0.338621] pnp 00:08: [io  0x0065-0x006f]
Apr  9 06:36:22 myfirstex kernel: [    0.338624] pnp 00:08: [io  0x0072-0x007f]
Apr  9 06:36:22 myfirstex kernel: [    0.338627] pnp 00:08: [io  0x0080]
Apr  9 06:36:22 myfirstex kernel: [    0.338629] pnp 00:08: [io  0x0084-0x0086]
Apr  9 06:36:22 myfirstex kernel: [    0.338632] pnp 00:08: [io  0x0088]
Apr  9 06:36:22 myfirstex kernel: [    0.338635] pnp 00:08: [io  0x008c-0x008e]
Apr  9 06:36:22 myfirstex kernel: [    0.338638] pnp 00:08: [io  0x0090-0x009f]
Apr  9 06:36:22 myfirstex kernel: [    0.338641] pnp 00:08: [io  0x00a2-0x00bf]
Apr  9 06:36:22 myfirstex kernel: [    0.338643] pnp 00:08: [io  0x00b1]
Apr  9 06:36:22 myfirstex kernel: [    0.338646] pnp 00:08: [io  0x00e0-0x00ef]
Apr  9 06:36:22 myfirstex kernel: [    0.338649] pnp 00:08: [io  0x04d0-0x04d1]
Apr  9 06:36:22 myfirstex kernel: [    0.338652] pnp 00:08: [io  0x040b]
Apr  9 06:36:22 myfirstex kernel: [    0.338654] pnp 00:08: [io  0x04d6]
Apr  9 06:36:22 myfirstex kernel: [    0.338657] pnp 00:08: [io  0x0c00-0x0c01]
Apr  9 06:36:22 myfirstex kernel: [    0.338660] pnp 00:08: [io  0x0c14]
Apr  9 06:36:22 myfirstex kernel: [    0.338663] pnp 00:08: [io  0x0c50-0x0c51]Apr  9 06:36:22 myfirstex kernel: [    0.338666] pnp 00:08: [io  0x0c52]
Apr  9 06:36:22 myfirstex kernel: [    0.338668] pnp 00:08: [io  0x0c6c]
Apr  9 06:36:22 myfirstex kernel: [    0.338671] pnp 00:08: [io  0x0c6f]
Apr  9 06:36:22 myfirstex kernel: [    0.338673] pnp 00:08: [io  0x0cd0-0x0cd1]
Apr  9 06:36:22 myfirstex kernel: [    0.338676] pnp 00:08: [io  0x0cd2-0x0cd3]
Apr  9 06:36:22 myfirstex kernel: [    0.338679] pnp 00:08: [io  0x0cd4-0x0cd5]
Apr  9 06:36:22 myfirstex kernel: [    0.338682] pnp 00:08: [io  0x0cd6-0x0cd7]
Apr  9 06:36:22 myfirstex kernel: [    0.338685] pnp 00:08: [io  0x0cd8-0x0cdf]
Apr  9 06:36:22 myfirstex kernel: [    0.338688] pnp 00:08: [io  0x0800-0x089f]
Apr  9 06:36:22 myfirstex kernel: [    0.338691] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
Apr  9 06:36:22 myfirstex kernel: [    0.338694] pnp 00:08: [io  0x0b00-0x0b1f]
Apr  9 06:36:22 myfirstex kernel: [    0.338697] pnp 00:08: [io  0x0b20-0x0b3f]
Apr  9 06:36:22 myfirstex kernel: [    0.338700] pnp 00:08: [io  0x0900-0x090f]
Apr  9 06:36:22 myfirstex kernel: [    0.338703] pnp 00:08: [io  0x0910-0x091f]
Apr  9 06:36:22 myfirstex kernel: [    0.338706] pnp 00:08: [io  0xfe00-0xfefe]
Apr  9 06:36:22 myfirstex kernel: [    0.338709] pnp 00:08: [io  0x0060]
Apr  9 06:36:22 myfirstex kernel: [    0.338711] pnp 00:08: [io  0x0064]
Apr  9 06:36:22 myfirstex kernel: [    0.338714] pnp 00:08: [mem 0xffb80000-0xffbfffff]
Apr  9 06:36:22 myfirstex kernel: [    0.338718] pnp 00:08: [mem 0xfec10000-0xfec1001f]
Apr  9 06:36:22 myfirstex kernel: [    0.338721] pnp 00:08: [mem 0xfed80000-0xfed80fff]
Apr  9 06:36:22 myfirstex kernel: [    0.338725] pnp 00:08: [mem 0x00000000-0xffffffffffffffff disabled]
Apr  9 06:36:22 myfirstex kernel: [    0.338853] system 00:08: [io  0x04d0-0x04d1] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338857] system 00:08: [io  0x040b] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338861] system 00:08: [io  0x04d6] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338864] system 00:08: [io  0x0c00-0x0c01] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338868] system 00:08: [io  0x0c14] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338872] system 00:08: [io  0x0c50-0x0c51] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338876] system 00:08: [io  0x0c52] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338879] system 00:08: [io  0x0c6c] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338883] system 00:08: [io  0x0c6f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338887] system 00:08: [io  0x0cd0-0x0cd1] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338891] system 00:08: [io  0x0cd2-0x0cd3] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338894] system 00:08: [io  0x0cd4-0x0cd5] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338898] system 00:08: [io  0x0cd6-0x0cd7] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338902] system 00:08: [io  0x0cd8-0x0cdf] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338906] system 00:08: [io  0x0800-0x089f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338910] system 00:08: [io  0x0b00-0x0b1f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338914] system 00:08: [io  0x0b20-0x0b3f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338918] system 00:08: [io  0x0900-0x090f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338922] system 00:08: [io  0x0910-0x091f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338926] system 00:08: [io  0xfe00-0xfefe] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338931] system 00:08: [mem 0xffb80000-0xffbfffff] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338936] system 00:08: [mem 0xfec10000-0xfec1001f] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338940] system 00:08: [mem 0xfed80000-0xfed80fff] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.338945] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.339002] pnp 00:09: [mem 0xe0000000-0xefffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.339064] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
Apr  9 06:36:22 myfirstex kernel: [    0.339069] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.339196] pnp 00:0a: [mem 0x00000000-0x0009ffff]
Apr  9 06:36:22 myfirstex kernel: [    0.339200] pnp 00:0a: [mem 0x00000000-0xffffffffffffffff disabled]
Apr  9 06:36:22 myfirstex kernel: [    0.339204] pnp 00:0a: [mem 0x000e0000-0x000fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.339207] pnp 00:0a: [mem 0x00100000-0xd7ffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.339210] pnp 00:0a: [mem 0xfec00000-0xffffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.339239] pnp 00:0a: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xefffffff]; add$
Apr  9 06:36:22 myfirstex kernel: [    0.339295] system 00:0a: [mem 0x00000000-0x0009ffff] could not be reserved
Apr  9 06:36:22 myfirstex kernel: [    0.339300] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  9 06:36:22 myfirstex kernel: [    0.339305] system 00:0a: [mem 0x00100000-0xd7ffffff] could not be reserved
Apr  9 06:36:22 myfirstex kernel: [    0.339309] system 00:0a: [mem 0xfec00000-0xffffffff] could not be reserved
Apr  9 06:36:22 myfirstex kernel: [    0.339314] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr  9 06:36:22 myfirstex kernel: [    0.339430] pnp: PnP ACPI: found 11 devices
Apr  9 06:36:22 myfirstex kernel: [    0.339433] ACPI: ACPI bus type pnp unregistered
Apr  9 06:36:22 myfirstex kernel: [    0.346241] PCI: max bus depth: 1 pci_try_num: 2
Apr  9 06:36:22 myfirstex kernel: [    0.346271] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr  9 06:36:22 myfirstex kernel: [    0.346275] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
Apr  9 06:36:22 myfirstex kernel: [    0.346280] pci 0000:00:01.0:   bridge window [mem 0xfe500000-0xfe6fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346286] pci 0000:00:01.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 06:36:22 myfirstex kernel: [    0.346292] pci 0000:00:02.0: PCI bridge to [bus 02-02]
Apr  9 06:36:22 myfirstex kernel: [    0.346296] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Apr  9 06:36:22 myfirstex kernel: [    0.346301] pci 0000:00:02.0:   bridge window [mem 0xfe700000-0xfe7fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346308] pci 0000:00:04.0: PCI bridge to [bus 03-03]
Apr  9 06:36:22 myfirstex kernel: [    0.346312] pci 0000:00:04.0:   bridge window [mem 0xfe800000-0xfe8fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346319] pci 0000:00:06.0: PCI bridge to [bus 04-04]
Apr  9 06:36:22 myfirstex kernel: [    0.346323] pci 0000:00:06.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346330] pci 0000:00:14.4: PCI bridge to [bus 05-05]
Apr  9 06:36:22 myfirstex kernel: [    0.346362] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    0.346366] pci 0000:00:02.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    0.346379] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 06:36:22 myfirstex kernel: [    0.346384] pci 0000:00:04.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    0.346391] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    0.346395] pci 0000:00:06.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    0.346405] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Apr  9 06:36:22 myfirstex kernel: [    0.346409] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346413] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346416] pci_bus 0000:00: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346420] pci_bus 0000:00: resource 8 [mem 0xf0000000-0xffffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346424] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
Apr  9 06:36:22 myfirstex kernel: [    0.346428] pci_bus 0000:01: resource 1 [mem 0xfe500000-0xfe6fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346432] pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
Apr  9 06:36:22 myfirstex kernel: [    0.346436] pci_bus 0000:02: resource 0 [io  0xe000-0xefff]
Apr  9 06:36:22 myfirstex kernel: [    0.346440] pci_bus 0000:02: resource 1 [mem 0xfe700000-0xfe7fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346444] pci_bus 0000:03: resource 1 [mem 0xfe800000-0xfe8fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346448] pci_bus 0000:04: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346452] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Apr  9 06:36:22 myfirstex kernel: [    0.346456] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346460] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346463] pci_bus 0000:05: resource 7 [mem 0xd8000000-0xdfffffff]
Apr  9 06:36:22 myfirstex kernel: [    0.346467] pci_bus 0000:05: resource 8 [mem 0xf0000000-0xffffffff]
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex kernel: [    0.346522] NET: Registered protocol family 2
Apr  9 06:36:22 myfirstex kernel: [    0.346817] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.348798] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)Apr  9 06:36:22 myfirstex kernel: [    0.353350] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.353918] TCP: Hash tables configured (established 524288 bind 65536)
Apr  9 06:36:22 myfirstex kernel: [    0.353922] TCP reno registered
Apr  9 06:36:22 myfirstex kernel: [    0.353946] UDP hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.354044] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
Apr  9 06:36:22 myfirstex kernel: [    0.354255] NET: Registered protocol family 1[/COLOR]
Apr  9 06:36:22 myfirstex kernel: [    0.354272] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
Apr  9 06:36:22 myfirstex kernel: [    0.354309] pci 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.172123] pci 0000:00:12.0: PCI INT A disabled
Apr  9 06:36:22 myfirstex kernel: [    1.172160] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.172199] pci 0000:00:12.2: PCI INT B disabled
Apr  9 06:36:22 myfirstex kernel: [    1.172210] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.252128] pci 0000:00:13.0: PCI INT A disabled
Apr  9 06:36:22 myfirstex kernel: [    1.252153] pci 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.252188] pci 0000:00:13.2: PCI INT B disabled
Apr  9 06:36:22 myfirstex kernel: [    1.252208] pci 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.332117] pci 0000:00:16.0: PCI INT A disabled
Apr  9 06:36:22 myfirstex kernel: [    1.332140] pci 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.332176] pci 0000:00:16.2: PCI INT B disabled
Apr  9 06:36:22 myfirstex kernel: [    1.332197] pci 0000:01:05.0: Boot video device
Apr  9 06:36:22 myfirstex kernel: [    1.332212] PCI: CLS 64 bytes, default 64
Apr  9 06:36:22 myfirstex kernel: [    1.338730] PCI-DMA: Disabling AGP.
Apr  9 06:36:22 myfirstex kernel: [    1.338851] PCI-DMA: aperture base @ cc000000 size 65536 KB
Apr  9 06:36:22 myfirstex kernel: [    1.338853] PCI-DMA: using GART IOMMU.
Apr  9 06:36:22 myfirstex kernel: [    1.338857] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr  9 06:36:22 myfirstex kernel: [    1.343915] IBS: LVT offset 1 assigned
Apr  9 06:36:22 myfirstex kernel: [    1.343933] perf: AMD IBS detected (0x0000001f)
Apr  9 06:36:22 myfirstex kernel: [    1.344209] audit: initializing netlink socket (disabled)
Apr  9 06:36:22 myfirstex kernel: [    1.344224] type=2000 audit(1365482170.344:1): initialized
Apr  9 06:36:22 myfirstex kernel: [    1.380817] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  9 06:36:22 myfirstex kernel: [    1.383981] VFS: Disk quotas dquot_6.5.2
Apr  9 06:36:22 myfirstex kernel: [    1.384084] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  9 06:36:22 myfirstex kernel: [    1.384794] fuse init (API version 7.17)
Apr  9 06:36:22 myfirstex kernel: [    1.384907] msgmni has been set to 11648
Apr  9 06:36:22 myfirstex kernel: [    1.385314] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  9 06:36:22 myfirstex kernel: [    1.385351] io scheduler noop registered
Apr  9 06:36:22 myfirstex kernel: [    1.385354] io scheduler deadline registered
Apr  9 06:36:22 myfirstex kernel: [    1.385399] io scheduler cfq registered (default)
Apr  9 06:36:22 myfirstex kernel: [    1.386121] pcieport 0000:00:02.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    1.386167] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [    1.386524] pcieport 0000:00:04.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    1.386555] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [    1.386906] pcieport 0000:00:06.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    1.386936] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [    1.387139] pcieport 0000:00:02.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387145] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387148] pci 0000:02:00.1: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387153] pcie_pme 0000:00:02.0:pcie01: service driver pcie_pme loaded
Apr  9 06:36:22 myfirstex kernel: [    1.387173] pcieport 0000:00:04.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387177] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387181] pcie_pme 0000:00:04.0:pcie01: service driver pcie_pme loaded
Apr  9 06:36:22 myfirstex kernel: [    1.387198] pcieport 0000:00:06.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387202] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
Apr  9 06:36:22 myfirstex kernel: [    1.387206] pcie_pme 0000:00:06.0:pcie01: service driver pcie_pme loaded
Apr  9 06:36:22 myfirstex kernel: [    1.387231] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  9 06:36:22 myfirstex kernel: [    1.387264] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  9 06:36:22 myfirstex kernel: [    1.387448] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Apr  9 06:36:22 myfirstex kernel: [    1.387456] ACPI: Power Button [PWRB]
Apr  9 06:36:22 myfirstex kernel: [    1.387515] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  9 06:36:22 myfirstex kernel: [    1.387520] ACPI: Power Button [PWRF]
Apr  9 06:36:22 myfirstex kernel: [    1.387745] ACPI: processor limited to max C-state 1
Apr  9 06:36:22 myfirstex kernel: [    1.388995] APEI: Can not request iomem region <00000000d7fc21ea-00000000d7fc21ec> for GARs.
Apr  9 06:36:22 myfirstex kernel: [    1.389043] [Firmware Warn]: GHES: Poll interval is 0 for generic hardware error source: 1, disabled.
Apr  9 06:36:22 myfirstex kernel: [    1.389120] GHES: APEI firmware first mode is enabled by WHEA _OSC.
Apr  9 06:36:22 myfirstex kernel: [    1.389286] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr  9 06:36:22 myfirstex kernel: [    1.456960] Freeing initrd memory: 17252k freed
Apr  9 06:36:22 myfirstex kernel: [    1.496868] Linux agpgart interface v0.103
Apr  9 06:36:22 myfirstex kernel: [    1.500048] brd: module loaded
Apr  9 06:36:22 myfirstex kernel: [    1.501879] loop: module loaded
Apr  9 06:36:22 myfirstex kernel: [    1.502083] ahci 0000:00:11.0: version 3.0
Apr  9 06:36:22 myfirstex kernel: [    1.502115] ahci 0000:00:11.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  9 06:36:22 myfirstex kernel: [    1.502190] ahci 0000:00:11.0: irq 43 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [    1.502282] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
Apr  9 06:36:22 myfirstex kernel: [    1.502288] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part
Apr  9 06:36:22 myfirstex kernel: [    1.503140] scsi0 : ahci
Apr  9 06:36:22 myfirstex kernel: [    1.503349] scsi1 : ahci
Apr  9 06:36:22 myfirstex kernel: [    1.503540] scsi2 : ahci
Apr  9 06:36:22 myfirstex kernel: [    1.503743] scsi3 : ahci
Apr  9 06:36:22 myfirstex kernel: [    1.503838] ata1: SATA max UDMA/133 abar m1024@0xfe4ffc00 port 0xfe4ffd00 irq 43
Apr  9 06:36:22 myfirstex kernel: [    1.503844] ata2: SATA max UDMA/133 abar m1024@0xfe4ffc00 port 0xfe4ffd80 irq 43
Apr  9 06:36:22 myfirstex kernel: [    1.503849] ata3: SATA max UDMA/133 abar m1024@0xfe4ffc00 port 0xfe4ffe00 irq 43
Apr  9 06:36:22 myfirstex kernel: [    1.503854] ata4: SATA max UDMA/133 abar m1024@0xfe4ffc00 port 0xfe4ffe80 irq 43
Apr  9 06:36:22 myfirstex kernel: [    1.504027] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.504064] pata_acpi 0000:00:14.1: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    1.504520] Fixed MDIO Bus: probed
Apr  9 06:36:22 myfirstex kernel: [    1.504548] tun: Universal TUN/TAP device driver, 1.6
Apr  9 06:36:22 myfirstex kernel: [    1.504551] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  9 06:36:22 myfirstex kernel: [    1.504667] PPP generic driver version 2.4.2
Apr  9 06:36:22 myfirstex kernel: [    1.504891] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  9 06:36:22 myfirstex kernel: [    1.504914] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.504947] ehci_hcd 0000:00:12.2: EHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.505076] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr  9 06:36:22 myfirstex kernel: [    1.505089] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 06:36:22 myfirstex kernel: [    1.505114] QUIRK: Enable AMD PLL fix
Apr  9 06:36:22 myfirstex kernel: [    1.505128] ehci_hcd 0000:00:12.2: debug port 1
Apr  9 06:36:22 myfirstex kernel: [    1.505158] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe4ff800
Apr  9 06:36:22 myfirstex kernel: [    1.516151] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr  9 06:36:22 myfirstex kernel: [    1.516431] hub 1-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.516439] hub 1-0:1.0: 5 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.516605] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.516636] ehci_hcd 0000:00:13.2: EHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.516785] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr  9 06:36:22 myfirstex kernel: [    1.516797] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 06:36:22 myfirstex kernel: [    1.516828] ehci_hcd 0000:00:13.2: debug port 1
Apr  9 06:36:22 myfirstex kernel: [    1.516847] ehci_hcd 0000:00:13.2: irq 17, io mem 0xfe4ff400
Apr  9 06:36:22 myfirstex kernel: [    1.528128] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr  9 06:36:22 myfirstex kernel: [    1.528414] hub 2-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.528421] hub 2-0:1.0: 5 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.528587] ehci_hcd 0000:00:16.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Apr  9 06:36:22 myfirstex kernel: [    1.528618] ehci_hcd 0000:00:16.2: EHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.528782] ehci_hcd 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr  9 06:36:22 myfirstex kernel: [    1.528796] ehci_hcd 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr  9 06:36:22 myfirstex kernel: [    1.528826] ehci_hcd 0000:00:16.2: debug port 1
Apr  9 06:36:22 myfirstex kernel: [    1.528845] ehci_hcd 0000:00:16.2: irq 17, io mem 0xfe4ff000
Apr  9 06:36:22 myfirstex kernel: [    1.540128] ehci_hcd 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr  9 06:36:22 myfirstex kernel: [    1.540412] hub 3-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.540419] hub 3-0:1.0: 4 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.540584] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  9 06:36:22 myfirstex kernel: [    1.540667] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.540705] ohci_hcd 0000:00:12.0: OHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.540855] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr  9 06:36:22 myfirstex kernel: [    1.540897] ohci_hcd 0000:00:12.0: irq 18, io mem 0xfe4fe000
Apr  9 06:36:22 myfirstex kernel: [    1.600387] hub 4-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.600401] hub 4-0:1.0: 5 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.600553] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.600587] ohci_hcd 0000:00:13.0: OHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.600737] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr  9 06:36:22 myfirstex kernel: [    1.600767] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfe4fd000
Apr  9 06:36:22 myfirstex kernel: [    1.660384] hub 5-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.660398] hub 5-0:1.0: 5 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.660559] ohci_hcd 0000:00:16.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    1.660590] ohci_hcd 0000:00:16.0: OHCI Host Controller
Apr  9 06:36:22 myfirstex kernel: [    1.660701] ohci_hcd 0000:00:16.0: new USB bus registered, assigned bus number 6
Apr  9 06:36:22 myfirstex kernel: [    1.660728] ohci_hcd 0000:00:16.0: irq 18, io mem 0xfe4fc000
Apr  9 06:36:22 myfirstex kernel: [    1.720386] hub 6-0:1.0: USB hub found
Apr  9 06:36:22 myfirstex kernel: [    1.720399] hub 6-0:1.0: 4 ports detected
Apr  9 06:36:22 myfirstex kernel: [    1.720546] uhci_hcd: USB Universal Host Controller Interface driver
Apr  9 06:36:22 myfirstex kernel: [    1.720667] usbcore: registered new interface driver libusual
Apr  9 06:36:22 myfirstex kernel: [    1.720718] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr  9 06:36:22 myfirstex kernel: [    2.234757] ata3: SATA link down (SStatus 0 SControl 300)
Apr  9 06:36:22 myfirstex kernel: [    2.234880] ata4: SATA link down (SStatus 0 SControl 300)
Apr  9 06:36:22 myfirstex kernel: [    2.404089] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 06:36:22 myfirstex kernel: [    2.404122] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  9 06:36:22 myfirstex kernel: [    2.404753] ata1.00: failed to enable AA (error_mask=0x1)
Apr  9 06:36:22 myfirstex kernel: [    2.404760] ata1.00: ATA-8: VB0250EAVER, HPG7, max UDMA/100
Apr  9 06:36:22 myfirstex kernel: [    2.404764] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Apr  9 06:36:22 myfirstex kernel: [    2.404787] ata2.00: failed to enable AA (error_mask=0x1)
Apr  9 06:36:22 myfirstex kernel: [    2.404792] ata2.00: ATA-8: VB0250EAVER, HPG7, max UDMA/100
Apr  9 06:36:22 myfirstex kernel: [    2.404796] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
Apr  9 06:36:22 myfirstex kernel: [    2.405611] ata1.00: failed to enable AA (error_mask=0x1)
Apr  9 06:36:22 myfirstex kernel: [    2.405622] ata1.00: configured for UDMA/100
Apr  9 06:36:22 myfirstex kernel: [    2.405659] ata2.00: failed to enable AA (error_mask=0x1)
Apr  9 06:36:22 myfirstex kernel: [    2.405665] ata2.00: configured for UDMA/100
Apr  9 06:36:22 myfirstex kernel: [    2.749427] i8042: No controller found
Apr  9 06:36:22 myfirstex kernel: [    2.749546] Refined TSC clocksource calibration: 1497.505 MHz.
Apr  9 06:36:22 myfirstex kernel: [    2.749557] Switching to clocksource tsc
Apr  9 06:36:22 myfirstex kernel: [    2.749643] scsi 0:0:0:0: Direct-Access     ATA      VB0250EAVER      HPG7 PQ: 0 ANSI: 5
Apr  9 06:36:22 myfirstex kernel: [    2.749717] mousedev: PS/2 mouse device common for all mice
Apr  9 06:36:22 myfirstex kernel: [    2.749902] rtc_cmos 00:03: RTC can wake from S4
Apr  9 06:36:22 myfirstex kernel: [    2.750095] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr  9 06:36:22 myfirstex kernel: [    2.750135] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr  9 06:36:22 myfirstex kernel: [    2.750138] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  9 06:36:22 myfirstex kernel: [    2.750284] scsi 1:0:0:0: Direct-Access     ATA      VB0250EAVER      HPG7 PQ: 0 ANSI: 5
Apr  9 06:36:22 myfirstex kernel: [    2.750289] device-mapper: uevent: version 1.0.3
Apr  9 06:36:22 myfirstex kernel: [    2.750483] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  9 06:36:22 myfirstex kernel: [    2.750494] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
Apr  9 06:36:22 myfirstex kernel: [    2.750504] cpuidle: using governor ladder
Apr  9 06:36:22 myfirstex kernel: [    2.750507] cpuidle: using governor menu
Apr  9 06:36:22 myfirstex kernel: [    2.750509] EFI Variables Facility v0.08 2004-May-17
Apr  9 06:36:22 myfirstex kernel: [    2.750571] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Apr  9 06:36:22 myfirstex kernel: [    2.750621] sd 0:0:0:0: [sda] Write Protect is off
Apr  9 06:36:22 myfirstex kernel: [    2.750625] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  9 06:36:22 myfirstex kernel: [    2.750647] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 06:36:22 myfirstex kernel: [    2.750827] TCP cubic registered
Apr  9 06:36:22 myfirstex kernel: [    2.750960] NET: Registered protocol family 10
Apr  9 06:36:22 myfirstex kernel: [    2.751633] NET: Registered protocol family 17
Apr  9 06:36:22 myfirstex kernel: [    2.751638] Registering the dns_resolver key type
Apr  9 06:36:22 myfirstex kernel: [    2.751706] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Apr  9 06:36:22 myfirstex kernel: [    2.751844] PM: Hibernation image not present or could not be loaded.
Apr  9 06:36:22 myfirstex kernel: [    2.751859] registered taskstats version 1
Apr  9 06:36:22 myfirstex kernel: [    2.752280] sd 1:0:0:0: [sdb] Write Protect is off
Apr  9 06:36:22 myfirstex kernel: [    2.752285] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  9 06:36:22 myfirstex kernel: [    2.752312] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr  9 06:36:22 myfirstex kernel: [    2.757369]  sdb: sdb1 sdb2
Apr  9 06:36:22 myfirstex kernel: [    2.757738] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  9 06:36:22 myfirstex kernel: [    2.760166]   Magic number: 9:664:615
Apr  9 06:36:22 myfirstex kernel: [    2.760188] misc tun: hash matches
Apr  9 06:36:22 myfirstex kernel: [    2.760316] rtc_cmos 00:03: setting system clock to 2013-04-09 04:36:12 UTC (1365482172)
Apr  9 06:36:22 myfirstex kernel: [    2.760324] powernow-k8: Found 1 AMD Turion(tm) II Neo N40L Dual-Core Processor (2 cpu cores) (version 2.20.00)
Apr  9 06:36:22 myfirstex kernel: [    2.760366] powernow-k8:    0 : pstate 0 (1500 MHz)
Apr  9 06:36:22 myfirstex kernel: [    2.760368] powernow-k8:    1 : pstate 1 (1300 MHz)
Apr  9 06:36:22 myfirstex kernel: [    2.760370] powernow-k8:    2 : pstate 2 (1000 MHz)
Apr  9 06:36:22 myfirstex kernel: [    2.760373] powernow-k8:    3 : pstate 3 (800 MHz)
Apr  9 06:36:22 myfirstex kernel: [    2.760666] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  9 06:36:22 myfirstex kernel: [    2.760671] EDD information not available.
Apr  9 06:36:22 myfirstex kernel: [    2.765675]  sda: sda1 sda2
Apr  9 06:36:22 myfirstex kernel: [    2.766593] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  9 06:36:22 myfirstex kernel: [    2.768934] Freeing unused kernel memory: 920k freed
Apr  9 06:36:22 myfirstex kernel: [    2.769214] Write protecting the kernel read-only data: 12288k
Apr  9 06:36:22 myfirstex kernel: [    2.777402] Freeing unused kernel memory: 1600k freed
Apr  9 06:36:22 myfirstex kernel: [    2.784072] Freeing unused kernel memory: 1192k freed
Apr  9 06:36:22 myfirstex kernel: [    2.884448] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
Apr  9 06:36:22 myfirstex kernel: [    2.884454] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
Apr  9 06:36:22 myfirstex kernel: [    2.884502] e1000e 0000:02:00.0: Disabling ASPM  L1
Apr  9 06:36:22 myfirstex kernel: [    2.884523] e1000e 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    2.884544] e1000e 0000:02:00.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    2.884671] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [    2.902499] [drm] Initialized drm 1.1.0 20060810
Apr  9 06:36:22 myfirstex kernel: [    2.924549] scsi4 : pata_atiixp
Apr  9 06:36:22 myfirstex kernel: [    2.925663] [drm] radeon defaulting to kernel modesetting.
Apr  9 06:36:22 myfirstex kernel: [    2.925666] [drm] radeon kernel modesetting enabled.
Apr  9 06:36:22 myfirstex kernel: [    2.925771] scsi5 : pata_atiixp
Apr  9 06:36:22 myfirstex kernel: [    2.926652] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
Apr  9 06:36:22 myfirstex kernel: [    2.926657] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
Apr  9 06:36:22 myfirstex kernel: [    2.926673] tg3.c:v3.121 (November 2, 2011)
Apr  9 06:36:22 myfirstex kernel: [    2.926690] tg3 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    2.926703] tg3 0000:04:00.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    2.927130] radeon 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  9 06:36:22 myfirstex kernel: [    2.927135] radeon 0000:01:05.0: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    2.927348] [drm] initializing kernel modesetting (RS880 0x1002:0x9712 0x103C:0x1609).
Apr  9 06:36:22 myfirstex kernel: [    2.927371] [drm] register mmio base: 0xFE6F0000
Apr  9 06:36:22 myfirstex kernel: [    2.927373] [drm] register mmio size: 65536
Apr  9 06:36:22 myfirstex kernel: [    2.928233] ATOM BIOS: AMD_1407_150
Apr  9 06:36:22 myfirstex kernel: [    2.928264] radeon 0000:01:05.0: VRAM: 128M 0x00000000C0000000 - 0x00000000C7FFFFFF (128M used)
Apr  9 06:36:22 myfirstex kernel: [    2.928269] radeon 0000:01:05.0: GTT: 512M 0x00000000A0000000 - 0x00000000BFFFFFFF
Apr  9 06:36:22 myfirstex kernel: [    2.928842] [drm] Detected VRAM RAM=128M, BAR=128M
Apr  9 06:36:22 myfirstex kernel: [    2.928847] [drm] RAM width 32bits DDR
Apr  9 06:36:22 myfirstex kernel: [    2.935534] [TTM] Zone  kernel: Available graphics memory: 2992512 kiB.
Apr  9 06:36:22 myfirstex kernel: [    2.935538] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
Apr  9 06:36:22 myfirstex kernel: [    2.935541] [TTM] Initializing pool allocator.
Apr  9 06:36:22 myfirstex kernel: [    2.935570] [drm] radeon: 128M of VRAM memory ready
Apr  9 06:36:22 myfirstex kernel: [    2.935573] [drm] radeon: 512M of GTT memory ready.
Apr  9 06:36:22 myfirstex kernel: [    2.935599] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Apr  9 06:36:22 myfirstex kernel: [    2.935601] [drm] Driver supports precise vblank timestamp query.
Apr  9 06:36:22 myfirstex kernel: [    2.935626] [drm] radeon: irq initialized.
Apr  9 06:36:22 myfirstex kernel: [    2.935633] [drm] GART: num cpu pages 131072, num gpu pages 131072
Apr  9 06:36:22 myfirstex kernel: [    2.937404] [drm] Loading RS780 Microcode
Apr  9 06:36:22 myfirstex kernel: [    2.977664] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM95723) rev 5784100] (PCI Express) MAC address a0:b3:cc:e2:5b:b4
Apr  9 06:36:22 myfirstex kernel: [    2.977671] tg3 0000:04:00.0: eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
Apr  9 06:36:22 myfirstex kernel: [    2.977676] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
Apr  9 06:36:22 myfirstex kernel: [    2.977680] tg3 0000:04:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Apr  9 06:36:22 myfirstex kernel: [    2.983248] md: bind<sdb2>
Apr  9 06:36:22 myfirstex kernel: [    2.986986] md: bind<sda1>
Apr  9 06:36:22 myfirstex kernel: [    2.990845] md: bind<sdb1>
Apr  9 06:36:22 myfirstex kernel: [    2.995134] md: raid1 personality registered for level 1
Apr  9 06:36:22 myfirstex kernel: [    3.002373] [drm] PCIE GART of 512M enabled (table at 0x00000000C0040000).
Apr  9 06:36:22 myfirstex kernel: [    3.002488] radeon 0000:01:05.0: WB enabled
Apr  9 06:36:22 myfirstex kernel: [    3.034733] [drm] ring test succeeded in 0 usecs
Apr  9 06:36:22 myfirstex kernel: [    3.034861] [drm] radeon: ib pool ready.
Apr  9 06:36:22 myfirstex kernel: [    3.034946] [drm] ib test succeeded in 0 usecs
Apr  9 06:36:22 myfirstex kernel: [    3.035212] [drm] Radeon Display Connectors
Apr  9 06:36:22 myfirstex kernel: [    3.035215] [drm] Connector 0:
Apr  9 06:36:22 myfirstex kernel: [    3.035217] [drm]   VGA
Apr  9 06:36:22 myfirstex kernel: [    3.035220] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
Apr  9 06:36:22 myfirstex kernel: [    3.035223] [drm]   Encoders:
Apr  9 06:36:22 myfirstex kernel: [    3.035225] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
Apr  9 06:36:22 myfirstex kernel: [    3.035247] [drm] radeon: power management initialized
Apr  9 06:36:22 myfirstex kernel: [    3.048445] No connectors reported connected with modes
Apr  9 06:36:22 myfirstex kernel: [    3.048453] [drm] Cannot find any crtc or sizes - going 1024x768
Apr  9 06:36:22 myfirstex kernel: [    3.057051] [drm] fb mappable at 0xF0142000
Apr  9 06:36:22 myfirstex kernel: [    3.057054] [drm] vram apper at 0xF0000000
Apr  9 06:36:22 myfirstex kernel: [    3.057056] [drm] size 3145728
Apr  9 06:36:22 myfirstex kernel: [    3.057058] [drm] fb depth is 24
Apr  9 06:36:22 myfirstex kernel: [    3.057060] [drm]    pitch is 4096
Apr  9 06:36:22 myfirstex kernel: [    3.057196] fbcon: radeondrmfb (fb0) is primary device
Apr  9 06:36:22 myfirstex kernel: [    3.057262] Console: switching to colour frame buffer device 128x48
Apr  9 06:36:22 myfirstex kernel: [    3.057290] fb0: radeondrmfb frame buffer device
Apr  9 06:36:22 myfirstex kernel: [    3.057293] drm: registered panic notifier
Apr  9 06:36:22 myfirstex kernel: [    3.057302] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex kernel: [    3.062875] e1000e 0000:02:00.0: eth1: (PCI Express:2.5GT/s:Width x4) 00:1b:78:57:ca:ae
Apr  9 06:36:22 myfirstex kernel: [    3.062881] e1000e 0000:02:00.0: eth1: Intel(R) PRO/1000 Network Connection
Apr  9 06:36:22 myfirstex kernel: [    3.062962] e1000e 0000:02:00.0: eth1: MAC: 0, PHY: 4, PBA No: D51930-003
Apr  9 06:36:22 myfirstex kernel: [    3.063031] e1000e 0000:02:00.1: Disabling ASPM  L1
Apr  9 06:36:22 myfirstex kernel: [    3.063048] e1000e 0000:02:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  9 06:36:22 myfirstex kernel: [    3.063066] e1000e 0000:02:00.1: setting latency timer to 64
Apr  9 06:36:22 myfirstex kernel: [    3.063193] e1000e 0000:02:00.1: irq 45 for MSI/MSI-X[/COLOR]
Apr  9 06:36:22 myfirstex kernel: [    3.105251] bio: create slab <bio-1> at 1
Apr  9 06:36:22 myfirstex kernel: [    3.107076] md/raid1:md0: active with 2 out of 2 mirrors
Apr  9 06:36:22 myfirstex kernel: [    3.107116] md0: detected capacity change from 0 to 11990335488
Apr  9 06:36:22 myfirstex kernel: [    3.117814]  md0: unknown partition table
Apr  9 06:36:22 myfirstex kernel: [    3.136745] md: bind<sda2>
Apr  9 06:36:22 myfirstex kernel: [    3.139853] md/raid1:md1: active with 2 out of 2 mirrors
Apr  9 06:36:22 myfirstex kernel: [    3.139889] md1: detected capacity change from 0 to 237924843520
Apr  9 06:36:22 myfirstex kernel: [    3.161125]  md1: unknown partition table
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex kernel: [    3.257059] e1000e 0000:02:00.1: eth2: (PCI Express:2.5GT/s:Width x4) 00:1b:78:57:ca:af
Apr  9 06:36:22 myfirstex kernel: [    3.257065] e1000e 0000:02:00.1: eth2: Intel(R) PRO/1000 Network Connection
Apr  9 06:36:22 myfirstex kernel: [    3.257147] e1000e 0000:02:00.1: eth2: MAC: 0, PHY: 4, PBA No: D51930-003[/COLOR]
Apr  9 06:36:22 myfirstex kernel: [    3.543469] md: linear personality registered for level -1
Apr  9 06:36:22 myfirstex kernel: [    3.545801] md: multipath personality registered for level -4
Apr  9 06:36:22 myfirstex kernel: [    3.548137] md: raid0 personality registered for level 0
Apr  9 06:36:22 myfirstex kernel: [    3.552699] async_tx: api initialized (async)
Apr  9 06:36:22 myfirstex kernel: [    3.620029] raid6: int64x1   1281 MB/s
Apr  9 06:36:22 myfirstex kernel: [    3.688029] raid6: int64x2   1865 MB/s
Apr  9 06:36:22 myfirstex kernel: [    3.756050] raid6: int64x4   1358 MB/s
Apr  9 06:36:22 myfirstex kernel: [    3.824059] raid6: int64x8   1191 MB/s
Apr  9 06:36:22 myfirstex kernel: [    3.892061] raid6: sse2x1    2160 MB/s
Apr  9 06:36:22 myfirstex kernel: [    3.960030] raid6: sse2x2    3622 MB/s
Apr  9 06:36:22 myfirstex kernel: [    4.028031] raid6: sse2x4    4022 MB/s
Apr  9 06:36:22 myfirstex kernel: [    4.028033] raid6: using algorithm sse2x4 (4022 MB/s)
Apr  9 06:36:22 myfirstex kernel: [    4.028788] xor: automatically using best checksumming function: generic_sse
Apr  9 06:36:22 myfirstex kernel: [    4.048053]    generic_sse:  6136.000 MB/sec
Apr  9 06:36:22 myfirstex kernel: [    4.048057] xor: using function: generic_sse (6136.000 MB/sec)
Apr  9 06:36:22 myfirstex kernel: [    4.049060] md: raid6 personality registered for level 6
Apr  9 06:36:22 myfirstex kernel: [    4.049063] md: raid5 personality registered for level 5
Apr  9 06:36:22 myfirstex kernel: [    4.049066] md: raid4 personality registered for level 4
Apr  9 06:36:22 myfirstex kernel: [    4.056863] md: raid10 personality registered for level 10
Apr  9 06:36:22 myfirstex kernel: [    9.250013] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)
Apr  9 06:36:22 myfirstex kernel: [   11.953298] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  9 06:36:22 myfirstex kernel: [   11.953308] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  9 06:36:22 myfirstex kernel: [   11.953317] ADDRCONF(NETDEV_UP): eth2: link is not ready
Apr  9 06:36:22 myfirstex kernel: [   12.027667] EXT4-fs (md1): re-mounted. Opts: errors=remount-ro
Apr  9 06:36:22 myfirstex kernel: [   12.196986] lp: driver loaded but no devices found
Apr  9 06:36:22 myfirstex kernel: [   12.216189] cfg80211: Calling CRDA to update world regulatory domain
Apr  9 06:36:22 myfirstex kernel: [   12.239581] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr  9 06:36:22 myfirstex kernel: [   12.268964] type=1400 audit(1365482182.005:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=489 comm="apparmor_parser"
Apr  9 06:36:22 myfirstex kernel: [   12.269087] type=1400 audit(1365482182.005:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=487 comm="apparmor_parser"
Apr  9 06:36:22 myfirstex kernel: [   12.269757] type=1400 audit(1365482182.005:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=489 com$
Apr  9 06:36:22 myfirstex kernel: [   12.269874] type=1400 audit(1365482182.005:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=487 $
Apr  9 06:36:22 myfirstex kernel: [   12.270177] type=1400 audit(1365482182.005:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=489 comm="ap$
Apr  9 06:36:22 myfirstex kernel: [   12.270283] type=1400 audit(1365482182.005:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=487 comm=$Apr  9 06:36:22 myfirstex kernel: [   12.272329] type=1400 audit(1365482182.009:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=490 comm="apparmor_parser"
Apr  9 06:36:22 myfirstex kernel: [   12.273117] type=1400 audit(1365482182.009:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 $
Apr  9 06:36:22 myfirstex kernel: [   12.273540] type=1400 audit(1365482182.009:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm$
Apr  9 06:36:22 myfirstex kernel: [   12.276606] MCE: In-kernel MCE decoding enabled.
Apr  9 06:36:22 myfirstex kernel: [   12.277159] type=1400 audit(1365482182.013:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=537 comm="apparmor_parser"
Apr  9 06:36:22 myfirstex kernel: [   12.298452] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Apr  9 06:36:22 myfirstex kernel: [   12.315649] EDAC MC: Ver: 2.1.0
Apr  9 06:36:22 myfirstex kernel: [   12.396607] cfg80211: World regulatory domain updated:
Apr  9 06:36:22 myfirstex kernel: [   12.396612] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr  9 06:36:22 myfirstex kernel: [   12.396616] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 06:36:22 myfirstex kernel: [   12.396620] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  9 06:36:22 myfirstex kernel: [   12.396624] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr  9 06:36:22 myfirstex kernel: [   12.396627] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 06:36:22 myfirstex kernel: [   12.396630] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr  9 06:36:22 myfirstex kernel: [   12.436504] AMD64 EDAC driver v3.4.0
Apr  9 06:36:22 myfirstex kernel: [   12.436556] EDAC amd64: DRAM ECC enabled.
Apr  9 06:36:22 myfirstex kernel: [   12.436564] EDAC amd64: F10h detected (node 0).
Apr  9 06:36:22 myfirstex kernel: [   12.436591] EDAC MC: DCT0 chip selects:
Apr  9 06:36:22 myfirstex kernel: [   12.436595] EDAC amd64: MC: 0:  1024MB 1:  1024MB
Apr  9 06:36:22 myfirstex kernel: [   12.436597] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436600] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436603] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436605] EDAC MC: DCT1 chip selects:
Apr  9 06:36:22 myfirstex kernel: [   12.436608] EDAC amd64: MC: 0:  2048MB 1:  2048MB
Apr  9 06:36:22 myfirstex kernel: [   12.436610] EDAC amd64: MC: 2:     0MB 3:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436613] EDAC amd64: MC: 4:     0MB 5:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436615] EDAC amd64: MC: 6:     0MB 7:     0MB
Apr  9 06:36:22 myfirstex kernel: [   12.436618] EDAC amd64: using x4 syndromes.
Apr  9 06:36:22 myfirstex kernel: [   12.436620] EDAC amd64: MCT channel count: 2
Apr  9 06:36:22 myfirstex kernel: [   12.436647] EDAC amd64: CS0: Unbuffered DDR3 RAM
Apr  9 06:36:22 myfirstex kernel: [   12.436650] EDAC amd64: CS1: Unbuffered DDR3 RAM
Apr  9 06:36:22 myfirstex kernel: [   12.436687] EDAC MC0: Giving out device to 'amd64_edac' 'F10h': DEV 0000:00:18.2
Apr  9 06:36:22 myfirstex kernel: [   12.436744] EDAC PCI0: Giving out device to module 'amd64_edac' controller 'EDAC PCI controller': DEV '0000:00:18.2' (POLLED)
Apr  9 06:36:22 myfirstex kernel: [   12.504371] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [   12.560135] e1000e 0000:02:00.0: irq 44 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [   12.561598] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr  9 06:36:22 myfirstex kernel: [   12.609214] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
Apr  9 06:36:22 myfirstex kernel: [   12.609363] SP5100 TCO timer: mmio address 0xb8fe00 already in use
Apr  9 06:36:22 myfirstex ntpd[723]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Apr  9 06:36:22 myfirstex ntpd[727]: proto: precision = 0.140 usec
Apr  9 06:36:22 myfirstex ntpd[727]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Apr  9 06:36:22 myfirstex ntpd[727]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Apr  9 06:36:22 myfirstex ntpd[727]: Listen and drop on 1 v6wildcard :: UDP 123
Apr  9 06:36:22 myfirstex kernel: [   12.706500] e1000e 0000:02:00.1: irq 45 for MSI/MSI-X
Apr  9 06:36:22 myfirstex ntpd[727]: Listen normally on 2 lo 127.0.0.1 UDP 123
Apr  9 06:36:22 myfirstex ntpd[727]: Listen normally on 3 eth1 192.168.1.25 UDP 123
Apr  9 06:36:22 myfirstex ntpd[727]: Listen normally on 4 eth2 192.168.2.25 UDP 123
Apr  9 06:36:22 myfirstex ntpd[727]: Listen normally on 5 lo ::1 UDP 123
Apr  9 06:36:22 myfirstex ntpd[727]: peers refreshed
Apr  9 06:36:22 myfirstex ntpd[727]: Listening on routing socket on fd #22 for interface updates
Apr  9 06:36:22 myfirstex ntpd[727]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex kernel: [   12.760141] e1000e 0000:02:00.1: irq 45 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [   12.761600] ADDRCONF(NETDEV_UP): eth2: link is not ready
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex ntpd[727]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[727]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[727]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[727]: Deferring DNS for ntp.ubuntu.com 1[/COLOR]
Apr  9 06:36:22 myfirstex failsafe: Failsafe of 120 seconds reached.
Apr  9 06:36:22 myfirstex ntpd[757]: signal_no_reset: signal 17 had flags 4000000
Apr  9 06:36:22 myfirstex kernel: [   12.801301] ath9k 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  9 06:36:22 myfirstex kernel: [   12.801314] ath9k 0000:03:00.0: setting latency timer to 64
[COLOR=#ff0000]Apr  9 06:36:22 myfirstex ntpd[727]: ntpd exiting on signal 15
Apr  9 06:36:22 myfirstex ntpdate[803]: name server cannot be used: Temporary failure in name resolution (-3)[/COLOR]
Apr  9 06:36:22 myfirstex ntpd[830]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Apr  9 06:36:22 myfirstex ntpd[831]: proto: precision = 0.151 usec
Apr  9 06:36:22 myfirstex ntpd[831]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Apr  9 06:36:22 myfirstex ntpd[831]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: Listen and drop on 1 v6wildcard :: UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: Listen normally on 2 lo 127.0.0.1 UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: Listen normally on 3 eth1 192.168.1.25 UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: Listen normally on 4 eth2 192.168.2.25 UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: Listen normally on 5 lo ::1 UDP 123
Apr  9 06:36:22 myfirstex ntpd[831]: peers refreshed
Apr  9 06:36:22 myfirstex ntpd[831]: Listening on routing socket on fd #22 for interface updates
Apr  9 06:36:22 myfirstex ntpd[831]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[831]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[831]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[831]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Apr  9 06:36:22 myfirstex ntpd[831]: Deferring DNS for ntp.ubuntu.com 1
Apr  9 06:36:22 myfirstex ntpd[833]: signal_no_reset: signal 17 had flags 4000000
Apr  9 06:36:22 myfirstex kernel: [   12.883237] tg3 0000:04:00.0: irq 46 for MSI/MSI-X
Apr  9 06:36:22 myfirstex kernel: [   12.895232] ath: EEPROM regdomain: 0x21
Apr  9 06:36:22 myfirstex kernel: [   12.895237] ath: EEPROM indicates we should expect a direct regpair map
Apr  9 06:36:22 myfirstex kernel: [   12.895241] ath: Country alpha2 being used: AU
Apr  9 06:36:22 myfirstex kernel: [   12.895244] ath: Regpair used: 0x21
Apr  9 06:36:22 myfirstex kernel: [   12.895248] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
.....
Apr  9 06:36:22 myfirstex kernel: [   12.901031] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
Apr  9 06:36:23 myfirstex kernel: [   13.661969] ADDRCONF(NETDEV_UP): eth0: link is not ready
[COLOR=#ff0000]Apr  9 06:36:23 myfirstex dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3[/COLOR]
Apr  9 06:36:23 myfirstex kernel: [   13.695877] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
Apr  9 06:36:23 myfirstex kernel: [   13.696819] Registered led device: ath9k-phy0
Apr  9 06:36:23 myfirstex kernel: [   13.696826] ieee80211 phy0: Atheros AR9300 Rev:3 mem=0xffffc90011bc0000, irq=16
Apr  9 06:36:23 myfirstex kernel: [   13.696835] cfg80211: Calling CRDA for country: AU
Apr  9 06:36:23 myfirstex kernel: [   13.706983] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
.....
Apr  9 06:36:23 myfirstex kernel: [   13.707005] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
Apr  9 06:36:23 myfirstex kernel: [   13.753268] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[COLOR=#ff0000]Apr  9 06:36:23 myfirstex ntpd[831]: ntpd exiting on signal 15
Apr  9 06:36:23 myfirstex ntpdate[959]: name server cannot be used: Temporary failure in name resolution (-3)
Apr  9 06:36:23 myfirstex ntpd[994]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Apr  9 06:36:23 myfirstex ntpd[995]: proto: precision = 0.140 usec
Apr  9 06:36:23 myfirstex ntpd[995]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Apr  9 06:36:23 myfirstex ntpd[995]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen and drop on 1 v6wildcard :: UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen normally on 2 lo 127.0.0.1 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen normally on 3 eth1 192.168.1.25 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen normally on 4 eth2 192.168.2.25 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen normally on 5 wlan0 192.168.3.25 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: Listen normally on 6 lo ::1 UDP 123
Apr  9 06:36:23 myfirstex ntpd[995]: peers refreshed
Apr  9 06:36:23 myfirstex ntpd[995]: Listening on routing socket on fd #23 for interface updates
Apr  9 06:36:23 myfirstex ntpd[995]: Deferring DNS for 0.ubuntu.pool.ntp.org 1
Apr  9 06:36:23 myfirstex ntpd[995]: Deferring DNS for 1.ubuntu.pool.ntp.org 1
Apr  9 06:36:23 myfirstex ntpd[995]: Deferring DNS for 2.ubuntu.pool.ntp.org 1
Apr  9 06:36:23 myfirstex ntpd[995]: Deferring DNS for 3.ubuntu.pool.ntp.org 1
Apr  9 06:36:23 myfirstex ntpd[995]: Deferring DNS for ntp.ubuntu.com 1[/COLOR]
Apr  9 06:36:23 myfirstex ntpd[997]: signal_no_reset: signal 17 had flags 4000000
Apr  9 06:36:23 myfirstex kernel: [   13.953016] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Apr  9 06:36:23 myfirstex kernel: [   13.953025] e1000e 0000:02:00.0: eth1: 10/100 speed: disabling TSO
Apr  9 06:36:23 myfirstex kernel: [   13.954290] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr  9 06:36:23 myfirstex kernel: [   14.104930] e1000e: eth2 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
Apr  9 06:36:23 myfirstex kernel: [   14.104939] e1000e 0000:02:00.1: eth2: 10/100 speed: disabling TSO
Apr  9 06:36:23 myfirstex kernel: [   14.106221] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
Apr  9 06:36:23 myfirstex kernel: [   14.216528] Adding 11709308k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:11709308k
Apr  9 06:36:24 myfirstex ntpd_intres[757]: parent died before we finished, exiting
Apr  9 06:36:24 myfirstex ntpd_intres[833]: parent died before we finished, exiting
Apr  9 06:36:24 myfirstex kernel: [   15.259776] tg3 0000:04:00.0: eth0: Link is up at 100 Mbps, full duplex
Apr  9 06:36:24 myfirstex kernel: [   15.259782] tg3 0000:04:00.0: eth0: Flow control is off for TX and off for RX
Apr  9 06:36:25 myfirstex kernel: [   15.261050] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[COLOR=#ff0000]Apr  9 06:36:26 myfirstex dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr  9 06:36:26 myfirstex dhclient: DHCPREQUEST of 212.186.51.184 on eth0 to 255.255.255.255 port 67
Apr  9 06:36:26 myfirstex dhclient: DHCPOFFER of 212.186.51.184 from 10.210.0.1
Apr  9 06:36:26 myfirstex dhclient: DHCPACK of 212.186.51.184 from 10.210.0.1
Apr  9 06:36:27 myfirstex dhclient: bound to 212.186.51.184 -- renewal in 228 seconds.
Apr  9 06:36:27 myfirstex ntpd[995]: ntpd exiting on signal 15[/COLOR]
Apr  9 06:36:27 myfirstex kernel: [   17.739552] init: failsafe main process (755) killed by TERM signal
Apr  9 06:36:27 myfirstex kernel: [   17.785985] audit_printk_skb: 6 callbacks suppressed
Apr  9 06:36:27 myfirstex kernel: [   17.785990] type=1400 audit(1365482187.521:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=1173 comm="apparmor_parser"
Apr  9 06:36:27 myfirstex kernel: [   17.786391] type=1400 audit(1365482187.521:15): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1172 comm="apparmor_parser"
Apr  9 06:36:27 myfirstex kernel: [   17.787180] type=1400 audit(1365482187.521:16): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=117$
Apr  9 06:36:27 myfirstex kernel: [   17.787589] type=1400 audit(1365482187.521:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1172 com$
Apr  9 06:36:27 myfirstex kernel: [   17.791077] type=1400 audit(1365482187.525:18): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1175 comm="apparmor_parser"
Apr  9 06:36:27 myfirstex cron[1204]: (CRON) INFO (pidfile fd = 3)
Apr  9 06:36:27 myfirstex cron[1215]: (CRON) STARTUP (fork ok)
Apr  9 06:36:27 myfirstex cron[1215]: (CRON) INFO (Running @reboot jobs)
[COLOR=#ff0000]Apr  9 06:36:27 myfirstex dnsmasq[1228]: started, version 2.59 cachesize 150
Apr  9 06:36:27 myfirstex dnsmasq[1228]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Apr  9 06:36:27 myfirstex dnsmasq-dhcp[1228]: DHCP, IP range 192.168.3.20 -- 192.168.3.30, lease time unendlich
Apr  9 06:36:27 myfirstex dnsmasq-dhcp[1228]: DHCP, IP range 192.168.2.20 -- 192.168.2.30, lease time unendlich
Apr  9 06:36:27 myfirstex dnsmasq-dhcp[1228]: DHCP, IP range 192.168.1.20 -- 192.168.1.30, lease time unendlich
Apr  9 06:36:27 myfirstex dnsmasq[1228]: Lesen von /var/run/dnsmasq/resolv.conf
Apr  9 06:36:27 myfirstex dnsmasq[1228]: using nameserver 195.34.133.21#53
Apr  9 06:36:27 myfirstex dnsmasq[1228]: using nameserver 212.186.211.21#53
Apr  9 06:36:27 myfirstex dnsmasq[1228]: /etc/hosts lesen – 7 Adressen[/COLOR]
Apr  9 06:36:28 myfirstex kernel: [   19.032570] ip_tables: (C) 2000-2006 Netfilter Core Team
Apr  9 06:36:28 myfirstex kernel: [   19.053606] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Apr  9 06:36:34 myfirstex kernel: [   24.640077] eth1: no IPv6 routers present
Apr  9 06:36:34 myfirstex kernel: [   24.960072] eth2: no IPv6 routers present
[COLOR=#ff0000]Apr  9 06:36:35 myfirstex dnsmasq[1228]: Lesen von /var/run/dnsmasq/resolv.conf
Apr  9 06:36:35 myfirstex dnsmasq[1228]: using nameserver 195.34.133.21#53
Apr  9 06:36:35 myfirstex dnsmasq[1228]: using nameserver 212.186.211.21#53[/COLOR]
Apr  9 06:36:35 myfirstex kernel: [   25.733278] cfg80211: Calling CRDA for country: DE
Apr  9 06:36:35 myfirstex ntpd[1590]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Apr  9 06:36:35 myfirstex ntpd[1591]: proto: precision = 0.140 usec
Apr  9 06:36:35 myfirstex ntpd[1591]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Apr  9 06:36:35 myfirstex ntpd[1591]: unable to bind to wildcard address 0.0.0.0 - another process may be running - EXITING
....
Apr  9 06:36:40 myfirstex ntpdate[1129]: adjust time server 193.171.23.163 offset -0.116934 sec
Apr  9 06:36:40 myfirstex ntpd[1680]: ntpd 4.2.6p3@1.2290-o Tue Jun  5 20:12:08 UTC 2012 (1)
Apr  9 06:36:40 myfirstex ntpd[1681]: proto: precision = 0.140 usec
Apr  9 06:36:40 myfirstex ntpd[1681]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen and drop on 1 v6wildcard :: UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 2 lo 127.0.0.1 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 3 eth0 212.186.51.184 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 4 eth1 192.168.1.25 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 5 eth2 192.168.2.25 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 6 wlan0 192.168.3.25 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 7 eth2 fe80::21b:78ff:fe57:caaf UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 8 eth1 fe80::21b:78ff:fe57:caae UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 9 wlan0 fe80::6670:2ff:fe2e:19fb UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: Listen normally on 10 lo ::1 UDP 123
Apr  9 06:36:40 myfirstex ntpd[1681]: peers refreshed
Apr  9 06:36:40 myfirstex ntpd[1681]: Listening on routing socket on fd #27 for interface updates
Apr  9 06:36:53 myfirstex dnsmasq-dhcp[1228]: DHCPDISCOVER(eth2) 192.168.2.35 44:1e:a1:e3:43:77
Apr  9 06:36:53 myfirstex dnsmasq-dhcp[1228]: DHCPOFFER(eth2) 192.168.2.35 44:1e:a1:e3:43:77
Apr  9 06:36:53 myfirstex dnsmasq-dhcp[1228]: DHCPREQUEST(eth2) 192.168.2.35 44:1e:a1:e3:43:77
Apr  9 06:36:53 myfirstex dnsmasq-dhcp[1228]: DHCPACK(eth2) 192.168.2.35 44:1e:a1:e3:43:77 kubuntuisiert
Apr  9 06:36:55 myfirstex ntpd_intres[997]: parent died before we finished, exiting
Apr  9 06:37:10 myfirstex kernel: [   60.420195] e1000e: eth2 NIC Link is Down
Apr  9 06:37:12 myfirstex kernel: [   62.720999] e1000e: eth2 NIC Link is Up 10 Mbps Half Duplex, Flow Control: None
Apr  9 06:37:12 myfirstex kernel: [   62.721008] e1000e 0000:02:00.1: eth2: 10/100 speed: disabling TSO




[COLOR=#ff0000]Apr  9 15:06:08 myfirstex dhclient: parse_option_buffer: malformed option dhcp.<unknown> (code 106): option length exceeds option buffer length.[/COLOR]
[COLOR=#ff0000]
[/COLOR]
[COLOR=#ff0000]Apr  9 15:06:17 myfirstex dhclient: parse_option_buffer: malformed option dhcp.<unknown> (code 106): option length exceeds option buffer length.[/COLOR]

```


2.) This is* route *from the ROUTER
```
myfirstex:~$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         chello212186051 0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2
192.168.3.0     *               255.255.255.0   U     0      0        0 wlan0
212.186.51.0    *               255.255.255.0   U     0      0        0 eth0

```

3.) This is a *traceroute* to ubuntuforums.org from the ROUTER
```
myfirstex:~$ traceroute ubuntuforums.orgtraceroute to ubuntuforums.org (91.189.94.12), 30 hops max, 60 byte packets
 1  * * *
 2  172.16.100.69 (172.16.100.69)  11.992 ms  12.057 ms  12.054 ms
 3  at-vie15a-rd1-vl-2048.aorta.net (84.116.228.149)  21.473 ms  21.550 ms  21.545 ms
 4  de-fra01a-rd3-xe-2-1-0.aorta.net (213.46.160.69)  36.193 ms  36.214 ms  36.207 ms
 5  84.116.132.178 (84.116.132.178)  35.943 ms  36.077 ms 84.116.132.186 (84.116.132.186)  35.874 ms
 6  4.68.62.237 (4.68.62.237)  56.318 ms  44.592 ms  34.118 ms
 7  vlan80.csw3.Frankfurt1.Level3.net (4.69.154.190)  49.130 ms vlan90.csw4.Frankfurt1.Level3.net (4.69.154.254)  43.522 ms vlan80.csw3.Frankfurt1.Level3.net (4.69.154.190)  47.386 ms
 8  ae-92-92.ebr2.Frankfurt1.Level3.net (4.69.140.29)  47.259 ms  46.389 ms  49.353 ms
 9  * * *
10  ae-57-222.csw2.London1.Level3.net (4.69.153.134)  49.338 ms  45.430 ms ae-59-224.csw2.London1.Level3.net (4.69.153.142)  44.843 ms
11  * * *
12  SOURCE-MANA.edge5.London1.Level3.net (212.187.138.82)  49.176 ms  49.016 ms  44.827 ms
13  eth0.lutin.canonical.com (91.189.88.10)  49.988 ms  49.830 ms  48.095 ms
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

4.) This is* route* from the CLIENT
```
kubuntuisiert:~$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         192.168.2.25    0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.168.2.0     *               255.255.255.0   U     1      0        0 eth0

```

5.) This is a *ping* from the CLIENT
```
kubuntuisiert:~$ ping -c 5 ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=55 time=44.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=55 time=48.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=55 time=45.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=55 time=45.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=5 ttl=55 time=48.5 ms


--- ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 44.768/46.465/48.590/1.604 ms

```

6.) This is a *traceroute* from the CLIENT
```
kubuntuisiert:~$ traceroute ubuntuforums.org
traceroute to ubuntuforums.org (91.189.94.12), 30 hops max, 60 byte packets                                                                                                                     
 1  192.168.2.25 (192.168.2.25)  0.359 ms  0.337 ms  0.322 ms                                                                                                                                   
 2  * * *                                                                                                                                                                                       
 3  172.16.100.69 (172.16.100.69)  10.454 ms  10.486 ms  10.480 ms
 4  at-vie15a-rd1-vl-2048.aorta.net (84.116.228.149)  20.529 ms  20.555 ms  20.549 ms
 5  de-fra01a-rd3-xe-2-1-0.aorta.net (213.46.160.69)  33.974 ms  33.975 ms  33.966 ms
 6  84.116.132.186 (84.116.132.186)  33.721 ms 84.116.132.178 (84.116.132.178)  29.414 ms  37.318 ms
 7  4.68.62.237 (4.68.62.237)  33.863 ms  35.344 ms  35.325 ms
 8  vlan80.csw3.Frankfurt1.Level3.net (4.69.154.190)  49.871 ms vlan70.csw2.Frankfurt1.Level3.net (4.69.154.126)  56.857 ms vlan90.csw4.Frankfurt1.Level3.net (4.69.154.254)  49.878 ms
 9  ae-62-62.ebr2.Frankfurt1.Level3.net (4.69.140.17)  46.772 ms  46.714 ms ae-72-72.ebr2.Frankfurt1.Level3.net (4.69.140.21)  46.742 ms
10  * * *
11  ae-57-222.csw2.London1.Level3.net (4.69.153.134)  50.053 ms ae-56-221.csw2.London1.Level3.net (4.69.153.130)  49.746 ms ae-57-222.csw2.London1.Level3.net (4.69.153.134)  44.806 ms
12  * * *
13  SOURCE-MANA.edge5.London1.Level3.net (212.187.138.82)  51.508 ms  51.503 ms  51.078 ms
14  eth0.lutin.canonical.com (91.189.88.10)  50.975 ms  51.019 ms  51.013 ms
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```

7.) This is a *syslog* entry from the CLIENT, when getting connected to the ROUTER
```
Apr 12 12:28:05 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 12 12:28:05 kubuntuisiert NetworkManager[860]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 12 12:28:05 kubuntuisiert dhclient: Listening on LPF/eth0/44:1e:a1:e3:43:77
Apr 12 12:28:05 kubuntuisiert dhclient: Sending on   LPF/eth0/44:1e:a1:e3:43:77
Apr 12 12:28:05 kubuntuisiert dhclient: Sending on   Socket/fallback
Apr 12 12:28:05 kubuntuisiert dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 12 12:28:07 kubuntuisiert avahi-daemon[531]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::461e:a1ff:fee3:4377.
Apr 12 12:28:07 kubuntuisiert avahi-daemon[531]: New relevant interface eth0.IPv6 for mDNS.
Apr 12 12:28:07 kubuntuisiert avahi-daemon[531]: Registering new address record for fe80::461e:a1ff:fee3:4377 on eth0.*.
Apr 12 12:28:08 kubuntuisiert dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Apr 12 12:28:08 kubuntuisiert dhclient: DHCPREQUEST of 192.168.2.35 on eth0 to 255.255.255.255 port 67
Apr 12 12:28:08 kubuntuisiert dhclient: DHCPOFFER of 192.168.2.35 from 192.168.2.25
Apr 12 12:28:08 kubuntuisiert dhclient: DHCPACK of 192.168.2.35 from 192.168.2.25
Apr 12 12:28:08 kubuntuisiert dhclient: bound to 192.168.2.35 -- renewal in 2147483648 seconds.
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info> (eth0): DHCPv4 state changed preinit -> bound
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info>   address 192.168.2.35
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info>   prefix 24 (255.255.255.0)
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info>   gateway 192.168.2.25
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info>   hostname 'kubuntuisiert'
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info>   nameserver '192.168.2.25'
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 12 12:28:08 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 12 12:28:08 kubuntuisiert avahi-daemon[531]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.35.
Apr 12 12:28:08 kubuntuisiert avahi-daemon[531]: New relevant interface eth0.IPv4 for mDNS.
Apr 12 12:28:08 kubuntuisiert avahi-daemon[531]: Registering new address record for 192.168.2.35 on eth0.IPv4.
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> DNS: starting dnsmasq...
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Apr 12 12:28:09 kubuntuisiert dnsmasq[1286]: started, version 2.59 cache disabled
Apr 12 12:28:09 kubuntuisiert dnsmasq[1286]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Apr 12 12:28:09 kubuntuisiert dnsmasq[1286]: using nameserver 192.168.2.25#53
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> Policy set 'Kabelnetzwerkverbindung 1' (eth0) as default for IPv4 routing and DNS.
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) successful, device activated.
Apr 12 12:28:09 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 12 12:28:16 kubuntuisiert kernel: [   23.581997] eth0: no IPv6 routers present
Apr 12 12:28:17 kubuntuisiert ntpdate[1346]: adjust time server 91.189.94.4 offset -0.222477 sec
Apr 12 12:28:25 kubuntuisiert NetworkManager[860]: <info> (eth0): IP6 addrconf timed out or failed.
Apr 12 12:28:25 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 12 12:28:25 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 12 12:28:25 kubuntuisiert NetworkManager[860]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

8.) This is what i get, when i try to do an update at the CLIENT
```
kubuntuisiert:~$ sudo apt-get update
OK   http://at.archive.ubuntu.com precise Release.gpg
OK   http://extras.ubuntu.com precise Release.gpg                                                                                                           
Hole:1 http://at.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                                     
Hole:2 http://at.archive.ubuntu.com precise-backports Release.gpg [198 B]                                   
OK   http://extras.ubuntu.com precise Release                                                               
OK   http://at.archive.ubuntu.com precise Release                                                  
OK   http://extras.ubuntu.com precise/main Sources                                                                                                        
OK   http://extras.ubuntu.com precise/main amd64 Packages                                                                          
OK   http://extras.ubuntu.com precise/main i386 Packages                                           
95% [Warten auf Kopfzeilen] [Warten auf Kopfzeilen] [Warten auf Kopfzeilen] [Warten auf Kopfzeilen] -> waiting for headers

```

I know,this is much to read, but i just can't figure out what the problem is.....sadley

---

### Post by duesentriebchen on 2013-04-16
[COLOR=#008000]**SOLVED!!!**[/COLOR]
Somehow the installation of the new kernel gave the MTU to 576. By changing it back to 1500 with ```
sudo ifconfig eth0 mtu 1500
``` the router does the job as good as before the update :P

---

### Post by duesentriebchen on 2013-04-24
Hy all.

Found the bug which caused the MTU-setting.
[https://lists.ubuntu.com/archives/foundations-bugs/2012-July/100243.html](https://lists.ubuntu.com/archives/foundations-bugs/2012-July/100243.html)
Just change a letter from t to e, and the problem is solved :D

---

### Post by dkerins on 2013-06-27
Thanks for posting the solution to this issue duesentriebchen.  I was scratching my head for a day after a release update from 10.04 LTS to 12.04 LTS.

Really frustrating little bug.  I should buy you a beer. :-)

> **duesentriebchen said:**
> Hy all.

Found the bug which caused the MTU-setting.
[https://lists.ubuntu.com/archives/foundations-bugs/2012-July/100243.html](https://lists.ubuntu.com/archives/foundations-bugs/2012-July/100243.html)
Just change a letter from t to e, and the problem is solved :D

---

