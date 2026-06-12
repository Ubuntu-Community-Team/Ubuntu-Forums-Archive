---
title: "How can I log *everything* from the Ubuntu boot process to a text file?"
date: 2009-11-22
forum: The Cafe
---

### Post by youbuntu on 2009-11-22
Hi there. For the purpose of learning and teaching others, I wish to output *every single thing* that happens from when grub starts up until when I get the Ubuntu login screen, out to a text file. Is this even possible?. It *has* to be verbatim, *exactly* as it would be on the screen, with all messages etc.

Thanks folks! :D

---

### Post by NoaHall on 2009-11-22
Well, try looking at the log files in System -> Admin -> Log file viewer
There's quite a lot of details there.

---

### Post by Dharmachakra on 2009-11-22
I do...

dmesg > bootup.log

EDIT AGAIN: Never mind, it is the correct command.

---

### Post by youbuntu on 2009-11-22
Just to re-iterate folks - are you *sure* the methods you are suggesting are verbatim, and *exactly* the same as what is on the screen?. This is vital, and if you are in doubt, please say so - thanks.

---

### Post by scorp123 on 2009-11-22
[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

---

### Post by youbuntu on 2009-11-22
> **scorp123 said:**
> [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)

Wonderful!. Thankyou. :D

[EDIT]

Well that hasn't worked :?

```

matt@matt-desktop:~$ cat /var/log/boot
(Nothing has been logged yet.)

```

---

### Post by scorp123 on 2009-11-22
> **glossywhite said:**
> Wonderful!. Thankyou. :D

[EDIT]

Well that hasn't worked :?

```

matt@matt-desktop:~$ cat /var/log/boot
(Nothing has been logged yet.)

``` [https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/440812](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/440812)

EDIT:

Apparently there is a workaround?
[http://ohioloco.ubuntuforums.org/showthread.php?t=1304754](http://ohioloco.ubuntuforums.org/showthread.php?t=1304754)

---

### Post by scorp123 on 2009-11-22
Googling around ... the devs disabled this feature on purpose because there are some nasty bugs in that package?

[https://bugs.launchpad.net/upstart/+bug/98955](https://bugs.launchpad.net/upstart/+bug/98955)

But this bug has been open since at least 2007 ... and not yet fixed? Strange.

---

### Post by scorp123 on 2009-11-22
This forum member here posted the same workaround (manually enabling the "bootlogd" process):

[http://ubuntuforums.org/showpost.php?p=2441664&postcount=17](http://ubuntuforums.org/showpost.php?p=2441664&postcount=17)


So I'd say: bug or no bug ... give it a shot. If you start seeing funky behaviour you can disable the "bootlogd" from auto-starting again. And if you don't see any funky behaviour you should actually get something into that boot log...

---

### Post by youbuntu on 2009-11-22
Is this the log?

```

Nov 23 00:15:04 matt-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 23 00:15:04 matt-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="575" x-info="http://www.rsyslog.com"] (re)start
Nov 23 00:15:04 matt-desktop rsyslogd: rsyslogd's groupid changed to 102
Nov 23 00:15:04 matt-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] KERNEL supported cpus:
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Intel GenuineIntel
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   NSC Geode by NSC
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 0000000040000000 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000040000000 - 0000000050000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 0000000050000000 - 00000000be4b7000 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be4b7000 - 00000000be6b8000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be6b8000 - 00000000be860000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be860000 - 00000000be862000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be862000 - 00000000be863000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be863000 - 00000000be865000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000be865000 - 00000000bfec6000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfec6000 - 00000000bfec8000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfec8000 - 00000000bfec9000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfec9000 - 00000000bfecb000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfecb000 - 00000000bfecd000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfecd000 - 00000000bfedf000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfedf000 - 00000000bfef9000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfef9000 - 00000000bfeff000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000bfeff000 - 00000000bff00000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000d3400000 - 00000000d3401000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] DMI 2.4 present.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] last_pfn = 0xbe4b7 max_arch_pfn = 0x100000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] modified physical RAM map:
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000000100000 - 0000000040000000 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000040000000 - 0000000050000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 0000000050000000 - 00000000be4b7000 (usable)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be4b7000 - 00000000be6b8000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be6b8000 - 00000000be860000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be860000 - 00000000be862000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be862000 - 00000000be863000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be863000 - 00000000be865000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000be865000 - 00000000bfec6000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfec6000 - 00000000bfec8000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfec8000 - 00000000bfec9000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfec9000 - 00000000bfecb000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfecb000 - 00000000bfecd000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfecd000 - 00000000bfedf000 (ACPI NVS)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfedf000 - 00000000bfef9000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfef9000 - 00000000bfeff000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000bfeff000 - 00000000bff00000 (ACPI data)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000d3400000 - 00000000d3401000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f4000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]  modified: 00000000ffc00000 - 0000000100000000 (reserved)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] RAMDISK: 2f8b8000 - 3003fe65
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 APPLE )
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: XSDT bfeee1c0 00074 (v01 APPLE   Apple00 00000081      01000013)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: FACP bfeec000 000F4 (v03 APPLE   Apple00 00000081 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: DSDT bfee0000 050B8 (v01 APPLE   Macmini 00030001 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: FACS bfecd000 00040
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: HPET bfeeb000 00038 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: APIC bfeea000 00068 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: MCFG bfee9000 0003C (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: ASF! bfee8000 000A5 (v32 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: SBST bfee7000 00030 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: ECDT bfee6000 00053 (v01 APPLE   Apple00 00000001 Loki 0000005F)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: SSDT bfec8000 004DC (v01  APPLE    CpuPm 00003000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: SSDT bfedf000 000A5 (v01 SataRe  SataPri 00001000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: SSDT bfecc000 0009F (v01 SataRe  SataSec 00001000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] 2156MB HIGHMEM available.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] 887MB LOWMEM available.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   low ram: 0 - 377fe000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   node 0 low ram: 00000000 - 377fe000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   node 0 bootmap 00008000 - 0000ef00
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #4 [002f8b8000 - 003003fe65]          RAMDISK ==> [002f8b8000 - 003003fe65]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #6 [00008a9000 - 00008ac1ad]              BRK ==> [00008a9000 - 00008ac1ad]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Zone PFN ranges:
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]   HighMem  0x000377fe -> 0x000be4b7
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Movable zone start PFN for each node
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] early_node_map[4] active PFN ranges
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     0: 0x00000000 -> 0x00000002
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     0: 0x00000006 -> 0x0000009f
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     0: 0x00000100 -> 0x00040000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     0: 0x00050000 -> 0x000be4b7
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Using APIC driver default
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Allocating PCI resources starting at d3401000 (gap: d3401000:1cbff000)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PERCPU: Embedded 14 pages at c27e0000, static data 35612 bytes
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 707720
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=8f2939c8-0ce2-4f55-9251-7e53b6e61a73 ro quiet splash
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Initializing CPU#0
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] allocated 15588940 bytes of page_cgroup
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000be4b7)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Memory: 2798056k/3117788k available (4565k kernel code, 56180k reserved, 2143k data, 540k init, 1946340k highmem)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] virtual kernel memory layout:
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]       .data : 0xc0575554 - 0xc078d308   (2143 kB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000]       .text : 0xc0100000 - 0xc0575554   (4565 kB)
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] NR_IRQS:2304 nr_irqs:424
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Extended CMOS year: 2000
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Fast TSC calibration using PIT
Nov 23 00:15:04 matt-desktop kernel: [    0.000000] Detected 1990.007 MHz processor.
Nov 23 00:15:04 matt-desktop kernel: [    0.001966] Console: colour VGA+ 80x25
Nov 23 00:15:04 matt-desktop kernel: [    0.001970] console [tty0] enabled
Nov 23 00:15:04 matt-desktop kernel: [    0.002155] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Nov 23 00:15:04 matt-desktop kernel: [    0.002161] Calibrating delay loop (skipped), value calculated using timer frequency.. 3980.01 BogoMIPS (lpj=7960028)
Nov 23 00:15:04 matt-desktop kernel: [    0.002181] Security Framework initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.002203] AppArmor: AppArmor initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.002210] Mount-cache hash table entries: 512
Nov 23 00:15:04 matt-desktop kernel: [    0.002348] Initializing cgroup subsys ns
Nov 23 00:15:04 matt-desktop kernel: [    0.002353] Initializing cgroup subsys cpuacct
Nov 23 00:15:04 matt-desktop kernel: [    0.002358] Initializing cgroup subsys memory
Nov 23 00:15:04 matt-desktop kernel: [    0.002366] Initializing cgroup subsys freezer
Nov 23 00:15:04 matt-desktop kernel: [    0.002368] Initializing cgroup subsys net_cls
Nov 23 00:15:04 matt-desktop kernel: [    0.002385] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 00:15:04 matt-desktop kernel: [    0.002388] CPU: L2 cache: 3072K
Nov 23 00:15:04 matt-desktop kernel: [    0.002391] CPU: Physical Processor ID: 0
Nov 23 00:15:04 matt-desktop kernel: [    0.002393] CPU: Processor Core ID: 0
Nov 23 00:15:04 matt-desktop kernel: [    0.002398] mce: CPU supports 6 MCE banks
Nov 23 00:15:04 matt-desktop kernel: [    0.002408] CPU0: Thermal monitoring enabled (TM2)
Nov 23 00:15:04 matt-desktop kernel: [    0.002411] using mwait in idle threads.
Nov 23 00:15:04 matt-desktop kernel: [    0.002418] Performance Counters: Core2 events, Intel PMU driver.
Nov 23 00:15:04 matt-desktop kernel: [    0.002428] ... version:                 2
Nov 23 00:15:04 matt-desktop kernel: [    0.002430] ... bit width:               40
Nov 23 00:15:04 matt-desktop kernel: [    0.002432] ... generic counters:        2
Nov 23 00:15:04 matt-desktop kernel: [    0.002434] ... value mask:              000000ffffffffff
Nov 23 00:15:04 matt-desktop kernel: [    0.002436] ... max period:              000000007fffffff
Nov 23 00:15:04 matt-desktop kernel: [    0.002438] ... fixed-purpose counters:  3
Nov 23 00:15:04 matt-desktop kernel: [    0.002440] ... counter mask:            0000000700000003
Nov 23 00:15:04 matt-desktop kernel: [    0.002446] Checking 'hlt' instruction... OK.
Nov 23 00:15:04 matt-desktop kernel: [    0.019382] ACPI: Core revision 20090521
Nov 23 00:15:04 matt-desktop kernel: [    0.030739] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Nov 23 00:15:04 matt-desktop kernel: [    0.070431] CPU0: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 0a
Nov 23 00:15:04 matt-desktop kernel: [    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] Initializing CPU#1
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3979.98 BogoMIPS (lpj=7959964)
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] CPU: L2 cache: 3072K
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] CPU: Physical Processor ID: 0
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] CPU: Processor Core ID: 1
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] mce: CPU supports 6 MCE banks
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] CPU1: Thermal monitoring enabled (TM2)
Nov 23 00:15:04 matt-desktop kernel: [    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
Nov 23 00:15:04 matt-desktop kernel: [    0.158033] CPU1: Intel(R) Core(TM)2 Duo CPU     P7350  @ 2.00GHz stepping 0a
Nov 23 00:15:04 matt-desktop kernel: [    0.158052] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Nov 23 00:15:04 matt-desktop kernel: [    0.160023] Brought up 2 CPUs
Nov 23 00:15:04 matt-desktop kernel: [    0.160026] Total of 2 processors activated (7959.99 BogoMIPS).
Nov 23 00:15:04 matt-desktop kernel: [    0.160197] Booting paravirtualized kernel on bare hardware
Nov 23 00:15:04 matt-desktop kernel: [    0.160293] regulator: core version 0.5
Nov 23 00:15:04 matt-desktop kernel: [    0.160293] Time:  0:14:56  Date: 11/23/09
Nov 23 00:15:04 matt-desktop kernel: [    0.160293] NET: Registered protocol family 16
Nov 23 00:15:04 matt-desktop kernel: [    0.160293] EISA bus registered
Nov 23 00:15:04 matt-desktop kernel: [    0.160293] ACPI: bus type pci registered
Nov 23 00:15:04 matt-desktop kernel: [    0.160605] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255
Nov 23 00:15:04 matt-desktop kernel: [    0.160610] PCI: MCFG area at f0000000 reserved in E820
Nov 23 00:15:04 matt-desktop kernel: [    0.160613] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
Nov 23 00:15:04 matt-desktop kernel: [    0.160615] PCI: Using MMCONFIG for extended config space
Nov 23 00:15:04 matt-desktop kernel: [    0.160618] PCI: Using configuration type 1 for base access
Nov 23 00:15:04 matt-desktop kernel: [    0.164587] bio: create slab <bio-0> at 0
Nov 23 00:15:04 matt-desktop kernel: [    0.165405] ACPI: EC: EC description table is found, configuring boot EC
Nov 23 00:15:04 matt-desktop kernel: [    0.165574] ACPI: EC: non-query interrupt received, switching to interrupt mode
Nov 23 00:15:04 matt-desktop kernel: [    0.174606] ACPI: BIOS _OSI(Linux) query ignored
Nov 23 00:15:04 matt-desktop kernel: [    0.175291] ACPI: Interpreter enabled
Nov 23 00:15:04 matt-desktop kernel: [    0.175298] ACPI: (supports S0 S3 S4 S5)
Nov 23 00:15:04 matt-desktop kernel: [    0.175323] ACPI: Using IOAPIC for interrupt routing
Nov 23 00:15:04 matt-desktop kernel: [    0.187260] ACPI: EC: GPE = 0x3f, I/O: command/status = 0x66, data = 0x62
Nov 23 00:15:04 matt-desktop kernel: [    0.187263] ACPI: EC: driver started in interrupt mode
Nov 23 00:15:04 matt-desktop kernel: [    0.187672] ACPI: No dock devices found.
Nov 23 00:15:04 matt-desktop kernel: [    0.188022] ACPI: PCI Root Bridge [PCI0] (0000:00)
Nov 23 00:15:04 matt-desktop kernel: [    0.188453] pci 0000:00:03.2: PME# supported from D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.188459] pci 0000:00:03.2: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.188787] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.188792] pci 0000:00:04.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.188873] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.188877] pci 0000:00:04.1: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.188956] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.188961] pci 0000:00:06.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189042] pci 0000:00:06.1: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189046] pci 0000:00:06.1: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189124] pci 0000:00:08.0: PME# supported from D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189128] pci 0000:00:08.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189254] pci 0000:00:0a.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189260] pci 0000:00:0a.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189407] pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189412] pci 0000:00:10.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189625] pci 0000:00:15.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189634] pci 0000:00:15.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189871] pci 0000:00:16.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.189879] pci 0000:00:16.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.189978] pci 0000:00:09.0: transparent bridge
Nov 23 00:15:04 matt-desktop kernel: [    0.190466] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.190471] pci 0000:03:00.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.190697] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Nov 23 00:15:04 matt-desktop kernel: [    0.190703] pci 0000:04:00.0: PME# disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.264743] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 10 11 14 15) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.265048] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 10 11 14 15) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.265350] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 10 11 14 15) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.265653] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 10 11 14 15) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.265955] ACPI: PCI Interrupt Link [Z003] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.266259] ACPI: PCI Interrupt Link [Z004] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.266563] ACPI: PCI Interrupt Link [Z005] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.266867] ACPI: PCI Interrupt Link [Z006] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.267171] ACPI: PCI Interrupt Link [Z007] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.267476] ACPI: PCI Interrupt Link [Z008] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.267780] ACPI: PCI Interrupt Link [Z009] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.268093] ACPI: PCI Interrupt Link [Z00A] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.268398] ACPI: PCI Interrupt Link [Z00B] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.268701] ACPI: PCI Interrupt Link [Z00C] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.269005] ACPI: PCI Interrupt Link [Z00D] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.269308] ACPI: PCI Interrupt Link [Z00E] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.269613] ACPI: PCI Interrupt Link [Z00F] (IRQs 16 17 18 19 20 21 22 23) *10
Nov 23 00:15:04 matt-desktop kernel: [    0.269916] ACPI: PCI Interrupt Link [Z00G] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.270219] ACPI: PCI Interrupt Link [Z00H] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.270523] ACPI: PCI Interrupt Link [Z00I] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.270827] ACPI: PCI Interrupt Link [Z00J] (IRQs 16 17 18 19 20 21 22 23) *7
Nov 23 00:15:04 matt-desktop kernel: [    0.271132] ACPI: PCI Interrupt Link [Z00K] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.271436] ACPI: PCI Interrupt Link [Z00L] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.271741] ACPI: PCI Interrupt Link [Z00M] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.272055] ACPI: PCI Interrupt Link [Z00N] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.272360] ACPI: PCI Interrupt Link [Z00O] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.272663] ACPI: PCI Interrupt Link [Z00P] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.272967] ACPI: PCI Interrupt Link [Z00Q] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.273273] ACPI: PCI Interrupt Link [Z00R] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.273577] ACPI: PCI Interrupt Link [Z00S] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.273882] ACPI: PCI Interrupt Link [Z00T] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.274186] ACPI: PCI Interrupt Link [Z00U] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.274489] ACPI: PCI Interrupt Link [LSMB] (IRQs 16 17 18 19 20 21 22 23) *15
Nov 23 00:15:04 matt-desktop kernel: [    0.274792] ACPI: PCI Interrupt Link [LUS0] (IRQs 16 17 18 19 20 21 22 23) *11
Nov 23 00:15:04 matt-desktop kernel: [    0.275099] ACPI: PCI Interrupt Link [LUS2] (IRQs 16 17 18 19 20 21 22 23) *10
Nov 23 00:15:04 matt-desktop kernel: [    0.275405] ACPI: PCI Interrupt Link [LMAC] (IRQs 16 17 18 19 20 21 22 23) *14
Nov 23 00:15:04 matt-desktop kernel: [    0.275708] ACPI: PCI Interrupt Link [LAZA] (IRQs 16 17 18 19 20 21 22 23) *15
Nov 23 00:15:04 matt-desktop kernel: [    0.276024] ACPI: PCI Interrupt Link [LGPU] (IRQs 16 17 18 19 20 21 22 23) *11
Nov 23 00:15:04 matt-desktop kernel: [    0.276329] ACPI: PCI Interrupt Link [LPID] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.276634] ACPI: PCI Interrupt Link [LSI0] (IRQs 16 17 18 19 20 21 22 23) *11
Nov 23 00:15:04 matt-desktop kernel: [    0.276940] ACPI: PCI Interrupt Link [LSI1] (IRQs 16 17 18 19 20 21 22 23) *0, disabled.
Nov 23 00:15:04 matt-desktop kernel: [    0.277245] ACPI: PCI Interrupt Link [Z000] (IRQs 16 17 18 19 20 21 22 23) *7
Nov 23 00:15:04 matt-desktop kernel: [    0.277552] ACPI: PCI Interrupt Link [Z001] (IRQs 16 17 18 19 20 21 22 23) *5
Nov 23 00:15:04 matt-desktop kernel: [    0.277858] ACPI: PCI Interrupt Link [LPMU] (IRQs 16 17 18 19 20 21 22 23) *14
Nov 23 00:15:04 matt-desktop kernel: [    0.278096] SCSI subsystem initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.278118] usbcore: registered new interface driver usbfs
Nov 23 00:15:04 matt-desktop kernel: [    0.278118] usbcore: registered new interface driver hub
Nov 23 00:15:04 matt-desktop kernel: [    0.278118] usbcore: registered new device driver usb
Nov 23 00:15:04 matt-desktop kernel: [    0.278118] ACPI: WMI: Mapper loaded
Nov 23 00:15:04 matt-desktop kernel: [    0.278118] PCI: Using ACPI for IRQ routing
Nov 23 00:15:04 matt-desktop kernel: [    0.288012] Bluetooth: Core ver 2.15
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] NET: Registered protocol family 31
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] Bluetooth: HCI device and connection manager initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] Bluetooth: HCI socket layer initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] NetLabel: Initializing
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] NetLabel:  domain hash size = 128
Nov 23 00:15:04 matt-desktop kernel: [    0.288027] NetLabel:  protocols = UNLABELED CIPSOv4
Nov 23 00:15:04 matt-desktop kernel: [    0.288039] NetLabel:  unlabeled traffic allowed by default
Nov 23 00:15:04 matt-desktop kernel: [    0.288074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31, 31
Nov 23 00:15:04 matt-desktop kernel: [    0.288081] hpet0: 4 comparators, 64-bit 25.000000 MHz counter
Nov 23 00:15:04 matt-desktop kernel: [    0.304009] pnp: PnP ACPI init
Nov 23 00:15:04 matt-desktop kernel: [    0.304020] ACPI: bus type pnp registered
Nov 23 00:15:04 matt-desktop kernel: [    0.308074] pnp: PnP ACPI: found 8 devices
Nov 23 00:15:04 matt-desktop kernel: [    0.308077] ACPI: ACPI bus type pnp unregistered
Nov 23 00:15:04 matt-desktop kernel: [    0.308081] PnPBIOS: Disabled by ACPI PNP
Nov 23 00:15:04 matt-desktop kernel: [    0.308093] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308102] system 00:04: iomem range 0xfed00000-0xfed003ff has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308109] system 00:06: ioport range 0x400-0x47f has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308113] system 00:06: ioport range 0x480-0x4ff has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308116] system 00:06: ioport range 0x500-0x57f has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308120] system 00:06: ioport range 0x580-0x5ff has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308123] system 00:06: ioport range 0x800-0x87f has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308126] system 00:06: ioport range 0x880-0x8ff has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308130] system 00:06: ioport range 0x2140-0x217f has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308133] system 00:06: ioport range 0x2100-0x213f has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308137] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.308141] system 00:06: ioport range 0x295-0x296 has been reserved
Nov 23 00:15:04 matt-desktop kernel: [    0.342825] AppArmor: AppArmor Filesystem Enabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342896] pci 0000:00:09.0: PCI bridge, secondary bus 0000:01
Nov 23 00:15:04 matt-desktop kernel: [    0.342899] pci 0000:00:09.0:   IO window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342904] pci 0000:00:09.0:   MEM window: 0xd3300000-0xd33fffff
Nov 23 00:15:04 matt-desktop kernel: [    0.342909] pci 0000:00:09.0:   PREFETCH window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342913] pci 0000:00:10.0: PCI bridge, secondary bus 0000:02
Nov 23 00:15:04 matt-desktop kernel: [    0.342917] pci 0000:00:10.0:   IO window: 0x1000-0x1fff
Nov 23 00:15:04 matt-desktop kernel: [    0.342922] pci 0000:00:10.0:   MEM window: 0xd2000000-0xd30fffff
Nov 23 00:15:04 matt-desktop kernel: [    0.342926] pci 0000:00:10.0:   PREFETCH window: 0x000000c0000000-0x000000d1ffffff
Nov 23 00:15:04 matt-desktop kernel: [    0.342932] pci 0000:00:15.0: PCI bridge, secondary bus 0000:03
Nov 23 00:15:04 matt-desktop kernel: [    0.342934] pci 0000:00:15.0:   IO window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342946] pci 0000:00:15.0:   MEM window: 0xd3200000-0xd32fffff
Nov 23 00:15:04 matt-desktop kernel: [    0.342954] pci 0000:00:15.0:   PREFETCH window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342963] pci 0000:00:16.0: PCI bridge, secondary bus 0000:04
Nov 23 00:15:04 matt-desktop kernel: [    0.342965] pci 0000:00:16.0:   IO window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342977] pci 0000:00:16.0:   MEM window: 0xd3100000-0xd31fffff
Nov 23 00:15:04 matt-desktop kernel: [    0.342985] pci 0000:00:16.0:   PREFETCH window: disabled
Nov 23 00:15:04 matt-desktop kernel: [    0.342996] pci 0000:00:09.0: enabling device (0000 -> 0002)
Nov 23 00:15:04 matt-desktop kernel: [    0.343458] ACPI: PCI Interrupt Link [Z00F] enabled at IRQ 23
Nov 23 00:15:04 matt-desktop kernel: [    0.343472] pci 0000:00:15.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
Nov 23 00:15:04 matt-desktop kernel: [    0.343919] ACPI: PCI Interrupt Link [Z00J] enabled at IRQ 22
Nov 23 00:15:04 matt-desktop kernel: [    0.343930] pci 0000:00:16.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
Nov 23 00:15:04 matt-desktop kernel: [    0.344020] NET: Registered protocol family 2
Nov 23 00:15:04 matt-desktop kernel: [    0.344126] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.344469] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.344897] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.345121] TCP: Hash tables configured (established 131072 bind 65536)
Nov 23 00:15:04 matt-desktop kernel: [    0.345123] TCP reno registered
Nov 23 00:15:04 matt-desktop kernel: [    0.345202] NET: Registered protocol family 1
Nov 23 00:15:04 matt-desktop kernel: [    0.345262] Trying to unpack rootfs image as initramfs...
Nov 23 00:15:04 matt-desktop kernel: [    0.585823] Freeing initrd memory: 7711k freed
Nov 23 00:15:04 matt-desktop kernel: [    0.589376] cpufreq-nforce2: No nForce2 chipset.
Nov 23 00:15:04 matt-desktop kernel: [    0.589410] Scanning for low memory corruption every 60 seconds
Nov 23 00:15:04 matt-desktop kernel: [    0.589527] audit: initializing netlink socket (disabled)
Nov 23 00:15:04 matt-desktop kernel: [    0.589544] type=2000 audit(1258935296.588:1): initialized
Nov 23 00:15:04 matt-desktop kernel: [    0.600290] highmem bounce pool size: 64 pages
Nov 23 00:15:04 matt-desktop kernel: [    0.600296] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Nov 23 00:15:04 matt-desktop kernel: [    0.602096] VFS: Disk quotas dquot_6.5.2
Nov 23 00:15:04 matt-desktop kernel: [    0.602166] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Nov 23 00:15:04 matt-desktop kernel: [    0.602829] fuse init (API version 7.12)
Nov 23 00:15:04 matt-desktop kernel: [    0.602930] msgmni has been set to 1680
Nov 23 00:15:04 matt-desktop kernel: [    0.603171] alg: No test for stdrng (krng)
Nov 23 00:15:04 matt-desktop kernel: [    0.603187] io scheduler noop registered
Nov 23 00:15:04 matt-desktop kernel: [    0.603190] io scheduler anticipatory registered
Nov 23 00:15:04 matt-desktop kernel: [    0.603193] io scheduler deadline registered
Nov 23 00:15:04 matt-desktop kernel: [    0.603243] io scheduler cfq registered (default)
Nov 23 00:15:04 matt-desktop kernel: [    0.617126] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Nov 23 00:15:04 matt-desktop kernel: [    0.617155] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Nov 23 00:15:04 matt-desktop kernel: [    0.617314] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Nov 23 00:15:04 matt-desktop kernel: [    0.617318] ACPI: Power Button [PWRF]
Nov 23 00:15:04 matt-desktop kernel: [    0.617382] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Nov 23 00:15:04 matt-desktop kernel: [    0.617385] ACPI: Power Button [PWRB]
Nov 23 00:15:04 matt-desktop kernel: [    0.617439] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
Nov 23 00:15:04 matt-desktop kernel: [    0.617443] ACPI: Sleep Button [SLPB]
Nov 23 00:15:04 matt-desktop kernel: [    0.618470] ACPI: SSDT bfecac98 001F6 (v01  APPLE  Cpu0Ist 00003000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.619012] ACPI: SSDT bfec9c18 002AD (v01  APPLE  Cpu0Cst 00003001 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.619609] Marking TSC unstable due to TSC halts in idle
Nov 23 00:15:04 matt-desktop kernel: [    0.619632] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Nov 23 00:15:04 matt-desktop kernel: [    0.619662] processor LNXCPU:00: registered as cooling_device0
Nov 23 00:15:04 matt-desktop kernel: [    0.619666] ACPI: Processor [CPU0] (supports 8 throttling states)
Nov 23 00:15:04 matt-desktop kernel: [    0.620093] ACPI: SSDT bfecaf18 000C8 (v01  APPLE  Cpu1Ist 00003000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.620546] ACPI: SSDT bfec9f18 00085 (v01  APPLE  Cpu1Cst 00003000 INTL 20061109)
Nov 23 00:15:04 matt-desktop kernel: [    0.621269] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Nov 23 00:15:04 matt-desktop kernel: [    0.621299] processor LNXCPU:01: registered as cooling_device1
Nov 23 00:15:04 matt-desktop kernel: [    0.621304] ACPI: Processor [CPU1] (supports 8 throttling states)
Nov 23 00:15:04 matt-desktop kernel: [    0.626051] isapnp: Scanning for PnP cards...
Nov 23 00:15:04 matt-desktop kernel: [    0.978915] isapnp: No Plug & Play device found
Nov 23 00:15:04 matt-desktop kernel: [    0.980331] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Nov 23 00:15:04 matt-desktop kernel: [    0.981835] brd: module loaded
Nov 23 00:15:04 matt-desktop kernel: [    0.982378] loop: module loaded
Nov 23 00:15:04 matt-desktop kernel: [    0.982455] input: Macintosh mouse button emulation as /devices/virtual/input/input3
Nov 23 00:15:04 matt-desktop kernel: [    0.982985] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 21
Nov 23 00:15:04 matt-desktop kernel: [    0.982999] ahci 0000:00:0b.0: PCI INT A -> Link[LSI0] -> GSI 21 (level, low) -> IRQ 21
Nov 23 00:15:04 matt-desktop kernel: [    0.983107] ahci 0000:00:0b.0: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3 impl IDE mode
Nov 23 00:15:04 matt-desktop kernel: [    0.983111] ahci 0000:00:0b.0: flags: 64bit ncq sntf pm led pmp pio slum part 
Nov 23 00:15:04 matt-desktop kernel: [    0.983275] scsi0 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983367] scsi1 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983430] scsi2 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983494] scsi3 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983558] scsi4 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983624] scsi5 : ahci
Nov 23 00:15:04 matt-desktop kernel: [    0.983780] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 26
Nov 23 00:15:04 matt-desktop kernel: [    0.983784] ata2: SATA max UDMA/133 irq_stat 0x00400000, PHY RDY changed irq 26
Nov 23 00:15:04 matt-desktop kernel: [    0.983786] ata3: DUMMY
Nov 23 00:15:04 matt-desktop kernel: [    0.983788] ata4: DUMMY
Nov 23 00:15:04 matt-desktop kernel: [    0.983790] ata5: DUMMY
Nov 23 00:15:04 matt-desktop kernel: [    0.983792] ata6: DUMMY
Nov 23 00:15:04 matt-desktop kernel: [    0.984878] Fixed MDIO Bus: probed
Nov 23 00:15:04 matt-desktop kernel: [    0.984919] PPP generic driver version 2.4.2
Nov 23 00:15:04 matt-desktop kernel: [    0.985025] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Nov 23 00:15:04 matt-desktop kernel: [    0.985478] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20
Nov 23 00:15:04 matt-desktop kernel: [    0.985490] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUS2] -> GSI 20 (level, low) -> IRQ 20
Nov 23 00:15:04 matt-desktop kernel: [    0.985504] ehci_hcd 0000:00:04.1: EHCI Host Controller
Nov 23 00:15:04 matt-desktop kernel: [    0.985556] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
Nov 23 00:15:04 matt-desktop kernel: [    0.985582] ehci_hcd 0000:00:04.1: debug port 1
Nov 23 00:15:04 matt-desktop kernel: [    0.985605] ehci_hcd 0000:00:04.1: irq 20, io mem 0xd3489200
Nov 23 00:15:04 matt-desktop kernel: [    0.997012] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
Nov 23 00:15:04 matt-desktop kernel: [    0.997094] usb usb1: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    0.997129] hub 1-0:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    0.997140] hub 1-0:1.0: 7 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    0.997632] ACPI: PCI Interrupt Link [Z001] enabled at IRQ 19
Nov 23 00:15:04 matt-desktop kernel: [    0.997644] ehci_hcd 0000:00:06.1: PCI INT B -> Link[Z001] -> GSI 19 (level, low) -> IRQ 19
Nov 23 00:15:04 matt-desktop kernel: [    0.997658] ehci_hcd 0000:00:06.1: EHCI Host Controller
Nov 23 00:15:04 matt-desktop kernel: [    0.997695] ehci_hcd 0000:00:06.1: new USB bus registered, assigned bus number 2
Nov 23 00:15:04 matt-desktop kernel: [    0.997718] ehci_hcd 0000:00:06.1: debug port 1
Nov 23 00:15:04 matt-desktop kernel: [    0.997739] ehci_hcd 0000:00:06.1: irq 19, io mem 0xd3489100
Nov 23 00:15:04 matt-desktop kernel: [    1.008017] ehci_hcd 0000:00:06.1: USB 2.0 started, EHCI 1.00
Nov 23 00:15:04 matt-desktop kernel: [    1.008090] usb usb2: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    1.008122] hub 2-0:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    1.008129] hub 2-0:1.0: 5 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    1.008192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Nov 23 00:15:04 matt-desktop kernel: [    1.008642] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
Nov 23 00:15:04 matt-desktop kernel: [    1.008654] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
Nov 23 00:15:04 matt-desktop kernel: [    1.008667] ohci_hcd 0000:00:04.0: OHCI Host Controller
Nov 23 00:15:04 matt-desktop kernel: [    1.008712] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 3
Nov 23 00:15:04 matt-desktop kernel: [    1.008733] ohci_hcd 0000:00:04.0: irq 18, io mem 0xd3488000
Nov 23 00:15:04 matt-desktop kernel: [    1.066071] usb usb3: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    1.066104] hub 3-0:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    1.066113] hub 3-0:1.0: 7 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    1.066602] ACPI: PCI Interrupt Link [Z000] enabled at IRQ 17
Nov 23 00:15:04 matt-desktop kernel: [    1.066614] ohci_hcd 0000:00:06.0: PCI INT A -> Link[Z000] -> GSI 17 (level, low) -> IRQ 17
Nov 23 00:15:04 matt-desktop kernel: [    1.066628] ohci_hcd 0000:00:06.0: OHCI Host Controller
Nov 23 00:15:04 matt-desktop kernel: [    1.066664] ohci_hcd 0000:00:06.0: new USB bus registered, assigned bus number 4
Nov 23 00:15:04 matt-desktop kernel: [    1.066685] ohci_hcd 0000:00:06.0: irq 17, io mem 0xd3487000
Nov 23 00:15:04 matt-desktop kernel: [    1.122073] usb usb4: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    1.122105] hub 4-0:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    1.122114] hub 4-0:1.0: 5 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    1.122174] uhci_hcd: USB Universal Host Controller Interface driver
Nov 23 00:15:04 matt-desktop kernel: [    1.122258] PNP: No PS/2 controller found. Probing ports directly.
Nov 23 00:15:04 matt-desktop kernel: [    1.123194] mice: PS/2 mouse device common for all mice
Nov 23 00:15:04 matt-desktop kernel: [    1.123359] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Nov 23 00:15:04 matt-desktop kernel: [    1.123409] rtc0: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
Nov 23 00:15:04 matt-desktop kernel: [    1.123523] device-mapper: uevent: version 1.0.3
Nov 23 00:15:04 matt-desktop kernel: [    1.123621] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Nov 23 00:15:04 matt-desktop kernel: [    1.123711] device-mapper: multipath: version 1.1.0 loaded
Nov 23 00:15:04 matt-desktop kernel: [    1.123714] device-mapper: multipath round-robin: version 1.0.0 loaded
Nov 23 00:15:04 matt-desktop kernel: [    1.123848] EISA: Probing bus 0 at eisa.0
Nov 23 00:15:04 matt-desktop kernel: [    1.123853] Cannot allocate resource for EISA slot 1
Nov 23 00:15:04 matt-desktop kernel: [    1.123856] Cannot allocate resource for EISA slot 2
Nov 23 00:15:04 matt-desktop kernel: [    1.123876] EISA: Detected 0 cards.
Nov 23 00:15:04 matt-desktop kernel: [    1.124059] cpuidle: using governor ladder
Nov 23 00:15:04 matt-desktop kernel: [    1.124203] cpuidle: using governor menu
Nov 23 00:15:04 matt-desktop kernel: [    1.124783] TCP cubic registered
Nov 23 00:15:04 matt-desktop kernel: [    1.124967] NET: Registered protocol family 10
Nov 23 00:15:04 matt-desktop kernel: [    1.125505] lo: Disabled Privacy Extensions
Nov 23 00:15:04 matt-desktop kernel: [    1.125906] NET: Registered protocol family 17
Nov 23 00:15:04 matt-desktop kernel: [    1.125925] Bluetooth: L2CAP ver 2.13
Nov 23 00:15:04 matt-desktop kernel: [    1.125928] Bluetooth: L2CAP socket layer initialized
Nov 23 00:15:04 matt-desktop kernel: [    1.125931] Bluetooth: SCO (Voice Link) ver 0.6
Nov 23 00:15:04 matt-desktop kernel: [    1.125933] Bluetooth: SCO socket layer initialized
Nov 23 00:15:04 matt-desktop kernel: [    1.125966] Bluetooth: RFCOMM TTY layer initialized
Nov 23 00:15:04 matt-desktop kernel: [    1.125972] Bluetooth: RFCOMM socket layer initialized
Nov 23 00:15:04 matt-desktop kernel: [    1.125974] Bluetooth: RFCOMM ver 1.11
Nov 23 00:15:04 matt-desktop kernel: [    1.126683] Using IPI No-Shortcut mode
Nov 23 00:15:04 matt-desktop kernel: [    1.126748] registered taskstats version 1
Nov 23 00:15:04 matt-desktop kernel: [    1.126850]   Magic number: 1:922:203
Nov 23 00:15:04 matt-desktop kernel: [    1.126872] acpi device:2b: hash matches
Nov 23 00:15:04 matt-desktop kernel: [    1.126957] rtc_cmos 00:07: setting system clock to 2009-11-23 00:14:57 UTC (1258935297)
Nov 23 00:15:04 matt-desktop kernel: [    1.126960] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Nov 23 00:15:04 matt-desktop kernel: [    1.126962] EDD information not available.
Nov 23 00:15:04 matt-desktop kernel: [    1.308107] usb 1-1: new high speed USB device using ehci_hcd and address 2
Nov 23 00:15:04 matt-desktop kernel: [    1.449453] usb 1-1: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    1.449545] hub 1-1:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    1.449662] hub 1-1:1.0: 3 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    1.500090] Clocksource tsc unstable (delta = -363119525 ns)
Nov 23 00:15:04 matt-desktop kernel: [    1.868099] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 00:15:04 matt-desktop kernel: [    1.868536] ata1.00: ATA-8: FUJITSU MHZ2120BH G1, 00810009, max UDMA/100
Nov 23 00:15:04 matt-desktop kernel: [    1.868540] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
Nov 23 00:15:04 matt-desktop kernel: [    1.869143] ata1.00: configured for UDMA/100
Nov 23 00:15:04 matt-desktop kernel: [    1.872092] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Nov 23 00:15:04 matt-desktop kernel: [    1.878413] ata2.00: ATAPI: OPTIARC DVD RW AD-5670S, 2AHF, max UDMA/100, ATAPI AN
Nov 23 00:15:04 matt-desktop kernel: [    1.883999] ata2.00: configured for UDMA/100
Nov 23 00:15:04 matt-desktop kernel: [    1.884139] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHZ2120B 0081 PQ: 0 ANSI: 5
Nov 23 00:15:04 matt-desktop kernel: [    1.884255] sd 0:0:0:0: Attached scsi generic sg0 type 0
Nov 23 00:15:04 matt-desktop kernel: [    1.884292] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Nov 23 00:15:04 matt-desktop kernel: [    1.884335] sd 0:0:0:0: [sda] Write Protect is off
Nov 23 00:15:04 matt-desktop kernel: [    1.884361] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Nov 23 00:15:04 matt-desktop kernel: [    1.884474]  sda:
Nov 23 00:15:04 matt-desktop kernel: [    1.905909] scsi 1:0:0:0: CD-ROM            OPTIARC  DVD RW AD-5670S  2AHF PQ: 0 ANSI: 5
Nov 23 00:15:04 matt-desktop kernel: [    1.911722]  sda1 sda2 sda3
Nov 23 00:15:04 matt-desktop kernel: [    1.929321] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda caddy
Nov 23 00:15:04 matt-desktop kernel: [    1.929325] Uniform CD-ROM driver Revision: 3.20
Nov 23 00:15:04 matt-desktop kernel: [    1.929457] sr 1:0:0:0: Attached scsi generic sg1 type 5
Nov 23 00:15:04 matt-desktop kernel: [    1.939507] sd 0:0:0:0: [sda] Attached SCSI disk
Nov 23 00:15:04 matt-desktop kernel: [    1.939551] Freeing unused kernel memory: 540k freed
Nov 23 00:15:04 matt-desktop kernel: [    1.939854] Write protecting the kernel text: 4568k
Nov 23 00:15:04 matt-desktop kernel: [    1.939906] Write protecting the kernel read-only data: 1836k
Nov 23 00:15:04 matt-desktop kernel: [    2.080093] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
Nov 23 00:15:04 matt-desktop kernel: [    2.080499] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 16
Nov 23 00:15:04 matt-desktop kernel: [    2.080514] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 16 (level, low) -> IRQ 16
Nov 23 00:15:04 matt-desktop kernel: [    2.127751] ohci1394 0000:04:00.0: PCI INT A -> Link[Z00J] -> GSI 22 (level, low) -> IRQ 22
Nov 23 00:15:04 matt-desktop kernel: [    2.136099] usb 4-1: new full speed USB device using ohci_hcd and address 2
Nov 23 00:15:04 matt-desktop kernel: [    2.145392] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:25:4b:a4:fa:3a
Nov 23 00:15:04 matt-desktop kernel: [    2.145395] forcedeth 0000:00:0a.0: highdma csum pwrctl gbit lnktim msi desc-v3
Nov 23 00:15:04 matt-desktop kernel: [    2.183223] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[d3100000-d31007ff]  Max Packet=[4096]  IR/IT contexts=[8/8]
Nov 23 00:15:04 matt-desktop kernel: [    2.358182] usb 4-1: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    2.361127] hub 4-1:1.0: USB hub found
Nov 23 00:15:04 matt-desktop kernel: [    2.364116] hub 4-1:1.0: 3 ports detected
Nov 23 00:15:04 matt-desktop kernel: [    2.684032] usb 4-2: new full speed USB device using ohci_hcd and address 3
Nov 23 00:15:04 matt-desktop kernel: [    2.891099] usb 4-2: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    3.167181] xor: automatically using best checksumming function: pIII_sse
Nov 23 00:15:04 matt-desktop kernel: [    3.185007]    pIII_sse  :  7605.000 MB/sec
Nov 23 00:15:04 matt-desktop kernel: [    3.185009] xor: using function: pIII_sse (7605.000 MB/sec)
Nov 23 00:15:04 matt-desktop kernel: [    3.187270] device-mapper: dm-raid45: initialized v0.2594b
Nov 23 00:15:04 matt-desktop kernel: [    3.200033] usb 3-5: new low speed USB device using ohci_hcd and address 2
Nov 23 00:15:04 matt-desktop kernel: [    3.428108] usb 3-5: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    3.440195] usbcore: registered new interface driver hiddev
Nov 23 00:15:04 matt-desktop kernel: [    3.440242] usbcore: registered new interface driver usbhid
Nov 23 00:15:04 matt-desktop kernel: [    3.440245] usbhid: v2.6:USB HID core driver
Nov 23 00:15:04 matt-desktop kernel: [    3.453139] apple 0003:05AC:8242.0001: hiddev96,hidraw0: USB HID v1.11 Device [Apple Computer, Inc. IR Receiver] on usb-0000:00:04.0-5/input0
Nov 23 00:15:04 matt-desktop kernel: [    3.462009] PM: Starting manual resume from disk
Nov 23 00:15:04 matt-desktop kernel: [    3.492924] EXT4-fs (sda2): barriers enabled
Nov 23 00:15:04 matt-desktop kernel: [    3.516141] kjournald2 starting: pid 427, dev sda2:8, commit interval 5 seconds
Nov 23 00:15:04 matt-desktop kernel: [    3.516162] EXT4-fs (sda2): delayed allocation enabled
Nov 23 00:15:04 matt-desktop kernel: [    3.516166] EXT4-fs: file extents enabled
Nov 23 00:15:04 matt-desktop kernel: [    3.524567] EXT4-fs: mballoc enabled
Nov 23 00:15:04 matt-desktop kernel: [    3.524578] EXT4-fs (sda2): mounted filesystem with ordered data mode
Nov 23 00:15:04 matt-desktop kernel: [    3.736097] usb 3-7: new full speed USB device using ohci_hcd and address 3
Nov 23 00:15:04 matt-desktop kernel: [    3.950202] usb 3-7: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    4.024783] usb 1-1.2: new low speed USB device using ehci_hcd and address 5
Nov 23 00:15:04 matt-desktop kernel: [    4.123282] usb 1-1.2: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    4.127852] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.2/1-1.2:1.0/input/input4
Nov 23 00:15:04 matt-desktop kernel: [    4.127915] apple 0003:05AC:0221.0002: input,hidraw1: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:04.1-1.2/input0
Nov 23 00:15:04 matt-desktop kernel: [    4.132059] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.2/1-1.2:1.1/input/input5
Nov 23 00:15:04 matt-desktop kernel: [    4.132128] apple 0003:05AC:0221.0003: input,hidraw2: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:04.1-1.2/input1
Nov 23 00:15:04 matt-desktop kernel: [    4.192206] type=1505 audit(1258935300.565:2): operation="profile_load" pid=453 name=/usr/share/gdm/guest-session/Xsession
Nov 23 00:15:04 matt-desktop kernel: [    4.194877] type=1505 audit(1258935300.565:3): operation="profile_load" pid=461 name=/sbin/dhclient3
Nov 23 00:15:04 matt-desktop kernel: [    4.195624] type=1505 audit(1258935300.565:4): operation="profile_load" pid=461 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 23 00:15:04 matt-desktop kernel: [    4.196036] type=1505 audit(1258935300.569:5): operation="profile_load" pid=461 name=/usr/lib/connman/scripts/dhclient-script
Nov 23 00:15:04 matt-desktop kernel: [    4.244824] type=1505 audit(1258935300.617:6): operation="profile_load" pid=462 name=/usr/bin/evince
Nov 23 00:15:04 matt-desktop kernel: [    4.256175] type=1505 audit(1258935300.629:7): operation="profile_load" pid=462 name=/usr/bin/evince-previewer
Nov 23 00:15:04 matt-desktop kernel: [    4.262891] type=1505 audit(1258935300.633:8): operation="profile_load" pid=462 name=/usr/bin/evince-thumbnailer
Nov 23 00:15:04 matt-desktop kernel: [    4.282701] type=1505 audit(1258935300.653:9): operation="profile_load" pid=464 name=/usr/lib/cups/backend/cups-pdf
Nov 23 00:15:04 matt-desktop kernel: [    4.340859] usb 1-1.3: new low speed USB device using ehci_hcd and address 6
Nov 23 00:15:04 matt-desktop kernel: [    4.437979] usb 1-1.3: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    4.441547] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.3/1-1.3:1.0/input/input6
Nov 23 00:15:04 matt-desktop kernel: [    4.441610] generic-usb 0003:1267:0210.0004: input,hidraw3: USB HID v1.00 Mouse [PS/2+USB Mouse] on usb-0000:00:04.1-1.3/input0
Nov 23 00:15:04 matt-desktop kernel: [    4.518108] usb 4-1.1: new full speed USB device using ohci_hcd and address 4
Nov 23 00:15:04 matt-desktop kernel: [    4.642182] usb 4-1.1: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    4.722105] usb 4-1.2: new full speed USB device using ohci_hcd and address 5
Nov 23 00:15:04 matt-desktop kernel: [    4.833174] usb 4-1.2: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    4.843383] input: HID 05ac:820a as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.2/4-1.2:1.0/input/input7
Nov 23 00:15:04 matt-desktop kernel: [    4.843435] generic-usb 0003:05AC:820A.0005: input,hidraw4: USB HID v1.11 Keyboard [HID 05ac:820a] on usb-0000:00:06.0-1.2/input0
Nov 23 00:15:04 matt-desktop kernel: [    4.918108] usb 4-1.3: new full speed USB device using ohci_hcd and address 6
Nov 23 00:15:04 matt-desktop kernel: [    5.029170] usb 4-1.3: configuration #1 chosen from 1 choice
Nov 23 00:15:04 matt-desktop kernel: [    5.039308] input: HID 05ac:820b as /devices/pci0000:00/0000:00:06.0/usb4/4-1/4-1.3/4-1.3:1.0/input/input8
Nov 23 00:15:04 matt-desktop kernel: [    5.039370] generic-usb 0003:05AC:820B.0006: input,hidraw5: USB HID v1.11 Mouse [HID 05ac:820b] on usb-0000:00:06.0-1.3/input0
Nov 23 00:15:04 matt-desktop kernel: [    5.630860] Adding 4806716k swap on /dev/sda3.  Priority:-1 extents:1 across:4806716k 
Nov 23 00:15:04 matt-desktop kernel: [    6.723994] EXT4-fs (sda2): internal journal on sda2:8
Nov 23 00:15:04 matt-desktop kernel: [    7.955187] udev: starting version 147
Nov 23 00:15:04 matt-desktop kernel: [    8.442995] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Nov 23 00:15:04 matt-desktop kernel: [    8.459994] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2140
Nov 23 00:15:04 matt-desktop kernel: [    8.460032] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2100
Nov 23 00:15:05 matt-desktop kernel: [    8.680538] Bluetooth: Generic Bluetooth USB driver ver 0.5
Nov 23 00:15:05 matt-desktop kernel: [    8.680653] usbcore: registered new interface driver btusb
Nov 23 00:15:05 matt-desktop kernel: [    8.738544] lib80211: common routines for IEEE802.11 drivers
Nov 23 00:15:05 matt-desktop kernel: [    8.755277] Linux agpgart interface v0.103
Nov 23 00:15:05 matt-desktop kernel: [    8.757922] lp: driver loaded but no devices found
Nov 23 00:15:05 matt-desktop kernel: [    8.958873] __ratelimit: 9 callbacks suppressed
Nov 23 00:15:05 matt-desktop kernel: [    8.958876] type=1505 audit(1258935305.329:13): operation="profile_replace" pid=901 name=/usr/share/gdm/guest-session/Xsession
Nov 23 00:15:05 matt-desktop kernel: [    8.960544] type=1505 audit(1258935305.333:14): operation="profile_replace" pid=902 name=/sbin/dhclient3
Nov 23 00:15:05 matt-desktop kernel: [    8.961288] type=1505 audit(1258935305.333:15): operation="profile_replace" pid=902 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 23 00:15:05 matt-desktop kernel: [    8.961686] type=1505 audit(1258935305.333:16): operation="profile_replace" pid=902 name=/usr/lib/connman/scripts/dhclient-script
Nov 23 00:15:05 matt-desktop kernel: [    8.965288] type=1505 audit(1258935305.337:17): operation="profile_replace" pid=903 name=/usr/bin/evince
Nov 23 00:15:05 matt-desktop kernel: [    8.977085] type=1505 audit(1258935305.349:18): operation="profile_replace" pid=903 name=/usr/bin/evince-previewer
Nov 23 00:15:05 matt-desktop kernel: [    8.984021] type=1505 audit(1258935305.357:19): operation="profile_replace" pid=903 name=/usr/bin/evince-thumbnailer
Nov 23 00:15:05 matt-desktop kernel: [    8.993726] type=1505 audit(1258935305.365:20): operation="profile_replace" pid=905 name=/usr/lib/cups/backend/cups-pdf
Nov 23 00:15:05 matt-desktop kernel: [    8.994572] type=1505 audit(1258935305.365:21): operation="profile_replace" pid=905 name=/usr/sbin/cupsd
Nov 23 00:15:05 matt-desktop kernel: [    8.996970] type=1505 audit(1258935305.369:22): operation="profile_replace" pid=906 name=/usr/sbin/mysqld-akonadi
Nov 23 00:15:05 matt-desktop kernel: [    9.467408] usbcore: registered new interface driver snd-usb-audio
Nov 23 00:15:06 matt-desktop kernel: [    9.717627] applesmc: Apple Macmini detected:
Nov 23 00:15:06 matt-desktop kernel: [    9.717630] applesmc:  - Model without accelerometer
Nov 23 00:15:06 matt-desktop kernel: [    9.717632] applesmc:  - Model without light sensors and backlight
Nov 23 00:15:06 matt-desktop kernel: [    9.717634] applesmc:  - Model with 2 temperature sensors
Nov 23 00:15:06 matt-desktop kernel: [    9.717679] applesmc: device successfully initialized.
Nov 23 00:15:06 matt-desktop kernel: [    9.718469] applesmc: 1 fans found.
Nov 23 00:15:06 matt-desktop kernel: [    9.718502] applesmc: driver successfully loaded.
Nov 23 00:15:08 matt-desktop kernel: [   11.931805] nvidia: module license 'NVIDIA' taints kernel.
Nov 23 00:15:08 matt-desktop kernel: [   11.931810] Disabling lock debugging due to kernel taint
Nov 23 00:15:08 matt-desktop kernel: [   11.949356] wl 0000:03:00.0: power state changed by ACPI to D0
Nov 23 00:15:08 matt-desktop kernel: [   11.949561] wl 0000:03:00.0: PCI INT A -> Link[Z00F] -> GSI 23 (level, low) -> IRQ 23
Nov 23 00:15:08 matt-desktop kernel: [   11.968572] ip_tables: (C) 2000-2006 Netfilter Core Team
Nov 23 00:15:08 matt-desktop kernel: [   12.185804] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 23
Nov 23 00:15:08 matt-desktop kernel: [   12.185810] nvidia 0000:02:00.0: PCI INT A -> Link[LGPU] -> GSI 23 (level, low) -> IRQ 23
Nov 23 00:15:08 matt-desktop kernel: [   12.185957] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.36  Fri Aug 14 17:18:04 PDT 2009
Nov 23 00:15:08 matt-desktop kernel: [   12.269033] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
Nov 23 00:15:08 matt-desktop kernel: [   12.269039] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
Nov 23 00:15:08 matt-desktop kernel: [   12.539068] eth1: Broadcom BCM4328 802.11 Wireless Controller 5.10.91.9
Nov 23 00:15:08 matt-desktop kernel: [   12.598988] udev: renamed network interface eth1 to eth2
Nov 23 00:15:09 matt-desktop kernel: [   12.820098] hda_codec: Unknown model for ALC889A, trying auto-probe from BIOS...
Nov 23 00:15:09 matt-desktop kernel: [   12.836075] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:08.0/input/input9
Nov 23 00:15:12 matt-desktop kernel: [   16.498078] vboxdrv: fAsync=0 offMin=0x18d offMax=0x1cbe
Nov 23 00:15:12 matt-desktop kernel: [   16.498116] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Nov 23 00:15:13 matt-desktop kernel: [   16.872414] ppdev: user-space parallel port driver
Nov 23 00:15:13 matt-desktop kernel: [   17.387340] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Nov 23 00:15:13 matt-desktop kernel: [   17.387344] Bluetooth: BNEP filters: protocol multicast
Nov 23 00:15:14 matt-desktop kernel: [   17.682571] Bridge firewalling registered
Nov 23 00:15:14 matt-desktop kernel: [   17.989968] usb 4-1.2: USB disconnect, address 5
Nov 23 00:15:14 matt-desktop kernel: [   18.156101] usb 4-1.3: USB disconnect, address 6
Nov 23 00:15:21 matt-desktop pulseaudio[2128]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from -37.00 dB to -37.00 dB which makes no sense.
Nov 23 00:15:30 matt-desktop pulseaudio[2225]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from -37.00 dB to -37.00 dB which makes no sense.

```

the /var/log/boot is empty, but these messages were found @:

/var/log/messages

---

### Post by Dharmachakra on 2009-11-22
Again, dmesg works just as well, without any trouble.

EDIT: Don't mean to sound snobby or anything! :)

---

### Post by scorp123 on 2009-11-22
> **glossywhite said:**
> but these messages were found @:

/var/log/messages That's the system log, e.g. stuff that "dmesg" would spit out. Parts of the boot process get logged in there as well, yes. But it's not a verbatim copy of what happens during boot.

EDIT:

I agree with the poster above ... In 99.99% of most cases reading /var/log/messages and checking here and there with "dmesg" (= daemon messages) what's going on should usually be enough.

---

### Post by youbuntu on 2009-11-22
> **scorp123 said:**
> That's the system log, e.g. stuff that "dmesg" would spit out. Parts of the boot process get logged in there as well, yes. But it's not a verbatim copy of what happens during boot.

EDIT:

I agree with the poster above ... In 99.99% of most cases reading /var/log/messages and checking here and there with "dmesg" (= daemon messages) what's going on should usually be enough.

I need *110%* verbatim copy of the *exact* messages, as they are, including the:
```

doing something vital [  OK  ]

```

type messages

---

### Post by t0p on 2009-11-22
> **glossywhite said:**
> I need *110%* verbatim copy of the *exact* messages, as they are, including the:
```

doing something vital [  OK  ]

```type messages

You mean 100%, right?  Unless you want the file to contain all of the boot messages plus a tenth of them again.

---

### Post by youbuntu on 2009-11-22
> **t0p said:**
> You mean 100%, right?  Unless you want the file to contain all of the boot messages plus a tenth of them again.

:popcorn:

Entertaining!

---

### Post by cariboo on 2009-11-22
Grub does no logging, but /var/log/messages and dmesg print out everything you need to diagnose a problem if you have one. Did you notice the problem with your sound card in the snippet of dmesg you posted?

Creating a text file of the boot process is all well and good, but if you don't understand what you are looking at, it doesn't do a lot of good.

---

### Post by MaxIBoy on 2009-11-22
EDIT: nevermind.

---

