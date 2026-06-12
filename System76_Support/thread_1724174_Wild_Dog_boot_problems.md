---
title: "Wild Dog boot problems"
date: 2011-04-08
forum: System76 Support
---

### Post by riseringseeker on 2011-04-08
Our Wild Dog is once again not booting.  It goes through the POST, and the Ubuntu logo and flashing lights show up, but after flashing by what appears to be a terminal login prompt (far too quickly to log in, almost too fast to see) it goes to a black screen with a non-blinking cursor that is several lines down from the top and about two tab spaces over.  No key combination worked to go past this.

It did this to us a month or so ago, and after spending time with the patient folks at S76, we jointly decided that a re-install would likely be the quickest fix.

This worked fine until yesterday, when the same problem occurred.  As during the first time, I can ssh into the WD, but someone sitting at the computer cannot login.  Both times this has happened someone had not logged out, but I don't know if this was contributory, or coincidence.

I am "on the road", writing this from Germany, but will be home in a few days.  If there is anything anyone can think of that I could retrieve from the logs that might solve this, I would be happy to post it here.  I am sure the final solution, whatever it may be will have to wait until I can sit in front of the keyboard again, but would sure like a head start on tracking down what might be the problem.

I would very much like this to not happen again, I shouldn't have to re-install every month or two.

I did e-mail Tom Aaron, but he is no doubt up to his eyeballs and overlooked it.

---

### Post by isantop on 2011-04-08
Go ahead and log in to the system (ssh is fine), then run this command:

```
cat /var/log/syslog >> ~/syslog.txt
```

This will create a syslog.txt file in your home directory. Send that here, and I'll have a look.

---

### Post by riseringseeker on 2011-04-08
> **isantop said:**
> Go ahead and log in to the system (ssh is fine), then run this command:

```
cat /var/log/syslog >> ~/syslog.txt
```

This will create a syslog.txt file in your home directory. Send that here, and I'll have a look.

Here it is:

```
Apr  8 08:00:13 lindholm rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1037" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Apr  8 08:00:22 lindholm anacron[3827]: Job `cron.daily' terminated
Apr  8 08:00:22 lindholm anacron[3827]: Normal exit (1 job run)
Apr  8 08:17:01 lindholm CRON[4035]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 09:17:01 lindholm CRON[4047]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 10:17:01 lindholm CRON[4059]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 11:17:01 lindholm CRON[4072]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 12:17:01 lindholm CRON[4091]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 13:17:01 lindholm CRON[4103]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  8 14:11:28 lindholm NetworkManager[1066]: <error> [1302289888.668649] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Apr  8 14:11:28 lindholm NetworkManager[1066]: <error> [1302289888.671213] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Apr  8 14:11:51 lindholm sudo: pam_sm_authenticate: Called
Apr  8 14:11:51 lindholm sudo: pam_sm_authenticate: username = [karl]
Apr  8 14:16:28 lindholm kernel: Kernel logging (proc) stopped.
Apr  8 14:16:28 lindholm rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1037" x-info="http://www.rsyslog.com"] exiting on signal 15.
Apr  8 14:17:49 lindholm kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr  8 14:17:49 lindholm rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1051" x-info="http://www.rsyslog.com"] (re)start
Apr  8 14:17:49 lindholm rsyslogd: rsyslogd's groupid changed to 103
Apr  8 14:17:49 lindholm rsyslogd: rsyslogd's userid changed to 101
Apr  8 14:17:49 lindholm rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Apr  8 14:17:49 lindholm kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr  8 14:17:49 lindholm kernel: [    0.000000] Initializing cgroup subsys cpu
Apr  8 14:17:49 lindholm kernel: [    0.000000] Linux version 2.6.35-28-generic (buildd@allspice) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 (Ubuntu 2.6.35-28.49-generic 2.6.35.11)
Apr  8 14:17:49 lindholm kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=982904df-fb8a-46d5-a035-8217d484a67a ro quiet splash
Apr  8 14:17:49 lindholm kernel: [    0.000000] BIOS-provided physical RAM map:
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfa17000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfa17000 - 00000000cfa19000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfa19000 - 00000000cfafe000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfafe000 - 00000000cfbe5000 (ACPI NVS)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfbe5000 - 00000000cfbea000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfbea000 - 00000000cfbf3000 (ACPI data)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfbf3000 - 00000000cfbf4000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfbf4000 - 00000000cfbff000 (ACPI data)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfbff000 - 00000000cfc00000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000cfc00000 - 00000000d0000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f8000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000012c000000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000] NX (Execute Disable) protection: active
Apr  8 14:17:49 lindholm kernel: [    0.000000] DMI 2.4 present.
Apr  8 14:17:49 lindholm kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000] No AGP bridge found
Apr  8 14:17:49 lindholm kernel: [    0.000000] last_pfn = 0x12c000 max_arch_pfn = 0x400000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] MTRR default type: uncachable
Apr  8 14:17:49 lindholm kernel: [    0.000000] MTRR fixed ranges enabled:
Apr  8 14:17:49 lindholm kernel: [    0.000000]   00000-9FFFF write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   A0000-FFFFF uncachable
Apr  8 14:17:49 lindholm kernel: [    0.000000] MTRR variable ranges enabled:
Apr  8 14:17:49 lindholm kernel: [    0.000000]   0 base 000000000 mask F80000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   1 base 080000000 mask FC0000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   2 base 0C0000000 mask FF0000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   3 base 0CFC00000 mask FFFC00000 uncachable
Apr  8 14:17:49 lindholm kernel: [    0.000000]   4 base 100000000 mask FE0000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   5 base 120000000 mask FF8000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   6 base 128000000 mask FFC000000 write-back
Apr  8 14:17:49 lindholm kernel: [    0.000000]   7 disabled
Apr  8 14:17:49 lindholm kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr  8 14:17:49 lindholm kernel: [    0.000000] e820 update range: 00000000cfc00000 - 0000000100000000 (usable) ==> (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000] last_pfn = 0xcfc00 max_arch_pfn = 0x400000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] e820 update range: 0000000000001000 - 0000000000010000 (usable) ==> (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr  8 14:17:49 lindholm kernel: [    0.000000] modified physical RAM map:
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 0000000000100000 - 00000000cfa17000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfa17000 - 00000000cfa19000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfa19000 - 00000000cfafe000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfafe000 - 00000000cfbe5000 (ACPI NVS)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfbe5000 - 00000000cfbea000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfbea000 - 00000000cfbf3000 (ACPI data)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfbf3000 - 00000000cfbf4000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfbf4000 - 00000000cfbff000 (ACPI data)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfbff000 - 00000000cfc00000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000cfc00000 - 00000000d0000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000f0000000 - 00000000f8000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
Apr  8 14:17:49 lindholm kernel: [    0.000000]  modified: 0000000100000000 - 000000012c000000 (usable)
Apr  8 14:17:49 lindholm kernel: [    0.000000] initial memory mapped : 0 - 20000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] found SMP MP-table at [ffff8800000fe200] fe200
Apr  8 14:17:49 lindholm kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000cfc00000
Apr  8 14:17:49 lindholm kernel: [    0.000000]  0000000000 - 00cfc00000 page 2M
Apr  8 14:17:49 lindholm kernel: [    0.000000] kernel direct mapping tables up to cfc00000 @ 16000-1b000
Apr  8 14:17:49 lindholm kernel: [    0.000000] init_memory_mapping: 0000000100000000-000000012c000000
Apr  8 14:17:49 lindholm kernel: [    0.000000]  0100000000 - 012c000000 page 2M
Apr  8 14:17:49 lindholm kernel: [    0.000000] kernel direct mapping tables up to 12c000000 @ 19000-1f000
Apr  8 14:17:49 lindholm kernel: [    0.000000] RAMDISK: 36f4a000 - 37ff0000
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: RSDP 00000000000fe020 00014 (v00 INTEL )
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: RSDT 00000000cfbfd038 0005C (v01 INTEL  DP35DP   00000125      01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: FACP 00000000cfbfc000 00074 (v01 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: DSDT 00000000cfbf8000 03D05 (v01 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: FACS 00000000cfb99000 00040
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: APIC 00000000cfbf7000 00078 (v01 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: WDDT 00000000cfbf6000 00040 (v01 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: MCFG 00000000cfbf5000 0003C (v01 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: ASF! 00000000cfbf4000 000A6 (v32 INTEL  DP35DP   00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbf2000 00204 (v01 INTEL     CpuPm 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbf1000 00175 (v01 INTEL   Cpu0Ist 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbf0000 00175 (v01 INTEL   Cpu1Ist 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbef000 00175 (v01 INTEL   Cpu2Ist 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbee000 00175 (v01 INTEL   Cpu3Ist 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbed000 000DD (v01 INTEL   Cpu0Cst 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbec000 000DD (v01 INTEL   Cpu1Cst 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbeb000 000DD (v01 INTEL   Cpu2Cst 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: SSDT 00000000cfbea000 000DD (v01 INTEL   Cpu3Cst 00000125 MSFT 01000013)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 14:17:49 lindholm kernel: [    0.000000] No NUMA configuration found
Apr  8 14:17:49 lindholm kernel: [    0.000000] Faking a node at 0000000000000000-000000012c000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] Initmem setup node 0 0000000000000000-000000012c000000
Apr  8 14:17:49 lindholm kernel: [    0.000000]   NODE_DATA [0000000100000000 - 0000000100004fff]
Apr  8 14:17:49 lindholm kernel: [    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff880100200000-ffff880103bfffff] on node 0
Apr  8 14:17:49 lindholm kernel: [    0.000000] Zone PFN ranges:
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Apr  8 14:17:49 lindholm kernel: [    0.000000]   Normal   0x00100000 -> 0x0012c000
Apr  8 14:17:49 lindholm kernel: [    0.000000] Movable zone start PFN for each node
Apr  8 14:17:49 lindholm kernel: [    0.000000] early_node_map[7] active PFN ranges
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x00000100 -> 0x000cfa17
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x000cfa19 -> 0x000cfafe
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x000cfbe5 -> 0x000cfbea
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x000cfbf3 -> 0x000cfbf4
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x000cfbff -> 0x000cfc00
Apr  8 14:17:49 lindholm kernel: [    0.000000]     0: 0x00100000 -> 0x0012c000
Apr  8 14:17:49 lindholm kernel: [    0.000000] On node 0 totalpages: 1030802
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA zone: 0 pages reserved
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA zone: 3927 pages, LIFO batch:0
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA32 zone: 14280 pages used for memmap
Apr  8 14:17:49 lindholm kernel: [    0.000000]   DMA32 zone: 832315 pages, LIFO batch:31
Apr  8 14:17:49 lindholm kernel: [    0.000000]   Normal zone: 2464 pages used for memmap
Apr  8 14:17:49 lindholm kernel: [    0.000000]   Normal zone: 177760 pages, LIFO batch:31
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Apr  8 14:17:49 lindholm kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr  8 14:17:49 lindholm kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr  8 14:17:49 lindholm kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr  8 14:17:49 lindholm kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Apr  8 14:17:49 lindholm kernel: [    0.000000] nr_irqs_gsi: 40
Apr  8 14:17:49 lindholm kernel: [    0.000000] early_res array is doubled to 64 at [1a000 - 1a7ff]
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000cfa17000 - 00000000cfa19000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000cfafe000 - 00000000cfbe5000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000cfbea000 - 00000000cfbf3000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000cfbf4000 - 00000000cfbff000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000cfc00000 - 00000000d0000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000f0000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000f0000000 - 00000000f8000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fff00000
Apr  8 14:17:49 lindholm kernel: [    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
Apr  8 14:17:49 lindholm kernel: [    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:20000000)
Apr  8 14:17:49 lindholm kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr  8 14:17:49 lindholm kernel: [    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
Apr  8 14:17:49 lindholm kernel: [    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u524288
Apr  8 14:17:49 lindholm kernel: [    0.000000] early_res array is doubled to 128 at [1a800 - 1b7ff]
Apr  8 14:17:49 lindholm kernel: [    0.000000] pcpu-alloc: s91520 r8192 d23168 u524288 alloc=1*2097152
Apr  8 14:17:49 lindholm kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Apr  8 14:17:49 lindholm kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1014002
Apr  8 14:17:49 lindholm kernel: [    0.000000] Policy zone: Normal
Apr  8 14:17:49 lindholm kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=982904df-fb8a-46d5-a035-8217d484a67a ro quiet splash
Apr  8 14:17:49 lindholm kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.000000] Checking aperture...
Apr  8 14:17:49 lindholm kernel: [    0.000000] No AGP bridge found
Apr  8 14:17:49 lindholm kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Apr  8 14:17:49 lindholm kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Apr  8 14:17:49 lindholm kernel: [    0.000000] Subtract (64 early reservations)
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #1 [0001000000 - 0001d18114]   TEXT DATA BSS
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #2 [0036f4a000 - 0037ff0000]         RAMDISK
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #3 [0001d19000 - 0001d1915e]             BRK
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #4 [000009fc00 - 00000fe200]   BIOS reserved
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #5 [00000fe200 - 00000fe210]    MP-table mpf
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #6 [00000fe250 - 0000100000]   BIOS reserved
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #7 [00000fe210 - 00000fe250]    MP-table mpc
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #8 [0000010000 - 0000012000]      TRAMPOLINE
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #9 [0000012000 - 0000016000]     ACPI WAKEUP
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #10 [0000016000 - 0000019000]         PGTABLE
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #11 [0000019000 - 000001a000]         PGTABLE
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #12 [0100000000 - 0100005000]       NODE_DATA
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #13 [0001d19180 - 0001d1a180]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #14 [0001d18140 - 0001d18440]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #15 [0100005000 - 0100006000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #16 [0100006000 - 0100007000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #17 [0100200000 - 0103c00000]        MEMMAP 0
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #18 [0001d18440 - 0001d185c0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #19 [0001d1a180 - 0001d32180]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #20 [0001d32180 - 0001d38180]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #21 [0001d39000 - 0001d3a000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #22 [0001d185c0 - 0001d18603]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #23 [0001d18640 - 0001d189f8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #24 [0001d18a00 - 0001d18a68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #25 [0001d18a80 - 0001d18ae8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #26 [0001d18b00 - 0001d18b68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #27 [0001d18b80 - 0001d18be8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #28 [0001d18c00 - 0001d18c68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #29 [0001d18c80 - 0001d18ce8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #30 [0001d18d00 - 0001d18d68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #31 [0001d18d80 - 0001d18de8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #32 [0001d18e00 - 0001d18e68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #33 [0001d18e80 - 0001d18ee8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #34 [0001d18f00 - 0001d18f68]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #35 [0001d18f80 - 0001d18fe8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #36 [0001d38180 - 0001d381e8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #37 [0001d38200 - 0001d38268]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #38 [0001d38280 - 0001d382e8]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #39 [0001d38300 - 0001d38368]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #40 [0001d38380 - 0001d383a0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #41 [0001d383c0 - 0001d383e0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #42 [0001d38400 - 0001d38420]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #43 [0001d38440 - 0001d38460]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #44 [0001d38480 - 0001d384a0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #45 [0001d384c0 - 0001d384e0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #46 [0001d38500 - 0001d3856a]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #47 [0001d38580 - 0001d385ea]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #48 [0001e00000 - 0001e1e000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #49 [0001e80000 - 0001e9e000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #50 [0001f00000 - 0001f1e000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #51 [0001f80000 - 0001f9e000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #52 [0001d38600 - 0001d38608]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #53 [0001d38640 - 0001d38648]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #54 [0001d38680 - 0001d38690]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #55 [0001d386c0 - 0001d386e0]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #56 [0001d38700 - 0001d38830]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #57 [0001d38840 - 0001d38890]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #58 [0001d388c0 - 0001d38910]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #59 [0001d3a000 - 0001d42000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #60 [0001f9e000 - 0005f9e000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #61 [0001d42000 - 0001d62000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #62 [0001d62000 - 0001da2000]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000]   #63 [000001b800 - 0000023800]         BOOTMEM
Apr  8 14:17:49 lindholm kernel: [    0.000000] Memory: 3966688k/4915200k available (5716k kernel code, 791992k absent, 156520k reserved, 5375k data, 912k init)
Apr  8 14:17:49 lindholm kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Apr  8 14:17:49 lindholm kernel: [    0.000000] Hierarchical RCU implementation.
Apr  8 14:17:49 lindholm kernel: [    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
Apr  8 14:17:49 lindholm kernel: [    0.000000] 	RCU-based detection of stalled CPUs is disabled.
Apr  8 14:17:49 lindholm kernel: [    0.000000] 	Verbose stalled-CPUs detection is disabled.
Apr  8 14:17:49 lindholm kernel: [    0.000000] NR_IRQS:4352 nr_irqs:712
Apr  8 14:17:49 lindholm kernel: [    0.000000] Console: colour VGA+ 80x25
Apr  8 14:17:49 lindholm kernel: [    0.000000] console [tty0] enabled
Apr  8 14:17:49 lindholm kernel: [    0.000000] allocated 41943040 bytes of page_cgroup
Apr  8 14:17:49 lindholm kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr  8 14:17:49 lindholm kernel: [    0.000000] Fast TSC calibration failed
Apr  8 14:17:49 lindholm kernel: [    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
Apr  8 14:17:49 lindholm kernel: [    0.000000] Detected 2333.058 MHz processor.
Apr  8 14:17:49 lindholm kernel: [    0.020009] Calibrating delay loop (skipped), value calculated using timer frequency.. 4666.11 BogoMIPS (lpj=23330580)
Apr  8 14:17:49 lindholm kernel: [    0.020013] pid_max: default: 32768 minimum: 301
Apr  8 14:17:49 lindholm kernel: [    0.020038] Security Framework initialized
Apr  8 14:17:49 lindholm kernel: [    0.020055] AppArmor: AppArmor initialized
Apr  8 14:17:49 lindholm kernel: [    0.020056] Yama: becoming mindful.
Apr  8 14:17:49 lindholm kernel: [    0.020498] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.022968] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.024128] Mount-cache hash table entries: 256
Apr  8 14:17:49 lindholm kernel: [    0.024277] Initializing cgroup subsys ns
Apr  8 14:17:49 lindholm kernel: [    0.024283] Initializing cgroup subsys cpuacct
Apr  8 14:17:49 lindholm kernel: [    0.024286] Initializing cgroup subsys memory
Apr  8 14:17:49 lindholm kernel: [    0.024295] Initializing cgroup subsys devices
Apr  8 14:17:49 lindholm kernel: [    0.024297] Initializing cgroup subsys freezer
Apr  8 14:17:49 lindholm kernel: [    0.024299] Initializing cgroup subsys net_cls
Apr  8 14:17:49 lindholm kernel: [    0.024328] CPU: Physical Processor ID: 0
Apr  8 14:17:49 lindholm kernel: [    0.024329] CPU: Processor Core ID: 0
Apr  8 14:17:49 lindholm kernel: [    0.024331] mce: CPU supports 6 MCE banks
Apr  8 14:17:49 lindholm kernel: [    0.024339] CPU0: Thermal monitoring enabled (TM2)
Apr  8 14:17:49 lindholm kernel: [    0.024343] using mwait in idle threads.
Apr  8 14:17:49 lindholm kernel: [    0.024345] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Apr  8 14:17:49 lindholm kernel: [    0.030012] PEBS disabled due to CPU errata.
Apr  8 14:17:49 lindholm kernel: [    0.030016] ... version:                2
Apr  8 14:17:49 lindholm kernel: [    0.030018] ... bit width:              40
Apr  8 14:17:49 lindholm kernel: [    0.030019] ... generic registers:      2
Apr  8 14:17:49 lindholm kernel: [    0.030021] ... value mask:             000000ffffffffff
Apr  8 14:17:49 lindholm kernel: [    0.030022] ... max period:             000000007fffffff
Apr  8 14:17:49 lindholm kernel: [    0.030024] ... fixed-purpose events:   3
Apr  8 14:17:49 lindholm kernel: [    0.030025] ... event mask:             0000000700000003
Apr  8 14:17:49 lindholm kernel: [    0.032345] ACPI: Core revision 20100428
Apr  8 14:17:49 lindholm kernel: [    0.040011] ftrace: converting mcount calls to 0f 1f 44 00 00
Apr  8 14:17:49 lindholm kernel: [    0.040016] ftrace: allocating 22688 entries in 89 pages
Apr  8 14:17:49 lindholm kernel: [    0.048886] Setting APIC routing to flat
Apr  8 14:17:49 lindholm kernel: [    0.049188] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr  8 14:17:49 lindholm kernel: [    0.149585] CPU0: Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz stepping 0b
Apr  8 14:17:49 lindholm kernel: [    0.150000] Booting Node   0, Processors  #1
Apr  8 14:17:49 lindholm kernel: [    0.310015] Brought up 2 CPUs
Apr  8 14:17:49 lindholm kernel: [    0.310019] Total of 2 processors activated (9332.33 BogoMIPS).
Apr  8 14:17:49 lindholm kernel: [    0.310624] devtmpfs: initialized
Apr  8 14:17:49 lindholm kernel: [    0.310648] regulator: core version 0.5
Apr  8 14:17:49 lindholm kernel: [    0.310671] Time: 19:17:22  Date: 04/08/11
Apr  8 14:17:49 lindholm kernel: [    0.310706] NET: Registered protocol family 16
Apr  8 14:17:49 lindholm kernel: [    0.310726] Trying to unpack rootfs image as initramfs...
Apr  8 14:17:49 lindholm kernel: [    0.310826] ACPI: bus type pci registered
Apr  8 14:17:49 lindholm kernel: [    0.310895] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
Apr  8 14:17:49 lindholm kernel: [    0.310898] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
Apr  8 14:17:49 lindholm kernel: [    0.344782] PCI: Using configuration type 1 for base access
Apr  8 14:17:49 lindholm kernel: [    0.350080] bio: create slab <bio-0> at 0
Apr  8 14:17:49 lindholm kernel: [    0.351054] ACPI: EC: Look up EC in DSDT
Apr  8 14:17:49 lindholm kernel: [    0.353751] ACPI: Interpreter enabled
Apr  8 14:17:49 lindholm kernel: [    0.353754] ACPI: (supports S0 S1 S3 S4 S5)
Apr  8 14:17:49 lindholm kernel: [    0.353774] ACPI: Using IOAPIC for interrupt routing
Apr  8 14:17:49 lindholm kernel: [    0.358150] ACPI: No dock devices found.
Apr  8 14:17:49 lindholm kernel: [    0.358154] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
Apr  8 14:17:49 lindholm kernel: [    0.359018] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr  8 14:17:49 lindholm kernel: [    0.360749] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360752] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360754] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360757] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000effff] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360759] pci_root PNP0A03:00: host bridge window [mem 0xf8000000-0xfeafffff] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360761] pci_root PNP0A03:00: host bridge window [mem 0xd0000000-0xefffffff] (ignored)
Apr  8 14:17:49 lindholm kernel: [    0.360827] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.360830] pci 0000:00:01.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.360856] pci 0000:00:03.0: reg 10: [mem 0xe3225900-0xe322590f 64bit]
Apr  8 14:17:49 lindholm kernel: [    0.360882] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.360885] pci 0000:00:03.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.360941] pci 0000:00:19.0: reg 10: [mem 0xe3200000-0xe321ffff]
Apr  8 14:17:49 lindholm kernel: [    0.360946] pci 0000:00:19.0: reg 14: [mem 0xe3224000-0xe3224fff]
Apr  8 14:17:49 lindholm kernel: [    0.360951] pci 0000:00:19.0: reg 18: [io  0x30e0-0x30ff]
Apr  8 14:17:49 lindholm kernel: [    0.360986] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.360989] pci 0000:00:19.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361029] pci 0000:00:1a.0: reg 20: [io  0x30c0-0x30df]
Apr  8 14:17:49 lindholm kernel: [    0.361087] pci 0000:00:1a.1: reg 20: [io  0x30a0-0x30bf]
Apr  8 14:17:49 lindholm kernel: [    0.361148] pci 0000:00:1a.2: reg 20: [io  0x3080-0x309f]
Apr  8 14:17:49 lindholm kernel: [    0.361205] pci 0000:00:1a.7: reg 10: [mem 0xe3225400-0xe32257ff]
Apr  8 14:17:49 lindholm kernel: [    0.361253] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361258] pci 0000:00:1a.7: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361291] pci 0000:00:1b.0: reg 10: [mem 0xe3220000-0xe3223fff 64bit]
Apr  8 14:17:49 lindholm kernel: [    0.361327] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361330] pci 0000:00:1b.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361388] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361391] pci 0000:00:1c.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361449] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361453] pci 0000:00:1c.1: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361518] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361521] pci 0000:00:1c.2: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361579] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361583] pci 0000:00:1c.3: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361641] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361644] pci 0000:00:1c.4: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.361690] pci 0000:00:1d.0: reg 20: [io  0x3060-0x307f]
Apr  8 14:17:49 lindholm kernel: [    0.361750] pci 0000:00:1d.1: reg 20: [io  0x3040-0x305f]
Apr  8 14:17:49 lindholm kernel: [    0.361808] pci 0000:00:1d.2: reg 20: [io  0x3020-0x303f]
Apr  8 14:17:49 lindholm kernel: [    0.361865] pci 0000:00:1d.7: reg 10: [mem 0xe3225000-0xe32253ff]
Apr  8 14:17:49 lindholm kernel: [    0.361914] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Apr  8 14:17:49 lindholm kernel: [    0.361918] pci 0000:00:1d.7: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.362034] pci 0000:00:1f.0: Force enabled HPET at 0xfed00000
Apr  8 14:17:49 lindholm kernel: [    0.362043] pci 0000:00:1f.0: quirk: [io  0x0400-0x047f] claimed by ICH6 ACPI/GPIO/TCO
Apr  8 14:17:49 lindholm kernel: [    0.362046] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
Apr  8 14:17:49 lindholm kernel: [    0.362050] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
Apr  8 14:17:49 lindholm kernel: [    0.362053] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at 0810 (mask 007f)
Apr  8 14:17:49 lindholm kernel: [    0.362097] pci 0000:00:1f.2: reg 10: [io  0x3458-0x345f]
Apr  8 14:17:49 lindholm kernel: [    0.362102] pci 0000:00:1f.2: reg 14: [io  0x346c-0x346f]
Apr  8 14:17:49 lindholm kernel: [    0.362107] pci 0000:00:1f.2: reg 18: [io  0x3450-0x3457]
Apr  8 14:17:49 lindholm kernel: [    0.362112] pci 0000:00:1f.2: reg 1c: [io  0x3468-0x346b]
Apr  8 14:17:49 lindholm kernel: [    0.362117] pci 0000:00:1f.2: reg 20: [io  0x3430-0x343f]
Apr  8 14:17:49 lindholm kernel: [    0.362122] pci 0000:00:1f.2: reg 24: [io  0x3420-0x342f]
Apr  8 14:17:49 lindholm kernel: [    0.362163] pci 0000:00:1f.3: reg 10: [mem 0xe3225800-0xe32258ff 64bit]
Apr  8 14:17:49 lindholm kernel: [    0.362175] pci 0000:00:1f.3: reg 20: [io  0x3000-0x301f]
Apr  8 14:17:49 lindholm kernel: [    0.362208] pci 0000:00:1f.5: reg 10: [io  0x3448-0x344f]
Apr  8 14:17:49 lindholm kernel: [    0.362213] pci 0000:00:1f.5: reg 14: [io  0x3464-0x3467]
Apr  8 14:17:49 lindholm kernel: [    0.362218] pci 0000:00:1f.5: reg 18: [io  0x3440-0x3447]
Apr  8 14:17:49 lindholm kernel: [    0.362223] pci 0000:00:1f.5: reg 1c: [io  0x3460-0x3463]
Apr  8 14:17:49 lindholm kernel: [    0.362228] pci 0000:00:1f.5: reg 20: [io  0x3410-0x341f]
Apr  8 14:17:49 lindholm kernel: [    0.362233] pci 0000:00:1f.5: reg 24: [io  0x3400-0x340f]
Apr  8 14:17:49 lindholm kernel: [    0.362303] pci 0000:01:00.0: reg 10: [mem 0xe2000000-0xe2ffffff]
Apr  8 14:17:49 lindholm kernel: [    0.362311] pci 0000:01:00.0: reg 14: [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.362319] pci 0000:01:00.0: reg 1c: [mem 0xe0000000-0xe1ffffff 64bit]
Apr  8 14:17:49 lindholm kernel: [    0.362324] pci 0000:01:00.0: reg 24: [io  0x2000-0x207f]
Apr  8 14:17:49 lindholm kernel: [    0.362329] pci 0000:01:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
Apr  8 14:17:49 lindholm kernel: [    0.362369] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr  8 14:17:49 lindholm kernel: [    0.362372] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Apr  8 14:17:49 lindholm kernel: [    0.362375] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe2ffffff]
Apr  8 14:17:49 lindholm kernel: [    0.362379] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.362414] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Apr  8 14:17:49 lindholm kernel: [    0.362418] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362422] pci 0000:00:1c.0:   bridge window [mem 0xe3300000-0xe33fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362427] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362490] pci 0000:03:00.0: reg 10: [io  0x1018-0x101f]
Apr  8 14:17:49 lindholm kernel: [    0.362497] pci 0000:03:00.0: reg 14: [io  0x1024-0x1027]
Apr  8 14:17:49 lindholm kernel: [    0.362504] pci 0000:03:00.0: reg 18: [io  0x1010-0x1017]
Apr  8 14:17:49 lindholm kernel: [    0.362512] pci 0000:03:00.0: reg 1c: [io  0x1020-0x1023]
Apr  8 14:17:49 lindholm kernel: [    0.362519] pci 0000:03:00.0: reg 20: [io  0x1000-0x100f]
Apr  8 14:17:49 lindholm kernel: [    0.362527] pci 0000:03:00.0: reg 24: [mem 0xe3100000-0xe31001ff]
Apr  8 14:17:49 lindholm kernel: [    0.362564] pci 0000:03:00.0: supports D1
Apr  8 14:17:49 lindholm kernel: [    0.362566] pci 0000:03:00.0: PME# supported from D0 D1 D3hot
Apr  8 14:17:49 lindholm kernel: [    0.362571] pci 0000:03:00.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.362588] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Apr  8 14:17:49 lindholm kernel: [    0.362597] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Apr  8 14:17:49 lindholm kernel: [    0.362601] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
Apr  8 14:17:49 lindholm kernel: [    0.362604] pci 0000:00:1c.1:   bridge window [mem 0xe3100000-0xe31fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362610] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362645] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Apr  8 14:17:49 lindholm kernel: [    0.362649] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362653] pci 0000:00:1c.2:   bridge window [mem 0xe3400000-0xe34fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362658] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362694] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Apr  8 14:17:49 lindholm kernel: [    0.362697] pci 0000:00:1c.3:   bridge window [io  0xf000-0x0000] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362701] pci 0000:00:1c.3:   bridge window [mem 0xe3500000-0xe35fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362706] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362742] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
Apr  8 14:17:49 lindholm kernel: [    0.362745] pci 0000:00:1c.4:   bridge window [io  0xf000-0x0000] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362749] pci 0000:00:1c.4:   bridge window [mem 0xe3600000-0xe36fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362754] pci 0000:00:1c.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362797] pci 0000:07:03.0: reg 10: [mem 0xe3004000-0xe30047ff]
Apr  8 14:17:49 lindholm kernel: [    0.362804] pci 0000:07:03.0: reg 14: [mem 0xe3000000-0xe3003fff]
Apr  8 14:17:49 lindholm kernel: [    0.362844] pci 0000:07:03.0: supports D1 D2
Apr  8 14:17:49 lindholm kernel: [    0.362845] pci 0000:07:03.0: PME# supported from D0 D1 D2 D3hot
Apr  8 14:17:49 lindholm kernel: [    0.362850] pci 0000:07:03.0: PME# disabled
Apr  8 14:17:49 lindholm kernel: [    0.362890] pci 0000:00:1e.0: PCI bridge to [bus 07-07] (subtractive decode)
Apr  8 14:17:49 lindholm kernel: [    0.362894] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362898] pci 0000:00:1e.0:   bridge window [mem 0xe3000000-0xe30fffff]
Apr  8 14:17:49 lindholm kernel: [    0.362903] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.362905] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
Apr  8 14:17:49 lindholm kernel: [    0.362908] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffffffffffff] (subtractive decode)
Apr  8 14:17:49 lindholm kernel: [    0.362934] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363130] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363329] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363384] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363439] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.363493] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX4._PRT]
Apr  8 14:17:49 lindholm kernel: [    0.369570] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Apr  8 14:17:49 lindholm kernel: [    0.369662] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12)
Apr  8 14:17:49 lindholm kernel: [    0.369751] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
Apr  8 14:17:49 lindholm kernel: [    0.369844] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Apr  8 14:17:49 lindholm kernel: [    0.369933] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11 12)
Apr  8 14:17:49 lindholm kernel: [    0.370047] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
Apr  8 14:17:49 lindholm kernel: [    0.370139] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 *10 11 12)
Apr  8 14:17:49 lindholm kernel: [    0.370227] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
Apr  8 14:17:49 lindholm kernel: [    0.370269] HEST: Table is not found!
Apr  8 14:17:49 lindholm kernel: [    0.370348] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr  8 14:17:49 lindholm kernel: [    0.370352] vgaarb: loaded
Apr  8 14:17:49 lindholm kernel: [    0.370490] SCSI subsystem initialized
Apr  8 14:17:49 lindholm kernel: [    0.370562] libata version 3.00 loaded.
Apr  8 14:17:49 lindholm kernel: [    0.370607] usbcore: registered new interface driver usbfs
Apr  8 14:17:49 lindholm kernel: [    0.370617] usbcore: registered new interface driver hub
Apr  8 14:17:49 lindholm kernel: [    0.370639] usbcore: registered new device driver usb
Apr  8 14:17:49 lindholm kernel: [    0.370747] ACPI: WMI: Mapper loaded
Apr  8 14:17:49 lindholm kernel: [    0.370749] PCI: Using ACPI for IRQ routing
Apr  8 14:17:49 lindholm kernel: [    0.370752] PCI: pci_cache_line_size set to 64 bytes
Apr  8 14:17:49 lindholm kernel: [    0.370839] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
Apr  8 14:17:49 lindholm kernel: [    0.370842] reserve RAM buffer: 00000000cfa17000 - 00000000cfffffff 
Apr  8 14:17:49 lindholm kernel: [    0.370845] reserve RAM buffer: 00000000cfafe000 - 00000000cfffffff 
Apr  8 14:17:49 lindholm kernel: [    0.370848] reserve RAM buffer: 00000000cfbea000 - 00000000cfffffff 
Apr  8 14:17:49 lindholm kernel: [    0.370850] reserve RAM buffer: 00000000cfbf4000 - 00000000cfffffff 
Apr  8 14:17:49 lindholm kernel: [    0.370852] reserve RAM buffer: 00000000cfc00000 - 00000000cfffffff 
Apr  8 14:17:49 lindholm kernel: [    0.370933] NetLabel: Initializing
Apr  8 14:17:49 lindholm kernel: [    0.370935] NetLabel:  domain hash size = 128
Apr  8 14:17:49 lindholm kernel: [    0.370937] NetLabel:  protocols = UNLABELED CIPSOv4
Apr  8 14:17:49 lindholm kernel: [    0.370948] NetLabel:  unlabeled traffic allowed by default
Apr  8 14:17:49 lindholm kernel: [    0.371086] hpet clockevent registered
Apr  8 14:17:49 lindholm kernel: [    0.371089] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Apr  8 14:17:49 lindholm kernel: [    0.371094] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Apr  8 14:17:49 lindholm kernel: [    0.371098] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Apr  8 14:17:49 lindholm kernel: [    0.390059] Switching to clocksource tsc
Apr  8 14:17:49 lindholm kernel: [    0.403513] AppArmor: AppArmor Filesystem Enabled
Apr  8 14:17:49 lindholm kernel: [    0.403530] pnp: PnP ACPI init
Apr  8 14:17:49 lindholm kernel: [    0.403551] ACPI: bus type pnp registered
Apr  8 14:17:49 lindholm kernel: [    0.405760] pnp: PnP ACPI: found 10 devices
Apr  8 14:17:49 lindholm kernel: [    0.405762] ACPI: ACPI bus type pnp unregistered
Apr  8 14:17:49 lindholm kernel: [    0.405775] system 00:01: [mem 0xf0000000-0xf7ffffff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405778] system 00:01: [mem 0xfeb00000-0xfeb03fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405784] system 00:01: [mem 0xfed13000-0xfed13fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405787] system 00:01: [mem 0xfed14000-0xfed17fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405789] system 00:01: [mem 0xfed18000-0xfed18fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405792] system 00:01: [mem 0xfed19000-0xfed19fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405794] system 00:01: [mem 0xfed1c000-0xfed1ffff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405797] system 00:01: [mem 0xfed20000-0xfed3ffff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405799] system 00:01: [mem 0xfed45000-0xfed99fff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405802] system 00:01: [mem 0x000c0000-0x000dffff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405805] system 00:01: [mem 0x000e0000-0x000fffff] could not be reserved
Apr  8 14:17:49 lindholm kernel: [    0.405808] system 00:01: [mem 0xffc00000-0xffffffff] could not be reserved
Apr  8 14:17:49 lindholm kernel: [    0.405814] system 00:06: [io  0x0500-0x053f] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405816] system 00:06: [io  0x0400-0x047f] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.405819] system 00:06: [io  0x0680-0x06ff] has been reserved
Apr  8 14:17:49 lindholm kernel: [    0.411655] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Apr  8 14:17:49 lindholm kernel: [    0.411715] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe3700000-0xe38fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411718] pci 0000:00:1c.1: BAR 15: assigned [mem 0xe3900000-0xe3afffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411721] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe3b00000-0xe3cfffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411724] pci 0000:00:1c.3: BAR 15: assigned [mem 0xe3d00000-0xe3efffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411727] pci 0000:00:1c.4: BAR 15: assigned [mem 0xe3f00000-0xe40fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411730] pci 0000:00:1c.0: BAR 13: assigned [io  0x4000-0x4fff]
Apr  8 14:17:49 lindholm kernel: [    0.411733] pci 0000:00:1c.2: BAR 13: assigned [io  0x5000-0x5fff]
Apr  8 14:17:49 lindholm kernel: [    0.411736] pci 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
Apr  8 14:17:49 lindholm kernel: [    0.411738] pci 0000:00:1c.4: BAR 13: assigned [io  0x7000-0x7fff]
Apr  8 14:17:49 lindholm kernel: [    0.411742] pci 0000:01:00.0: BAR 6: can't assign mem pref (size 0x20000)
Apr  8 14:17:49 lindholm kernel: [    0.411744] pci 0000:00:01.0: PCI bridge to [bus 01-01]
Apr  8 14:17:49 lindholm kernel: [    0.411747] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
Apr  8 14:17:49 lindholm kernel: [    0.411751] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xe2ffffff]
Apr  8 14:17:49 lindholm kernel: [    0.411754] pci 0000:00:01.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411758] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Apr  8 14:17:49 lindholm kernel: [    0.411761] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
Apr  8 14:17:49 lindholm kernel: [    0.411765] pci 0000:00:1c.0:   bridge window [mem 0xe3300000-0xe33fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411769] pci 0000:00:1c.0:   bridge window [mem 0xe3700000-0xe38fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411774] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Apr  8 14:17:49 lindholm kernel: [    0.411777] pci 0000:00:1c.1:   bridge window [io  0x1000-0x1fff]
Apr  8 14:17:49 lindholm kernel: [    0.411781] pci 0000:00:1c.1:   bridge window [mem 0xe3100000-0xe31fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411785] pci 0000:00:1c.1:   bridge window [mem 0xe3900000-0xe3afffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411790] pci 0000:00:1c.2: PCI bridge to [bus 04-04]
Apr  8 14:17:49 lindholm kernel: [    0.411793] pci 0000:00:1c.2:   bridge window [io  0x5000-0x5fff]
Apr  8 14:17:49 lindholm kernel: [    0.411797] pci 0000:00:1c.2:   bridge window [mem 0xe3400000-0xe34fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411801] pci 0000:00:1c.2:   bridge window [mem 0xe3b00000-0xe3cfffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411806] pci 0000:00:1c.3: PCI bridge to [bus 05-05]
Apr  8 14:17:49 lindholm kernel: [    0.411808] pci 0000:00:1c.3:   bridge window [io  0x6000-0x6fff]
Apr  8 14:17:49 lindholm kernel: [    0.411813] pci 0000:00:1c.3:   bridge window [mem 0xe3500000-0xe35fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411816] pci 0000:00:1c.3:   bridge window [mem 0xe3d00000-0xe3efffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411821] pci 0000:00:1c.4: PCI bridge to [bus 06-06]
Apr  8 14:17:49 lindholm kernel: [    0.411824] pci 0000:00:1c.4:   bridge window [io  0x7000-0x7fff]
Apr  8 14:17:49 lindholm kernel: [    0.411828] pci 0000:00:1c.4:   bridge window [mem 0xe3600000-0xe36fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411832] pci 0000:00:1c.4:   bridge window [mem 0xe3f00000-0xe40fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411837] pci 0000:00:1e.0: PCI bridge to [bus 07-07]
Apr  8 14:17:49 lindholm kernel: [    0.411839] pci 0000:00:1e.0:   bridge window [io  disabled]
Apr  8 14:17:49 lindholm kernel: [    0.411843] pci 0000:00:1e.0:   bridge window [mem 0xe3000000-0xe30fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411846] pci 0000:00:1e.0:   bridge window [mem pref disabled]
Apr  8 14:17:49 lindholm kernel: [    0.411859]   alloc irq_desc for 16 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411861]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411868] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 14:17:49 lindholm kernel: [    0.411872] pci 0000:00:01.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411878] pci 0000:00:1c.0: enabling device (0000 -> 0003)
Apr  8 14:17:49 lindholm kernel: [    0.411881]   alloc irq_desc for 17 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411883]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411886] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    0.411890] pci 0000:00:1c.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411897]   alloc irq_desc for 20 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411899]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411902] pci 0000:00:1c.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
Apr  8 14:17:49 lindholm kernel: [    0.411905] pci 0000:00:1c.1: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411912] pci 0000:00:1c.2: enabling device (0000 -> 0003)
Apr  8 14:17:49 lindholm kernel: [    0.411915]   alloc irq_desc for 18 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411916]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411919] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  8 14:17:49 lindholm kernel: [    0.411923] pci 0000:00:1c.2: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411930] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Apr  8 14:17:49 lindholm kernel: [    0.411933]   alloc irq_desc for 19 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411934]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.411937] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Apr  8 14:17:49 lindholm kernel: [    0.411942] pci 0000:00:1c.3: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411949] pci 0000:00:1c.4: enabling device (0000 -> 0003)
Apr  8 14:17:49 lindholm kernel: [    0.411952] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    0.411956] pci 0000:00:1c.4: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411963] pci 0000:00:1e.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.411967] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
Apr  8 14:17:49 lindholm kernel: [    0.411969] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffffffffffff]
Apr  8 14:17:49 lindholm kernel: [    0.411971] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
Apr  8 14:17:49 lindholm kernel: [    0.411973] pci_bus 0000:01: resource 1 [mem 0xe0000000-0xe2ffffff]
Apr  8 14:17:49 lindholm kernel: [    0.411975] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411978] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Apr  8 14:17:49 lindholm kernel: [    0.411980] pci_bus 0000:02: resource 1 [mem 0xe3300000-0xe33fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411982] pci_bus 0000:02: resource 2 [mem 0xe3700000-0xe38fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411984] pci_bus 0000:03: resource 0 [io  0x1000-0x1fff]
Apr  8 14:17:49 lindholm kernel: [    0.411986] pci_bus 0000:03: resource 1 [mem 0xe3100000-0xe31fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411988] pci_bus 0000:03: resource 2 [mem 0xe3900000-0xe3afffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411990] pci_bus 0000:04: resource 0 [io  0x5000-0x5fff]
Apr  8 14:17:49 lindholm kernel: [    0.411992] pci_bus 0000:04: resource 1 [mem 0xe3400000-0xe34fffff]
Apr  8 14:17:49 lindholm kernel: [    0.411994] pci_bus 0000:04: resource 2 [mem 0xe3b00000-0xe3cfffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.411996] pci_bus 0000:05: resource 0 [io  0x6000-0x6fff]
Apr  8 14:17:49 lindholm kernel: [    0.411998] pci_bus 0000:05: resource 1 [mem 0xe3500000-0xe35fffff]
Apr  8 14:17:49 lindholm kernel: [    0.412000] pci_bus 0000:05: resource 2 [mem 0xe3d00000-0xe3efffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.412002] pci_bus 0000:06: resource 0 [io  0x7000-0x7fff]
Apr  8 14:17:49 lindholm kernel: [    0.412004] pci_bus 0000:06: resource 1 [mem 0xe3600000-0xe36fffff]
Apr  8 14:17:49 lindholm kernel: [    0.412006] pci_bus 0000:06: resource 2 [mem 0xe3f00000-0xe40fffff 64bit pref]
Apr  8 14:17:49 lindholm kernel: [    0.412009] pci_bus 0000:07: resource 1 [mem 0xe3000000-0xe30fffff]
Apr  8 14:17:49 lindholm kernel: [    0.412011] pci_bus 0000:07: resource 4 [io  0x0000-0xffff]
Apr  8 14:17:49 lindholm kernel: [    0.412013] pci_bus 0000:07: resource 5 [mem 0x00000000-0xffffffffffffffff]
Apr  8 14:17:49 lindholm kernel: [    0.412044] NET: Registered protocol family 2
Apr  8 14:17:49 lindholm kernel: [    0.412194] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.413469] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.418680] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.419346] TCP: Hash tables configured (established 524288 bind 65536)
Apr  8 14:17:49 lindholm kernel: [    0.419349] TCP reno registered
Apr  8 14:17:49 lindholm kernel: [    0.419360] UDP hash table entries: 2048 (order: 4, 65536 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.419409] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.419563] NET: Registered protocol family 1
Apr  8 14:17:49 lindholm kernel: [    0.419986] pci 0000:01:00.0: Boot video device
Apr  8 14:17:49 lindholm kernel: [    0.419995] PCI: CLS 64 bytes, default 64
Apr  8 14:17:49 lindholm kernel: [    0.419998] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Apr  8 14:17:49 lindholm kernel: [    0.420001] Placing 64MB software IO TLB between ffff880001f9e000 - ffff880005f9e000
Apr  8 14:17:49 lindholm kernel: [    0.420003] software IO TLB at phys 0x1f9e000 - 0x5f9e000
Apr  8 14:17:49 lindholm kernel: [    0.420197] Scanning for low memory corruption every 60 seconds
Apr  8 14:17:49 lindholm kernel: [    0.420355] audit: initializing netlink socket (disabled)
Apr  8 14:17:49 lindholm kernel: [    0.420364] type=2000 audit(1302290241.410:1): initialized
Apr  8 14:17:49 lindholm kernel: [    0.433618] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr  8 14:17:49 lindholm kernel: [    0.434913] VFS: Disk quotas dquot_6.5.2
Apr  8 14:17:49 lindholm kernel: [    0.434965] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr  8 14:17:49 lindholm kernel: [    0.435495] fuse init (API version 7.14)
Apr  8 14:17:49 lindholm kernel: [    0.435568] msgmni has been set to 7747
Apr  8 14:17:49 lindholm kernel: [    0.658945] Freeing initrd memory: 17048k freed
Apr  8 14:17:49 lindholm kernel: [    0.667611] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Apr  8 14:17:49 lindholm kernel: [    0.667615] io scheduler noop registered
Apr  8 14:17:49 lindholm kernel: [    0.667617] io scheduler deadline registered
Apr  8 14:17:49 lindholm kernel: [    0.667651] io scheduler cfq registered (default)
Apr  8 14:17:49 lindholm kernel: [    0.667756] pcieport 0000:00:01.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.667778]   alloc irq_desc for 40 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667780]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667790] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.667844] pcieport 0000:00:1c.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.667871]   alloc irq_desc for 41 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667872]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667878] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.667946] pcieport 0000:00:1c.1: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.667972]   alloc irq_desc for 42 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667974]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.667980] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.668049] pcieport 0000:00:1c.2: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.668074]   alloc irq_desc for 43 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668076]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668082] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.668149] pcieport 0000:00:1c.3: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.668175]   alloc irq_desc for 44 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668176]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668182] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.668248] pcieport 0000:00:1c.4: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.668274]   alloc irq_desc for 45 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668276]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.668282] pcieport 0000:00:1c.4: irq 45 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    0.668365] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr  8 14:17:49 lindholm kernel: [    0.668465] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr  8 14:17:49 lindholm kernel: [    0.668537] intel_idle: MWAIT substates: 0x220
Apr  8 14:17:49 lindholm kernel: [    0.668539] intel_idle: does not run on family 6 model 15
Apr  8 14:17:49 lindholm kernel: [    0.668623] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
Apr  8 14:17:49 lindholm kernel: [    0.668635] ACPI: Sleep Button [SLPB]
Apr  8 14:17:49 lindholm kernel: [    0.668682] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr  8 14:17:49 lindholm kernel: [    0.668685] ACPI: Power Button [PWRF]
Apr  8 14:17:49 lindholm kernel: [    0.668852] ACPI: acpi_idle registered with cpuidle
Apr  8 14:17:49 lindholm kernel: [    0.668978] Monitor-Mwait will be used to enter C-1 state
Apr  8 14:17:49 lindholm kernel: [    0.670473] ERST: Table is not found!
Apr  8 14:17:49 lindholm kernel: [    0.670589] Linux agpgart interface v0.103
Apr  8 14:17:49 lindholm kernel: [    0.670607] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Apr  8 14:17:49 lindholm kernel: [    0.670696] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  8 14:17:49 lindholm kernel: [    0.670773] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
Apr  8 14:17:49 lindholm kernel: [    0.671035] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr  8 14:17:49 lindholm kernel: [    0.671988] brd: module loaded
Apr  8 14:17:49 lindholm kernel: [    0.672422] loop: module loaded
Apr  8 14:17:49 lindholm kernel: [    0.672566] ata_piix 0000:00:1f.2: version 2.13
Apr  8 14:17:49 lindholm kernel: [    0.672579]   alloc irq_desc for 21 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.672581]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.672587] ata_piix 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr  8 14:17:49 lindholm kernel: [    0.672592] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
Apr  8 14:17:49 lindholm kernel: [    0.672633] ata_piix 0000:00:1f.2: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.672694] scsi0 : ata_piix
Apr  8 14:17:49 lindholm kernel: [    0.672757] scsi1 : ata_piix
Apr  8 14:17:49 lindholm kernel: [    0.672891] ata1: SATA max UDMA/133 cmd 0x3458 ctl 0x346c bmdma 0x3430 irq 21
Apr  8 14:17:49 lindholm kernel: [    0.672896] ata2: SATA max UDMA/133 cmd 0x3450 ctl 0x3468 bmdma 0x3438 irq 21
Apr  8 14:17:49 lindholm kernel: [    0.672929] ata_piix 0000:00:1f.5: PCI INT A -> GSI 21 (level, low) -> IRQ 21
Apr  8 14:17:49 lindholm kernel: [    0.672937] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
Apr  8 14:17:49 lindholm kernel: [    0.672967] ata_piix 0000:00:1f.5: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.672997] scsi2 : ata_piix
Apr  8 14:17:49 lindholm kernel: [    0.673044] scsi3 : ata_piix
Apr  8 14:17:49 lindholm kernel: [    0.673126] ata3: SATA max UDMA/133 cmd 0x3448 ctl 0x3464 bmdma 0x3410 irq 21
Apr  8 14:17:49 lindholm kernel: [    0.673130] ata4: SATA max UDMA/133 cmd 0x3440 ctl 0x3460 bmdma 0x3418 irq 21
Apr  8 14:17:49 lindholm kernel: [    0.673177] pata_acpi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    0.673200] pata_acpi 0000:03:00.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.673211] pata_acpi 0000:03:00.0: PCI INT A disabled
Apr  8 14:17:49 lindholm kernel: [    0.673447] Fixed MDIO Bus: probed
Apr  8 14:17:49 lindholm kernel: [    0.673475] PPP generic driver version 2.4.2
Apr  8 14:17:49 lindholm kernel: [    0.673504] tun: Universal TUN/TAP device driver, 1.6
Apr  8 14:17:49 lindholm kernel: [    0.673506] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr  8 14:17:49 lindholm kernel: [    0.673574] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr  8 14:17:49 lindholm kernel: [    0.673589] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    0.673610] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.673613] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.673643] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Apr  8 14:17:49 lindholm kernel: [    0.673669] ehci_hcd 0000:00:1a.7: debug port 1
Apr  8 14:17:49 lindholm kernel: [    0.677555] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Apr  8 14:17:49 lindholm kernel: [    0.677567] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xe3225400
Apr  8 14:17:49 lindholm kernel: [    0.699695] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Apr  8 14:17:49 lindholm kernel: [    0.699802] hub 1-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.699807] hub 1-0:1.0: 6 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.699882]   alloc irq_desc for 23 on node -1
Apr  8 14:17:49 lindholm kernel: [    0.699884]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    0.699888] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  8 14:17:49 lindholm kernel: [    0.699900] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.699904] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.699937] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Apr  8 14:17:49 lindholm kernel: [    0.699958] ehci_hcd 0000:00:1d.7: debug port 1
Apr  8 14:17:49 lindholm kernel: [    0.703832] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Apr  8 14:17:49 lindholm kernel: [    0.703844] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe3225000
Apr  8 14:17:49 lindholm kernel: [    0.719700] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Apr  8 14:17:49 lindholm kernel: [    0.719799] hub 2-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.719803] hub 2-0:1.0: 6 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.719870] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr  8 14:17:49 lindholm kernel: [    0.719887] uhci_hcd: USB Universal Host Controller Interface driver
Apr  8 14:17:49 lindholm kernel: [    0.719930] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Apr  8 14:17:49 lindholm kernel: [    0.719935] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.719938] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.719965] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Apr  8 14:17:49 lindholm kernel: [    0.719993] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030c0
Apr  8 14:17:49 lindholm kernel: [    0.720091] hub 3-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.720095] hub 3-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.720144] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Apr  8 14:17:49 lindholm kernel: [    0.720149] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.720152] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.720180] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Apr  8 14:17:49 lindholm kernel: [    0.720201] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030a0
Apr  8 14:17:49 lindholm kernel: [    0.720294] hub 4-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.720298] hub 4-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.720349] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    0.720354] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.720357] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.720385] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Apr  8 14:17:49 lindholm kernel: [    0.720405] uhci_hcd 0000:00:1a.2: irq 17, io base 0x00003080
Apr  8 14:17:49 lindholm kernel: [    0.720496] hub 5-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.720500] hub 5-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.720552] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Apr  8 14:17:49 lindholm kernel: [    0.720557] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.720560] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.720587] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Apr  8 14:17:49 lindholm kernel: [    0.720607] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003060
Apr  8 14:17:49 lindholm kernel: [    0.720706] hub 6-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.720710] hub 6-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.720760] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Apr  8 14:17:49 lindholm kernel: [    0.720764] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.720767] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.720797] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Apr  8 14:17:49 lindholm kernel: [    0.720824] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003040
Apr  8 14:17:49 lindholm kernel: [    0.720922] hub 7-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.720926] hub 7-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.720978] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Apr  8 14:17:49 lindholm kernel: [    0.720982] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    0.720985] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Apr  8 14:17:49 lindholm kernel: [    0.721012] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Apr  8 14:17:49 lindholm kernel: [    0.721032] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003020
Apr  8 14:17:49 lindholm kernel: [    0.721124] hub 8-0:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    0.721128] hub 8-0:1.0: 2 ports detected
Apr  8 14:17:49 lindholm kernel: [    0.721226] PNP: No PS/2 controller found. Probing ports directly.
Apr  8 14:17:49 lindholm kernel: [    0.724259] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr  8 14:17:49 lindholm kernel: [    0.724264] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr  8 14:17:49 lindholm kernel: [    0.724318] mice: PS/2 mouse device common for all mice
Apr  8 14:17:49 lindholm kernel: [    0.724405] rtc_cmos 00:03: RTC can wake from S4
Apr  8 14:17:49 lindholm kernel: [    0.724442] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
Apr  8 14:17:49 lindholm kernel: [    0.724467] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
Apr  8 14:17:49 lindholm kernel: [    0.724547] device-mapper: uevent: version 1.0.3
Apr  8 14:17:49 lindholm kernel: [    0.724607] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
Apr  8 14:17:49 lindholm kernel: [    0.724661] device-mapper: multipath: version 1.1.1 loaded
Apr  8 14:17:49 lindholm kernel: [    0.724663] device-mapper: multipath round-robin: version 1.0.0 loaded
Apr  8 14:17:49 lindholm kernel: [    0.724790] cpuidle: using governor ladder
Apr  8 14:17:49 lindholm kernel: [    0.724791] cpuidle: using governor menu
Apr  8 14:17:49 lindholm kernel: [    0.725016] TCP cubic registered
Apr  8 14:17:49 lindholm kernel: [    0.725126] NET: Registered protocol family 10
Apr  8 14:17:49 lindholm kernel: [    0.725418] lo: Disabled Privacy Extensions
Apr  8 14:17:49 lindholm kernel: [    0.725589] NET: Registered protocol family 17
Apr  8 14:17:49 lindholm kernel: [    0.725958] PM: Resume from disk failed.
Apr  8 14:17:49 lindholm kernel: [    0.725969] registered taskstats version 1
Apr  8 14:17:49 lindholm kernel: [    0.726249]   Magic number: 7:323:293
Apr  8 14:17:49 lindholm kernel: [    0.726275] tty tty26: hash matches
Apr  8 14:17:49 lindholm kernel: [    0.726324] rtc_cmos 00:03: setting system clock to 2011-04-08 19:17:22 UTC (1302290242)
Apr  8 14:17:49 lindholm kernel: [    0.726327] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr  8 14:17:49 lindholm kernel: [    0.726329] EDD information not available.
Apr  8 14:17:49 lindholm kernel: [    1.030764] ata3: SATA link down (SStatus 0 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.041424] ata4: SATA link down (SStatus 0 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.090106] usb 1-2: new high speed USB device using ehci_hcd and address 3
Apr  8 14:17:49 lindholm kernel: [    1.480020] usb 1-3: new high speed USB device using ehci_hcd and address 4
Apr  8 14:17:49 lindholm kernel: [    1.530129] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.530140] ata2.01: SATA link down (SStatus 0 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.540110] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.540120] ata1.01: SATA link down (SStatus 0 SControl 300)
Apr  8 14:17:49 lindholm kernel: [    1.550512] ata2.00: ATA-8: ST3500320AS, SD15, max UDMA/133
Apr  8 14:17:49 lindholm kernel: [    1.550516] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr  8 14:17:49 lindholm kernel: [    1.560532] ata1.00: ATA-8: ST3500320AS, SD15, max UDMA/133
Apr  8 14:17:49 lindholm kernel: [    1.560535] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
Apr  8 14:17:49 lindholm kernel: [    1.580488] ata2.00: configured for UDMA/133
Apr  8 14:17:49 lindholm kernel: [    1.600515] ata1.00: configured for UDMA/133
Apr  8 14:17:49 lindholm kernel: [    1.600621] scsi 0:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
Apr  8 14:17:49 lindholm kernel: [    1.600737] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr  8 14:17:49 lindholm kernel: [    1.600744] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  8 14:17:49 lindholm kernel: [    1.600820] sd 0:0:0:0: [sda] Write Protect is off
Apr  8 14:17:49 lindholm kernel: [    1.600823] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr  8 14:17:49 lindholm kernel: [    1.600837] scsi 1:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
Apr  8 14:17:49 lindholm kernel: [    1.600843] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 14:17:49 lindholm kernel: [    1.600940] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr  8 14:17:49 lindholm kernel: [    1.601000]  sda:
Apr  8 14:17:49 lindholm kernel: [    1.601003] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Apr  8 14:17:49 lindholm kernel: [    1.601106] sd 1:0:0:0: [sdb] Write Protect is off
Apr  8 14:17:49 lindholm kernel: [    1.601109] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr  8 14:17:49 lindholm kernel: [    1.601132] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  8 14:17:49 lindholm kernel: [    1.601273]  sdb: sda1 sda2 sda3
Apr  8 14:17:49 lindholm kernel: [    1.617943]  sdb1
Apr  8 14:17:49 lindholm kernel: [    1.618134] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr  8 14:17:49 lindholm kernel: [    1.632387] sd 0:0:0:0: [sda] Attached SCSI disk
Apr  8 14:17:49 lindholm kernel: [    1.632404] Freeing unused kernel memory: 912k freed
Apr  8 14:17:49 lindholm kernel: [    1.632659] Write protecting the kernel read-only data: 10240k
Apr  8 14:17:49 lindholm kernel: [    1.632819] Freeing unused kernel memory: 408k freed
Apr  8 14:17:49 lindholm kernel: [    1.633049] Freeing unused kernel memory: 1640k freed
Apr  8 14:17:49 lindholm kernel: [    1.647679] udev[86]: starting version 163
Apr  8 14:17:49 lindholm kernel: [    1.713244] pata_marvell 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Apr  8 14:17:49 lindholm kernel: [    1.713275] pata_marvell 0000:03:00.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    1.716619] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
Apr  8 14:17:49 lindholm kernel: [    1.716622] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
Apr  8 14:17:49 lindholm kernel: [    1.716646] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Apr  8 14:17:49 lindholm kernel: [    1.716655] e1000e 0000:00:19.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [    1.716747] scsi4 : pata_marvell
Apr  8 14:17:49 lindholm kernel: [    1.716780]   alloc irq_desc for 46 on node -1
Apr  8 14:17:49 lindholm kernel: [    1.716782]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [    1.716792] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [    1.716819] scsi5 : pata_marvell
Apr  8 14:17:49 lindholm kernel: [    1.716853] ata5: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 17
Apr  8 14:17:49 lindholm kernel: [    1.716855] ata6: DUMMY
Apr  8 14:17:49 lindholm kernel: [    1.810070] usb 1-5: new high speed USB device using ehci_hcd and address 6
Apr  8 14:17:49 lindholm kernel: [    1.890407] ata5.00: ATAPI: Optiarc DVD RW AD-7190A, 1.04, max UDMA/66
Apr  8 14:17:49 lindholm kernel: [    1.930446] ata5.00: configured for UDMA/66
Apr  8 14:17:49 lindholm kernel: [    1.932375] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7190A  1.04 PQ: 0 ANSI: 5
Apr  8 14:17:49 lindholm kernel: [    1.938451] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
Apr  8 14:17:49 lindholm kernel: [    1.938455] Uniform CD-ROM driver Revision: 3.20
Apr  8 14:17:49 lindholm kernel: [    1.938570] sr 4:0:0:0: Attached scsi CD-ROM sr0
Apr  8 14:17:49 lindholm kernel: [    1.938632] sr 4:0:0:0: Attached scsi generic sg2 type 5
Apr  8 14:17:49 lindholm kernel: [    1.940098] firewire_ohci 0000:07:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Apr  8 14:17:49 lindholm kernel: [    1.971663] hub 1-5:1.0: USB hub found
Apr  8 14:17:49 lindholm kernel: [    1.972009] hub 1-5:1.0: 4 ports detected
Apr  8 14:17:49 lindholm kernel: [    1.991292] firewire_ohci: Added fw-ohci device 0000:07:03.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
Apr  8 14:17:49 lindholm kernel: [    2.091285] usb 1-6: new high speed USB device using ehci_hcd and address 7
Apr  8 14:17:49 lindholm kernel: [    2.173610] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:37:7f:bb
Apr  8 14:17:49 lindholm kernel: [    2.173613] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Apr  8 14:17:49 lindholm kernel: [    2.173634] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 6, PBA No: ffffff-0ff
Apr  8 14:17:49 lindholm kernel: [    2.265697] Initializing USB Mass Storage driver...
Apr  8 14:17:49 lindholm kernel: [    2.265824] scsi6 : usb-storage 1-6:1.0
Apr  8 14:17:49 lindholm kernel: [    2.265918] usbcore: registered new interface driver usb-storage
Apr  8 14:17:49 lindholm kernel: [    2.265920] USB Mass Storage support registered.
Apr  8 14:17:49 lindholm kernel: [    2.348877] xor: automatically using best checksumming function: generic_sse
Apr  8 14:17:49 lindholm kernel: [    2.391249]    generic_sse:  8684.000 MB/sec
Apr  8 14:17:49 lindholm kernel: [    2.391251] xor: using function: generic_sse (8684.000 MB/sec)
Apr  8 14:17:49 lindholm kernel: [    2.393368] device-mapper: dm-raid45: initialized v0.2594b
Apr  8 14:17:49 lindholm kernel: [    2.491429] firewire_core: created device fw0: GUID 00902700003cb8c1, S400
Apr  8 14:17:49 lindholm kernel: [    2.531326] usb 3-1: new low speed USB device using uhci_hcd and address 2
Apr  8 14:17:49 lindholm kernel: [    2.619134] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr  8 14:17:49 lindholm kernel: [    3.001297] usb 4-2: new low speed USB device using uhci_hcd and address 2
Apr  8 14:17:49 lindholm kernel: [    3.270400] usb 1-5.1: new full speed USB device using ehci_hcd and address 8
Apr  8 14:17:49 lindholm kernel: [    3.303548] scsi 6:0:0:0: Direct-Access     Samsung  STORY Station         PQ: 0 ANSI: 2 CCS
Apr  8 14:17:49 lindholm kernel: [    3.303924] sd 6:0:0:0: Attached scsi generic sg3 type 0
Apr  8 14:17:49 lindholm kernel: [    3.304526] sd 6:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
Apr  8 14:17:49 lindholm kernel: [    3.305272] sd 6:0:0:0: [sdc] Write Protect is off
Apr  8 14:17:49 lindholm kernel: [    3.305276] sd 6:0:0:0: [sdc] Mode Sense: 28 00 00 00
Apr  8 14:17:49 lindholm kernel: [    3.305278] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Apr  8 14:17:49 lindholm kernel: [    3.306649] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Apr  8 14:17:49 lindholm kernel: [    3.306655]  sdc: sdc1 sdc2
Apr  8 14:17:49 lindholm kernel: [    3.308522] sd 6:0:0:0: [sdc] Assuming drive cache: write through
Apr  8 14:17:49 lindholm kernel: [    3.308526] sd 6:0:0:0: [sdc] Attached SCSI disk
Apr  8 14:17:49 lindholm kernel: [    3.460406] usb 1-5.2: new full speed USB device using ehci_hcd and address 9
Apr  8 14:17:49 lindholm kernel: [    4.461655] usb 1-5.3: new low speed USB device using ehci_hcd and address 10
Apr  8 14:17:49 lindholm kernel: [   10.058201] udev[418]: starting version 163
Apr  8 14:17:49 lindholm kernel: [   10.163187] lp: driver loaded but no devices found
Apr  8 14:17:49 lindholm kernel: [   10.218453] Adding 5866248k swap on /dev/sda3.  Priority:-1 extents:1 across:5866248k 
Apr  8 14:17:49 lindholm kernel: [   10.353880] Linux video capture interface: v2.00
Apr  8 14:17:49 lindholm kernel: [   10.372610] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2D12
Apr  8 14:17:49 lindholm kernel: [   10.372660] type=1400 audit(1302290252.135:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=683 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.372871] usbcore: registered new interface driver usblp
Apr  8 14:17:49 lindholm kernel: [   10.373320] type=1400 audit(1302290252.135:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=683 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.373694] type=1400 audit(1302290252.135:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=683 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.379720] usbcore: registered new interface driver hiddev
Apr  8 14:17:49 lindholm kernel: [   10.380128] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0990)
Apr  8 14:17:49 lindholm kernel: [   10.393269] nvidia: module license 'NVIDIA' taints kernel.
Apr  8 14:17:49 lindholm kernel: [   10.393273] Disabling lock debugging due to kernel taint
Apr  8 14:17:49 lindholm kernel: [   10.393362] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1:1.0/input/input2
Apr  8 14:17:49 lindholm kernel: [   10.393471] generic-usb 0003:046D:C040.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1a.0-1/input0
Apr  8 14:17:49 lindholm kernel: [   10.402105] type=1400 audit(1302290252.165:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=704 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.402724] type=1400 audit(1302290252.165:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=704 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.403064] type=1400 audit(1302290252.165:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=704 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   10.407909] Bluetooth: Core ver 2.15
Apr  8 14:17:49 lindholm kernel: [   10.407949] NET: Registered protocol family 31
Apr  8 14:17:49 lindholm kernel: [   10.407950] Bluetooth: HCI device and connection manager initialized
Apr  8 14:17:49 lindholm kernel: [   10.407953] Bluetooth: HCI socket layer initialized
Apr  8 14:17:49 lindholm kernel: [   10.408564] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/input/input3
Apr  8 14:17:49 lindholm kernel: [   10.408647] generic-usb 0003:046D:C313.0002: input,hidraw1: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1a.1-2/input0
Apr  8 14:17:49 lindholm kernel: [   10.412771] Bluetooth: Generic Bluetooth USB driver ver 0.6
Apr  8 14:17:49 lindholm kernel: [   10.415908] input: UVC Camera (046d:0990) as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2:1.0/input/input4
Apr  8 14:17:49 lindholm kernel: [   10.416190] usbcore: registered new interface driver uvcvideo
Apr  8 14:17:49 lindholm kernel: [   10.416192] USB Video Class driver (v0.1.0)
Apr  8 14:17:49 lindholm kernel: [   10.443262] usbcore: registered new interface driver btusb
Apr  8 14:17:49 lindholm kernel: [   10.452340] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.1/input/input5
Apr  8 14:17:49 lindholm kernel: [   10.452444] generic-usb 0003:046D:C313.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1a.1-2/input1
Apr  8 14:17:49 lindholm kernel: [   10.455302] input: Plantronics Wireless Audio Plantronics Wireless Audio as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5.2/1-5.2:1.3/input/input6
Apr  8 14:17:49 lindholm kernel: [   10.455402] generic-usb 0003:047F:D955.0004: input,hiddev97,hidraw3: USB HID v1.01 Device [Plantronics Wireless Audio Plantronics Wireless Audio] on usb-0000:00:1a.7-5.2/input3
Apr  8 14:17:49 lindholm kernel: [   10.575309]   alloc irq_desc for 22 on node -1
Apr  8 14:17:49 lindholm kernel: [   10.575312]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [   10.575319] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Apr  8 14:17:49 lindholm kernel: [   10.575380]   alloc irq_desc for 47 on node -1
Apr  8 14:17:49 lindholm kernel: [   10.575382]   alloc kstat_irqs on node -1
Apr  8 14:17:49 lindholm kernel: [   10.575390] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
Apr  8 14:17:49 lindholm kernel: [   10.575412] HDA Intel 0000:00:1b.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [   10.641390] generic-usb 0003:050D:1100.0005: hiddev98,hidraw4: USB HID v1.11 Device [Belkin  Belkin UPS] on usb-0000:00:1a.7-5.3/input0
Apr  8 14:17:49 lindholm kernel: [   10.641413] usbcore: registered new interface driver usbhid
Apr  8 14:17:49 lindholm kernel: [   10.641415] usbhid: USB HID core driver
Apr  8 14:17:49 lindholm kernel: [   10.894314] 9:1:1: endpoint lacks sample rate attribute bit, cannot set.
Apr  8 14:17:49 lindholm kernel: [   10.894807] 9:2:1: endpoint lacks sample rate attribute bit, cannot set.
Apr  8 14:17:49 lindholm kernel: [   10.901960] usbcore: registered new interface driver snd-usb-audio
Apr  8 14:17:49 lindholm kernel: [   11.153061] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Apr  8 14:17:49 lindholm kernel: [   11.153069] nvidia 0000:01:00.0: setting latency timer to 64
Apr  8 14:17:49 lindholm kernel: [   11.153074] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Apr  8 14:17:49 lindholm kernel: [   11.153422] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
Apr  8 14:17:49 lindholm kernel: [   11.260143] input: HDA Intel Line In at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
Apr  8 14:17:49 lindholm kernel: [   11.260234] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Apr  8 14:17:49 lindholm kernel: [   11.260287] input: HDA Intel Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Apr  8 14:17:49 lindholm kernel: [   11.260336] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Apr  8 14:17:49 lindholm kernel: [   11.260387] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Apr  8 14:17:49 lindholm kernel: [   11.260439] input: HDA Intel Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Apr  8 14:17:49 lindholm kernel: [   11.260491] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
Apr  8 14:17:49 lindholm kernel: [   15.952818] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Apr  8 14:17:49 lindholm kernel: [   24.263385] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
Apr  8 14:17:49 lindholm kernel: [   28.009095] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
Apr  8 14:17:49 lindholm init: ubiquity main process (1074) terminated with status 1
Apr  8 14:17:49 lindholm kernel: [   28.215831] type=1400 audit(1302290269.975:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1079 comm="apparmor_parser"
Apr  8 14:17:49 lindholm kernel: [   28.216588] type=1400 audit(1302290269.975:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1079 comm="apparmor_parser"
Apr  8 14:17:49 lindholm NetworkManager[1093]: <info> NetworkManager (version 0.8.1) is starting...
Apr  8 14:17:49 lindholm NetworkManager[1093]: <info> Read config file /etc/NetworkManager/nm-system-settings.conf
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Found user 'avahi' (UID 104) and group 'avahi' (GID 109).
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Successfully dropped root privileges.
Apr  8 14:17:50 lindholm avahi-daemon[1089]: avahi-daemon 0.6.27 starting up.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> trying to start the modem manager...
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Successfully called chroot().
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Successfully dropped remaining capabilities.
Apr  8 14:17:50 lindholm avahi-daemon[1089]: No service file found in /etc/avahi/services.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: init!
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: update_system_hostname
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPluginIfupdown: management mode: unmanaged
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0)
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:19.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: end _init.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: (33582544) ... get_connections.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    SCPlugin-Ifupdown: (33582544) ... get_connections (managed=false): return empty list.
Apr  8 14:17:50 lindholm NetworkManager[1093]:    Ifupdown: get unmanaged devices count: 0
Apr  8 14:17:50 lindholm modem-manager: ModemManager (version 0.4) starting...
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> Networking is enabled by state file
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): carrier is OFF
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): new Ethernet device (driver: 'e1000e' ifindex: 2)
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): now managed
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): device state change: 1 -> 2 (reason 2)
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): bringing up device.
Apr  8 14:17:50 lindholm kernel: [   28.235993] ppdev: user-space parallel port driver
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Nokia
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Generic
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Ericsson MBM
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Novatel
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Huawei
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin MotoC
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin ZTE
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Option High-Speed
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Longcheer
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Gobi
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Sierra
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin Option
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin AnyData
Apr  8 14:17:50 lindholm modem-manager: Loaded plugin SimTech
Apr  8 14:17:50 lindholm modem-manager: (tty/ttyS1): port's parent platform driver is not whitelisted
Apr  8 14:17:50 lindholm kernel: [   28.247885] type=1400 audit(1302290270.005:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1110 comm="apparmor_parser"
Apr  8 14:17:50 lindholm modem-manager: (tty/ttyS2): port's parent platform driver is not whitelisted
Apr  8 14:17:50 lindholm modem-manager: (tty/ttyS3): port's parent platform driver is not whitelisted
Apr  8 14:17:50 lindholm modem-manager: (tty/ttyS0): could not get port's parent device
Apr  8 14:17:50 lindholm kernel: [   28.251835] type=1400 audit(1302290270.015:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1111 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.252457] type=1400 audit(1302290270.015:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1111 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.252799] type=1400 audit(1302290270.015:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1111 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.260111] type=1400 audit(1302290270.025:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1120 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.272395] type=1400 audit(1302290270.035:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1126 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.273170] type=1400 audit(1302290270.035:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1126 comm="apparmor_parser"
Apr  8 14:17:50 lindholm kernel: [   28.278175] type=1400 audit(1302290270.035:17): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1120 comm="apparmor_parser"
Apr  8 14:17:50 lindholm ddclient[1182]: WARNING:  cannot connect to checkip.dyndns.com:80 socket: IO::Socket::INET: Bad hostname 'checkip.dyndns.com'
Apr  8 14:17:50 lindholm cron[1179]: (CRON) INFO (pidfile fd = 3)
Apr  8 14:17:50 lindholm init: apport pre-start process (1174) terminated with status 1
Apr  8 14:17:50 lindholm anacron[1205]: Anacron 2.3 started on 2011-04-08
Apr  8 14:17:50 lindholm acpid: starting up with proc fs
Apr  8 14:17:50 lindholm acpid: 36 rules loaded
Apr  8 14:17:50 lindholm acpid: waiting for events: event logging is off
Apr  8 14:17:50 lindholm cron[1208]: (CRON) STARTUP (fork ok)
Apr  8 14:17:50 lindholm init: apport post-stop process (1209) terminated with status 1
Apr  8 14:17:50 lindholm anacron[1205]: Normal exit (0 jobs run)
Apr  8 14:17:50 lindholm kernel: [   28.561440] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
Apr  8 14:17:50 lindholm cron[1208]: (CRON) INFO (Running @reboot jobs)
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): preparing device.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> (eth0): deactivating device (reason: 2).
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Network interface enumeration completed.
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Registering HINFO record with values 'X86_64'/'LINUX'.
Apr  8 14:17:50 lindholm avahi-daemon[1089]: Server startup complete. Host name is lindholm.local. Local service cookie is 672045154.
Apr  8 14:17:50 lindholm NetworkManager[1093]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> modem-manager is now available
Apr  8 14:17:50 lindholm NetworkManager[1093]: <info> Trying to start the supplicant...
Apr  8 14:17:50 lindholm kernel: [   28.621327] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
Apr  8 14:17:50 lindholm kernel: [   28.621847] ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr  8 14:17:50 lindholm halevt: halevt 0.1.5, http://www.environnement.ens.fr/perso/dumas/halevt.html
Apr  8 14:17:50 lindholm bluetoothd[1269]: Bluetooth deamon 4.69
Apr  8 14:17:50 lindholm bluetoothd[1274]: Starting SDP server
Apr  8 14:17:50 lindholm bluetoothd[1274]: Starting experimental netlink support
Apr  8 14:17:50 lindholm bluetoothd[1274]: Failed to find Bluetooth netlink family
Apr  8 14:17:50 lindholm bluetoothd[1274]: Failed to init netlink plugin
Apr  8 14:17:50 lindholm kernel: [   28.734964] Bluetooth: L2CAP ver 2.14
Apr  8 14:17:50 lindholm kernel: [   28.734966] Bluetooth: L2CAP socket layer initialized
Apr  8 14:17:50 lindholm kernel: [   28.739450] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr  8 14:17:50 lindholm kernel: [   28.739453] Bluetooth: BNEP filters: protocol multicast
Apr  8 14:17:50 lindholm bluetoothd[1274]: HCI dev 0 registered
Apr  8 14:17:50 lindholm kernel: [   28.745302] Bluetooth: SCO (Voice Link) ver 0.6
Apr  8 14:17:50 lindholm kernel: [   28.745305] Bluetooth: SCO socket layer initialized
Apr  8 14:17:50 lindholm bluetoothd[1274]: HCI dev 0 up
Apr  8 14:17:50 lindholm bluetoothd[1274]: Starting security manager 0
Apr  8 14:17:50 lindholm udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.1
Apr  8 14:17:50 lindholm udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-3
Apr  8 14:17:50 lindholm udev-configure-printer: Device vendor/product is 03F0:2D12
Apr  8 14:17:50 lindholm udev-configure-printer: add /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.1/usb/lp0
Apr  8 14:17:50 lindholm bluetoothd[1274]: ioctl(HCIUNBLOCKADDR): Invalid argument (22)
Apr  8 14:17:50 lindholm bluetoothd[1274]: Adapter /org/bluez/1269/hci0 has been enabled
Apr  8 14:17:50 lindholm kernel: [   28.892138] Bluetooth: RFCOMM TTY layer initialized
Apr  8 14:17:50 lindholm kernel: [   28.892144] Bluetooth: RFCOMM socket layer initialized
Apr  8 14:17:50 lindholm kernel: [   28.892146] Bluetooth: RFCOMM ver 1.11
Apr  8 14:17:50 lindholm anacron[1448]: Anacron 2.3 started on 2011-04-08
Apr  8 14:17:50 lindholm anacron[1448]: Normal exit (0 jobs run)
Apr  8 14:17:50 lindholm udev-configure-printer: failed to claim interface
Apr  8 14:17:50 lindholm udev-configure-printer: invalid or missing IEEE 1284 Device ID
Apr  8 14:17:50 lindholm udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1a.7/usb1/1-3
Apr  8 14:17:50 lindholm udev-configure-printer: MFG:HP MDL:Officejet 4500 G510g-m SERN:CN025F61D205CQ serial:CN025F61D205CQ
Apr  8 14:17:51 lindholm halevt: Running: halevt-mount -u /org/freedesktop/Hal/devices/volume_uuid_f2b8e477_d3b1_4508_9a7b_97632104285d -o sync -m 002
Apr  8 14:17:51 lindholm halevt: Running: halevt-mount -u /org/freedesktop/Hal/devices/volume_uuid_12F9_176B -o sync -m 002
Apr  8 14:17:51 lindholm acpid: client connected from 1484[114:123]
Apr  8 14:17:51 lindholm acpid: 1 client rule loaded
Apr  8 14:17:51 lindholm kernel: [   29.367138] EXT3-fs: barriers not enabled
Apr  8 14:17:51 lindholm hald: mounted /dev/sdc2 on behalf of uid 115
Apr  8 14:17:51 lindholm kernel: [   29.401267] kjournald starting.  Commit interval 5 seconds
Apr  8 14:17:51 lindholm kernel: [   29.401563] EXT3-fs (sdc2): warning: maximal mount count reached, running e2fsck is recommended
Apr  8 14:17:51 lindholm kernel: [   29.402267] EXT3-fs (sdc2): using internal journal
Apr  8 14:17:51 lindholm kernel: [   29.402271] EXT3-fs (sdc2): mounted filesystem with ordered data mode
Apr  8 14:17:51 lindholm halevt: Running: halevt-mount -s
Apr  8 14:17:51 lindholm halevt: Running: halevt-mount -s
Apr  8 14:17:51 lindholm hald: mounted /dev/sdc1 on behalf of uid 115
Apr  8 14:17:51 lindholm kernel: [   30.042707] usb 1-3: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Apr  8 14:17:52 lindholm udev-configure-printer: SERN fields match
Apr  8 14:17:52 lindholm udev-configure-printer: URI match: usb://HP/Officejet%204500%20G510g-m?serial=CN025F61D205CQ
Apr  8 14:17:52 lindholm udev-configure-printer: SERN fields match
Apr  8 14:17:52 lindholm udev-configure-printer: URI match: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ
Apr  8 14:17:52 lindholm udev-configure-printer: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ twinned with hpfax:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ
Apr  8 14:17:52 lindholm udev-configure-printer: Consider also queues with "/usb/lp0" or "/usblp0" in their URIs as matching
Apr  8 14:17:52 lindholm udev-configure-printer: URI of print queue: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: Queue ipp://localhost:631/printers/Officejet-4500-G510g-m has matching device URI
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: Queue ipp://localhost:631/printers/Officejet-4500-G510g-m has matching device URI
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hpfax:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: hpfax usb officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of print queue: hpfax:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: hpfax usb officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hpfax:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: hpfax usb officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: Queue ipp://localhost:631/printers/Officejet-4500-G510g-m-Fax has matching device URI
Apr  8 14:17:52 lindholm udev-configure-printer: URI of print queue: cups-pdf:/, normalized: cups pdf
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: usb://HP/Officejet%204500%20G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hp:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm udev-configure-printer: URI of detected printer: hpfax:/usb/Officejet_4500_G510g-m?serial=CN025F61D205CQ, normalized: hpfax usb officejet 4500 g510g m serial cn025f61d205cq
Apr  8 14:17:52 lindholm kernel: [   30.420084] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Apr  8 14:17:52 lindholm kernel: [   30.422939] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Apr  8 14:17:52 lindholm kernel: [   30.425145] EXT4-fs (sda2): re-mounted. Opts: commit=0
Apr  8 14:17:53 lindholm ubiquity[1572]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:53 lindholm ubiquity[1576]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:54 lindholm kernel: [   32.509863] vga16fb: initializing
Apr  8 14:17:54 lindholm kernel: [   32.509867] vga16fb: mapped to 0xffff8800000a0000
Apr  8 14:17:54 lindholm kernel: [   32.672116] Console: switching to colour frame buffer device 80x30
Apr  8 14:17:54 lindholm kernel: [   32.677725] fb0: VGA16 VGA frame buffer device
Apr  8 14:17:54 lindholm ubiquity[1589]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:55 lindholm kernel: [   33.836453] do_general_protection: 10 callbacks suppressed
Apr  8 14:17:55 lindholm kernel: [   33.836457] bterm[1589] general protection ip:40400e sp:7fff494dd808 error:0 in bterm[400000+b000]
Apr  8 14:17:55 lindholm ubiquity[1599]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:56 lindholm kernel: [   34.974764] bterm[1599] general protection ip:40400e sp:7fffbcdac0f8 error:0 in bterm[400000+b000]
Apr  8 14:17:56 lindholm ubiquity[1609]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:57 lindholm kernel: [   36.129177] bterm[1609] general protection ip:40400e sp:7fff0d737048 error:0 in bterm[400000+b000]
Apr  8 14:17:57 lindholm ubiquity[1619]: Ubiquity 2.4.8 (oem-config)
Apr  8 14:17:59 lindholm kernel: [   37.268480] bterm[1619] general protection ip:40400e sp:7fffa6053ce8 error:0 in bterm[400000+b000]
Apr  8 14:18:02 lindholm kernel: [   40.370870] e1000e: eth0 NIC Link is Up 10 Mbps Full Duplex, Flow Control: RX/TX
Apr  8 14:18:02 lindholm kernel: [   40.370874] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
Apr  8 14:18:02 lindholm kernel: [   40.371373] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> (eth0): carrier now ON (device state 2)
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) starting connection 'eth0'
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Apr  8 14:18:02 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Apr  8 14:18:02 lindholm avahi-daemon[1089]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Apr  8 14:18:02 lindholm avahi-daemon[1089]: New relevant interface eth0.IPv4 for mDNS.
Apr  8 14:18:02 lindholm avahi-daemon[1089]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Apr  8 14:18:03 lindholm NetworkManager[1093]: <warn> could not commit DNS changes: 'Could not replace /etc/resolv.conf: Operation not permitted#012'
Apr  8 14:18:03 lindholm NetworkManager[1093]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Apr  8 14:18:03 lindholm NetworkManager[1093]: <warn> could not commit DNS changes: 'Could not replace /etc/resolv.conf: Operation not permitted#012'
Apr  8 14:18:03 lindholm NetworkManager[1093]: <info> Policy set 'eth0' (eth0) as default for IPv4 routing and DNS.
Apr  8 14:18:03 lindholm NetworkManager[1093]: <info> Activation (eth0) successful, device activated.
Apr  8 14:18:03 lindholm NetworkManager[1093]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Apr  8 14:18:03 lindholm avahi-daemon[1089]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::21c:c0ff:fe37:7fbb.
Apr  8 14:18:03 lindholm avahi-daemon[1089]: New relevant interface eth0.IPv6 for mDNS.
Apr  8 14:18:03 lindholm avahi-daemon[1089]: Registering new address record for fe80::21c:c0ff:fe37:7fbb on eth0.*.
Apr  8 14:18:13 lindholm ntpdate[1691]: step time server 91.189.94.4 offset 9.714759 sec
Apr  8 14:18:14 lindholm init: tty1 main process (1560) terminated with status 1
Apr  8 14:18:14 lindholm init: tty1 main process ended, respawning
Apr  8 14:18:22 lindholm kernel: [   50.821264] eth0: no IPv6 routers present
```

---

### Post by thomasaaron on 2011-04-08
Karl, there are some weird lines in there about oem-config. Those don't appear in my system. Kind of looks like the machine was installed in oem mode, but not prepared afterwards via clicking the "Prepare for End User" icon.

If I'm right, running oem-config-prepare *could* fix the problem, but I'm not sure what effect that will have on files you have stored in any other created accounts (such as /home/karl_the_world_traver). It shouldn't loose them. But if you have anything important installed in /home/oem/* it would be lost.

Am I off base here?

---

### Post by riseringseeker on 2011-04-08
> **thomasaaron said:**
> Karl, there are some weird lines in there about oem-config. Those don't appear in my system. Kind of looks like the machine was installed in oem mode, but not prepared afterwards via clicking the "Prepare for End User" icon.


IIRC, when doing the reinstall, I was given a choice between install type 1 and type 2 - no explanation what either were, so I believe I choose 1, figuring that would be the logical default install for an end user.

> If I'm right, running oem-config-prepare *could* fix the problem, but I'm not sure what effect that will have on files you have stored in any other created accounts (such as /home/karl_the_world_traver). It shouldn't loose them. But if you have anything important installed in /home/oem/* it would be lost.

I have an automated backup that runs to an external USB drive every Saturday, and I keep the Darter and Dog largely synced for the most important files anyway, so it shouldn't be a problem.  I just looked, and unless it's weirdly hidden, I don't **have** an /home/oem file/directory.  I did both an ls -lna with the terminal, and then opened nautilus and looked after hitting ctrl-H, and neither show an oem file.

I ran locate oem, and came up with this:

```
locate oem
/etc/init/oem-config.conf
/etc/init.d/oem-config
/usr/lib/oem-config
/usr/lib/oem-config/post-install
/usr/lib/oem-config/post-install/ubi-reload-keyboard
/usr/lib/ubiquity/debian-installer-utils/register-module.post-base-installer-oem
/usr/lib/ubiquity/tzsetup/post-base-installer-oem
/usr/lib/ubiquity/user-setup/reserved-usernames-oem
/usr/lib/ubiquity/user-setup/user-setup-ask-oem
/usr/sbin/oem-config
/usr/sbin/oem-config-firstboot
/usr/sbin/oem-config-prepare
/usr/sbin/oem-config-remove
/usr/sbin/oem-config-wrapper
/usr/share/app-install/desktop/gnoemoe.desktop
/usr/share/app-install/icons/gnoemoe-logo.svg
/usr/share/doc/oem-config
/usr/share/doc/oem-config-debconf
/usr/share/doc/oem-config/changelog.gz
/usr/share/doc/oem-config/copyright
/usr/share/doc/oem-config-debconf/changelog.gz
/usr/share/doc/oem-config-debconf/copyright
/usr/share/lintian/overrides/oem-config
/usr/share/man/man8/oem-config-firstboot.8.gz
/usr/share/man/man8/oem-config-prepare.8.gz
/usr/share/man/man8/oem-config.8.gz
/var/cache/apt/archives/oem-config-debconf_2.4.8_all.deb
/var/cache/apt/archives/oem-config_2.4.8_all.deb
/var/lib/oem-config
/var/lib/dpkg/info/oem-config-debconf.list
/var/lib/dpkg/info/oem-config-debconf.md5sums
/var/lib/dpkg/info/oem-config.conffiles
/var/lib/dpkg/info/oem-config.list
/var/lib/dpkg/info/oem-config.md5sums
/var/lib/dpkg/info/oem-config.postinst
/var/lib/dpkg/info/oem-config.postrm
/var/lib/dpkg/info/oem-config.templates
/var/lib/oem-config/run
/var/log/oem-config.log

```

Curious as the contents of the oem-config.log, I looked at it, and see:

```
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault
Ubiquity 2.4.8 (oem-config)
Segmentation fault

```

> Am I off base here?

You are usually spot on, and given the output of the above, you may have hit the proverbial nail on the head,  I may want to wait until I get home to try it.  Leaving for Hong Kong tomorrow, and if the current forecast holds, might be home as early as Tuesday afternoon.

It's 23:00+ here now, so I am off to bed for the evening.

---

### Post by thomasaaron on 2011-04-08
I think that's what's going on. Tell me this... when you installed and rebooted, did it bring you through the customer set-up routine (username, password, time zone)?

If not, did you have to specifically create accounts for your wife and yourself?

Since there's no /home/oem directory, I think your safe in just running oem-config-prepare (sudo it). It will remove the oem-config program that's segfaulting, which I believe is what's keeping the Dog from... barking. But it might do some other configuration-related junk...

Another thought (amazing that I'm having two in one day :confused: ), is to run...

sudo apt-get remove oem-confg

That might be a better way to go, as it will delete the unnecessary program that's segfaulting and not risk botching everything else.

---

### Post by riseringseeker on 2011-04-08
> **thomasaaron said:**
> I think that's what's going on. Tell me this... when you installed and rebooted, did it bring you through the customer set-up routine (username, password, time zone)?

Other than it asking which type of install I wanted to do (1 or 2), I don't recall it doing anything that I hadn't seen in dozens of installs before, so I would say yes.

> If not, did you have to specifically create accounts for your wife and yourself?

Just for her, which would be normal - by that I mean I later added her once I got it up and running.  Should I have seen an option along the way to add additional users before the install was finished?

> Since there's no /home/oem directory, I think your safe in just running oem-config-prepare (sudo it). It will remove the oem-config program that's segfaulting, which I believe is what's keeping the Dog from... barking. But it might do some other configuration-related junk...

I may try that from Hong Kong, the computer is no use to the wife right now, and I can get along without accessing the files or using the printer until I get home if it borks everything.

> Another thought (amazing that I'm having two in one day :confused: ), is to run...

sudo apt-get remove oem-confg

That might be a better way to go, as it will delete the unnecessary program that's segfaulting and not risk botching everything else.

OK, will try that first, once the moon is in phase and the wife and I can be up at the same time so she can give me feedback.

---

### Post by riseringseeker on 2011-04-10
Well decided to give the sudo apt-get remove oem-config a shot, figuring I would only be out a few days access to the files and printer at home if it went badly, and could give the wife a working computer if it went well.

It worked as you thought it would, Tom.  It also removed jasper that I had installed for gyache instant messenger web cam access a couple of weeks ago - that might have caused the problem!  I had installed jasper before it went out the first time as well, but given that it ran fine for days or weeks before shorting out, I never had reason to suspect it.

I've got another glitch, but will start a new thread for that.

---

