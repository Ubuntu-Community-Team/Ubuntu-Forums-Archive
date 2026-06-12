---
title: "Darter Ultra 2 - touch pad stops working"
date: 2008-12-23
forum: System76 Support
---

### Post by imhavoc on 2008-12-23
My touchpad on my trusty ol' Darter Ultra 2 decided to take Christmas vacation off today.

After a couple of reboots earlier today it started working again, but stopped responding once again.

Linux schoolbook 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

lsusb:
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 147e:2016  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0db0:a97a Micro Star International 
Bus 001 Device 001: ID 0000:0000  

```

anything else I can give to help diagnose?

---

### Post by thomasaaron on 2008-12-23
Please run theses command and attach the files they creates on your Desktop to this thread.

cat /var/log/messages ~/Desktop/messages.txt
cat /var/log/syslog ~/Desktop/syslog.txt

---

### Post by imhavoc on 2008-12-23
/var/log/messages:
```
Dec 22 12:55:40 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 22 13:01:40 schoolbook kernel: [  575.632328] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 13:01:40 schoolbook kernel: [  575.632337] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 13:01:40 schoolbook kernel: [  575.633589] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 13:01:40 schoolbook kernel: [  575.633596] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 13:25:08 schoolbook -- MARK --
Dec 22 13:35:41 schoolbook kernel: [ 1473.803957] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x006f000a
Dec 22 14:05:08 schoolbook -- MARK --
Dec 22 14:06:27 schoolbook kernel: [ 2837.838408] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 22 14:06:27 schoolbook kernel: [ 2837.838418] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 14:06:27 schoolbook kernel: [ 2837.839103] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 22 14:06:27 schoolbook kernel: [ 2837.839109] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 14:06:28 schoolbook kernel: [ 2838.072439] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 22 14:06:28 schoolbook kernel: [ 2838.317185] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 22 14:06:29 schoolbook kernel: [ 2838.576616] usb 3-1: new full speed USB device using uhci_hcd and address 4
Dec 22 14:06:29 schoolbook kernel: [ 2838.877384] usb 3-1: new full speed USB device using uhci_hcd and address 5
Dec 22 14:06:35 schoolbook kernel: [ 2841.414032] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 22 14:06:35 schoolbook kernel: [ 2841.414042] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 14:06:35 schoolbook kernel: [ 2841.415253] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 22 14:06:35 schoolbook kernel: [ 2841.415258] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 14:06:43 schoolbook kernel: [ 2845.372083] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:43 schoolbook kernel: [ 2845.372093] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:43 schoolbook kernel: [ 2845.581053] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:43 schoolbook kernel: [ 2845.581063] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:45 schoolbook kernel: [ 2846.337185] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:45 schoolbook kernel: [ 2846.337194] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:45 schoolbook kernel: [ 2846.486332] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:45 schoolbook kernel: [ 2846.486342] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:47 schoolbook kernel: [ 2847.202717] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:47 schoolbook kernel: [ 2847.202727] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:47 schoolbook kernel: [ 2847.345603] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:47 schoolbook kernel: [ 2847.345613] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:49 schoolbook kernel: [ 2848.295841] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:49 schoolbook kernel: [ 2848.295852] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:49 schoolbook kernel: [ 2848.440751] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:49 schoolbook kernel: [ 2848.440763] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:50 schoolbook kernel: [ 2848.871063] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:50 schoolbook kernel: [ 2848.871073] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:50 schoolbook kernel: [ 2849.019520] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:50 schoolbook kernel: [ 2849.019531] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:53 schoolbook kernel: [ 2850.604502] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:53 schoolbook kernel: [ 2850.604512] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:06:53 schoolbook kernel: [ 2850.663580] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 14:06:53 schoolbook kernel: [ 2850.663589] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 14:08:03 schoolbook kernel: [ 2885.432846] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:08:03 schoolbook kernel: [ 2885.432857] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:08:03 schoolbook kernel: [ 2885.434127] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:08:03 schoolbook kernel: [ 2885.434136] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:08:04 schoolbook kernel: [ 2886.117371] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:08:04 schoolbook kernel: [ 2886.117375] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:08:04 schoolbook kernel: [ 2886.118628] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:08:04 schoolbook kernel: [ 2886.118631] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:08:21 schoolbook kernel: [ 2892.254889] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:08:23 schoolbook exiting on signal 15
Dec 22 14:09:56 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 22 14:09:57 schoolbook kernel: Inspecting /boot/System.map-2.6.24-19-generic
Dec 22 14:09:57 schoolbook kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Dec 22 14:09:57 schoolbook kernel: Symbols match kernel version 2.6.24.
Dec 22 14:09:57 schoolbook kernel: Loaded 18154 symbols from 89 modules.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Dec 22 14:09:57 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] 1143MB HIGHMEM available.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] 896MB LOWMEM available.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Zone PFN ranges:
Dec 22 14:09:57 schoolbook kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 14:09:57 schoolbook kernel: [    0.000000]   Normal       4096 ->   229376
Dec 22 14:09:57 schoolbook kernel: [    0.000000]   HighMem    229376 ->   522144
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 22 14:09:57 schoolbook kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 14:09:57 schoolbook kernel: [    0.000000]     0:        0 ->   522144
Dec 22 14:09:57 schoolbook kernel: [    0.000000] DMI present.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: RSDT 7F7A0000, 0044 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 052807 FACP1333 20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: DSDT 7F7A05B0, 5B1B (r1  A1221 A1221000        0 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 052807 APIC1333 20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 052807 OEMMCFG  20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: SLIC 7F7A0430, 0176 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0071 (r1 052807 OEMB1333 20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: HPET 7F7A60D0, 0038 (r1 052807 OEMHPET  20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: GSCI 7F7AE0C0, 2024 (r1 052807 GMCHSCI  20070528 MSFT       97)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: SSDT 7F7B09B0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 22 14:09:57 schoolbook kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 14:09:57 schoolbook kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009a000 - 000000000009b000
Dec 22 14:09:57 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
Dec 22 14:09:57 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Dec 22 14:09:57 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518065
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Kernel command line: root=UUID=63c2c38b-8e0d-4df8-b0e2-f0d556007b0e ro quiet splash ec_intr=0
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Initializing CPU#0
Dec 22 14:09:57 schoolbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 22 14:09:57 schoolbook kernel: [    0.000000] Detected 1995.035 MHz processor.
Dec 22 14:09:57 schoolbook kernel: [   19.703837] Console: colour VGA+ 80x25
Dec 22 14:09:57 schoolbook kernel: [   19.703842] console [tty0] enabled
Dec 22 14:09:57 schoolbook kernel: [   19.704160] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 22 14:09:57 schoolbook kernel: [   19.704542] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 14:09:57 schoolbook kernel: [   19.835881] Memory: 2058228k/2088576k available (2177k kernel code, 29064k reserved, 1006k data, 368k init, 1171072k highmem)
Dec 22 14:09:57 schoolbook kernel: [   19.835890] virtual kernel memory layout:
Dec 22 14:09:57 schoolbook kernel: [   19.835891]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Dec 22 14:09:57 schoolbook kernel: [   19.835893]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 14:09:57 schoolbook kernel: [   19.835894]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 22 14:09:57 schoolbook kernel: [   19.835896]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 22 14:09:57 schoolbook kernel: [   19.835897]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Dec 22 14:09:57 schoolbook kernel: [   19.835899]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Dec 22 14:09:57 schoolbook kernel: [   19.835900]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Dec 22 14:09:57 schoolbook kernel: [   19.835904] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 22 14:09:57 schoolbook kernel: [   19.835952] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 22 14:09:57 schoolbook kernel: [   19.916049] Calibrating delay using timer specific routine.. 3995.17 BogoMIPS (lpj=7990359)
Dec 22 14:09:57 schoolbook kernel: [   19.916074] Security Framework initialized
Dec 22 14:09:57 schoolbook kernel: [   19.916081] SELinux:  Disabled at boot.
Dec 22 14:09:57 schoolbook kernel: [   19.916097] AppArmor: AppArmor initialized
Dec 22 14:09:57 schoolbook kernel: [   19.916103] Failure registering capabilities with primary security module.
Dec 22 14:09:57 schoolbook kernel: [   19.916113] Mount-cache hash table entries: 512
Dec 22 14:09:57 schoolbook kernel: [   19.916262] Initializing cgroup subsys ns
Dec 22 14:09:57 schoolbook kernel: [   19.916268] Initializing cgroup subsys cpuacct
Dec 22 14:09:57 schoolbook kernel: [   19.916290] monitor/mwait feature present.
Dec 22 14:09:57 schoolbook kernel: [   19.916293] using mwait in idle threads.
Dec 22 14:09:57 schoolbook kernel: [   19.916298] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:09:57 schoolbook kernel: [   19.916301] CPU: L2 cache: 4096K
Dec 22 14:09:57 schoolbook kernel: [   19.916304] CPU: Physical Processor ID: 0
Dec 22 14:09:57 schoolbook kernel: [   19.916306] CPU: Processor Core ID: 0
Dec 22 14:09:57 schoolbook kernel: [   19.916321] Compat vDSO mapped to ffffe000.
Dec 22 14:09:57 schoolbook kernel: [   19.916337] Checking 'hlt' instruction... OK.
Dec 22 14:09:57 schoolbook kernel: [   19.932556] SMP alternatives: switching to UP code
Dec 22 14:09:57 schoolbook kernel: [   19.934753] Early unpacking initramfs... done
Dec 22 14:09:57 schoolbook kernel: [   20.435209] ACPI: Core revision 20070126
Dec 22 14:09:57 schoolbook kernel: [   20.435264] ACPI: Looking for DSDT in initramfs... successfully read 23336 bytes from /DSDT.aml.
Dec 22 14:09:57 schoolbook kernel: [   20.435291] ACPI: Table DSDT replaced by host OS
Dec 22 14:09:57 schoolbook kernel: [   20.435295] ACPI: DSDT 00000000, 5B28 (r1  A1221 A1221000        0 INTL 20061109)
Dec 22 14:09:57 schoolbook kernel: [   20.435302] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:09:57 schoolbook kernel: [   20.439261] SMP alternatives: switching to SMP code
Dec 22 14:09:57 schoolbook kernel: [   20.440189] Booting processor 1/1 eip 3000
Dec 22 14:09:57 schoolbook kernel: [   20.450837] Initializing CPU#1
Dec 22 14:09:57 schoolbook kernel: [   20.527700] Calibrating delay using timer specific routine.. 3990.06 BogoMIPS (lpj=7980125)
Dec 22 14:09:57 schoolbook kernel: [   20.527716] monitor/mwait feature present.
Dec 22 14:09:57 schoolbook kernel: [   20.527720] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:09:57 schoolbook kernel: [   20.527722] CPU: L2 cache: 4096K
Dec 22 14:09:57 schoolbook kernel: [   20.527725] CPU: Physical Processor ID: 0
Dec 22 14:09:57 schoolbook kernel: [   20.527726] CPU: Processor Core ID: 1
Dec 22 14:09:57 schoolbook kernel: [   20.528775] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:09:57 schoolbook kernel: [   20.528803] Total of 2 processors activated (7985.24 BogoMIPS).
Dec 22 14:09:57 schoolbook kernel: [   20.528996] ENABLING IO-APIC IRQs
Dec 22 14:09:57 schoolbook kernel: [   20.529197] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 22 14:09:57 schoolbook kernel: [   20.675757] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 22 14:09:57 schoolbook kernel: [   20.695766] Brought up 2 CPUs
Dec 22 14:09:57 schoolbook kernel: [   20.696093] net_namespace: 64 bytes
Dec 22 14:09:57 schoolbook kernel: [   20.696108] Booting paravirtualized kernel on bare hardware
Dec 22 14:09:57 schoolbook kernel: [   20.696734] Time: 21:09:12  Date: 12/22/08
Dec 22 14:09:57 schoolbook kernel: [   20.696768] NET: Registered protocol family 16
Dec 22 14:09:57 schoolbook kernel: [   20.697015] EISA bus registered
Dec 22 14:09:57 schoolbook kernel: [   20.697021] ACPI: bus type pci registered
Dec 22 14:09:57 schoolbook kernel: [   20.697331] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 22 14:09:57 schoolbook kernel: [   20.697334] PCI: Using configuration type 1
Dec 22 14:09:57 schoolbook kernel: [   20.697367] Setting up standard PCI resources
Dec 22 14:09:57 schoolbook kernel: [   20.713047] ACPI: Interpreter enabled
Dec 22 14:09:57 schoolbook kernel: [   20.713051] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 14:09:57 schoolbook kernel: [   20.713073] ACPI: Using IOAPIC for interrupt routing
Dec 22 14:09:57 schoolbook kernel: [   20.713436] Error attaching device data
Dec 22 14:09:57 schoolbook kernel: [   20.713492] Error attaching device data
Dec 22 14:09:57 schoolbook kernel: [   20.715677] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 22 14:09:57 schoolbook kernel: [   20.722480] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 22 14:09:57 schoolbook kernel: [   20.722484] ACPI: EC: driver started in interrupt mode
Dec 22 14:09:57 schoolbook kernel: [   20.722634] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 22 14:09:57 schoolbook kernel: [   20.723820] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 22 14:09:57 schoolbook kernel: [   20.723826] PCI quirk: region 0500-053f claimed by ICH6 GPIO
Dec 22 14:09:57 schoolbook kernel: [   20.725414] PCI: Transparent bridge - 0000:00:1e.0
Dec 22 14:09:57 schoolbook kernel: [   20.747184] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.747361] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.747533] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.747711] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.747882] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.748053] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 22 14:09:57 schoolbook kernel: [   20.748225] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.748397] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec 22 14:09:57 schoolbook kernel: [   20.748592] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 22 14:09:57 schoolbook kernel: [   20.748632] pnp: PnP ACPI init
Dec 22 14:09:57 schoolbook kernel: [   20.748642] ACPI: bus type pnp registered
Dec 22 14:09:57 schoolbook kernel: [   20.751615] pnp: PnP ACPI: found 13 devices
Dec 22 14:09:57 schoolbook kernel: [   20.751618] ACPI: ACPI bus type pnp unregistered
Dec 22 14:09:57 schoolbook kernel: [   20.751623] PnPBIOS: Disabled by ACPI PNP
Dec 22 14:09:57 schoolbook kernel: [   20.751961] PCI: Using ACPI for IRQ routing
Dec 22 14:09:57 schoolbook kernel: [   20.751965] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 22 14:09:57 schoolbook kernel: [   20.807560] NET: Registered protocol family 8
Dec 22 14:09:57 schoolbook kernel: [   20.807563] NET: Registered protocol family 20
Dec 22 14:09:57 schoolbook kernel: [   20.807607] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 22 14:09:57 schoolbook kernel: [   20.807613] hpet0: 3 64-bit timers, 14318180 Hz
Dec 22 14:09:57 schoolbook kernel: [   20.808653] AppArmor: AppArmor Filesystem Enabled
Dec 22 14:09:57 schoolbook kernel: [   20.811550] Time: tsc clocksource has been installed.
Dec 22 14:09:57 schoolbook kernel: [   20.827540] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827553] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827557] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827561] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827564] system 00:08: ioport range 0x500-0x53f has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827568] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827572] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827576] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827585] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827589] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827597] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827605] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827609] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827613] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827617] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.827621] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 22 14:09:57 schoolbook kernel: [   20.858168] PCI: Bridge: 0000:00:1c.0
Dec 22 14:09:57 schoolbook kernel: [   20.858172]   IO window: e000-efff
Dec 22 14:09:57 schoolbook kernel: [   20.858180]   MEM window: fe000000-febfffff
Dec 22 14:09:57 schoolbook kernel: [   20.858186]   PREFETCH window: fa000000-fcffffff
Dec 22 14:09:57 schoolbook kernel: [   20.858194] PCI: Bridge: 0000:00:1c.1
Dec 22 14:09:57 schoolbook kernel: [   20.858198]   IO window: d000-dfff
Dec 22 14:09:57 schoolbook kernel: [   20.858205]   MEM window: fdf00000-fdffffff
Dec 22 14:09:57 schoolbook kernel: [   20.858211]   PREFETCH window: disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.858218] PCI: Bridge: 0000:00:1c.2
Dec 22 14:09:57 schoolbook kernel: [   20.858219]   IO window: disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.858227]   MEM window: fde00000-fdefffff
Dec 22 14:09:57 schoolbook kernel: [   20.858232]   PREFETCH window: disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.858239] PCI: Bridge: 0000:00:1e.0
Dec 22 14:09:57 schoolbook kernel: [   20.858241]   IO window: disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.858248]   MEM window: fdd00000-fddfffff
Dec 22 14:09:57 schoolbook kernel: [   20.858254]   PREFETCH window: disabled.
Dec 22 14:09:57 schoolbook kernel: [   20.858291] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:09:57 schoolbook kernel: [   20.858330] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Dec 22 14:09:57 schoolbook kernel: [   20.858367] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:09:57 schoolbook kernel: [   20.858407] NET: Registered protocol family 2
Dec 22 14:09:57 schoolbook kernel: [   20.895529] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 14:09:57 schoolbook kernel: [   20.895820] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 22 14:09:57 schoolbook kernel: [   20.896366] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 22 14:09:57 schoolbook kernel: [   20.896609] TCP: Hash tables configured (established 131072 bind 65536)
Dec 22 14:09:57 schoolbook kernel: [   20.896612] TCP reno registered
Dec 22 14:09:57 schoolbook kernel: [   20.907602] checking if image is initramfs... it is
Dec 22 14:09:57 schoolbook kernel: [   21.893465] Freeing initrd memory: 7744k freed
Dec 22 14:09:57 schoolbook kernel: [   21.894434] audit: initializing netlink socket (disabled)
Dec 22 14:09:57 schoolbook kernel: [   21.894450] audit(1229980151.933:1): initialized
Dec 22 14:09:57 schoolbook kernel: [   21.894712] highmem bounce pool size: 64 pages
Dec 22 14:09:57 schoolbook kernel: [   21.897336] VFS: Disk quotas dquot_6.5.1
Dec 22 14:09:57 schoolbook kernel: [   21.897435] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 14:09:57 schoolbook kernel: [   21.897603] io scheduler noop registered
Dec 22 14:09:57 schoolbook kernel: [   21.897606] io scheduler anticipatory registered
Dec 22 14:09:57 schoolbook kernel: [   21.897609] io scheduler deadline registered
Dec 22 14:09:57 schoolbook kernel: [   21.897624] io scheduler cfq registered (default)
Dec 22 14:09:57 schoolbook kernel: [   21.897989] assign_interrupt_mode Found MSI capability
Dec 22 14:09:57 schoolbook kernel: [   21.898289] assign_interrupt_mode Found MSI capability
Dec 22 14:09:57 schoolbook kernel: [   21.898582] assign_interrupt_mode Found MSI capability
Dec 22 14:09:57 schoolbook kernel: [   21.899029] isapnp: Scanning for PnP cards...
Dec 22 14:09:57 schoolbook kernel: [   22.253434] isapnp: No Plug & Play device found
Dec 22 14:09:57 schoolbook kernel: [   22.287229] Real Time Clock Driver v1.12ac
Dec 22 14:09:57 schoolbook kernel: [   22.287495] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 22 14:09:57 schoolbook kernel: [   22.289052] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 22 14:09:57 schoolbook kernel: [   22.289142] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 22 14:09:57 schoolbook kernel: [   22.289271] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 22 14:09:57 schoolbook kernel: [   22.289647] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 22 14:09:57 schoolbook kernel: [   22.289728] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 14:09:57 schoolbook kernel: [   22.289734] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 22 14:09:57 schoolbook kernel: [   22.289738] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 22 14:09:57 schoolbook kernel: [   22.289741] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 22 14:09:57 schoolbook kernel: [   22.289744] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 22 14:09:57 schoolbook kernel: [   22.298746] mice: PS/2 mouse device common for all mice
Dec 22 14:09:57 schoolbook kernel: [   22.298888] EISA: Probing bus 0 at eisa.0
Dec 22 14:09:57 schoolbook kernel: [   22.298932] EISA: Detected 0 cards.
Dec 22 14:09:57 schoolbook kernel: [   22.298936] cpuidle: using governor ladder
Dec 22 14:09:57 schoolbook kernel: [   22.298938] cpuidle: using governor menu
Dec 22 14:09:57 schoolbook kernel: [   22.299037] NET: Registered protocol family 1
Dec 22 14:09:57 schoolbook kernel: [   22.299070] Using IPI No-Shortcut mode
Dec 22 14:09:57 schoolbook kernel: [   22.299104] registered taskstats version 1
Dec 22 14:09:57 schoolbook kernel: [   22.299249]   Magic number: 4:535:197
Dec 22 14:09:57 schoolbook kernel: [   22.299265]   hash matches device ttys9
Dec 22 14:09:57 schoolbook kernel: [   22.299271]   hash matches device ttypc
Dec 22 14:09:57 schoolbook kernel: [   22.299306]   hash matches device PNP0100:00
Dec 22 14:09:57 schoolbook kernel: [   22.299311] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 22 14:09:57 schoolbook kernel: [   22.299313] EDD information not available.
Dec 22 14:09:57 schoolbook kernel: [   22.299538] Freeing unused kernel memory: 368k freed
Dec 22 14:09:57 schoolbook kernel: [   22.301925] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 22 14:09:57 schoolbook kernel: [   23.618919] fuse init (API version 7.9)
Dec 22 14:09:57 schoolbook kernel: [   23.668500] ACPI: SSDT 7F7B01C0, 0297 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [   23.668799] ACPI: SSDT 7F7B04F0, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [   23.669414] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:09:57 schoolbook kernel: [   23.669713] ACPI: SSDT 7F7B00F0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [   23.669997] ACPI: SSDT 7F7B0460, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Dec 22 14:09:57 schoolbook kernel: [   23.670745] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:09:57 schoolbook kernel: [   23.673357] ACPI: Thermal Zone [THRM] (55 C)
Dec 22 14:09:57 schoolbook kernel: [   23.865937] usbcore: registered new interface driver usbfs
Dec 22 14:09:57 schoolbook kernel: [   23.865966] usbcore: registered new interface driver hub
Dec 22 14:09:57 schoolbook kernel: [   23.866552] usbcore: registered new device driver usb
Dec 22 14:09:57 schoolbook kernel: [   23.868637] USB Universal Host Controller Interface driver v3.0
Dec 22 14:09:57 schoolbook kernel: [   23.868691] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:09:57 schoolbook kernel: [   23.868709] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   23.868925] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 22 14:09:57 schoolbook kernel: [   23.868962] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Dec 22 14:09:57 schoolbook kernel: [   23.869147] usb usb1: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   23.869179] hub 1-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   23.869186] hub 1-0:1.0: 2 ports detected
Dec 22 14:09:57 schoolbook kernel: [   23.969798] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Dec 22 14:09:57 schoolbook kernel: [   23.969817] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   23.969846] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 22 14:09:57 schoolbook kernel: [   23.969881] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000b880
Dec 22 14:09:57 schoolbook kernel: [   23.970025] usb usb2: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   23.970056] hub 2-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   23.970062] hub 2-0:1.0: 2 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.073715] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:09:57 schoolbook kernel: [   24.073734] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   24.073765] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Dec 22 14:09:57 schoolbook kernel: [   24.073799] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bc00
Dec 22 14:09:57 schoolbook kernel: [   24.073946] usb usb3: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   24.073977] hub 3-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   24.073984] hub 3-0:1.0: 2 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.177652] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:09:57 schoolbook kernel: [   24.177671] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   24.177703] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Dec 22 14:09:57 schoolbook kernel: [   24.177737] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c000
Dec 22 14:09:57 schoolbook kernel: [   24.177879] usb usb4: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   24.177912] hub 4-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   24.177919] hub 4-0:1.0: 2 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.209556] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 22 14:09:57 schoolbook kernel: [   24.243972] SCSI subsystem initialized
Dec 22 14:09:57 schoolbook kernel: [   24.281597] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:09:57 schoolbook kernel: [   24.281617] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   24.281648] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Dec 22 14:09:57 schoolbook kernel: [   24.281682] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c080
Dec 22 14:09:57 schoolbook kernel: [   24.281830] usb usb5: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   24.281862] hub 5-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   24.281869] hub 5-0:1.0: 2 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.385554] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 22 14:09:57 schoolbook kernel: [   24.385586] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 22 14:09:57 schoolbook kernel: [   24.385695] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:09:57 schoolbook kernel: [   24.385719] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   24.385754] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Dec 22 14:09:57 schoolbook kernel: [   24.386052] eth0: RTL8168b/8111b at 0xf8828000, 00:19:db:3c:e3:55, XID 38000000 IRQ 220
Dec 22 14:09:57 schoolbook kernel: [   24.389661] ehci_hcd 0000:00:1a.7: debug port 1
Dec 22 14:09:57 schoolbook kernel: [   24.389677] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdcff000
Dec 22 14:09:57 schoolbook kernel: [   24.405415] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:09:57 schoolbook kernel: [   24.405550] usb usb6: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   24.405586] hub 6-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   24.405593] hub 6-0:1.0: 4 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.509487] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:09:57 schoolbook kernel: [   24.509508] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 22 14:09:57 schoolbook kernel: [   24.509538] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Dec 22 14:09:57 schoolbook kernel: [   24.513465] ehci_hcd 0000:00:1d.7: debug port 1
Dec 22 14:09:57 schoolbook kernel: [   24.513481] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfdcff400
Dec 22 14:09:57 schoolbook kernel: [   24.529363] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:09:57 schoolbook kernel: [   24.529493] usb usb7: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   24.529525] hub 7-0:1.0: USB hub found
Dec 22 14:09:57 schoolbook kernel: [   24.529532] hub 7-0:1.0: 6 ports detected
Dec 22 14:09:57 schoolbook kernel: [   24.633428] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:09:57 schoolbook kernel: [   25.372925] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 22 14:09:57 schoolbook kernel: [   25.456835] Clocksource tsc unstable (delta = -12542896045 ns)
Dec 22 14:09:57 schoolbook kernel: [   25.460818] Time: hpet clocksource has been installed.
Dec 22 14:09:57 schoolbook kernel: [   25.474439] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   25.504377] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Dec 22 14:09:57 schoolbook kernel: [   25.504383] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
Dec 22 14:09:57 schoolbook kernel: [   25.504673] scsi0 : ahci
Dec 22 14:09:57 schoolbook kernel: [   25.505030] scsi1 : ahci
Dec 22 14:09:57 schoolbook kernel: [   25.505265] scsi2 : ahci
Dec 22 14:09:57 schoolbook kernel: [   25.505363] ata1: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff900 irq 219
Dec 22 14:09:57 schoolbook kernel: [   25.505368] ata2: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff980 irq 219
Dec 22 14:09:57 schoolbook kernel: [   25.505372] ata3: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcffa00 irq 219
Dec 22 14:09:57 schoolbook kernel: [   25.517300] usb 5-1: new full speed USB device using uhci_hcd and address 2
Dec 22 14:09:57 schoolbook kernel: [   25.538948] usb 5-1: configuration #1 chosen from 1 choice
Dec 22 14:09:57 schoolbook kernel: [   25.630977] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 14:09:57 schoolbook kernel: [   25.631894] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
Dec 22 14:09:57 schoolbook kernel: [   25.631899] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Dec 22 14:09:57 schoolbook kernel: [   25.633000] ata1.00: configured for UDMA/100
Dec 22 14:09:57 schoolbook kernel: [   25.666813] ata2: SATA link down (SStatus 0 SControl 300)
Dec 22 14:09:57 schoolbook kernel: [   25.696214] ata3: SATA link down (SStatus 0 SControl 300)
Dec 22 14:09:57 schoolbook kernel: [   25.696474] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Dec 22 14:09:57 schoolbook kernel: [   25.701964] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:09:57 schoolbook kernel: [   25.702646] scsi3 : ata_piix
Dec 22 14:09:57 schoolbook kernel: [   25.702927] scsi4 : ata_piix
Dec 22 14:09:57 schoolbook kernel: [   25.704482] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 22 14:09:57 schoolbook kernel: [   25.704486] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 22 14:09:57 schoolbook kernel: [   25.708919] Driver 'sd' needs updating - please use bus_type methods
Dec 22 14:09:57 schoolbook kernel: [   25.711448] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:09:57 schoolbook kernel: [   25.711465] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:09:57 schoolbook kernel: [   25.711492] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:09:57 schoolbook kernel: [   25.711555] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:09:57 schoolbook kernel: [   25.711569] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:09:57 schoolbook kernel: [   25.711595] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:09:57 schoolbook kernel: [   25.711600]  sda:<6>ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WA03, max UDMA/33
Dec 22 14:09:57 schoolbook kernel: [   26.124189]  sda1 sda2 < sda5 >
Dec 22 14:09:57 schoolbook kernel: [   26.142795] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 14:09:57 schoolbook kernel: [   26.149585] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 14:09:57 schoolbook kernel: [   26.194280] ata4.00: configured for UDMA/33
Dec 22 14:09:57 schoolbook kernel: [   26.197951] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WA03 PQ: 0 ANSI: 5
Dec 22 14:09:57 schoolbook kernel: [   26.198049] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 22 14:09:57 schoolbook kernel: [   26.210830] Driver 'sr' needs updating - please use bus_type methods
Dec 22 14:09:57 schoolbook kernel: [   26.227993] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 22 14:09:57 schoolbook kernel: [   26.227997] Uniform CD-ROM driver Revision: 3.20
Dec 22 14:09:57 schoolbook kernel: [   26.383289] Attempting manual resume
Dec 22 14:09:57 schoolbook kernel: [   26.437381] kjournald starting.  Commit interval 5 seconds
Dec 22 14:09:57 schoolbook kernel: [   26.437408] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 14:09:57 schoolbook kernel: [   39.845715] input: PC Speaker as /devices/platform/pcspkr/input/input2
Dec 22 14:09:57 schoolbook kernel: [   39.902015] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 14:09:57 schoolbook kernel: [   39.944604] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 14:09:57 schoolbook kernel: [   39.999999] Linux agpgart interface v0.102
Dec 22 14:09:57 schoolbook kernel: [   40.185188] iTCO_vendor_support: vendor-support=0
Dec 22 14:09:57 schoolbook kernel: [   40.218548] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 22 14:09:57 schoolbook kernel: [   40.218639] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
Dec 22 14:09:57 schoolbook kernel: [   40.218685] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 22 14:09:57 schoolbook kernel: [   40.266493] agpgart: Detected an Intel 965GM Chipset.
Dec 22 14:09:57 schoolbook kernel: [   40.269263] agpgart: Detected 7676K stolen memory.
Dec 22 14:09:57 schoolbook kernel: [   40.290737] agpgart: AGP aperture is 256M @ 0xd0000000
Dec 22 14:09:57 schoolbook kernel: [   40.377528] input: Power Button (FF) as /devices/virtual/input/input3
Dec 22 14:09:57 schoolbook kernel: [   40.400921] sdhci: Secure Digital Host Controller Interface driver
Dec 22 14:09:57 schoolbook kernel: [   40.400925] sdhci: Copyright(c) Pierre Ossman
Dec 22 14:09:57 schoolbook kernel: [   40.400971] sdhci: SDHCI controller found at 0000:01:04.1 [1524:0750] (rev 0)
Dec 22 14:09:57 schoolbook kernel: [   40.400996] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:09:57 schoolbook kernel: [   40.401068] mmc0: SDHCI at 0xfddff400 irq 16 DMA
Dec 22 14:09:57 schoolbook kernel: [   40.401080] sdhci: SDHCI controller found at 0000:01:04.3 [1524:0751] (rev 0)
Dec 22 14:09:57 schoolbook kernel: [   40.401101] ACPI: PCI Interrupt 0000:01:04.3[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:09:57 schoolbook kernel: [   40.401115] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 22 14:09:57 schoolbook kernel: [   40.401155] mmc1: SDHCI at 0xfddffc00 irq 16 DMA
Dec 22 14:09:57 schoolbook kernel: [   40.430374] ACPI: Power Button (FF) [PWRF]
Dec 22 14:09:57 schoolbook kernel: [   40.430464] input: Lid Switch as /devices/virtual/input/input4
Dec 22 14:09:57 schoolbook kernel: [   40.462810] ACPI: Lid Switch [LID0]
Dec 22 14:09:57 schoolbook kernel: [   40.462905] input: Power Button (CM) as /devices/virtual/input/input5
Dec 22 14:09:57 schoolbook kernel: [   40.510312] ACPI: Power Button (CM) [PWRB]
Dec 22 14:09:57 schoolbook kernel: [   40.916046] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
Dec 22 14:09:57 schoolbook kernel: [   40.946041] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 22 14:09:57 schoolbook kernel: [   41.096157] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Dec 22 14:09:57 schoolbook kernel: [   41.096162] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Dec 22 14:09:57 schoolbook kernel: [   41.096287] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:09:57 schoolbook kernel: [   41.096337] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 22 14:09:57 schoolbook kernel: [   41.262670] ACPI: AC Adapter [ADP1] (on-line)
Dec 22 14:09:57 schoolbook kernel: [   41.545759] ACPI: Battery Slot [BAT1] (battery present)
Dec 22 14:09:57 schoolbook kernel: [   41.574477] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec 22 14:09:57 schoolbook kernel: [   41.603662] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Dec 22 14:09:57 schoolbook kernel: [   41.636712] Bluetooth: Core ver 2.11
Dec 22 14:09:57 schoolbook kernel: [   41.637730] NET: Registered protocol family 31
Dec 22 14:09:57 schoolbook kernel: [   41.637733] Bluetooth: HCI device and connection manager initialized
Dec 22 14:09:57 schoolbook kernel: [   41.637737] Bluetooth: HCI socket layer initialized
Dec 22 14:09:57 schoolbook kernel: [   41.686786] Bluetooth: HCI USB driver ver 2.9
Dec 22 14:09:57 schoolbook kernel: [   41.688342] usbcore: registered new interface driver hci_usb
Dec 22 14:09:57 schoolbook kernel: [   41.750104] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 22
Dec 22 14:09:57 schoolbook kernel: [   42.787492] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 22 14:09:57 schoolbook kernel: [   43.072273] udev: renamed network interface wlan0 to eth1
Dec 22 14:09:57 schoolbook kernel: [   43.132036] lp: driver loaded but no devices found
Dec 22 14:09:57 schoolbook kernel: [   43.156841] snd-bt-sco revision 1.19 $
Dec 22 14:09:57 schoolbook kernel: [   43.156863] snd-bt-sco: snd-bt-scod thread starting
Dec 22 14:09:57 schoolbook kernel: [   43.615599] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Dec 22 14:09:57 schoolbook kernel: [   44.069402] EXT3 FS on sda1, internal journal
Dec 22 14:09:57 schoolbook kernel: [   44.289994] device-mapper: uevent: version 1.0.3
Dec 22 14:09:57 schoolbook kernel: [   44.290029] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Dec 22 14:09:57 schoolbook kernel: [   47.898963] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:09:57 schoolbook kernel: [   49.779375] No dock devices found.
Dec 22 14:10:00 schoolbook kernel: [   52.493755] NET: Registered protocol family 10
Dec 22 14:10:00 schoolbook kernel: [   52.493961] lo: Disabled Privacy Extensions
Dec 22 14:10:00 schoolbook kernel: [   53.032680] ppdev: user-space parallel port driver
Dec 22 14:10:00 schoolbook kernel: [   53.347938] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:00 schoolbook kernel: [   53.347942] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:00 schoolbook kernel: [   53.349201] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:00 schoolbook kernel: [   53.349204] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:01 schoolbook kernel: [   53.598533] audit(1229980201.207:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5475 profile="/usr/sbin/cupsd" namespace="default"
Dec 22 14:10:01 schoolbook kernel: [   53.653370] apm: BIOS not found.
Dec 22 14:10:01 schoolbook kernel: [   54.255730] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:01 schoolbook kernel: [   54.255735] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:01 schoolbook kernel: [   54.256991] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:01 schoolbook kernel: [   54.256994] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:02 schoolbook kernel: [   54.816530] [drm] Initialized drm 1.1.0 20060810
Dec 22 14:10:02 schoolbook kernel: [   54.822798] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:10:02 schoolbook kernel: [   54.822849] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 22 14:10:02 schoolbook kernel: [   55.124644] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:02 schoolbook kernel: [   55.124649] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:02 schoolbook kernel: [   55.125906] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:02 schoolbook kernel: [   55.125908] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:03 schoolbook kernel: [   55.825802] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:03 schoolbook kernel: [   55.825807] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:03 schoolbook kernel: [   55.827063] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:03 schoolbook kernel: [   55.827066] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:07 schoolbook dhcdbd: Started up.
Dec 22 14:10:09 schoolbook kernel: [   60.830312] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 14:10:09 schoolbook kernel: [   60.877744] r8169: eth0: link down
Dec 22 14:10:09 schoolbook kernel: [   60.882078] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 22 14:10:10 schoolbook kernel: [   61.268815] Bluetooth: L2CAP ver 2.9
Dec 22 14:10:10 schoolbook kernel: [   61.268824] Bluetooth: L2CAP socket layer initialized
Dec 22 14:10:10 schoolbook kernel: [   61.350820] Bluetooth: RFCOMM socket layer initialized
Dec 22 14:10:10 schoolbook kernel: [   61.350841] Bluetooth: RFCOMM TTY layer initialized
Dec 22 14:10:10 schoolbook kernel: [   61.350845] Bluetooth: RFCOMM ver 1.8
Dec 22 14:10:10 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 22 14:10:13 schoolbook kernel: [   64.585282] vmmon: module license 'unspecified' taints kernel.
Dec 22 14:10:13 schoolbook kernel: [   65.100811] bridge-eth1: already up
Dec 22 14:10:13 schoolbook kernel: [   65.104771] bridge-eth0: already up
Dec 22 14:10:27 schoolbook kernel: [   70.096198] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:27 schoolbook kernel: [   70.096210] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:27 schoolbook kernel: [   70.097455] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:10:27 schoolbook kernel: [   70.097462] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:10:28 schoolbook kernel: [   70.809773] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:28 schoolbook kernel: [   70.809777] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:28 schoolbook kernel: [   70.811016] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:10:28 schoolbook kernel: [   70.811019] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:10:45 schoolbook kernel: [   75.891709] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:10:47 schoolbook kernel: [   77.061222] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x00db2001
Dec 22 14:10:49 schoolbook exiting on signal 15
Dec 22 14:15:56 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 22 14:15:56 schoolbook kernel: Inspecting /boot/System.map-2.6.24-19-generic
Dec 22 14:15:56 schoolbook kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Dec 22 14:15:56 schoolbook kernel: Symbols match kernel version 2.6.24.
Dec 22 14:15:56 schoolbook kernel: Loaded 18154 symbols from 89 modules.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Dec 22 14:15:56 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] 1143MB HIGHMEM available.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] 896MB LOWMEM available.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Zone PFN ranges:
Dec 22 14:15:56 schoolbook kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 14:15:56 schoolbook kernel: [    0.000000]   Normal       4096 ->   229376
Dec 22 14:15:56 schoolbook kernel: [    0.000000]   HighMem    229376 ->   522144
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 22 14:15:56 schoolbook kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 14:15:56 schoolbook kernel: [    0.000000]     0:        0 ->   522144
Dec 22 14:15:56 schoolbook kernel: [    0.000000] DMI present.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: RSDT 7F7A0000, 0044 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 052807 FACP1333 20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: DSDT 7F7A05B0, 5B1B (r1  A1221 A1221000        0 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 052807 APIC1333 20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 052807 OEMMCFG  20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: SLIC 7F7A0430, 0176 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0071 (r1 052807 OEMB1333 20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: HPET 7F7A60D0, 0038 (r1 052807 OEMHPET  20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: GSCI 7F7AE0C0, 2024 (r1 052807 GMCHSCI  20070528 MSFT       97)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: SSDT 7F7B09B0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 22 14:15:56 schoolbook kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 14:15:56 schoolbook kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009a000 - 000000000009b000
Dec 22 14:15:56 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
Dec 22 14:15:56 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Dec 22 14:15:56 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518065
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Kernel command line: root=UUID=63c2c38b-8e0d-4df8-b0e2-f0d556007b0e ro quiet splash ec_intr=0
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Initializing CPU#0
Dec 22 14:15:56 schoolbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 22 14:15:56 schoolbook kernel: [    0.000000] Detected 1995.167 MHz processor.
Dec 22 14:15:56 schoolbook kernel: [  199.262765] Console: colour VGA+ 80x25
Dec 22 14:15:56 schoolbook kernel: [  199.262770] console [tty0] enabled
Dec 22 14:15:56 schoolbook kernel: [  199.263089] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 22 14:15:56 schoolbook kernel: [  199.263471] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 14:15:56 schoolbook kernel: [  199.394287] Memory: 2058228k/2088576k available (2177k kernel code, 29064k reserved, 1006k data, 368k init, 1171072k highmem)
Dec 22 14:15:56 schoolbook kernel: [  199.394296] virtual kernel memory layout:
Dec 22 14:15:56 schoolbook kernel: [  199.394297]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Dec 22 14:15:56 schoolbook kernel: [  199.394299]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 14:15:56 schoolbook kernel: [  199.394300]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 22 14:15:56 schoolbook kernel: [  199.394302]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 22 14:15:56 schoolbook kernel: [  199.394303]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Dec 22 14:15:56 schoolbook kernel: [  199.394305]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Dec 22 14:15:56 schoolbook kernel: [  199.394306]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Dec 22 14:15:56 schoolbook kernel: [  199.394311] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 22 14:15:56 schoolbook kernel: [  199.394357] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 22 14:15:56 schoolbook kernel: [  199.474454] Calibrating delay using timer specific routine.. 3995.18 BogoMIPS (lpj=7990362)
Dec 22 14:15:56 schoolbook kernel: [  199.474480] Security Framework initialized
Dec 22 14:15:56 schoolbook kernel: [  199.474487] SELinux:  Disabled at boot.
Dec 22 14:15:56 schoolbook kernel: [  199.474503] AppArmor: AppArmor initialized
Dec 22 14:15:56 schoolbook kernel: [  199.474509] Failure registering capabilities with primary security module.
Dec 22 14:15:56 schoolbook kernel: [  199.474519] Mount-cache hash table entries: 512
Dec 22 14:15:56 schoolbook kernel: [  199.474668] Initializing cgroup subsys ns
Dec 22 14:15:56 schoolbook kernel: [  199.474674] Initializing cgroup subsys cpuacct
Dec 22 14:15:56 schoolbook kernel: [  199.474698] monitor/mwait feature present.
Dec 22 14:15:56 schoolbook kernel: [  199.474700] using mwait in idle threads.
Dec 22 14:15:56 schoolbook kernel: [  199.474705] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:15:56 schoolbook kernel: [  199.474708] CPU: L2 cache: 4096K
Dec 22 14:15:56 schoolbook kernel: [  199.474711] CPU: Physical Processor ID: 0
Dec 22 14:15:56 schoolbook kernel: [  199.474714] CPU: Processor Core ID: 0
Dec 22 14:15:56 schoolbook kernel: [  199.474729] Compat vDSO mapped to ffffe000.
Dec 22 14:15:56 schoolbook kernel: [  199.474745] Checking 'hlt' instruction... OK.
Dec 22 14:15:56 schoolbook kernel: [  199.490961] SMP alternatives: switching to UP code
Dec 22 14:15:56 schoolbook kernel: [  199.493157] Early unpacking initramfs... done
Dec 22 14:15:56 schoolbook kernel: [  199.993519] ACPI: Core revision 20070126
Dec 22 14:15:56 schoolbook kernel: [  199.993576] ACPI: Looking for DSDT in initramfs... successfully read 23336 bytes from /DSDT.aml.
Dec 22 14:15:56 schoolbook kernel: [  199.993603] ACPI: Table DSDT replaced by host OS
Dec 22 14:15:56 schoolbook kernel: [  199.993607] ACPI: DSDT 00000000, 5B28 (r1  A1221 A1221000        0 INTL 20061109)
Dec 22 14:15:56 schoolbook kernel: [  199.993614] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:15:56 schoolbook kernel: [  199.997616] SMP alternatives: switching to SMP code
Dec 22 14:15:56 schoolbook kernel: [  199.998542] Booting processor 1/1 eip 3000
Dec 22 14:15:56 schoolbook kernel: [  200.009191] Initializing CPU#1
Dec 22 14:15:56 schoolbook kernel: [  200.086105] Calibrating delay using timer specific routine.. 3990.01 BogoMIPS (lpj=7980032)
Dec 22 14:15:56 schoolbook kernel: [  200.086121] monitor/mwait feature present.
Dec 22 14:15:56 schoolbook kernel: [  200.086125] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:15:56 schoolbook kernel: [  200.086127] CPU: L2 cache: 4096K
Dec 22 14:15:56 schoolbook kernel: [  200.086130] CPU: Physical Processor ID: 0
Dec 22 14:15:56 schoolbook kernel: [  200.086132] CPU: Processor Core ID: 1
Dec 22 14:15:56 schoolbook kernel: [  200.087139] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:15:56 schoolbook kernel: [  200.087166] Total of 2 processors activated (7985.19 BogoMIPS).
Dec 22 14:15:56 schoolbook kernel: [  200.087361] ENABLING IO-APIC IRQs
Dec 22 14:15:56 schoolbook kernel: [  200.087561] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 22 14:15:56 schoolbook kernel: [  200.234162] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 22 14:15:56 schoolbook kernel: [  200.254173] Brought up 2 CPUs
Dec 22 14:15:56 schoolbook kernel: [  200.254497] net_namespace: 64 bytes
Dec 22 14:15:56 schoolbook kernel: [  200.254512] Booting paravirtualized kernel on bare hardware
Dec 22 14:15:56 schoolbook kernel: [  200.255137] Time: 21:15:15  Date: 12/22/08
Dec 22 14:15:56 schoolbook kernel: [  200.255171] NET: Registered protocol family 16
Dec 22 14:15:56 schoolbook kernel: [  200.255420] EISA bus registered
Dec 22 14:15:56 schoolbook kernel: [  200.255426] ACPI: bus type pci registered
Dec 22 14:15:56 schoolbook kernel: [  200.255735] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 22 14:15:56 schoolbook kernel: [  200.255738] PCI: Using configuration type 1
Dec 22 14:15:56 schoolbook kernel: [  200.255770] Setting up standard PCI resources
Dec 22 14:15:56 schoolbook kernel: [  200.271451] ACPI: Interpreter enabled
Dec 22 14:15:56 schoolbook kernel: [  200.271455] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 14:15:56 schoolbook kernel: [  200.271477] ACPI: Using IOAPIC for interrupt routing
Dec 22 14:15:56 schoolbook kernel: [  200.271840] Error attaching device data
Dec 22 14:15:56 schoolbook kernel: [  200.271896] Error attaching device data
Dec 22 14:15:56 schoolbook kernel: [  200.274084] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 22 14:15:56 schoolbook kernel: [  200.280209] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 22 14:15:56 schoolbook kernel: [  200.280213] ACPI: EC: driver started in interrupt mode
Dec 22 14:15:56 schoolbook kernel: [  200.280362] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 22 14:15:56 schoolbook kernel: [  200.281546] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 22 14:15:56 schoolbook kernel: [  200.281552] PCI quirk: region 0500-053f claimed by ICH6 GPIO
Dec 22 14:15:56 schoolbook kernel: [  200.283132] PCI: Transparent bridge - 0000:00:1e.0
Dec 22 14:15:56 schoolbook kernel: [  200.304937] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305113] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305285] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305456] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305627] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305798] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 22 14:15:56 schoolbook kernel: [  200.305969] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.306149] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec 22 14:15:56 schoolbook kernel: [  200.306344] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 22 14:15:56 schoolbook kernel: [  200.306383] pnp: PnP ACPI init
Dec 22 14:15:56 schoolbook kernel: [  200.306393] ACPI: bus type pnp registered
Dec 22 14:15:56 schoolbook kernel: [  200.309352] pnp: PnP ACPI: found 13 devices
Dec 22 14:15:56 schoolbook kernel: [  200.309355] ACPI: ACPI bus type pnp unregistered
Dec 22 14:15:56 schoolbook kernel: [  200.309360] PnPBIOS: Disabled by ACPI PNP
Dec 22 14:15:56 schoolbook kernel: [  200.309644] PCI: Using ACPI for IRQ routing
Dec 22 14:15:56 schoolbook kernel: [  200.309648] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 22 14:15:56 schoolbook kernel: [  200.357978] NET: Registered protocol family 8
Dec 22 14:15:56 schoolbook kernel: [  200.357981] NET: Registered protocol family 20
Dec 22 14:15:56 schoolbook kernel: [  200.358024] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 22 14:15:56 schoolbook kernel: [  200.358030] hpet0: 3 64-bit timers, 14318180 Hz
Dec 22 14:15:56 schoolbook kernel: [  200.359072] AppArmor: AppArmor Filesystem Enabled
Dec 22 14:15:56 schoolbook kernel: [  200.361959] Time: tsc clocksource has been installed.
Dec 22 14:15:56 schoolbook kernel: [  200.373951] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373964] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373968] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373972] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373975] system 00:08: ioport range 0x500-0x53f has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373979] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373983] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373987] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.373996] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374000] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374008] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374016] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374020] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374024] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374028] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.374032] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 22 14:15:56 schoolbook kernel: [  200.404561] PCI: Bridge: 0000:00:1c.0
Dec 22 14:15:56 schoolbook kernel: [  200.404565]   IO window: e000-efff
Dec 22 14:15:56 schoolbook kernel: [  200.404573]   MEM window: fe000000-febfffff
Dec 22 14:15:56 schoolbook kernel: [  200.404579]   PREFETCH window: fa000000-fcffffff
Dec 22 14:15:56 schoolbook kernel: [  200.404587] PCI: Bridge: 0000:00:1c.1
Dec 22 14:15:56 schoolbook kernel: [  200.404591]   IO window: d000-dfff
Dec 22 14:15:56 schoolbook kernel: [  200.404598]   MEM window: fdf00000-fdffffff
Dec 22 14:15:56 schoolbook kernel: [  200.404603]   PREFETCH window: disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.404611] PCI: Bridge: 0000:00:1c.2
Dec 22 14:15:56 schoolbook kernel: [  200.404613]   IO window: disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.404620]   MEM window: fde00000-fdefffff
Dec 22 14:15:56 schoolbook kernel: [  200.404625]   PREFETCH window: disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.404633] PCI: Bridge: 0000:00:1e.0
Dec 22 14:15:56 schoolbook kernel: [  200.404635]   IO window: disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.404642]   MEM window: fdd00000-fddfffff
Dec 22 14:15:56 schoolbook kernel: [  200.404647]   PREFETCH window: disabled.
Dec 22 14:15:56 schoolbook kernel: [  200.404684] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:15:56 schoolbook kernel: [  200.404723] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Dec 22 14:15:56 schoolbook kernel: [  200.404760] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:15:56 schoolbook kernel: [  200.404800] NET: Registered protocol family 2
Dec 22 14:15:56 schoolbook kernel: [  200.441947] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 14:15:56 schoolbook kernel: [  200.442239] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 22 14:15:56 schoolbook kernel: [  200.442789] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 22 14:15:56 schoolbook kernel: [  200.443034] TCP: Hash tables configured (established 131072 bind 65536)
Dec 22 14:15:56 schoolbook kernel: [  200.443037] TCP reno registered
Dec 22 14:15:56 schoolbook kernel: [  200.454020] checking if image is initramfs... it is
Dec 22 14:15:56 schoolbook kernel: [  201.439258] Freeing initrd memory: 7744k freed
Dec 22 14:15:56 schoolbook kernel: [  201.440965] audit: initializing netlink socket (disabled)
Dec 22 14:15:56 schoolbook kernel: [  201.440981] audit(1229980515.920:1): initialized
Dec 22 14:15:56 schoolbook kernel: [  201.441246] highmem bounce pool size: 64 pages
Dec 22 14:15:56 schoolbook kernel: [  201.443873] VFS: Disk quotas dquot_6.5.1
Dec 22 14:15:56 schoolbook kernel: [  201.443972] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 14:15:56 schoolbook kernel: [  201.444139] io scheduler noop registered
Dec 22 14:15:56 schoolbook kernel: [  201.444142] io scheduler anticipatory registered
Dec 22 14:15:56 schoolbook kernel: [  201.444144] io scheduler deadline registered
Dec 22 14:15:56 schoolbook kernel: [  201.444160] io scheduler cfq registered (default)
Dec 22 14:15:56 schoolbook kernel: [  201.444524] assign_interrupt_mode Found MSI capability
Dec 22 14:15:56 schoolbook kernel: [  201.444826] assign_interrupt_mode Found MSI capability
Dec 22 14:15:56 schoolbook kernel: [  201.445121] assign_interrupt_mode Found MSI capability
Dec 22 14:15:56 schoolbook kernel: [  201.445581] isapnp: Scanning for PnP cards...
Dec 22 14:15:56 schoolbook kernel: [  201.799569] isapnp: No Plug & Play device found
Dec 22 14:15:56 schoolbook kernel: [  201.832963] Real Time Clock Driver v1.12ac
Dec 22 14:15:56 schoolbook kernel: [  201.833232] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 22 14:15:56 schoolbook kernel: [  201.834835] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 22 14:15:56 schoolbook kernel: [  201.834921] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 22 14:15:56 schoolbook kernel: [  201.835052] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 22 14:15:56 schoolbook kernel: [  201.835430] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 22 14:15:56 schoolbook kernel: [  201.835514] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 14:15:56 schoolbook kernel: [  201.835520] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 22 14:15:56 schoolbook kernel: [  201.835523] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 22 14:15:56 schoolbook kernel: [  201.835526] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 22 14:15:56 schoolbook kernel: [  201.835530] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 22 14:15:56 schoolbook kernel: [  201.865282] mice: PS/2 mouse device common for all mice
Dec 22 14:15:56 schoolbook kernel: [  201.865422] EISA: Probing bus 0 at eisa.0
Dec 22 14:15:56 schoolbook kernel: [  201.865467] EISA: Detected 0 cards.
Dec 22 14:15:56 schoolbook kernel: [  201.865471] cpuidle: using governor ladder
Dec 22 14:15:56 schoolbook kernel: [  201.865473] cpuidle: using governor menu
Dec 22 14:15:56 schoolbook kernel: [  201.865571] NET: Registered protocol family 1
Dec 22 14:15:56 schoolbook kernel: [  201.865607] Using IPI No-Shortcut mode
Dec 22 14:15:56 schoolbook kernel: [  201.865639] registered taskstats version 1
Dec 22 14:15:56 schoolbook kernel: [  201.865784]   Magic number: 4:638:298
Dec 22 14:15:56 schoolbook kernel: [  201.865794]   hash matches device ttywf
Dec 22 14:15:56 schoolbook kernel: [  201.865842] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 22 14:15:56 schoolbook kernel: [  201.865845] EDD information not available.
Dec 22 14:15:56 schoolbook kernel: [  201.866066] Freeing unused kernel memory: 368k freed
Dec 22 14:15:56 schoolbook kernel: [  201.868457] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 22 14:15:56 schoolbook kernel: [  203.216406] fuse init (API version 7.9)
Dec 22 14:15:56 schoolbook kernel: [  203.246719] ACPI: SSDT 7F7B01C0, 0297 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [  203.247015] ACPI: SSDT 7F7B04F0, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [  203.247627] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:15:56 schoolbook kernel: [  203.247926] ACPI: SSDT 7F7B00F0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [  203.248201] ACPI: SSDT 7F7B0460, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Dec 22 14:15:56 schoolbook kernel: [  203.248953] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:15:56 schoolbook kernel: [  203.251556] ACPI: Thermal Zone [THRM] (64 C)
Dec 22 14:15:56 schoolbook kernel: [  203.560325] usbcore: registered new interface driver usbfs
Dec 22 14:15:56 schoolbook kernel: [  203.560356] usbcore: registered new interface driver hub
Dec 22 14:15:56 schoolbook kernel: [  203.560408] usbcore: registered new device driver usb
Dec 22 14:15:56 schoolbook kernel: [  203.568675] USB Universal Host Controller Interface driver v3.0
Dec 22 14:15:56 schoolbook kernel: [  203.568731] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:15:56 schoolbook kernel: [  203.568750] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  203.568973] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 22 14:15:56 schoolbook kernel: [  203.569011] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Dec 22 14:15:56 schoolbook kernel: [  203.569195] usb usb1: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  203.569227] hub 1-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  203.569233] hub 1-0:1.0: 2 ports detected
Dec 22 14:15:56 schoolbook kernel: [  203.672310] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Dec 22 14:15:56 schoolbook kernel: [  203.672328] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  203.672356] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 22 14:15:56 schoolbook kernel: [  203.672391] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000b880
Dec 22 14:15:56 schoolbook kernel: [  203.672539] usb usb2: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  203.672570] hub 2-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  203.672577] hub 2-0:1.0: 2 ports detected
Dec 22 14:15:56 schoolbook kernel: [  203.776312] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:15:56 schoolbook kernel: [  203.776334] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  203.776366] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Dec 22 14:15:56 schoolbook kernel: [  203.780277] ehci_hcd 0000:00:1a.7: debug port 1
Dec 22 14:15:56 schoolbook kernel: [  203.780298] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdcff000
Dec 22 14:15:56 schoolbook kernel: [  203.793145] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:15:56 schoolbook kernel: [  203.793285] usb usb3: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  203.793316] hub 3-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  203.793323] hub 3-0:1.0: 4 ports detected
Dec 22 14:15:56 schoolbook kernel: [  203.898042] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:15:56 schoolbook kernel: [  203.898063] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  203.898096] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Dec 22 14:15:56 schoolbook kernel: [  203.898131] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bc00
Dec 22 14:15:56 schoolbook kernel: [  203.898279] usb usb4: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  203.898310] hub 4-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  203.898317] hub 4-0:1.0: 2 ports detected
Dec 22 14:15:56 schoolbook kernel: [  203.920373] SCSI subsystem initialized
Dec 22 14:15:56 schoolbook kernel: [  204.004147] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:15:56 schoolbook kernel: [  204.004167] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  204.004196] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Dec 22 14:15:56 schoolbook kernel: [  204.004231] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c000
Dec 22 14:15:56 schoolbook kernel: [  204.004382] usb usb5: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  204.004417] hub 5-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  204.004423] hub 5-0:1.0: 2 ports detected
Dec 22 14:15:56 schoolbook kernel: [  204.108106] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:15:56 schoolbook kernel: [  204.108125] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  204.108155] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Dec 22 14:15:56 schoolbook kernel: [  204.108185] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c080
Dec 22 14:15:56 schoolbook kernel: [  204.108333] usb usb6: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  204.108366] hub 6-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  204.108372] hub 6-0:1.0: 2 ports detected
Dec 22 14:15:56 schoolbook kernel: [  204.212184] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:15:56 schoolbook kernel: [  204.212203] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 22 14:15:56 schoolbook kernel: [  204.212233] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Dec 22 14:15:56 schoolbook kernel: [  204.216141] ehci_hcd 0000:00:1d.7: debug port 1
Dec 22 14:15:56 schoolbook kernel: [  204.216157] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfdcff400
Dec 22 14:15:56 schoolbook kernel: [  204.231941] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:15:56 schoolbook kernel: [  204.232086] usb usb7: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  204.232119] hub 7-0:1.0: USB hub found
Dec 22 14:15:56 schoolbook kernel: [  204.232126] hub 7-0:1.0: 6 ports detected
Dec 22 14:15:56 schoolbook kernel: [  204.336083] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 22 14:15:56 schoolbook kernel: [  204.336112] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 22 14:15:56 schoolbook kernel: [  204.336559] eth0: RTL8168b/8111b at 0xf882a000, 00:19:db:3c:e3:55, XID 38000000 IRQ 220
Dec 22 14:15:56 schoolbook kernel: [  204.342234] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:15:56 schoolbook kernel: [  204.411846] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 22 14:15:56 schoolbook kernel: [  204.618158] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  205.015570] Clocksource tsc unstable (delta = -11368009325 ns)
Dec 22 14:15:56 schoolbook kernel: [  205.019563] Time: hpet clocksource has been installed.
Dec 22 14:15:56 schoolbook kernel: [  205.044629] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Dec 22 14:15:56 schoolbook kernel: [  205.044635] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
Dec 22 14:15:56 schoolbook kernel: [  205.044914] scsi0 : ahci
Dec 22 14:15:56 schoolbook kernel: [  205.045217] scsi1 : ahci
Dec 22 14:15:56 schoolbook kernel: [  205.045417] scsi2 : ahci
Dec 22 14:15:56 schoolbook kernel: [  205.045514] ata1: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff900 irq 219
Dec 22 14:15:56 schoolbook kernel: [  205.045525] ata2: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff980 irq 219
Dec 22 14:15:56 schoolbook kernel: [  205.045529] ata3: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcffa00 irq 219
Dec 22 14:15:56 schoolbook kernel: [  205.047667] usb 6-1: new full speed USB device using uhci_hcd and address 2
Dec 22 14:15:56 schoolbook kernel: [  205.066630] usb 6-1: configuration #1 chosen from 1 choice
Dec 22 14:15:56 schoolbook kernel: [  205.189535] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 14:15:56 schoolbook kernel: [  205.190451] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
Dec 22 14:15:56 schoolbook kernel: [  205.190455] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Dec 22 14:15:56 schoolbook kernel: [  205.191557] ata1.00: configured for UDMA/100
Dec 22 14:15:56 schoolbook kernel: [  205.218567] ata2: SATA link down (SStatus 0 SControl 300)
Dec 22 14:15:56 schoolbook kernel: [  205.244865] ata3: SATA link down (SStatus 0 SControl 300)
Dec 22 14:15:56 schoolbook kernel: [  205.245116] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Dec 22 14:15:56 schoolbook kernel: [  205.245574] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:15:56 schoolbook kernel: [  205.245720] scsi3 : ata_piix
Dec 22 14:15:56 schoolbook kernel: [  205.245926] scsi4 : ata_piix
Dec 22 14:15:56 schoolbook kernel: [  205.247474] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 22 14:15:56 schoolbook kernel: [  205.247479] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 22 14:15:56 schoolbook kernel: [  205.256411] Driver 'sd' needs updating - please use bus_type methods
Dec 22 14:15:56 schoolbook kernel: [  205.258707] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:15:56 schoolbook kernel: [  205.258756] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:15:56 schoolbook kernel: [  205.258844] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:15:56 schoolbook kernel: [  205.258975] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:15:56 schoolbook kernel: [  205.259019] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:15:56 schoolbook kernel: [  205.259098] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:15:56 schoolbook kernel: [  205.259103]  sda:<6>ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WA03, max UDMA/33
Dec 22 14:15:56 schoolbook kernel: [  205.670670]  sda1 sda2 < sda5 >
Dec 22 14:15:56 schoolbook kernel: [  205.700395] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 14:15:56 schoolbook kernel: [  205.706215] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 14:15:56 schoolbook kernel: [  205.730568] ata4.00: configured for UDMA/33
Dec 22 14:15:56 schoolbook kernel: [  205.734266] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WA03 PQ: 0 ANSI: 5
Dec 22 14:15:56 schoolbook kernel: [  205.734366] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 22 14:15:56 schoolbook kernel: [  205.748733] Driver 'sr' needs updating - please use bus_type methods
Dec 22 14:15:56 schoolbook kernel: [  205.765860] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 22 14:15:56 schoolbook kernel: [  205.765865] Uniform CD-ROM driver Revision: 3.20
Dec 22 14:15:56 schoolbook kernel: [  205.949366] Attempting manual resume
Dec 22 14:15:56 schoolbook kernel: [  205.996807] kjournald starting.  Commit interval 5 seconds
Dec 22 14:15:56 schoolbook kernel: [  205.996838] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 14:15:56 schoolbook kernel: [  219.391742] input: PC Speaker as /devices/platform/pcspkr/input/input2
Dec 22 14:15:56 schoolbook kernel: [  219.488339] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 14:15:56 schoolbook kernel: [  219.535061] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 14:15:56 schoolbook kernel: [  219.602719] iTCO_vendor_support: vendor-support=0
Dec 22 14:15:56 schoolbook kernel: [  219.635095] Linux agpgart interface v0.102
Dec 22 14:15:56 schoolbook kernel: [  219.711953] input: Power Button (FF) as /devices/virtual/input/input3
Dec 22 14:15:56 schoolbook kernel: [  219.734838] ACPI: Power Button (FF) [PWRF]
Dec 22 14:15:56 schoolbook kernel: [  219.734957] input: Lid Switch as /devices/virtual/input/input4
Dec 22 14:15:56 schoolbook kernel: [  219.748377] ACPI: Lid Switch [LID0]
Dec 22 14:15:56 schoolbook kernel: [  219.748500] input: Power Button (CM) as /devices/virtual/input/input5
Dec 22 14:15:56 schoolbook kernel: [  219.758848] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 22 14:15:56 schoolbook kernel: [  219.758941] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
Dec 22 14:15:56 schoolbook kernel: [  219.758990] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 22 14:15:56 schoolbook kernel: [  219.780256] ACPI: Power Button (CM) [PWRB]
Dec 22 14:15:56 schoolbook kernel: [  219.877814] agpgart: Detected an Intel 965GM Chipset.
Dec 22 14:15:56 schoolbook kernel: [  219.880595] agpgart: Detected 7676K stolen memory.
Dec 22 14:15:56 schoolbook kernel: [  219.895491] agpgart: AGP aperture is 256M @ 0xd0000000
Dec 22 14:15:56 schoolbook kernel: [  220.285548] sdhci: Secure Digital Host Controller Interface driver
Dec 22 14:15:56 schoolbook kernel: [  220.285553] sdhci: Copyright(c) Pierre Ossman
Dec 22 14:15:56 schoolbook kernel: [  220.285604] sdhci: SDHCI controller found at 0000:01:04.1 [1524:0750] (rev 0)
Dec 22 14:15:56 schoolbook kernel: [  220.285632] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:15:56 schoolbook kernel: [  220.285706] mmc0: SDHCI at 0xfddff400 irq 16 DMA
Dec 22 14:15:56 schoolbook kernel: [  220.285719] sdhci: SDHCI controller found at 0000:01:04.3 [1524:0751] (rev 0)
Dec 22 14:15:56 schoolbook kernel: [  220.285740] ACPI: PCI Interrupt 0000:01:04.3[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:15:56 schoolbook kernel: [  220.285754] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 22 14:15:56 schoolbook kernel: [  220.285796] mmc1: SDHCI at 0xfddffc00 irq 16 DMA
Dec 22 14:15:56 schoolbook kernel: [  220.502592] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
Dec 22 14:15:56 schoolbook kernel: [  220.570350] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 22 14:15:56 schoolbook kernel: [  220.793674] ACPI: AC Adapter [ADP1] (on-line)
Dec 22 14:15:56 schoolbook kernel: [  221.024736] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec 22 14:15:56 schoolbook kernel: [  221.056317] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Dec 22 14:15:56 schoolbook kernel: [  221.056322] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Dec 22 14:15:56 schoolbook kernel: [  221.056442] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:15:56 schoolbook kernel: [  221.056491] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 22 14:15:56 schoolbook kernel: [  221.056724] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Dec 22 14:15:56 schoolbook kernel: [  221.104040] ACPI: Battery Slot [BAT1] (battery present)
Dec 22 14:15:56 schoolbook kernel: [  221.113560] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 22
Dec 22 14:15:56 schoolbook kernel: [  221.157464] Bluetooth: Core ver 2.11
Dec 22 14:15:56 schoolbook kernel: [  221.157666] NET: Registered protocol family 31
Dec 22 14:15:56 schoolbook kernel: [  221.157669] Bluetooth: HCI device and connection manager initialized
Dec 22 14:15:56 schoolbook kernel: [  221.157674] Bluetooth: HCI socket layer initialized
Dec 22 14:15:56 schoolbook kernel: [  221.186931] Bluetooth: HCI USB driver ver 2.9
Dec 22 14:15:56 schoolbook kernel: [  221.189271] usbcore: registered new interface driver hci_usb
Dec 22 14:15:56 schoolbook kernel: [  222.375858] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 22 14:15:56 schoolbook kernel: [  222.673753] udev: renamed network interface wlan0 to eth1
Dec 22 14:15:56 schoolbook kernel: [  222.694015] lp: driver loaded but no devices found
Dec 22 14:15:56 schoolbook kernel: [  222.717043] snd-bt-sco revision 1.19 $
Dec 22 14:15:56 schoolbook kernel: [  222.717068] snd-bt-sco: snd-bt-scod thread starting
Dec 22 14:15:56 schoolbook kernel: [  223.206931] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Dec 22 14:15:56 schoolbook kernel: [  223.671021] EXT3 FS on sda1, internal journal
Dec 22 14:15:56 schoolbook kernel: [  223.914135] device-mapper: uevent: version 1.0.3
Dec 22 14:15:56 schoolbook kernel: [  223.914171] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Dec 22 14:15:56 schoolbook kernel: [  225.110135] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:15:56 schoolbook kernel: [  226.485762] No dock devices found.
Dec 22 14:15:59 schoolbook kernel: [  229.272555] NET: Registered protocol family 10
Dec 22 14:15:59 schoolbook kernel: [  229.272767] lo: Disabled Privacy Extensions
Dec 22 14:15:59 schoolbook kernel: [  229.867528] ppdev: user-space parallel port driver
Dec 22 14:15:59 schoolbook kernel: [  229.894073] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:15:59 schoolbook kernel: [  229.894077] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:15:59 schoolbook kernel: [  229.895335] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:15:59 schoolbook kernel: [  229.895338] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:16:00 schoolbook kernel: [  230.400066] audit(1229980560.402:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5543 profile="/usr/sbin/cupsd" namespace="default"
Dec 22 14:16:00 schoolbook kernel: [  230.454756] apm: BIOS not found.
Dec 22 14:16:00 schoolbook kernel: [  230.777674] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:00 schoolbook kernel: [  230.777678] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:00 schoolbook kernel: [  230.778939] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:00 schoolbook kernel: [  230.778942] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:01 schoolbook kernel: [  231.371459] [drm] Initialized drm 1.1.0 20060810
Dec 22 14:16:01 schoolbook kernel: [  231.373338] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:16:01 schoolbook kernel: [  231.373388] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 22 14:16:01 schoolbook kernel: [  231.685974] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:16:01 schoolbook kernel: [  231.685979] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:16:01 schoolbook kernel: [  231.687235] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:16:01 schoolbook kernel: [  231.687238] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:16:02 schoolbook kernel: [  232.358252] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:02 schoolbook kernel: [  232.358258] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:02 schoolbook kernel: [  232.359511] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:02 schoolbook kernel: [  232.359515] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:06 schoolbook dhcdbd: Started up.
Dec 22 14:16:08 schoolbook kernel: [  237.421405] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 14:16:08 schoolbook kernel: [  237.516320] r8169: eth0: link down
Dec 22 14:16:08 schoolbook kernel: [  237.520643] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 22 14:16:09 schoolbook kernel: [  238.052588] Bluetooth: L2CAP ver 2.9
Dec 22 14:16:09 schoolbook kernel: [  238.052595] Bluetooth: L2CAP socket layer initialized
Dec 22 14:16:09 schoolbook kernel: [  238.159248] Bluetooth: RFCOMM socket layer initialized
Dec 22 14:16:09 schoolbook kernel: [  238.159270] Bluetooth: RFCOMM TTY layer initialized
Dec 22 14:16:09 schoolbook kernel: [  238.159274] Bluetooth: RFCOMM ver 1.8
Dec 22 14:16:09 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 22 14:16:12 schoolbook kernel: [  241.550802] vmmon: module license 'unspecified' taints kernel.
Dec 22 14:16:13 schoolbook kernel: [  242.166279] bridge-eth1: already up
Dec 22 14:16:13 schoolbook kernel: [  242.174188] bridge-eth0: already up
Dec 22 14:16:20 schoolbook kernel: [  247.022478] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:16:20 schoolbook kernel: [  247.022489] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:16:20 schoolbook kernel: [  247.023735] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:16:20 schoolbook kernel: [  247.023742] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:16:21 schoolbook kernel: [  247.729156] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:21 schoolbook kernel: [  247.729160] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:21 schoolbook kernel: [  247.730420] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:16:21 schoolbook kernel: [  247.730422] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:16:38 schoolbook kernel: [  253.126412] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:16:39 schoolbook kernel: [  253.243813] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 14:16:40 schoolbook exiting on signal 15
Dec 22 14:18:17 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 22 14:18:17 schoolbook kernel: Inspecting /boot/System.map-2.6.24-19-generic
Dec 22 14:18:17 schoolbook kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Dec 22 14:18:17 schoolbook kernel: Symbols match kernel version 2.6.24.
Dec 22 14:18:17 schoolbook kernel: Loaded 17952 symbols from 88 modules.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Dec 22 14:18:17 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] 1143MB HIGHMEM available.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] 896MB LOWMEM available.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Zone PFN ranges:
Dec 22 14:18:17 schoolbook kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 14:18:17 schoolbook kernel: [    0.000000]   Normal       4096 ->   229376
Dec 22 14:18:17 schoolbook kernel: [    0.000000]   HighMem    229376 ->   522144
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 22 14:18:17 schoolbook kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 14:18:17 schoolbook kernel: [    0.000000]     0:        0 ->   522144
Dec 22 14:18:17 schoolbook kernel: [    0.000000] DMI present.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: RSDT 7F7A0000, 0044 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 052807 FACP1333 20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: DSDT 7F7A05B0, 5B1B (r1  A1221 A1221000        0 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 052807 APIC1333 20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 052807 OEMMCFG  20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: SLIC 7F7A0430, 0176 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0071 (r1 052807 OEMB1333 20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: HPET 7F7A60D0, 0038 (r1 052807 OEMHPET  20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: GSCI 7F7AE0C0, 2024 (r1 052807 GMCHSCI  20070528 MSFT       97)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: SSDT 7F7B09B0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 22 14:18:17 schoolbook kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 14:18:17 schoolbook kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009a000 - 000000000009b000
Dec 22 14:18:17 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
Dec 22 14:18:17 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Dec 22 14:18:17 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518065
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Kernel command line: root=UUID=63c2c38b-8e0d-4df8-b0e2-f0d556007b0e ro quiet splash ec_intr=0
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Initializing CPU#0
Dec 22 14:18:17 schoolbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 22 14:18:17 schoolbook kernel: [    0.000000] Detected 1995.061 MHz processor.
Dec 22 14:18:17 schoolbook kernel: [   18.868661] Console: colour VGA+ 80x25
Dec 22 14:18:17 schoolbook kernel: [   18.868666] console [tty0] enabled
Dec 22 14:18:17 schoolbook kernel: [   18.868987] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 22 14:18:17 schoolbook kernel: [   18.869368] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 14:18:17 schoolbook kernel: [   18.999361] Memory: 2058228k/2088576k available (2177k kernel code, 29064k reserved, 1006k data, 368k init, 1171072k highmem)
Dec 22 14:18:17 schoolbook kernel: [   18.999370] virtual kernel memory layout:
Dec 22 14:18:17 schoolbook kernel: [   18.999372]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Dec 22 14:18:17 schoolbook kernel: [   18.999373]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 14:18:17 schoolbook kernel: [   18.999375]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 22 14:18:17 schoolbook kernel: [   18.999376]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 22 14:18:17 schoolbook kernel: [   18.999377]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Dec 22 14:18:17 schoolbook kernel: [   18.999379]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Dec 22 14:18:17 schoolbook kernel: [   18.999380]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Dec 22 14:18:17 schoolbook kernel: [   18.999385] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 22 14:18:17 schoolbook kernel: [   18.999432] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 22 14:18:17 schoolbook kernel: [   19.079530] Calibrating delay using timer specific routine.. 3995.20 BogoMIPS (lpj=7990401)
Dec 22 14:18:17 schoolbook kernel: [   19.079557] Security Framework initialized
Dec 22 14:18:17 schoolbook kernel: [   19.079564] SELinux:  Disabled at boot.
Dec 22 14:18:17 schoolbook kernel: [   19.079580] AppArmor: AppArmor initialized
Dec 22 14:18:17 schoolbook kernel: [   19.079585] Failure registering capabilities with primary security module.
Dec 22 14:18:17 schoolbook kernel: [   19.079595] Mount-cache hash table entries: 512
Dec 22 14:18:17 schoolbook kernel: [   19.079742] Initializing cgroup subsys ns
Dec 22 14:18:17 schoolbook kernel: [   19.079748] Initializing cgroup subsys cpuacct
Dec 22 14:18:17 schoolbook kernel: [   19.079771] monitor/mwait feature present.
Dec 22 14:18:17 schoolbook kernel: [   19.079773] using mwait in idle threads.
Dec 22 14:18:17 schoolbook kernel: [   19.079778] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:18:17 schoolbook kernel: [   19.079781] CPU: L2 cache: 4096K
Dec 22 14:18:17 schoolbook kernel: [   19.079784] CPU: Physical Processor ID: 0
Dec 22 14:18:17 schoolbook kernel: [   19.079787] CPU: Processor Core ID: 0
Dec 22 14:18:17 schoolbook kernel: [   19.079802] Compat vDSO mapped to ffffe000.
Dec 22 14:18:17 schoolbook kernel: [   19.079817] Checking 'hlt' instruction... OK.
Dec 22 14:18:17 schoolbook kernel: [   19.096037] SMP alternatives: switching to UP code
Dec 22 14:18:17 schoolbook kernel: [   19.098235] Early unpacking initramfs... done
Dec 22 14:18:17 schoolbook kernel: [   19.598714] ACPI: Core revision 20070126
Dec 22 14:18:17 schoolbook kernel: [   19.598771] ACPI: Looking for DSDT in initramfs... successfully read 23336 bytes from /DSDT.aml.
Dec 22 14:18:17 schoolbook kernel: [   19.598797] ACPI: Table DSDT replaced by host OS
Dec 22 14:18:17 schoolbook kernel: [   19.598801] ACPI: DSDT 00000000, 5B28 (r1  A1221 A1221000        0 INTL 20061109)
Dec 22 14:18:17 schoolbook kernel: [   19.598808] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:18:17 schoolbook kernel: [   19.602782] SMP alternatives: switching to SMP code
Dec 22 14:18:17 schoolbook kernel: [   19.603711] Booting processor 1/1 eip 3000
Dec 22 14:18:17 schoolbook kernel: [   19.614359] Initializing CPU#1
Dec 22 14:18:17 schoolbook kernel: [   19.691181] Calibrating delay using timer specific routine.. 3990.02 BogoMIPS (lpj=7980057)
Dec 22 14:18:17 schoolbook kernel: [   19.691197] monitor/mwait feature present.
Dec 22 14:18:17 schoolbook kernel: [   19.691201] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 14:18:17 schoolbook kernel: [   19.691203] CPU: L2 cache: 4096K
Dec 22 14:18:17 schoolbook kernel: [   19.691206] CPU: Physical Processor ID: 0
Dec 22 14:18:17 schoolbook kernel: [   19.691208] CPU: Processor Core ID: 1
Dec 22 14:18:17 schoolbook kernel: [   19.692213] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 14:18:17 schoolbook kernel: [   19.692241] Total of 2 processors activated (7985.22 BogoMIPS).
Dec 22 14:18:17 schoolbook kernel: [   19.692435] ENABLING IO-APIC IRQs
Dec 22 14:18:17 schoolbook kernel: [   19.692636] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 22 14:18:17 schoolbook kernel: [   19.839237] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 22 14:18:17 schoolbook kernel: [   19.859245] Brought up 2 CPUs
Dec 22 14:18:17 schoolbook kernel: [   19.859571] net_namespace: 64 bytes
Dec 22 14:18:17 schoolbook kernel: [   19.859586] Booting paravirtualized kernel on bare hardware
Dec 22 14:18:17 schoolbook kernel: [   19.860212] Time: 21:17:29  Date: 12/22/08
Dec 22 14:18:17 schoolbook kernel: [   19.860246] NET: Registered protocol family 16
Dec 22 14:18:17 schoolbook kernel: [   19.860494] EISA bus registered
Dec 22 14:18:17 schoolbook kernel: [   19.860500] ACPI: bus type pci registered
Dec 22 14:18:17 schoolbook kernel: [   19.860809] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 22 14:18:17 schoolbook kernel: [   19.860812] PCI: Using configuration type 1
Dec 22 14:18:17 schoolbook kernel: [   19.860844] Setting up standard PCI resources
Dec 22 14:18:17 schoolbook kernel: [   19.875984] ACPI: Interpreter enabled
Dec 22 14:18:17 schoolbook kernel: [   19.875988] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 14:18:17 schoolbook kernel: [   19.876010] ACPI: Using IOAPIC for interrupt routing
Dec 22 14:18:17 schoolbook kernel: [   19.876373] Error attaching device data
Dec 22 14:18:17 schoolbook kernel: [   19.876429] Error attaching device data
Dec 22 14:18:17 schoolbook kernel: [   19.878613] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 22 14:18:17 schoolbook kernel: [   19.885243] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 22 14:18:17 schoolbook kernel: [   19.885247] ACPI: EC: driver started in interrupt mode
Dec 22 14:18:17 schoolbook kernel: [   19.885397] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 22 14:18:17 schoolbook kernel: [   19.886579] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 22 14:18:17 schoolbook kernel: [   19.886585] PCI quirk: region 0500-053f claimed by ICH6 GPIO
Dec 22 14:18:17 schoolbook kernel: [   19.888036] PCI: Transparent bridge - 0000:00:1e.0
Dec 22 14:18:17 schoolbook kernel: [   19.909727] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.909907] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.910080] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.910251] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.910423] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.910594] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 22 14:18:17 schoolbook kernel: [   19.910765] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 22 14:18:17 schoolbook kernel: [   19.910937] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec 22 14:18:17 schoolbook kernel: [   19.911136] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 22 14:18:17 schoolbook kernel: [   19.911176] pnp: PnP ACPI init
Dec 22 14:18:17 schoolbook kernel: [   19.911186] ACPI: bus type pnp registered
Dec 22 14:18:17 schoolbook kernel: [   19.914187] pnp: PnP ACPI: found 13 devices
Dec 22 14:18:17 schoolbook kernel: [   19.914190] ACPI: ACPI bus type pnp unregistered
Dec 22 14:18:17 schoolbook kernel: [   19.914195] PnPBIOS: Disabled by ACPI PNP
Dec 22 14:18:17 schoolbook kernel: [   19.914477] PCI: Using ACPI for IRQ routing
Dec 22 14:18:17 schoolbook kernel: [   19.914481] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 22 14:18:17 schoolbook kernel: [   19.959056] NET: Registered protocol family 8
Dec 22 14:18:17 schoolbook kernel: [   19.959059] NET: Registered protocol family 20
Dec 22 14:18:17 schoolbook kernel: [   19.959101] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 22 14:18:17 schoolbook kernel: [   19.959107] hpet0: 3 64-bit timers, 14318180 Hz
Dec 22 14:18:17 schoolbook kernel: [   19.960149] AppArmor: AppArmor Filesystem Enabled
Dec 22 14:18:17 schoolbook kernel: [   19.963037] Time: tsc clocksource has been installed.
Dec 22 14:18:17 schoolbook kernel: [   19.975028] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975041] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975045] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975049] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975052] system 00:08: ioport range 0x500-0x53f has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975056] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975060] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975064] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975073] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975077] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975085] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975093] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975097] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975101] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975105] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   19.975109] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 22 14:18:17 schoolbook kernel: [   20.005635] PCI: Bridge: 0000:00:1c.0
Dec 22 14:18:17 schoolbook kernel: [   20.005640]   IO window: e000-efff
Dec 22 14:18:17 schoolbook kernel: [   20.005647]   MEM window: fe000000-febfffff
Dec 22 14:18:17 schoolbook kernel: [   20.005653]   PREFETCH window: fa000000-fcffffff
Dec 22 14:18:17 schoolbook kernel: [   20.005661] PCI: Bridge: 0000:00:1c.1
Dec 22 14:18:17 schoolbook kernel: [   20.005662]   IO window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005669]   MEM window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005675]   PREFETCH window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005682] PCI: Bridge: 0000:00:1c.2
Dec 22 14:18:17 schoolbook kernel: [   20.005684]   IO window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005691]   MEM window: fdf00000-fdffffff
Dec 22 14:18:17 schoolbook kernel: [   20.005696]   PREFETCH window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005704] PCI: Bridge: 0000:00:1e.0
Dec 22 14:18:17 schoolbook kernel: [   20.005705]   IO window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005712]   MEM window: fde00000-fdefffff
Dec 22 14:18:17 schoolbook kernel: [   20.005718]   PREFETCH window: disabled.
Dec 22 14:18:17 schoolbook kernel: [   20.005755] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:18:17 schoolbook kernel: [   20.005794] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Dec 22 14:18:17 schoolbook kernel: [   20.005832] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:18:17 schoolbook kernel: [   20.005871] NET: Registered protocol family 2
Dec 22 14:18:17 schoolbook kernel: [   20.043021] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 14:18:17 schoolbook kernel: [   20.043312] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 22 14:18:17 schoolbook kernel: [   20.043862] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 22 14:18:17 schoolbook kernel: [   20.044108] TCP: Hash tables configured (established 131072 bind 65536)
Dec 22 14:18:17 schoolbook kernel: [   20.044111] TCP reno registered
Dec 22 14:18:17 schoolbook kernel: [   20.055093] checking if image is initramfs... it is
Dec 22 14:18:17 schoolbook kernel: [   21.041126] Freeing initrd memory: 7744k freed
Dec 22 14:18:17 schoolbook kernel: [   21.042096] audit: initializing netlink socket (disabled)
Dec 22 14:18:17 schoolbook kernel: [   21.042112] audit(1229980648.916:1): initialized
Dec 22 14:18:17 schoolbook kernel: [   21.042375] highmem bounce pool size: 64 pages
Dec 22 14:18:17 schoolbook kernel: [   21.045005] VFS: Disk quotas dquot_6.5.1
Dec 22 14:18:17 schoolbook kernel: [   21.045104] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 14:18:17 schoolbook kernel: [   21.045271] io scheduler noop registered
Dec 22 14:18:17 schoolbook kernel: [   21.045275] io scheduler anticipatory registered
Dec 22 14:18:17 schoolbook kernel: [   21.045277] io scheduler deadline registered
Dec 22 14:18:17 schoolbook kernel: [   21.045292] io scheduler cfq registered (default)
Dec 22 14:18:17 schoolbook kernel: [   21.045651] assign_interrupt_mode Found MSI capability
Dec 22 14:18:17 schoolbook kernel: [   21.045950] assign_interrupt_mode Found MSI capability
Dec 22 14:18:17 schoolbook kernel: [   21.046207] assign_interrupt_mode Found MSI capability
Dec 22 14:18:17 schoolbook kernel: [   21.046651] isapnp: Scanning for PnP cards...
Dec 22 14:18:17 schoolbook kernel: [   21.401042] isapnp: No Plug & Play device found
Dec 22 14:18:17 schoolbook kernel: [   21.434530] Real Time Clock Driver v1.12ac
Dec 22 14:18:17 schoolbook kernel: [   21.434799] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 22 14:18:17 schoolbook kernel: [   21.436352] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 22 14:18:17 schoolbook kernel: [   21.436435] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 22 14:18:17 schoolbook kernel: [   21.436562] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 22 14:18:17 schoolbook kernel: [   21.436941] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 22 14:18:17 schoolbook kernel: [   21.437024] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 14:18:17 schoolbook kernel: [   21.437029] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 22 14:18:17 schoolbook kernel: [   21.437033] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 22 14:18:17 schoolbook kernel: [   21.437036] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 22 14:18:17 schoolbook kernel: [   21.437039] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 22 14:18:17 schoolbook kernel: [   21.458244] mice: PS/2 mouse device common for all mice
Dec 22 14:18:17 schoolbook kernel: [   21.458385] EISA: Probing bus 0 at eisa.0
Dec 22 14:18:17 schoolbook kernel: [   21.458429] EISA: Detected 0 cards.
Dec 22 14:18:17 schoolbook kernel: [   21.458432] cpuidle: using governor ladder
Dec 22 14:18:17 schoolbook kernel: [   21.458435] cpuidle: using governor menu
Dec 22 14:18:17 schoolbook kernel: [   21.458533] NET: Registered protocol family 1
Dec 22 14:18:17 schoolbook kernel: [   21.458566] Using IPI No-Shortcut mode
Dec 22 14:18:17 schoolbook kernel: [   21.458600] registered taskstats version 1
Dec 22 14:18:17 schoolbook kernel: [   21.458739]   Magic number: 4:638:298
Dec 22 14:18:17 schoolbook kernel: [   21.458750]   hash matches device ttywf
Dec 22 14:18:17 schoolbook kernel: [   21.458796] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 22 14:18:17 schoolbook kernel: [   21.458798] EDD information not available.
Dec 22 14:18:17 schoolbook kernel: [   21.459025] Freeing unused kernel memory: 368k freed
Dec 22 14:18:17 schoolbook kernel: [   21.461421] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 22 14:18:17 schoolbook kernel: [   22.759521] fuse init (API version 7.9)
Dec 22 14:18:17 schoolbook kernel: [   22.790361] ACPI: SSDT 7F7B01C0, 0297 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [   22.790664] ACPI: SSDT 7F7B04F0, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [   22.791306] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:18:17 schoolbook kernel: [   22.791620] ACPI: SSDT 7F7B00F0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [   22.791901] ACPI: SSDT 7F7B0460, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Dec 22 14:18:17 schoolbook kernel: [   22.792595] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 14:18:17 schoolbook kernel: [   22.795078] ACPI: Thermal Zone [THRM] (59 C)
Dec 22 14:18:17 schoolbook kernel: [   22.978369] usbcore: registered new interface driver usbfs
Dec 22 14:18:17 schoolbook kernel: [   22.978400] usbcore: registered new interface driver hub
Dec 22 14:18:17 schoolbook kernel: [   22.986292] usbcore: registered new device driver usb
Dec 22 14:18:17 schoolbook kernel: [   22.988364] USB Universal Host Controller Interface driver v3.0
Dec 22 14:18:17 schoolbook kernel: [   22.988420] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:18:17 schoolbook kernel: [   22.988439] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   22.988651] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 22 14:18:17 schoolbook kernel: [   22.988687] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c800
Dec 22 14:18:17 schoolbook kernel: [   22.988856] usb usb1: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   22.988888] hub 1-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   22.988894] hub 1-0:1.0: 2 ports detected
Dec 22 14:18:17 schoolbook kernel: [   23.090329] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Dec 22 14:18:17 schoolbook kernel: [   23.090348] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   23.090380] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 22 14:18:17 schoolbook kernel: [   23.090415] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000c880
Dec 22 14:18:17 schoolbook kernel: [   23.090560] usb usb2: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   23.090591] hub 2-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   23.090597] hub 2-0:1.0: 2 ports detected
Dec 22 14:18:17 schoolbook kernel: [   23.194278] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:18:17 schoolbook kernel: [   23.194296] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   23.194324] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Dec 22 14:18:17 schoolbook kernel: [   23.194360] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000cc00
Dec 22 14:18:17 schoolbook kernel: [   23.194510] usb usb3: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   23.194542] hub 3-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   23.194548] hub 3-0:1.0: 2 ports detected
Dec 22 14:18:17 schoolbook kernel: [   23.298316] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:18:17 schoolbook kernel: [   23.298333] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   23.298362] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Dec 22 14:18:17 schoolbook kernel: [   23.298396] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000d000
Dec 22 14:18:17 schoolbook kernel: [   23.298539] usb usb4: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   23.298570] hub 4-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   23.298577] hub 4-0:1.0: 2 ports detected
Dec 22 14:18:17 schoolbook kernel: [   23.330079] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 22 14:18:17 schoolbook kernel: [   23.402140] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:18:17 schoolbook kernel: [   23.402160] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   23.402191] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Dec 22 14:18:17 schoolbook kernel: [   23.402226] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d080
Dec 22 14:18:17 schoolbook kernel: [   23.402371] usb usb5: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   23.402404] hub 5-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   23.402410] hub 5-0:1.0: 2 ports detected
Dec 22 14:18:17 schoolbook kernel: [   23.409339] SCSI subsystem initialized
Dec 22 14:18:17 schoolbook kernel: [   23.506143] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:18:17 schoolbook kernel: [   23.552536] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   23.793835] usb 5-1: new full speed USB device using uhci_hcd and address 2
Dec 22 14:18:17 schoolbook kernel: [   23.972092] usb 5-1: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   24.508464] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Dec 22 14:18:17 schoolbook kernel: [   24.508470] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
Dec 22 14:18:17 schoolbook kernel: [   24.508757] scsi0 : ahci
Dec 22 14:18:17 schoolbook kernel: [   24.509125] scsi1 : ahci
Dec 22 14:18:17 schoolbook kernel: [   24.509350] scsi2 : ahci
Dec 22 14:18:17 schoolbook kernel: [   24.509457] ata1: SATA max UDMA/133 abar m2048@0xfddff800 port 0xfddff900 irq 220
Dec 22 14:18:17 schoolbook kernel: [   24.509463] ata2: SATA max UDMA/133 abar m2048@0xfddff800 port 0xfddff980 irq 220
Dec 22 14:18:17 schoolbook kernel: [   24.509467] ata3: SATA max UDMA/133 abar m2048@0xfddff800 port 0xfddffa00 irq 220
Dec 22 14:18:17 schoolbook kernel: [   24.620344] Clocksource tsc unstable (delta = -18916525281 ns)
Dec 22 14:18:17 schoolbook kernel: [   24.624535] Time: hpet clocksource has been installed.
Dec 22 14:18:17 schoolbook kernel: [   24.713208] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 14:18:17 schoolbook kernel: [   24.714139] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
Dec 22 14:18:17 schoolbook kernel: [   24.714143] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Dec 22 14:18:17 schoolbook kernel: [   24.715250] ata1.00: configured for UDMA/100
Dec 22 14:18:17 schoolbook kernel: [   24.742873] ata2: SATA link down (SStatus 0 SControl 300)
Dec 22 14:18:17 schoolbook kernel: [   24.771817] ata3: SATA link down (SStatus 0 SControl 300)
Dec 22 14:18:17 schoolbook kernel: [   24.772052] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Dec 22 14:18:17 schoolbook kernel: [   24.772507] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:18:17 schoolbook kernel: [   24.772528] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   24.772565] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Dec 22 14:18:17 schoolbook kernel: [   24.776498] ehci_hcd 0000:00:1a.7: debug port 1
Dec 22 14:18:17 schoolbook kernel: [   24.776514] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfddff000
Dec 22 14:18:17 schoolbook kernel: [   24.787136] Driver 'sd' needs updating - please use bus_type methods
Dec 22 14:18:17 schoolbook kernel: [   24.787217] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:18:17 schoolbook kernel: [   24.787232] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:18:17 schoolbook kernel: [   24.787258] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:18:17 schoolbook kernel: [   24.787315] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 14:18:17 schoolbook kernel: [   24.787328] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 14:18:17 schoolbook kernel: [   24.787353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 14:18:17 schoolbook kernel: [   24.787358]  sda:<6>ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:18:17 schoolbook kernel: [   24.791840] usb usb6: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   24.791873] hub 6-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   24.791881] hub 6-0:1.0: 4 ports detected
Dec 22 14:18:17 schoolbook kernel: [   24.894725] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 14:18:17 schoolbook kernel: [   24.894743] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 22 14:18:17 schoolbook kernel: [   24.894772] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Dec 22 14:18:17 schoolbook kernel: [   24.898685] ehci_hcd 0000:00:1d.7: debug port 1
Dec 22 14:18:17 schoolbook kernel: [   24.898701] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfddff400
Dec 22 14:18:17 schoolbook kernel: [   24.911611] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 14:18:17 schoolbook kernel: [   24.911732] usb usb7: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   24.911763] hub 7-0:1.0: USB hub found
Dec 22 14:18:17 schoolbook kernel: [   24.911769] hub 7-0:1.0: 6 ports detected
Dec 22 14:18:17 schoolbook kernel: [   25.019406] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Dec 22 14:18:17 schoolbook kernel: [   25.019838] scsi3 : ata_piix
Dec 22 14:18:17 schoolbook kernel: [   25.019902] scsi4 : ata_piix
Dec 22 14:18:17 schoolbook kernel: [   25.021449] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 22 14:18:17 schoolbook kernel: [   25.021453] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 22 14:18:17 schoolbook kernel: [   25.134522] usb 1-2: USB disconnect, address 2
Dec 22 14:18:17 schoolbook kernel: [   25.219781]  sda1 sda2 < sda5 >
Dec 22 14:18:17 schoolbook kernel: [   25.249493] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 14:18:17 schoolbook kernel: [   25.255804] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 14:18:17 schoolbook kernel: [   25.338795] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WA03, max UDMA/33
Dec 22 14:18:17 schoolbook kernel: [   25.378332] usb 1-2: new full speed USB device using uhci_hcd and address 3
Dec 22 14:18:17 schoolbook kernel: [   25.472134] ata4.00: configured for UDMA/33
Dec 22 14:18:17 schoolbook kernel: [   25.474632] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WA03 PQ: 0 ANSI: 5
Dec 22 14:18:17 schoolbook kernel: [   25.474751] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 22 14:18:17 schoolbook kernel: [   25.487550] Driver 'sr' needs updating - please use bus_type methods
Dec 22 14:18:17 schoolbook kernel: [   25.496849] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 22 14:18:17 schoolbook kernel: [   25.496855] Uniform CD-ROM driver Revision: 3.20
Dec 22 14:18:17 schoolbook kernel: [   25.542126] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   25.544247] usb 5-1: USB disconnect, address 2
Dec 22 14:18:17 schoolbook kernel: [   25.596816] Attempting manual resume
Dec 22 14:18:17 schoolbook kernel: [   25.646300] kjournald starting.  Commit interval 5 seconds
Dec 22 14:18:17 schoolbook kernel: [   25.646325] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 14:18:17 schoolbook kernel: [   26.145479] usb 5-1: new full speed USB device using uhci_hcd and address 3
Dec 22 14:18:17 schoolbook kernel: [   26.324469] usb 5-1: configuration #1 chosen from 1 choice
Dec 22 14:18:17 schoolbook kernel: [   39.063504] input: PC Speaker as /devices/platform/pcspkr/input/input2
Dec 22 14:18:17 schoolbook kernel: [   39.202010] iTCO_vendor_support: vendor-support=0
Dec 22 14:18:17 schoolbook kernel: [   39.237110] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 22 14:18:17 schoolbook kernel: [   39.237209] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
Dec 22 14:18:17 schoolbook kernel: [   39.237256] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 22 14:18:17 schoolbook kernel: [   39.281331] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 14:18:17 schoolbook kernel: [   39.305634] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 14:18:17 schoolbook kernel: [   39.336477] Linux agpgart interface v0.102
Dec 22 14:18:17 schoolbook kernel: [   39.409173] agpgart: Detected an Intel 965GM Chipset.
Dec 22 14:18:17 schoolbook kernel: [   39.411985] agpgart: Detected 7676K stolen memory.
Dec 22 14:18:17 schoolbook kernel: [   39.426810] agpgart: AGP aperture is 256M @ 0xd0000000
Dec 22 14:18:17 schoolbook kernel: [   39.497603] input: Power Button (FF) as /devices/virtual/input/input3
Dec 22 14:18:17 schoolbook kernel: [   39.604885] ACPI: Power Button (FF) [PWRF]
Dec 22 14:18:17 schoolbook kernel: [   39.604978] input: Lid Switch as /devices/virtual/input/input4
Dec 22 14:18:17 schoolbook kernel: [   39.629308] ACPI: Lid Switch [LID0]
Dec 22 14:18:17 schoolbook kernel: [   39.629408] input: Power Button (CM) as /devices/virtual/input/input5
Dec 22 14:18:17 schoolbook kernel: [   39.663831] ACPI: Power Button (CM) [PWRB]
Dec 22 14:18:17 schoolbook kernel: [   39.808451] sdhci: Secure Digital Host Controller Interface driver
Dec 22 14:18:17 schoolbook kernel: [   39.808455] sdhci: Copyright(c) Pierre Ossman
Dec 22 14:18:17 schoolbook kernel: [   39.808504] sdhci: SDHCI controller found at 0000:01:04.1 [1524:0750] (rev 0)
Dec 22 14:18:17 schoolbook kernel: [   39.808529] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:18:17 schoolbook kernel: [   39.808603] mmc0: SDHCI at 0xfdeff400 irq 16 DMA
Dec 22 14:18:17 schoolbook kernel: [   39.808616] sdhci: SDHCI controller found at 0000:01:04.3 [1524:0751] (rev 0)
Dec 22 14:18:17 schoolbook kernel: [   39.808637] ACPI: PCI Interrupt 0000:01:04.3[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:18:17 schoolbook kernel: [   39.808651] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 22 14:18:17 schoolbook kernel: [   39.808690] mmc1: SDHCI at 0xfdeffc00 irq 16 DMA
Dec 22 14:18:17 schoolbook kernel: [   40.106463] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
Dec 22 14:18:17 schoolbook kernel: [   40.159569] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 22 14:18:17 schoolbook kernel: [   40.281521] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 22
Dec 22 14:18:17 schoolbook kernel: [   40.400342] ACPI: AC Adapter [ADP1] (on-line)
Dec 22 14:18:17 schoolbook kernel: [   40.498456] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec 22 14:18:17 schoolbook kernel: [   40.529122] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Dec 22 14:18:17 schoolbook kernel: [   40.532345] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Dec 22 14:18:17 schoolbook kernel: [   40.532349] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Dec 22 14:18:17 schoolbook kernel: [   40.532470] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 22 14:18:17 schoolbook kernel: [   40.532520] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 22 14:18:17 schoolbook kernel: [   40.684320] ACPI: Battery Slot [BAT1] (battery present)
Dec 22 14:18:17 schoolbook kernel: [   40.775035] Bluetooth: Core ver 2.11
Dec 22 14:18:17 schoolbook kernel: [   40.775239] NET: Registered protocol family 31
Dec 22 14:18:17 schoolbook kernel: [   40.775242] Bluetooth: HCI device and connection manager initialized
Dec 22 14:18:17 schoolbook kernel: [   40.775247] Bluetooth: HCI socket layer initialized
Dec 22 14:18:17 schoolbook kernel: [   40.814402] Bluetooth: HCI USB driver ver 2.9
Dec 22 14:18:17 schoolbook kernel: [   40.816438] usbcore: registered new interface driver hci_usb
Dec 22 14:18:17 schoolbook kernel: [   42.109363] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 22 14:18:17 schoolbook kernel: [   42.319253] udev: renamed network interface wlan0 to eth1
Dec 22 14:18:17 schoolbook kernel: [   42.360880] lp: driver loaded but no devices found
Dec 22 14:18:17 schoolbook kernel: [   42.413952] snd-bt-sco revision 1.19 $
Dec 22 14:18:17 schoolbook kernel: [   42.413978] snd-bt-sco: snd-bt-scod thread starting
Dec 22 14:18:17 schoolbook kernel: [   42.844496] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Dec 22 14:18:17 schoolbook kernel: [   43.290130] EXT3 FS on sda1, internal journal
Dec 22 14:18:17 schoolbook kernel: [   43.523541] device-mapper: uevent: version 1.0.3
Dec 22 14:18:17 schoolbook kernel: [   43.523578] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Dec 22 14:18:17 schoolbook kernel: [   44.769664] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 14:18:17 schoolbook kernel: [   46.237273] No dock devices found.
Dec 22 14:18:20 schoolbook kernel: [   49.093124] NET: Registered protocol family 10
Dec 22 14:18:20 schoolbook kernel: [   49.093323] lo: Disabled Privacy Extensions
Dec 22 14:18:21 schoolbook kernel: [   49.634010] ppdev: user-space parallel port driver
Dec 22 14:18:21 schoolbook kernel: [   49.831766] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:18:21 schoolbook kernel: [   49.831771] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:18:21 schoolbook kernel: [   49.833026] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:18:21 schoolbook kernel: [   49.833030] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:18:21 schoolbook kernel: [   50.209656] audit(1229980701.677:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5547 profile="/usr/sbin/cupsd" namespace="default"
Dec 22 14:18:21 schoolbook kernel: [   50.264397] apm: BIOS not found.
Dec 22 14:18:22 schoolbook kernel: [   50.720468] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:18:22 schoolbook kernel: [   50.720472] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:18:22 schoolbook kernel: [   50.721731] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:18:22 schoolbook kernel: [   50.721734] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:18:22 schoolbook kernel: [   51.131431] [drm] Initialized drm 1.1.0 20060810
Dec 22 14:18:22 schoolbook kernel: [   51.243077] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 14:18:22 schoolbook kernel: [   51.243128] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 22 14:18:22 schoolbook kernel: [   51.511086] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:18:22 schoolbook kernel: [   51.511092] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:18:23 schoolbook kernel: [   51.512346] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:18:23 schoolbook kernel: [   51.512350] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:18:23 schoolbook kernel: [   52.212685] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:18:23 schoolbook kernel: [   52.212693] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:18:23 schoolbook kernel: [   52.213950] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 14:18:23 schoolbook kernel: [   52.213956] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 14:18:28 schoolbook dhcdbd: Started up.
Dec 22 14:18:30 schoolbook kernel: [   57.522216] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 14:18:30 schoolbook kernel: [   58.037404] Bluetooth: L2CAP ver 2.9
Dec 22 14:18:30 schoolbook kernel: [   58.037412] Bluetooth: L2CAP socket layer initialized
Dec 22 14:18:30 schoolbook kernel: [   58.349515] Bluetooth: RFCOMM socket layer initialized
Dec 22 14:18:30 schoolbook kernel: [   58.349535] Bluetooth: RFCOMM TTY layer initialized
Dec 22 14:18:30 schoolbook kernel: [   58.349538] Bluetooth: RFCOMM ver 1.8
Dec 22 14:18:33 schoolbook kernel: [   61.281946] vmmon: module license 'unspecified' taints kernel.
Dec 22 14:18:34 schoolbook kernel: [   61.964122] bridge-eth1: already up
Dec 22 14:19:38 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 22 14:19:41 schoolbook kernel: [  118.029932] NET: Registered protocol family 17
Dec 22 14:19:43 schoolbook kernel: [  119.918482] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec 22 14:19:50 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Dec 22 14:19:50 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec 22 14:19:50 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec 22 14:19:50 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Dec 22 14:20:01 schoolbook kernel: [  136.448504] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:20:01 schoolbook kernel: [  136.448513] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:20:01 schoolbook kernel: [  136.449764] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 14:20:01 schoolbook kernel: [  136.449770] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 14:38:18 schoolbook -- MARK --
Dec 22 14:58:18 schoolbook -- MARK --
Dec 22 15:04:33 schoolbook kernel: [ 2456.752594] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 15:04:33 schoolbook kernel: [ 2456.752607] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 15:04:33 schoolbook kernel: [ 2456.753847] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 15:04:33 schoolbook kernel: [ 2456.753855] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 15:18:18 schoolbook -- MARK --
Dec 22 15:27:59 schoolbook kernel: [ 3281.635981] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Dec 22 15:27:59 schoolbook kernel: [ 3281.635997] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Dec 22 15:27:59 schoolbook kernel: [ 3281.636020] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7c4a108), AE_TIME
Dec 22 15:27:59 schoolbook kernel: [ 3281.636106] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f7c4a0a8), AE_TIME
Dec 22 15:27:59 schoolbook kernel: [ 3281.636181] ACPI Exception (battery-0356): AE_TIME, Evaluating _BST [20070126]
Dec 22 15:30:29 schoolbook kernel: [ 3366.245531] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Dec 22 15:30:29 schoolbook kernel: [ 3366.245549] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Dec 22 15:30:29 schoolbook kernel: [ 3366.245571] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7c4a108), AE_TIME
Dec 22 15:30:29 schoolbook kernel: [ 3366.245661] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f7c4a0a8), AE_TIME
Dec 22 15:30:29 schoolbook kernel: [ 3366.245736] ACPI Exception (battery-0356): AE_TIME, Evaluating _BST [20070126]
Dec 22 15:58:18 schoolbook -- MARK --
Dec 22 16:18:18 schoolbook -- MARK --
Dec 22 16:21:15 schoolbook kernel: [ 4898.755572] atkbd.c: Unknown key pressed (translated set 2, code 0xf2 on isa0060/serio0).
Dec 22 16:21:15 schoolbook kernel: [ 4898.755585] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
Dec 22 16:21:15 schoolbook kernel: [ 4898.756823] atkbd.c: Unknown key released (translated set 2, code 0xf2 on isa0060/serio0).
Dec 22 16:21:15 schoolbook kernel: [ 4898.756831] atkbd.c: Use 'setkeycodes e072 <keycode>' to make it known.
Dec 22 16:21:19 schoolbook kernel: [ 4900.657694] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
Dec 22 16:21:19 schoolbook kernel: [ 4900.657704] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec 22 16:21:19 schoolbook kernel: [ 4900.658930] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
Dec 22 16:21:19 schoolbook kernel: [ 4900.658937] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
Dec 22 16:21:21 schoolbook kernel: [ 4901.353058] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 16:21:21 schoolbook kernel: [ 4901.353069] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 16:21:21 schoolbook kernel: [ 4901.354298] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 16:21:21 schoolbook kernel: [ 4901.354308] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 16:24:18 schoolbook kernel: [ 4933.847547] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 16:24:19 schoolbook kernel: [ 4933.847557] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 16:24:19 schoolbook kernel: [ 4933.848783] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 16:24:19 schoolbook kernel: [ 4933.848790] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 16:38:18 schoolbook -- MARK --
Dec 22 16:58:18 schoolbook -- MARK --
Dec 22 17:18:18 schoolbook -- MARK --
Dec 22 17:38:18 schoolbook -- MARK --
Dec 22 17:58:18 schoolbook -- MARK --
Dec 22 18:18:18 schoolbook -- MARK --
Dec 22 18:38:18 schoolbook -- MARK --
Dec 22 18:58:18 schoolbook -- MARK --
Dec 22 19:18:18 schoolbook -- MARK --
Dec 22 19:38:18 schoolbook -- MARK --
Dec 22 19:41:16 schoolbook kernel: [ 7480.305705] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 19:41:16 schoolbook kernel: [ 7480.305715] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 19:41:16 schoolbook kernel: [ 7480.306937] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 19:41:16 schoolbook kernel: [ 7480.306945] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 19:58:18 schoolbook -- MARK --
Dec 22 20:15:49 schoolbook kernel: [ 8008.431250] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 20:15:49 schoolbook kernel: [ 8008.431260] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 20:15:49 schoolbook kernel: [ 8008.432909] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 20:15:49 schoolbook kernel: [ 8008.432917] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 20:38:18 schoolbook -- MARK --
Dec 22 20:45:29 schoolbook kernel: [ 8478.131107] ACPI Exception (evregion-0420): AE_TIME, Returned by Handler for [EmbeddedControl] [20070126]
Dec 22 20:45:29 schoolbook kernel: [ 8478.131124] ACPI Exception (dswexec-0462): AE_TIME, While resolving operands for [OpcodeName unavailable] [20070126]
Dec 22 20:45:29 schoolbook kernel: [ 8478.131148] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1.UPBS] (Node f7c4a108), AE_TIME
Dec 22 20:45:29 schoolbook kernel: [ 8478.131237] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.SBRG.EC__.BAT1._BST] (Node f7c4a0a8), AE_TIME
Dec 22 20:45:29 schoolbook kernel: [ 8478.131314] ACPI Exception (battery-0356): AE_TIME, Evaluating _BST [20070126]
Dec 22 20:58:18 schoolbook -- MARK --
Dec 22 21:18:18 schoolbook -- MARK --
Dec 22 21:38:18 schoolbook -- MARK --
Dec 22 21:58:18 schoolbook -- MARK --
Dec 22 22:18:18 schoolbook -- MARK --
Dec 22 22:20:15 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 22 22:20:15 schoolbook kernel: Inspecting /boot/System.map-2.6.24-19-generic
Dec 22 22:20:15 schoolbook kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Dec 22 22:20:15 schoolbook kernel: Symbols match kernel version 2.6.24.
Dec 22 22:20:15 schoolbook kernel: Loaded 18154 symbols from 89 modules.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Dec 22 22:20:15 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] 1143MB HIGHMEM available.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] 896MB LOWMEM available.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Zone PFN ranges:
Dec 22 22:20:15 schoolbook kernel: [    0.000000]   DMA             0 ->     4096
Dec 22 22:20:15 schoolbook kernel: [    0.000000]   Normal       4096 ->   229376
Dec 22 22:20:15 schoolbook kernel: [    0.000000]   HighMem    229376 ->   522144
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 22 22:20:15 schoolbook kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 22 22:20:15 schoolbook kernel: [    0.000000]     0:        0 ->   522144
Dec 22 22:20:15 schoolbook kernel: [    0.000000] DMI present.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: RSDT 7F7A0000, 0044 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 052807 FACP1333 20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: DSDT 7F7A05B0, 5B1B (r1  A1221 A1221000        0 INTL 20051117)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 052807 APIC1333 20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 052807 OEMMCFG  20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: SLIC 7F7A0430, 0176 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0071 (r1 052807 OEMB1333 20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: HPET 7F7A60D0, 0038 (r1 052807 OEMHPET  20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: GSCI 7F7AE0C0, 2024 (r1 052807 GMCHSCI  20070528 MSFT       97)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: SSDT 7F7B09B0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 22 22:20:15 schoolbook kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 22 22:20:15 schoolbook kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009a000 - 000000000009b000
Dec 22 22:20:15 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
Dec 22 22:20:15 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Dec 22 22:20:15 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518065
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Kernel command line: root=UUID=63c2c38b-8e0d-4df8-b0e2-f0d556007b0e ro quiet splash ec_intr=0
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Initializing CPU#0
Dec 22 22:20:15 schoolbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 22 22:20:15 schoolbook kernel: [    0.000000] Detected 1995.119 MHz processor.
Dec 22 22:20:15 schoolbook kernel: [   21.171351] Console: colour VGA+ 80x25
Dec 22 22:20:15 schoolbook kernel: [   21.171356] console [tty0] enabled
Dec 22 22:20:15 schoolbook kernel: [   21.171673] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 22 22:20:15 schoolbook kernel: [   21.172054] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 22 22:20:15 schoolbook kernel: [   21.303024] Memory: 2058228k/2088576k available (2177k kernel code, 29064k reserved, 1006k data, 368k init, 1171072k highmem)
Dec 22 22:20:15 schoolbook kernel: [   21.303033] virtual kernel memory layout:
Dec 22 22:20:15 schoolbook kernel: [   21.303034]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Dec 22 22:20:15 schoolbook kernel: [   21.303036]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 22 22:20:15 schoolbook kernel: [   21.303037]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 22 22:20:15 schoolbook kernel: [   21.303039]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 22 22:20:15 schoolbook kernel: [   21.303040]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Dec 22 22:20:15 schoolbook kernel: [   21.303042]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Dec 22 22:20:15 schoolbook kernel: [   21.303043]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Dec 22 22:20:15 schoolbook kernel: [   21.303047] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 22 22:20:15 schoolbook kernel: [   21.303094] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 22 22:20:15 schoolbook kernel: [   21.383191] Calibrating delay using timer specific routine.. 3995.18 BogoMIPS (lpj=7990363)
Dec 22 22:20:15 schoolbook kernel: [   21.383217] Security Framework initialized
Dec 22 22:20:15 schoolbook kernel: [   21.383223] SELinux:  Disabled at boot.
Dec 22 22:20:15 schoolbook kernel: [   21.383240] AppArmor: AppArmor initialized
Dec 22 22:20:15 schoolbook kernel: [   21.383245] Failure registering capabilities with primary security module.
Dec 22 22:20:15 schoolbook kernel: [   21.383256] Mount-cache hash table entries: 512
Dec 22 22:20:15 schoolbook kernel: [   21.383405] Initializing cgroup subsys ns
Dec 22 22:20:15 schoolbook kernel: [   21.383411] Initializing cgroup subsys cpuacct
Dec 22 22:20:15 schoolbook kernel: [   21.383434] monitor/mwait feature present.
Dec 22 22:20:15 schoolbook kernel: [   21.383436] using mwait in idle threads.
Dec 22 22:20:15 schoolbook kernel: [   21.383442] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 22:20:15 schoolbook kernel: [   21.383445] CPU: L2 cache: 4096K
Dec 22 22:20:15 schoolbook kernel: [   21.383448] CPU: Physical Processor ID: 0
Dec 22 22:20:15 schoolbook kernel: [   21.383450] CPU: Processor Core ID: 0
Dec 22 22:20:15 schoolbook kernel: [   21.383465] Compat vDSO mapped to ffffe000.
Dec 22 22:20:15 schoolbook kernel: [   21.383481] Checking 'hlt' instruction... OK.
Dec 22 22:20:15 schoolbook kernel: [   21.399698] SMP alternatives: switching to UP code
Dec 22 22:20:15 schoolbook kernel: [   21.401894] Early unpacking initramfs... done
Dec 22 22:20:15 schoolbook kernel: [   21.902309] ACPI: Core revision 20070126
Dec 22 22:20:15 schoolbook kernel: [   21.902364] ACPI: Looking for DSDT in initramfs... successfully read 23336 bytes from /DSDT.aml.
Dec 22 22:20:15 schoolbook kernel: [   21.902391] ACPI: Table DSDT replaced by host OS
Dec 22 22:20:15 schoolbook kernel: [   21.902395] ACPI: DSDT 00000000, 5B28 (r1  A1221 A1221000        0 INTL 20061109)
Dec 22 22:20:15 schoolbook kernel: [   21.902402] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 22:20:15 schoolbook kernel: [   21.906365] SMP alternatives: switching to SMP code
Dec 22 22:20:15 schoolbook kernel: [   21.907295] Booting processor 1/1 eip 3000
Dec 22 22:20:15 schoolbook kernel: [   21.917945] Initializing CPU#1
Dec 22 22:20:15 schoolbook kernel: [   21.994842] Calibrating delay using timer specific routine.. 3990.00 BogoMIPS (lpj=7980006)
Dec 22 22:20:15 schoolbook kernel: [   21.994858] monitor/mwait feature present.
Dec 22 22:20:15 schoolbook kernel: [   21.994862] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 22 22:20:15 schoolbook kernel: [   21.994865] CPU: L2 cache: 4096K
Dec 22 22:20:15 schoolbook kernel: [   21.994867] CPU: Physical Processor ID: 0
Dec 22 22:20:15 schoolbook kernel: [   21.994869] CPU: Processor Core ID: 1
Dec 22 22:20:15 schoolbook kernel: [   21.995897] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 22 22:20:15 schoolbook kernel: [   21.995924] Total of 2 processors activated (7985.18 BogoMIPS).
Dec 22 22:20:15 schoolbook kernel: [   21.996118] ENABLING IO-APIC IRQs
Dec 22 22:20:15 schoolbook kernel: [   21.996319] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 22 22:20:15 schoolbook kernel: [   22.142901] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 22 22:20:15 schoolbook kernel: [   22.162912] Brought up 2 CPUs
Dec 22 22:20:15 schoolbook kernel: [   22.163239] net_namespace: 64 bytes
Dec 22 22:20:15 schoolbook kernel: [   22.163253] Booting paravirtualized kernel on bare hardware
Dec 22 22:20:15 schoolbook kernel: [   22.163878] Time:  5:19:22  Date: 12/23/08
Dec 22 22:20:15 schoolbook kernel: [   22.163913] NET: Registered protocol family 16
Dec 22 22:20:15 schoolbook kernel: [   22.164161] EISA bus registered
Dec 22 22:20:15 schoolbook kernel: [   22.164167] ACPI: bus type pci registered
Dec 22 22:20:15 schoolbook kernel: [   22.164476] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 22 22:20:15 schoolbook kernel: [   22.164479] PCI: Using configuration type 1
Dec 22 22:20:15 schoolbook kernel: [   22.164511] Setting up standard PCI resources
Dec 22 22:20:15 schoolbook kernel: [   22.180187] ACPI: Interpreter enabled
Dec 22 22:20:15 schoolbook kernel: [   22.180191] ACPI: (supports S0 S1 S3 S4 S5)
Dec 22 22:20:15 schoolbook kernel: [   22.180213] ACPI: Using IOAPIC for interrupt routing
Dec 22 22:20:15 schoolbook kernel: [   22.180576] Error attaching device data
Dec 22 22:20:15 schoolbook kernel: [   22.180631] Error attaching device data
Dec 22 22:20:15 schoolbook kernel: [   22.182817] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 22 22:20:15 schoolbook kernel: [   22.189765] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 22 22:20:15 schoolbook kernel: [   22.189769] ACPI: EC: driver started in interrupt mode
Dec 22 22:20:15 schoolbook kernel: [   22.189918] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 22 22:20:15 schoolbook kernel: [   22.191105] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 22 22:20:15 schoolbook kernel: [   22.191110] PCI quirk: region 0500-053f claimed by ICH6 GPIO
Dec 22 22:20:15 schoolbook kernel: [   22.192689] PCI: Transparent bridge - 0000:00:1e.0
Dec 22 22:20:15 schoolbook kernel: [   22.214479] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.214655] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.214834] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.215006] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.215177] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.215348] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 22 22:20:15 schoolbook kernel: [   22.215519] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.215691] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec 22 22:20:15 schoolbook kernel: [   22.215886] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 22 22:20:15 schoolbook kernel: [   22.215925] pnp: PnP ACPI init
Dec 22 22:20:15 schoolbook kernel: [   22.215935] ACPI: bus type pnp registered
Dec 22 22:20:15 schoolbook kernel: [   22.218958] pnp: PnP ACPI: found 13 devices
Dec 22 22:20:15 schoolbook kernel: [   22.218961] ACPI: ACPI bus type pnp unregistered
Dec 22 22:20:15 schoolbook kernel: [   22.218965] PnPBIOS: Disabled by ACPI PNP
Dec 22 22:20:15 schoolbook kernel: [   22.219268] PCI: Using ACPI for IRQ routing
Dec 22 22:20:15 schoolbook kernel: [   22.219272] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 22 22:20:15 schoolbook kernel: [   22.274703] NET: Registered protocol family 8
Dec 22 22:20:15 schoolbook kernel: [   22.274706] NET: Registered protocol family 20
Dec 22 22:20:15 schoolbook kernel: [   22.274749] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 22 22:20:15 schoolbook kernel: [   22.274755] hpet0: 3 64-bit timers, 14318180 Hz
Dec 22 22:20:15 schoolbook kernel: [   22.275796] AppArmor: AppArmor Filesystem Enabled
Dec 22 22:20:15 schoolbook kernel: [   22.278693] Time: tsc clocksource has been installed.
Dec 22 22:20:15 schoolbook kernel: [   22.294684] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294697] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294701] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294705] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294709] system 00:08: ioport range 0x500-0x53f has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294713] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294716] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294720] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294729] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294733] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294741] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294749] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294753] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294757] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294761] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.294765] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 22 22:20:15 schoolbook kernel: [   22.325313] PCI: Bridge: 0000:00:1c.0
Dec 22 22:20:15 schoolbook kernel: [   22.325318]   IO window: e000-efff
Dec 22 22:20:15 schoolbook kernel: [   22.325325]   MEM window: fe000000-febfffff
Dec 22 22:20:15 schoolbook kernel: [   22.325331]   PREFETCH window: fa000000-fcffffff
Dec 22 22:20:15 schoolbook kernel: [   22.325339] PCI: Bridge: 0000:00:1c.1
Dec 22 22:20:15 schoolbook kernel: [   22.325343]   IO window: d000-dfff
Dec 22 22:20:15 schoolbook kernel: [   22.325350]   MEM window: fdf00000-fdffffff
Dec 22 22:20:15 schoolbook kernel: [   22.325355]   PREFETCH window: disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.325362] PCI: Bridge: 0000:00:1c.2
Dec 22 22:20:15 schoolbook kernel: [   22.325364]   IO window: disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.325371]   MEM window: fde00000-fdefffff
Dec 22 22:20:15 schoolbook kernel: [   22.325377]   PREFETCH window: disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.325384] PCI: Bridge: 0000:00:1e.0
Dec 22 22:20:15 schoolbook kernel: [   22.325386]   IO window: disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.325393]   MEM window: fdd00000-fddfffff
Dec 22 22:20:15 schoolbook kernel: [   22.325398]   PREFETCH window: disabled.
Dec 22 22:20:15 schoolbook kernel: [   22.325436] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 22:20:15 schoolbook kernel: [   22.325475] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Dec 22 22:20:15 schoolbook kernel: [   22.325513] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 22:20:15 schoolbook kernel: [   22.325551] NET: Registered protocol family 2
Dec 22 22:20:15 schoolbook kernel: [   22.362677] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 22 22:20:15 schoolbook kernel: [   22.362969] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 22 22:20:15 schoolbook kernel: [   22.363519] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 22 22:20:15 schoolbook kernel: [   22.363764] TCP: Hash tables configured (established 131072 bind 65536)
Dec 22 22:20:15 schoolbook kernel: [   22.363767] TCP reno registered
Dec 22 22:20:15 schoolbook kernel: [   22.374750] checking if image is initramfs... it is
Dec 22 22:20:15 schoolbook kernel: [   23.360585] Freeing initrd memory: 7744k freed
Dec 22 22:20:15 schoolbook kernel: [   23.361556] audit: initializing netlink socket (disabled)
Dec 22 22:20:15 schoolbook kernel: [   23.361572] audit(1230009561.933:1): initialized
Dec 22 22:20:15 schoolbook kernel: [   23.361835] highmem bounce pool size: 64 pages
Dec 22 22:20:15 schoolbook kernel: [   23.364460] VFS: Disk quotas dquot_6.5.1
Dec 22 22:20:15 schoolbook kernel: [   23.364559] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 22 22:20:15 schoolbook kernel: [   23.364727] io scheduler noop registered
Dec 22 22:20:15 schoolbook kernel: [   23.364730] io scheduler anticipatory registered
Dec 22 22:20:15 schoolbook kernel: [   23.364732] io scheduler deadline registered
Dec 22 22:20:15 schoolbook kernel: [   23.364747] io scheduler cfq registered (default)
Dec 22 22:20:15 schoolbook kernel: [   23.365110] assign_interrupt_mode Found MSI capability
Dec 22 22:20:15 schoolbook kernel: [   23.365409] assign_interrupt_mode Found MSI capability
Dec 22 22:20:15 schoolbook kernel: [   23.365701] assign_interrupt_mode Found MSI capability
Dec 22 22:20:16 schoolbook kernel: [   23.366136] isapnp: Scanning for PnP cards...
Dec 22 22:20:16 schoolbook kernel: [   23.720530] isapnp: No Plug & Play device found
Dec 22 22:20:16 schoolbook kernel: [   23.754042] Real Time Clock Driver v1.12ac
Dec 22 22:20:16 schoolbook kernel: [   23.754309] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 22 22:20:16 schoolbook kernel: [   23.756260] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 22 22:20:16 schoolbook kernel: [   23.756346] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 22 22:20:16 schoolbook kernel: [   23.756474] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 22 22:20:16 schoolbook kernel: [   23.756847] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 22 22:20:16 schoolbook kernel: [   23.756928] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 22 22:20:16 schoolbook kernel: [   23.756934] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 22 22:20:16 schoolbook kernel: [   23.756937] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 22 22:20:16 schoolbook kernel: [   23.756940] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 22 22:20:16 schoolbook kernel: [   23.756944] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 22 22:20:16 schoolbook kernel: [   23.778948] mice: PS/2 mouse device common for all mice
Dec 22 22:20:16 schoolbook kernel: [   23.779091] EISA: Probing bus 0 at eisa.0
Dec 22 22:20:16 schoolbook kernel: [   23.779135] EISA: Detected 0 cards.
Dec 22 22:20:16 schoolbook kernel: [   23.779138] cpuidle: using governor ladder
Dec 22 22:20:16 schoolbook kernel: [   23.779140] cpuidle: using governor menu
Dec 22 22:20:16 schoolbook kernel: [   23.779237] NET: Registered protocol family 1
Dec 22 22:20:16 schoolbook kernel: [   23.779270] Using IPI No-Shortcut mode
Dec 22 22:20:16 schoolbook kernel: [   23.779302] registered taskstats version 1
Dec 22 22:20:16 schoolbook kernel: [   23.779447]   Magic number: 4:564:315
Dec 22 22:20:16 schoolbook kernel: [   23.779487]   hash matches device tty40
Dec 22 22:20:16 schoolbook kernel: [   23.779504] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 22 22:20:16 schoolbook kernel: [   23.779507] EDD information not available.
Dec 22 22:20:16 schoolbook kernel: [   23.779728] Freeing unused kernel memory: 368k freed
Dec 22 22:20:16 schoolbook kernel: [   23.782135] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 22 22:20:16 schoolbook kernel: [   25.119120] fuse init (API version 7.9)
Dec 22 22:20:16 schoolbook kernel: [   25.150437] ACPI: SSDT 7F7B01C0, 0297 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Dec 22 22:20:16 schoolbook kernel: [   25.150734] ACPI: SSDT 7F7B04F0, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Dec 22 22:20:16 schoolbook kernel: [   25.151349] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 22:20:16 schoolbook kernel: [   25.151648] ACPI: SSDT 7F7B00F0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Dec 22 22:20:16 schoolbook kernel: [   25.151922] ACPI: SSDT 7F7B0460, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Dec 22 22:20:16 schoolbook kernel: [   25.152669] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 22 22:20:16 schoolbook kernel: [   25.155301] ACPI: Thermal Zone [THRM] (58 C)
Dec 22 22:20:16 schoolbook kernel: [   25.619648] usbcore: registered new interface driver usbfs
Dec 22 22:20:16 schoolbook kernel: [   25.619678] usbcore: registered new interface driver hub
Dec 22 22:20:16 schoolbook kernel: [   25.619714] usbcore: registered new device driver usb
Dec 22 22:20:16 schoolbook kernel: [   25.641545] USB Universal Host Controller Interface driver v3.0
Dec 22 22:20:16 schoolbook kernel: [   25.641602] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 22:20:16 schoolbook kernel: [   25.641620] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   25.641851] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 22 22:20:16 schoolbook kernel: [   25.641887] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Dec 22 22:20:16 schoolbook kernel: [   25.642066] usb usb1: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   25.642099] hub 1-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   25.642106] hub 1-0:1.0: 2 ports detected
Dec 22 22:20:16 schoolbook kernel: [   25.744884] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Dec 22 22:20:16 schoolbook kernel: [   25.744904] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   25.744933] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 22 22:20:16 schoolbook kernel: [   25.744968] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000b880
Dec 22 22:20:16 schoolbook kernel: [   25.745112] usb usb2: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   25.745143] hub 2-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   25.745150] hub 2-0:1.0: 2 ports detected
Dec 22 22:20:16 schoolbook kernel: [   25.756443] SCSI subsystem initialized
Dec 22 22:20:16 schoolbook kernel: [   25.848829] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 22:20:16 schoolbook kernel: [   25.848847] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   25.848884] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Dec 22 22:20:16 schoolbook kernel: [   25.848918] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bc00
Dec 22 22:20:16 schoolbook kernel: [   25.849067] usb usb3: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   25.849099] hub 3-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   25.849106] hub 3-0:1.0: 2 ports detected
Dec 22 22:20:16 schoolbook kernel: [   25.952772] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Dec 22 22:20:16 schoolbook kernel: [   25.952791] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   25.952822] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Dec 22 22:20:16 schoolbook kernel: [   25.952857] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c000
Dec 22 22:20:16 schoolbook kernel: [   25.953004] usb usb4: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   25.953036] hub 4-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   25.953042] hub 4-0:1.0: 2 ports detected
Dec 22 22:20:16 schoolbook kernel: [   25.984651] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 22 22:20:16 schoolbook kernel: [   26.056734] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 22:20:16 schoolbook kernel: [   26.056751] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   26.056779] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Dec 22 22:20:16 schoolbook kernel: [   26.056814] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c080
Dec 22 22:20:16 schoolbook kernel: [   26.056962] usb usb5: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   26.056995] hub 5-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   26.057002] hub 5-0:1.0: 2 ports detected
Dec 22 22:20:16 schoolbook kernel: [   26.161475] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 22 22:20:16 schoolbook kernel: [   26.161495] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   26.161526] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Dec 22 22:20:16 schoolbook kernel: [   26.165445] ehci_hcd 0000:00:1a.7: debug port 1
Dec 22 22:20:16 schoolbook kernel: [   26.165460] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdcff000
Dec 22 22:20:16 schoolbook kernel: [   26.180563] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 22:20:16 schoolbook kernel: [   26.180705] usb usb6: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   26.180737] hub 6-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   26.180745] hub 6-0:1.0: 4 ports detected
Dec 22 22:20:16 schoolbook kernel: [   26.284623] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 22 22:20:16 schoolbook kernel: [   26.284643] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 22 22:20:16 schoolbook kernel: [   26.284673] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Dec 22 22:20:16 schoolbook kernel: [   26.288576] ehci_hcd 0000:00:1d.7: debug port 1
Dec 22 22:20:16 schoolbook kernel: [   26.288592] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfdcff400
Dec 22 22:20:16 schoolbook kernel: [   26.304494] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 22 22:20:16 schoolbook kernel: [   26.304634] usb usb7: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   26.304666] hub 7-0:1.0: USB hub found
Dec 22 22:20:16 schoolbook kernel: [   26.304672] hub 7-0:1.0: 6 ports detected
Dec 22 22:20:16 schoolbook kernel: [   26.408846] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 22 22:20:16 schoolbook kernel: [   26.408875] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 22 22:20:16 schoolbook kernel: [   26.409315] eth0: RTL8168b/8111b at 0xf882a000, 00:19:db:3c:e3:55, XID 38000000 IRQ 220
Dec 22 22:20:16 schoolbook kernel: [   26.410483] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 18
Dec 22 22:20:16 schoolbook kernel: [   26.924142] Clocksource tsc unstable (delta = -12625601231 ns)
Dec 22 22:20:16 schoolbook kernel: [   26.928136] Time: hpet clocksource has been installed.
Dec 22 22:20:16 schoolbook kernel: [   26.944880] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 22 22:20:16 schoolbook kernel: [   26.966858] usb 1-2: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   26.990607] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Dec 22 22:20:16 schoolbook kernel: [   26.990613] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
Dec 22 22:20:16 schoolbook kernel: [   26.990899] scsi0 : ahci
Dec 22 22:20:16 schoolbook kernel: [   26.991260] scsi1 : ahci
Dec 22 22:20:16 schoolbook kernel: [   26.991504] scsi2 : ahci
Dec 22 22:20:16 schoolbook kernel: [   26.991604] ata1: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff900 irq 219
Dec 22 22:20:16 schoolbook kernel: [   26.991609] ata2: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff980 irq 219
Dec 22 22:20:16 schoolbook kernel: [   26.991614] ata3: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcffa00 irq 219
Dec 22 22:20:16 schoolbook kernel: [   27.010554] usb 5-1: new full speed USB device using uhci_hcd and address 2
Dec 22 22:20:16 schoolbook kernel: [   27.028000] usb 5-1: configuration #1 chosen from 1 choice
Dec 22 22:20:16 schoolbook kernel: [   27.133600] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 22 22:20:16 schoolbook kernel: [   27.134539] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
Dec 22 22:20:16 schoolbook kernel: [   27.134543] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Dec 22 22:20:16 schoolbook kernel: [   27.135649] ata1.00: configured for UDMA/100
Dec 22 22:20:16 schoolbook kernel: [   27.161933] ata2: SATA link down (SStatus 0 SControl 300)
Dec 22 22:20:16 schoolbook kernel: [   27.188195] ata3: SATA link down (SStatus 0 SControl 300)
Dec 22 22:20:16 schoolbook kernel: [   27.188446] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Dec 22 22:20:16 schoolbook kernel: [   27.188928] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Dec 22 22:20:16 schoolbook kernel: [   27.189043] scsi3 : ata_piix
Dec 22 22:20:16 schoolbook kernel: [   27.189249] scsi4 : ata_piix
Dec 22 22:20:16 schoolbook kernel: [   27.190786] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 22 22:20:16 schoolbook kernel: [   27.190790] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 22 22:20:16 schoolbook kernel: [   27.199707] Driver 'sd' needs updating - please use bus_type methods
Dec 22 22:20:16 schoolbook kernel: [   27.201704] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 22:20:16 schoolbook kernel: [   27.201721] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 22:20:16 schoolbook kernel: [   27.201749] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 22:20:16 schoolbook kernel: [   27.201812] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 22 22:20:16 schoolbook kernel: [   27.201826] sd 0:0:0:0: [sda] Write Protect is off
Dec 22 22:20:16 schoolbook kernel: [   27.201852] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 22 22:20:16 schoolbook kernel: [   27.201857]  sda:<6>ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WA03, max UDMA/33
Dec 22 22:20:16 schoolbook kernel: [   27.617650]  sda1 sda2 < sda5 >
Dec 22 22:20:16 schoolbook kernel: [   27.636269] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 22 22:20:16 schoolbook kernel: [   27.642028] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 22 22:20:16 schoolbook kernel: [   27.677699] ata4.00: configured for UDMA/33
Dec 22 22:20:16 schoolbook kernel: [   27.681359] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WA03 PQ: 0 ANSI: 5
Dec 22 22:20:16 schoolbook kernel: [   27.681453] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 22 22:20:16 schoolbook kernel: [   27.694265] Driver 'sr' needs updating - please use bus_type methods
Dec 22 22:20:16 schoolbook kernel: [   27.711469] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 22 22:20:16 schoolbook kernel: [   27.711473] Uniform CD-ROM driver Revision: 3.20
Dec 22 22:20:16 schoolbook kernel: [   27.828332] Attempting manual resume
Dec 22 22:20:16 schoolbook kernel: [   27.847090] EXT3-fs: INFO: recovery required on readonly filesystem.
Dec 22 22:20:16 schoolbook kernel: [   27.847094] EXT3-fs: write access will be enabled during recovery.
Dec 22 22:20:16 schoolbook kernel: [   30.162750] kjournald starting.  Commit interval 5 seconds
Dec 22 22:20:16 schoolbook kernel: [   30.162785] EXT3-fs: sda1: orphan cleanup on readonly fs
Dec 22 22:20:16 schoolbook kernel: [   30.200163] EXT3-fs: sda1: 1 orphan inode deleted
Dec 22 22:20:16 schoolbook kernel: [   30.200166] EXT3-fs: recovery complete.
Dec 22 22:20:16 schoolbook kernel: [   30.214714] EXT3-fs: mounted filesystem with ordered data mode.
Dec 22 22:20:16 schoolbook kernel: [   43.296703] input: PC Speaker as /devices/platform/pcspkr/input/input2
Dec 22 22:20:16 schoolbook kernel: [   43.809412] iTCO_vendor_support: vendor-support=0
Dec 22 22:20:16 schoolbook kernel: [   43.941327] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 22 22:20:16 schoolbook kernel: [   43.941426] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
Dec 22 22:20:16 schoolbook kernel: [   43.941473] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 22 22:20:16 schoolbook kernel: [   44.014020] Linux agpgart interface v0.102
Dec 22 22:20:16 schoolbook kernel: [   44.077257] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 22 22:20:16 schoolbook kernel: [   44.103349] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 22 22:20:16 schoolbook kernel: [   44.152338] input: Power Button (FF) as /devices/virtual/input/input3
Dec 22 22:20:16 schoolbook kernel: [   44.182198] agpgart: Detected an Intel 965GM Chipset.
Dec 22 22:20:16 schoolbook kernel: [   44.184961] agpgart: Detected 7676K stolen memory.
Dec 22 22:20:16 schoolbook kernel: [   44.199696] agpgart: AGP aperture is 256M @ 0xd0000000
Dec 22 22:20:16 schoolbook kernel: [   44.222143] ACPI: Power Button (FF) [PWRF]
Dec 22 22:20:16 schoolbook kernel: [   44.222234] input: Lid Switch as /devices/virtual/input/input4
Dec 22 22:20:16 schoolbook kernel: [   44.254572] ACPI: Lid Switch [LID0]
Dec 22 22:20:16 schoolbook kernel: [   44.254665] input: Power Button (CM) as /devices/virtual/input/input5
Dec 22 22:20:16 schoolbook kernel: [   44.318059] ACPI: Power Button (CM) [PWRB]
Dec 22 22:20:16 schoolbook kernel: [   44.553423] sdhci: Unknown symbol mmc_request_done
Dec 22 22:20:16 schoolbook kernel: [   44.553578] sdhci: Unknown symbol mmc_remove_host
Dec 22 22:20:16 schoolbook kernel: [   44.553677] sdhci: Unknown symbol mmc_alloc_host
Dec 22 22:20:16 schoolbook kernel: [   44.553724] sdhci: Unknown symbol mmc_add_host
Dec 22 22:20:16 schoolbook kernel: [   44.553939] sdhci: Unknown symbol mmc_suspend_host
Dec 22 22:20:16 schoolbook kernel: [   44.554014] sdhci: Unknown symbol mmc_resume_host
Dec 22 22:20:16 schoolbook kernel: [   44.554061] sdhci: Unknown symbol mmc_free_host
Dec 22 22:20:16 schoolbook kernel: [   44.554121] sdhci: Unknown symbol mmc_detect_change
Dec 22 22:20:16 schoolbook kernel: [   44.733801] sdhci: Secure Digital Host Controller Interface driver
Dec 22 22:20:16 schoolbook kernel: [   44.733805] sdhci: Copyright(c) Pierre Ossman
Dec 22 22:20:16 schoolbook kernel: [   44.733849] sdhci: SDHCI controller found at 0000:01:04.1 [1524:0750] (rev 0)
Dec 22 22:20:16 schoolbook kernel: [   44.733875] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 22:20:16 schoolbook kernel: [   44.733948] mmc0: SDHCI at 0xfddff400 irq 16 DMA
Dec 22 22:20:16 schoolbook kernel: [   44.733960] sdhci: SDHCI controller found at 0000:01:04.3 [1524:0751] (rev 0)
Dec 22 22:20:16 schoolbook kernel: [   44.733981] ACPI: PCI Interrupt 0000:01:04.3[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 22:20:16 schoolbook kernel: [   44.733995] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 22 22:20:16 schoolbook kernel: [   44.734036] mmc1: SDHCI at 0xfddffc00 irq 16 DMA
Dec 22 22:20:16 schoolbook kernel: [   44.792532] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
Dec 22 22:20:16 schoolbook kernel: [   44.840752] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 22 22:20:16 schoolbook kernel: [   45.020741] ACPI: AC Adapter [ADP1] (on-line)
Dec 22 22:20:16 schoolbook kernel: [   45.290812] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Dec 22 22:20:16 schoolbook kernel: [   45.290817] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Dec 22 22:20:16 schoolbook kernel: [   45.290941] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 22 22:20:16 schoolbook kernel: [   45.290991] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 22 22:20:16 schoolbook kernel: [   45.301118] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec 22 22:20:16 schoolbook kernel: [   45.333520] ACPI: Battery Slot [BAT1] (battery present)
Dec 22 22:20:16 schoolbook kernel: [   45.333785] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Dec 22 22:20:16 schoolbook kernel: [   45.428498] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 22
Dec 22 22:20:16 schoolbook kernel: [   45.460149] Bluetooth: Core ver 2.11
Dec 22 22:20:16 schoolbook kernel: [   45.474225] NET: Registered protocol family 31
Dec 22 22:20:16 schoolbook kernel: [   45.474229] Bluetooth: HCI device and connection manager initialized
Dec 22 22:20:16 schoolbook kernel: [   45.474234] Bluetooth: HCI socket layer initialized
Dec 22 22:20:16 schoolbook kernel: [   45.508548] Bluetooth: HCI USB driver ver 2.9
Dec 22 22:20:16 schoolbook kernel: [   45.510710] usbcore: registered new interface driver hci_usb
Dec 22 22:20:16 schoolbook kernel: [   46.611261] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 22 22:20:16 schoolbook kernel: [   46.917704] udev: renamed network interface wlan0 to eth1
Dec 22 22:20:16 schoolbook kernel: [   46.974548] lp: driver loaded but no devices found
Dec 22 22:20:16 schoolbook kernel: [   47.007477] snd-bt-sco revision 1.19 $
Dec 22 22:20:16 schoolbook kernel: [   47.007501] snd-bt-sco: snd-bt-scod thread starting
Dec 22 22:20:16 schoolbook kernel: [   47.485669] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Dec 22 22:20:16 schoolbook kernel: [   47.848586] EXT3 FS on sda1, internal journal
Dec 22 22:20:16 schoolbook kernel: [   48.101808] device-mapper: uevent: version 1.0.3
Dec 22 22:20:16 schoolbook kernel: [   48.101846] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Dec 22 22:20:16 schoolbook kernel: [   57.956759] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 22:20:16 schoolbook kernel: [   60.172821] No dock devices found.
Dec 22 22:20:19 schoolbook kernel: [   63.469597] NET: Registered protocol family 10
Dec 22 22:20:19 schoolbook kernel: [   63.469802] lo: Disabled Privacy Extensions
Dec 22 22:20:19 schoolbook kernel: [   63.740236] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:20:19 schoolbook kernel: [   63.740240] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:20:19 schoolbook kernel: [   63.741498] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:20:19 schoolbook kernel: [   63.741500] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:20:19 schoolbook kernel: [   63.919004] ppdev: user-space parallel port driver
Dec 22 22:20:20 schoolbook kernel: [   64.462685] audit(1230009620.076:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5573 profile="/usr/sbin/cupsd" namespace="default"
Dec 22 22:20:20 schoolbook kernel: [   64.517526] apm: BIOS not found.
Dec 22 22:20:20 schoolbook kernel: [   64.623822] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 22:20:20 schoolbook kernel: [   64.623826] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 22:20:20 schoolbook kernel: [   64.625083] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 22:20:20 schoolbook kernel: [   64.625085] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 22:20:20 schoolbook kernel: [   65.245478] [drm] Initialized drm 1.1.0 20060810
Dec 22 22:20:21 schoolbook kernel: [   65.401735] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 22 22:20:21 schoolbook kernel: [   65.401785] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 22 22:20:21 schoolbook kernel: [   65.749437] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:20:21 schoolbook kernel: [   65.749442] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:20:21 schoolbook kernel: [   65.750699] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:20:21 schoolbook kernel: [   65.750702] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:20:22 schoolbook kernel: [   66.430743] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 22:20:22 schoolbook kernel: [   66.430747] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 22:20:22 schoolbook kernel: [   66.432006] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 22:20:22 schoolbook kernel: [   66.432009] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 22:20:26 schoolbook dhcdbd: Started up.
Dec 22 22:20:28 schoolbook kernel: [   71.881165] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 22 22:20:28 schoolbook kernel: [   71.922817] r8169: eth0: link down
Dec 22 22:20:28 schoolbook kernel: [   71.927157] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 22 22:20:28 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 22 22:20:28 schoolbook kernel: [   72.221983] Bluetooth: L2CAP ver 2.9
Dec 22 22:20:28 schoolbook kernel: [   72.221992] Bluetooth: L2CAP socket layer initialized
Dec 22 22:20:28 schoolbook kernel: [   72.313533] Bluetooth: RFCOMM socket layer initialized
Dec 22 22:20:28 schoolbook kernel: [   72.313554] Bluetooth: RFCOMM TTY layer initialized
Dec 22 22:20:28 schoolbook kernel: [   72.313558] Bluetooth: RFCOMM ver 1.8
Dec 22 22:20:29 schoolbook kernel: [   73.239782] NET: Registered protocol family 17
Dec 22 22:20:32 schoolbook kernel: [   75.521713] vmmon: module license 'unspecified' taints kernel.
Dec 22 22:20:32 schoolbook kernel: [   76.037399] bridge-eth1: already up
Dec 22 22:20:32 schoolbook kernel: [   76.042443] bridge-eth0: already up
Dec 22 22:29:53 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 22 22:29:57 schoolbook kernel: [  146.707958] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec 22 22:30:01 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Dec 22 22:30:01 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec 22 22:30:01 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec 22 22:30:01 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Dec 22 22:30:24 schoolbook kernel: [  171.704484] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:30:24 schoolbook kernel: [  171.704496] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:30:24 schoolbook kernel: [  171.705744] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 22:30:24 schoolbook kernel: [  171.705753] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 22:32:42 schoolbook kernel: [  271.291932] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 22:32:42 schoolbook kernel: [  271.291942] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 22:32:42 schoolbook kernel: [  271.356997] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 22:32:42 schoolbook kernel: [  271.357007] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 22:32:47 schoolbook kernel: [  273.852512] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 22:32:47 schoolbook kernel: [  273.852524] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 22:32:48 schoolbook kernel: [  273.945343] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 22 22:32:48 schoolbook kernel: [  273.945354] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 22 22:38:52 schoolbook kernel: [  439.919834] usb 1-1: new low speed USB device using uhci_hcd and address 5
Dec 22 22:38:52 schoolbook kernel: [  439.991247] usb 1-1: configuration #1 chosen from 1 choice
Dec 22 22:38:52 schoolbook kernel: [  440.144402] usbcore: registered new interface driver hiddev
Dec 22 22:38:52 schoolbook kernel: [  440.152697] input: Logitech Trackball as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0/input/input8
Dec 22 22:38:52 schoolbook kernel: [  440.168649] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1a.0-1
Dec 22 22:38:52 schoolbook kernel: [  440.168689] usbcore: registered new interface driver usbhid
Dec 22 22:38:52 schoolbook kernel: [  440.168697] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Dec 22 22:57:48 schoolbook kernel: [  944.303095] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
Dec 22 22:57:48 schoolbook kernel: [  944.303105] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 22:57:48 schoolbook kernel: [  944.303720] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
Dec 22 22:57:48 schoolbook kernel: [  944.303726] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
Dec 22 22:57:49 schoolbook kernel: [  944.440518] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 22 22:57:49 schoolbook kernel: [  944.698710] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 22 22:57:50 schoolbook kernel: [  944.881101] usb 3-1: new full speed USB device using uhci_hcd and address 4
Dec 22 22:57:50 schoolbook kernel: [  945.022329] usb 3-1: new full speed USB device using uhci_hcd and address 5
Dec 22 22:57:55 schoolbook kernel: [  946.516714] usb 3-1: new full speed USB device using uhci_hcd and address 6
Dec 22 22:57:56 schoolbook kernel: [  946.833610] usb 3-1: new full speed USB device using uhci_hcd and address 7
Dec 22 22:57:56 schoolbook kernel: [  947.016721] usb 3-1: new full speed USB device using uhci_hcd and address 8
Dec 22 22:57:57 schoolbook kernel: [  947.151683] usb 3-1: new full speed USB device using uhci_hcd and address 9
Dec 22 22:59:16 schoolbook kernel: [  976.986904] usb 3-1: new full speed USB device using uhci_hcd and address 10
Dec 22 22:59:16 schoolbook kernel: [  977.317520] usb 3-1: new full speed USB device using uhci_hcd and address 11
Dec 22 22:59:17 schoolbook kernel: [  977.478673] usb 3-1: new full speed USB device using uhci_hcd and address 12
Dec 22 22:59:17 schoolbook kernel: [  977.602390] usb 3-1: new full speed USB device using uhci_hcd and address 13
Dec 22 23:04:58 schoolbook kernel: [ 1118.842729] usb 1-1: USB disconnect, address 5
Dec 22 23:08:54 schoolbook kernel: [ 1188.526058] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 23:08:54 schoolbook kernel: [ 1188.526063] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 23:08:54 schoolbook kernel: [ 1188.527323] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 23:08:54 schoolbook kernel: [ 1188.527327] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 23:12:12 schoolbook kernel: [ 1244.144627] usb 3-1: new full speed USB device using uhci_hcd and address 14
Dec 22 23:12:12 schoolbook kernel: [ 1244.395990] usb 3-1: new full speed USB device using uhci_hcd and address 15
Dec 22 23:12:13 schoolbook kernel: [ 1244.513360] usb 3-1: new full speed USB device using uhci_hcd and address 16
Dec 22 23:12:13 schoolbook kernel: [ 1244.616901] usb 3-1: new full speed USB device using uhci_hcd and address 17
Dec 22 23:26:46 schoolbook kernel: [ 1471.130575] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 23:26:46 schoolbook kernel: [ 1471.130586] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 23:26:46 schoolbook kernel: [ 1471.131827] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 22 23:26:46 schoolbook kernel: [ 1471.131835] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 22 23:26:47 schoolbook kernel: [ 1471.807535] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 23:26:47 schoolbook kernel: [ 1471.807538] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 23:26:47 schoolbook kernel: [ 1471.808825] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 22 23:26:47 schoolbook kernel: [ 1471.808828] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 22 23:27:03 schoolbook kernel: [ 1476.836815] ip6_tables: (C) 2000-2006 Netfilter Core Team
Dec 22 23:27:05 schoolbook exiting on signal 15
Dec 23 07:22:52 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 23 07:22:52 schoolbook kernel: Inspecting /boot/System.map-2.6.24-19-generic
Dec 23 07:22:52 schoolbook kernel: Loaded 27884 symbols from /boot/System.map-2.6.24-19-generic.
Dec 23 07:22:52 schoolbook kernel: Symbols match kernel version 2.6.24.
Dec 23 07:22:52 schoolbook kernel: Loaded 18154 symbols from 89 modules.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008 (Ubuntu 2.6.24-19.41-generic)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ac00 (usable)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 000000000009ac00 - 00000000000a0000 (reserved)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Dec 23 07:22:52 schoolbook kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] 1143MB HIGHMEM available.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] 896MB LOWMEM available.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] found SMP MP-table at 000ff780
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Zone PFN ranges:
Dec 23 07:22:52 schoolbook kernel: [    0.000000]   DMA             0 ->     4096
Dec 23 07:22:52 schoolbook kernel: [    0.000000]   Normal       4096 ->   229376
Dec 23 07:22:52 schoolbook kernel: [    0.000000]   HighMem    229376 ->   522144
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Movable zone start PFN for each node
Dec 23 07:22:52 schoolbook kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 23 07:22:52 schoolbook kernel: [    0.000000]     0:        0 ->   522144
Dec 23 07:22:52 schoolbook kernel: [    0.000000] DMI present.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F8750 checksum 0
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: RSDP 000F8750, 0014 (r0 ACPIAM)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: RSDT 7F7A0000, 0044 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: FACP 7F7A0200, 0084 (r2 052807 FACP1333 20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: DSDT 7F7A05B0, 5B1B (r1  A1221 A1221000        0 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 052807 APIC1333 20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: MCFG 7F7A03F0, 003C (r1 052807 OEMMCFG  20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: SLIC 7F7A0430, 0176 (r1 MSI_NB MEGABOOK 20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0071 (r1 052807 OEMB1333 20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: HPET 7F7A60D0, 0038 (r1 052807 OEMHPET  20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: GSCI 7F7AE0C0, 2024 (r1 052807 GMCHSCI  20070528 MSFT       97)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: SSDT 7F7B09B0, 04E6 (r1  PmRef    CpuPm     3000 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Processor #0 6:15 APIC version 20
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Processor #1 6:15 APIC version 20
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Dec 23 07:22:52 schoolbook kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 23 07:22:52 schoolbook kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Allocating PCI resources starting at 80000000 (gap: 7f800000:7f600000)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009a000 - 000000000009b000
Dec 23 07:22:52 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009b000 - 00000000000a0000
Dec 23 07:22:52 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
Dec 23 07:22:52 schoolbook kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 518065
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Kernel command line: root=UUID=63c2c38b-8e0d-4df8-b0e2-f0d556007b0e ro quiet splash ec_intr=0
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Initializing CPU#0
Dec 23 07:22:52 schoolbook kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 23 07:22:52 schoolbook kernel: [    0.000000] Detected 1995.114 MHz processor.
Dec 23 07:22:52 schoolbook kernel: [   19.583899] Console: colour VGA+ 80x25
Dec 23 07:22:52 schoolbook kernel: [   19.583904] console [tty0] enabled
Dec 23 07:22:52 schoolbook kernel: [   19.584220] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 23 07:22:52 schoolbook kernel: [   19.584603] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 23 07:22:52 schoolbook kernel: [   19.714618] Memory: 2058228k/2088576k available (2177k kernel code, 29064k reserved, 1006k data, 368k init, 1171072k highmem)
Dec 23 07:22:52 schoolbook kernel: [   19.714627] virtual kernel memory layout:
Dec 23 07:22:52 schoolbook kernel: [   19.714628]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Dec 23 07:22:52 schoolbook kernel: [   19.714630]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 23 07:22:52 schoolbook kernel: [   19.714631]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 23 07:22:52 schoolbook kernel: [   19.714633]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 23 07:22:52 schoolbook kernel: [   19.714634]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Dec 23 07:22:52 schoolbook kernel: [   19.714635]       .data : 0xc03204c4 - 0xc041bdc4   (1006 kB)
Dec 23 07:22:52 schoolbook kernel: [   19.714637]       .text : 0xc0100000 - 0xc03204c4   (2177 kB)
Dec 23 07:22:52 schoolbook kernel: [   19.714641] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 23 07:22:52 schoolbook kernel: [   19.714689] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Dec 23 07:22:52 schoolbook kernel: [   19.794787] Calibrating delay using timer specific routine.. 3995.25 BogoMIPS (lpj=7990500)
Dec 23 07:22:52 schoolbook kernel: [   19.794812] Security Framework initialized
Dec 23 07:22:52 schoolbook kernel: [   19.794819] SELinux:  Disabled at boot.
Dec 23 07:22:52 schoolbook kernel: [   19.794835] AppArmor: AppArmor initialized
Dec 23 07:22:52 schoolbook kernel: [   19.794841] Failure registering capabilities with primary security module.
Dec 23 07:22:52 schoolbook kernel: [   19.794851] Mount-cache hash table entries: 512
Dec 23 07:22:52 schoolbook kernel: [   19.794999] Initializing cgroup subsys ns
Dec 23 07:22:52 schoolbook kernel: [   19.795005] Initializing cgroup subsys cpuacct
Dec 23 07:22:52 schoolbook kernel: [   19.795029] monitor/mwait feature present.
Dec 23 07:22:52 schoolbook kernel: [   19.795031] using mwait in idle threads.
Dec 23 07:22:52 schoolbook kernel: [   19.795036] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 23 07:22:52 schoolbook kernel: [   19.795039] CPU: L2 cache: 4096K
Dec 23 07:22:52 schoolbook kernel: [   19.795042] CPU: Physical Processor ID: 0
Dec 23 07:22:52 schoolbook kernel: [   19.795044] CPU: Processor Core ID: 0
Dec 23 07:22:52 schoolbook kernel: [   19.795059] Compat vDSO mapped to ffffe000.
Dec 23 07:22:52 schoolbook kernel: [   19.795075] Checking 'hlt' instruction... OK.
Dec 23 07:22:52 schoolbook kernel: [   19.811294] SMP alternatives: switching to UP code
Dec 23 07:22:52 schoolbook kernel: [   19.813492] Early unpacking initramfs... done
Dec 23 07:22:52 schoolbook kernel: [   20.313984] ACPI: Core revision 20070126
Dec 23 07:22:52 schoolbook kernel: [   20.314040] ACPI: Looking for DSDT in initramfs... successfully read 23336 bytes from /DSDT.aml.
Dec 23 07:22:52 schoolbook kernel: [   20.314066] ACPI: Table DSDT replaced by host OS
Dec 23 07:22:52 schoolbook kernel: [   20.314071] ACPI: DSDT 00000000, 5B28 (r1  A1221 A1221000        0 INTL 20061109)
Dec 23 07:22:52 schoolbook kernel: [   20.314077] ACPI: DSDT override uses original SSDTs unless "acpi_no_auto_ssdt"CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 23 07:22:52 schoolbook kernel: [   20.318045] SMP alternatives: switching to SMP code
Dec 23 07:22:52 schoolbook kernel: [   20.318972] Booting processor 1/1 eip 3000
Dec 23 07:22:52 schoolbook kernel: [   20.329621] Initializing CPU#1
Dec 23 07:22:52 schoolbook kernel: [   20.406438] Calibrating delay using timer specific routine.. 3990.05 BogoMIPS (lpj=7980114)
Dec 23 07:22:52 schoolbook kernel: [   20.406453] monitor/mwait feature present.
Dec 23 07:22:52 schoolbook kernel: [   20.406457] CPU: L1 I cache: 32K, L1 D cache: 32K
Dec 23 07:22:52 schoolbook kernel: [   20.406460] CPU: L2 cache: 4096K
Dec 23 07:22:52 schoolbook kernel: [   20.406462] CPU: Physical Processor ID: 0
Dec 23 07:22:52 schoolbook kernel: [   20.406464] CPU: Processor Core ID: 1
Dec 23 07:22:52 schoolbook kernel: [   20.407470] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
Dec 23 07:22:52 schoolbook kernel: [   20.407498] Total of 2 processors activated (7985.30 BogoMIPS).
Dec 23 07:22:52 schoolbook kernel: [   20.407692] ENABLING IO-APIC IRQs
Dec 23 07:22:52 schoolbook kernel: [   20.407893] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 23 07:22:52 schoolbook kernel: [   20.554494] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Dec 23 07:22:52 schoolbook kernel: [   20.574505] Brought up 2 CPUs
Dec 23 07:22:52 schoolbook kernel: [   20.574832] net_namespace: 64 bytes
Dec 23 07:22:52 schoolbook kernel: [   20.574847] Booting paravirtualized kernel on bare hardware
Dec 23 07:22:52 schoolbook kernel: [   20.575471] Time: 14:22:09  Date: 12/23/08
Dec 23 07:22:52 schoolbook kernel: [   20.575506] NET: Registered protocol family 16
Dec 23 07:22:52 schoolbook kernel: [   20.575752] EISA bus registered
Dec 23 07:22:52 schoolbook kernel: [   20.575758] ACPI: bus type pci registered
Dec 23 07:22:52 schoolbook kernel: [   20.576068] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
Dec 23 07:22:52 schoolbook kernel: [   20.576071] PCI: Using configuration type 1
Dec 23 07:22:52 schoolbook kernel: [   20.576103] Setting up standard PCI resources
Dec 23 07:22:52 schoolbook kernel: [   20.591784] ACPI: Interpreter enabled
Dec 23 07:22:52 schoolbook kernel: [   20.591789] ACPI: (supports S0 S1 S3 S4 S5)
Dec 23 07:22:52 schoolbook kernel: [   20.591811] ACPI: Using IOAPIC for interrupt routing
Dec 23 07:22:52 schoolbook kernel: [   20.592174] Error attaching device data
Dec 23 07:22:52 schoolbook kernel: [   20.592229] Error attaching device data
Dec 23 07:22:52 schoolbook kernel: [   20.594412] ACPI: EC: non-query interrupt received, switching to interrupt mode
Dec 23 07:22:52 schoolbook kernel: [   20.600631] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Dec 23 07:22:52 schoolbook kernel: [   20.600635] ACPI: EC: driver started in interrupt mode
Dec 23 07:22:52 schoolbook kernel: [   20.600785] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 23 07:22:52 schoolbook kernel: [   20.601969] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
Dec 23 07:22:52 schoolbook kernel: [   20.601974] PCI quirk: region 0500-053f claimed by ICH6 GPIO
Dec 23 07:22:52 schoolbook kernel: [   20.603561] PCI: Transparent bridge - 0000:00:1e.0
Dec 23 07:22:52 schoolbook kernel: [   20.625321] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.625497] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.625669] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.625840] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 10 11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.626011] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 *7 10 11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.626182] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 6 7 10 11 12 14 15)
Dec 23 07:22:52 schoolbook kernel: [   20.626358] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.626532] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 *15)
Dec 23 07:22:52 schoolbook kernel: [   20.626727] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 23 07:22:52 schoolbook kernel: [   20.626766] pnp: PnP ACPI init
Dec 23 07:22:52 schoolbook kernel: [   20.626776] ACPI: bus type pnp registered
Dec 23 07:22:52 schoolbook kernel: [   20.629749] pnp: PnP ACPI: found 13 devices
Dec 23 07:22:52 schoolbook kernel: [   20.629753] ACPI: ACPI bus type pnp unregistered
Dec 23 07:22:52 schoolbook kernel: [   20.629757] PnPBIOS: Disabled by ACPI PNP
Dec 23 07:22:52 schoolbook kernel: [   20.630041] PCI: Using ACPI for IRQ routing
Dec 23 07:22:52 schoolbook kernel: [   20.630044] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 23 07:22:52 schoolbook kernel: [   20.678311] NET: Registered protocol family 8
Dec 23 07:22:52 schoolbook kernel: [   20.678314] NET: Registered protocol family 20
Dec 23 07:22:52 schoolbook kernel: [   20.678357] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Dec 23 07:22:52 schoolbook kernel: [   20.678363] hpet0: 3 64-bit timers, 14318180 Hz
Dec 23 07:22:52 schoolbook kernel: [   20.679404] AppArmor: AppArmor Filesystem Enabled
Dec 23 07:22:52 schoolbook kernel: [   20.682292] Time: tsc clocksource has been installed.
Dec 23 07:22:52 schoolbook kernel: [   20.694283] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694297] system 00:08: ioport range 0x400-0x41f has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694300] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694304] system 00:08: ioport range 0x800-0x87f has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694308] system 00:08: ioport range 0x500-0x53f has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694312] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694316] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694320] system 00:08: iomem range 0xfed40000-0xfed8ffff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694328] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694332] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694340] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694349] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694353] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694357] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694361] system 00:0c: iomem range 0x100000-0x7f7fffff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.694365] system 00:0c: iomem range 0xfed90000-0xffffffff could not be reserved
Dec 23 07:22:52 schoolbook kernel: [   20.724892] PCI: Bridge: 0000:00:1c.0
Dec 23 07:22:52 schoolbook kernel: [   20.724896]   IO window: e000-efff
Dec 23 07:22:52 schoolbook kernel: [   20.724904]   MEM window: fe000000-febfffff
Dec 23 07:22:52 schoolbook kernel: [   20.724910]   PREFETCH window: fa000000-fcffffff
Dec 23 07:22:52 schoolbook kernel: [   20.724917] PCI: Bridge: 0000:00:1c.1
Dec 23 07:22:52 schoolbook kernel: [   20.724921]   IO window: d000-dfff
Dec 23 07:22:52 schoolbook kernel: [   20.724928]   MEM window: fdf00000-fdffffff
Dec 23 07:22:52 schoolbook kernel: [   20.724934]   PREFETCH window: disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.724941] PCI: Bridge: 0000:00:1c.2
Dec 23 07:22:52 schoolbook kernel: [   20.724943]   IO window: disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.724950]   MEM window: fde00000-fdefffff
Dec 23 07:22:52 schoolbook kernel: [   20.724955]   PREFETCH window: disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.724963] PCI: Bridge: 0000:00:1e.0
Dec 23 07:22:52 schoolbook kernel: [   20.724964]   IO window: disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.724972]   MEM window: fdd00000-fddfffff
Dec 23 07:22:52 schoolbook kernel: [   20.724977]   PREFETCH window: disabled.
Dec 23 07:22:52 schoolbook kernel: [   20.725014] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 23 07:22:52 schoolbook kernel: [   20.725053] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
Dec 23 07:22:52 schoolbook kernel: [   20.725091] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 23 07:22:52 schoolbook kernel: [   20.725130] NET: Registered protocol family 2
Dec 23 07:22:52 schoolbook kernel: [   20.762277] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 23 07:22:52 schoolbook kernel: [   20.762568] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 23 07:22:52 schoolbook kernel: [   20.763117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 23 07:22:52 schoolbook kernel: [   20.763359] TCP: Hash tables configured (established 131072 bind 65536)
Dec 23 07:22:52 schoolbook kernel: [   20.763363] TCP reno registered
Dec 23 07:22:52 schoolbook kernel: [   20.774351] checking if image is initramfs... it is
Dec 23 07:22:52 schoolbook kernel: [   21.760365] Freeing initrd memory: 7744k freed
Dec 23 07:22:52 schoolbook kernel: [   21.761333] audit: initializing netlink socket (disabled)
Dec 23 07:22:52 schoolbook kernel: [   21.761350] audit(1230042128.920:1): initialized
Dec 23 07:22:52 schoolbook kernel: [   21.761612] highmem bounce pool size: 64 pages
Dec 23 07:22:52 schoolbook kernel: [   21.764241] VFS: Disk quotas dquot_6.5.1
Dec 23 07:22:52 schoolbook kernel: [   21.764340] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 23 07:22:52 schoolbook kernel: [   21.764507] io scheduler noop registered
Dec 23 07:22:52 schoolbook kernel: [   21.764510] io scheduler anticipatory registered
Dec 23 07:22:52 schoolbook kernel: [   21.764513] io scheduler deadline registered
Dec 23 07:22:52 schoolbook kernel: [   21.764528] io scheduler cfq registered (default)
Dec 23 07:22:52 schoolbook kernel: [   21.764893] assign_interrupt_mode Found MSI capability
Dec 23 07:22:52 schoolbook kernel: [   21.765194] assign_interrupt_mode Found MSI capability
Dec 23 07:22:52 schoolbook kernel: [   21.765488] assign_interrupt_mode Found MSI capability
Dec 23 07:22:52 schoolbook kernel: [   21.765935] isapnp: Scanning for PnP cards...
Dec 23 07:22:52 schoolbook kernel: [   22.120326] isapnp: No Plug & Play device found
Dec 23 07:22:52 schoolbook kernel: [   22.154126] Real Time Clock Driver v1.12ac
Dec 23 07:22:52 schoolbook kernel: [   22.154393] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 23 07:22:52 schoolbook kernel: [   22.155945] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 23 07:22:52 schoolbook kernel: [   22.156030] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Dec 23 07:22:52 schoolbook kernel: [   22.156158] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
Dec 23 07:22:52 schoolbook kernel: [   22.156535] i8042.c: Detected active multiplexing controller, rev 1.1.
Dec 23 07:22:52 schoolbook kernel: [   22.156618] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 23 07:22:52 schoolbook kernel: [   22.156623] serio: i8042 AUX0 port at 0x60,0x64 irq 12
Dec 23 07:22:52 schoolbook kernel: [   22.156627] serio: i8042 AUX1 port at 0x60,0x64 irq 12
Dec 23 07:22:52 schoolbook kernel: [   22.156630] serio: i8042 AUX2 port at 0x60,0x64 irq 12
Dec 23 07:22:52 schoolbook kernel: [   22.156633] serio: i8042 AUX3 port at 0x60,0x64 irq 12
Dec 23 07:22:52 schoolbook kernel: [   22.177545] mice: PS/2 mouse device common for all mice
Dec 23 07:22:52 schoolbook kernel: [   22.177688] EISA: Probing bus 0 at eisa.0
Dec 23 07:22:52 schoolbook kernel: [   22.177733] EISA: Detected 0 cards.
Dec 23 07:22:52 schoolbook kernel: [   22.177736] cpuidle: using governor ladder
Dec 23 07:22:52 schoolbook kernel: [   22.177738] cpuidle: using governor menu
Dec 23 07:22:52 schoolbook kernel: [   22.177835] NET: Registered protocol family 1
Dec 23 07:22:52 schoolbook kernel: [   22.177869] Using IPI No-Shortcut mode
Dec 23 07:22:52 schoolbook kernel: [   22.177903] registered taskstats version 1
Dec 23 07:22:52 schoolbook kernel: [   22.178047]   Magic number: 4:74:385
Dec 23 07:22:52 schoolbook kernel: [   22.178110] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 23 07:22:52 schoolbook kernel: [   22.178112] EDD information not available.
Dec 23 07:22:52 schoolbook kernel: [   22.178327] Freeing unused kernel memory: 368k freed
Dec 23 07:22:52 schoolbook kernel: [   22.180733] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Dec 23 07:22:52 schoolbook kernel: [   23.497770] fuse init (API version 7.9)
Dec 23 07:22:52 schoolbook kernel: [   23.543251] ACPI: SSDT 7F7B01C0, 0297 (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [   23.543547] ACPI: SSDT 7F7B04F0, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [   23.544183] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Dec 23 07:22:52 schoolbook kernel: [   23.544495] ACPI: SSDT 7F7B00F0, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [   23.544783] ACPI: SSDT 7F7B0460, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20051117)
Dec 23 07:22:52 schoolbook kernel: [   23.545544] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Dec 23 07:22:52 schoolbook kernel: [   23.548121] ACPI: Thermal Zone [THRM] (33 C)
Dec 23 07:22:52 schoolbook kernel: [   23.740783] usbcore: registered new interface driver usbfs
Dec 23 07:22:52 schoolbook kernel: [   23.740811] usbcore: registered new interface driver hub
Dec 23 07:22:52 schoolbook kernel: [   23.741416] usbcore: registered new device driver usb
Dec 23 07:22:52 schoolbook kernel: [   23.744432] USB Universal Host Controller Interface driver v3.0
Dec 23 07:22:52 schoolbook kernel: [   23.744489] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 23 07:22:52 schoolbook kernel: [   23.744507] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   23.744759] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Dec 23 07:22:52 schoolbook kernel: [   23.744796] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
Dec 23 07:22:52 schoolbook kernel: [   23.744983] usb usb1: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   23.745015] hub 1-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   23.745021] hub 1-0:1.0: 2 ports detected
Dec 23 07:22:52 schoolbook kernel: [   23.848663] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
Dec 23 07:22:52 schoolbook kernel: [   23.848682] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   23.848710] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Dec 23 07:22:52 schoolbook kernel: [   23.848745] uhci_hcd 0000:00:1a.1: irq 19, io base 0x0000b880
Dec 23 07:22:52 schoolbook kernel: [   23.848890] usb usb2: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   23.848921] hub 2-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   23.848927] hub 2-0:1.0: 2 ports detected
Dec 23 07:22:52 schoolbook kernel: [   23.952597] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
Dec 23 07:22:52 schoolbook kernel: [   23.952616] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   23.952647] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Dec 23 07:22:52 schoolbook kernel: [   23.952681] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bc00
Dec 23 07:22:52 schoolbook kernel: [   23.952825] usb usb3: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   23.952856] hub 3-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   23.952862] hub 3-0:1.0: 2 ports detected
Dec 23 07:22:52 schoolbook kernel: [   24.056535] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
Dec 23 07:22:52 schoolbook kernel: [   24.056554] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   24.056584] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Dec 23 07:22:52 schoolbook kernel: [   24.056619] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000c000
Dec 23 07:22:52 schoolbook kernel: [   24.056762] usb usb4: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   24.056793] hub 4-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   24.056800] hub 4-0:1.0: 2 ports detected
Dec 23 07:22:52 schoolbook kernel: [   24.088405] usb 1-2: new full speed USB device using uhci_hcd and address 2
Dec 23 07:22:52 schoolbook kernel: [   24.165619] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Dec 23 07:22:52 schoolbook kernel: [   24.165639] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   24.165668] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Dec 23 07:22:52 schoolbook kernel: [   24.165705] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c080
Dec 23 07:22:52 schoolbook kernel: [   24.165852] usb usb5: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   24.165884] hub 5-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   24.165890] hub 5-0:1.0: 2 ports detected
Dec 23 07:22:52 schoolbook kernel: [   24.195421] SCSI subsystem initialized
Dec 23 07:22:52 schoolbook kernel: [   24.268551] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Dec 23 07:22:52 schoolbook kernel: [   24.268571] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   24.268603] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Dec 23 07:22:52 schoolbook kernel: [   24.272517] ehci_hcd 0000:00:1a.7: debug port 1
Dec 23 07:22:52 schoolbook kernel: [   24.272533] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdcff000
Dec 23 07:22:52 schoolbook kernel: [   24.288295] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 23 07:22:52 schoolbook kernel: [   24.288432] usb usb6: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   24.288468] hub 6-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   24.288476] hub 6-0:1.0: 4 ports detected
Dec 23 07:22:52 schoolbook kernel: [   24.392374] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
Dec 23 07:22:52 schoolbook kernel: [   24.392395] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 23 07:22:52 schoolbook kernel: [   24.392427] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Dec 23 07:22:52 schoolbook kernel: [   24.396350] ehci_hcd 0000:00:1d.7: debug port 1
Dec 23 07:22:52 schoolbook kernel: [   24.396366] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfdcff400
Dec 23 07:22:52 schoolbook kernel: [   24.412246] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 23 07:22:52 schoolbook kernel: [   24.412374] usb usb7: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   24.412407] hub 7-0:1.0: USB hub found
Dec 23 07:22:52 schoolbook kernel: [   24.412413] hub 7-0:1.0: 6 ports detected
Dec 23 07:22:52 schoolbook kernel: [   24.516622] r8169 Gigabit Ethernet driver 2.2LK loaded
Dec 23 07:22:52 schoolbook kernel: [   24.516652] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Dec 23 07:22:52 schoolbook kernel: [   24.517096] eth0: RTL8168b/8111b at 0xf882a000, 00:19:db:3c:e3:55, XID 38000000 IRQ 220
Dec 23 07:22:52 schoolbook kernel: [   24.518266] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 18
Dec 23 07:22:52 schoolbook kernel: [   25.335722] Clocksource tsc unstable (delta = -13408828434 ns)
Dec 23 07:22:52 schoolbook kernel: [   25.339863] Time: hpet clocksource has been installed.
Dec 23 07:22:52 schoolbook kernel: [   25.355831] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Dec 23 07:22:52 schoolbook kernel: [   25.355837] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part 
Dec 23 07:22:52 schoolbook kernel: [   25.356140] scsi0 : ahci
Dec 23 07:22:52 schoolbook kernel: [   25.356507] scsi1 : ahci
Dec 23 07:22:52 schoolbook kernel: [   25.356747] scsi2 : ahci
Dec 23 07:22:52 schoolbook kernel: [   25.356850] ata1: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff900 irq 219
Dec 23 07:22:52 schoolbook kernel: [   25.356855] ata2: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcff980 irq 219
Dec 23 07:22:52 schoolbook kernel: [   25.356859] ata3: SATA max UDMA/133 abar m2048@0xfdcff800 port 0xfdcffa00 irq 219
Dec 23 07:22:52 schoolbook kernel: [   25.364795] usb 1-2: new full speed USB device using uhci_hcd and address 4
Dec 23 07:22:52 schoolbook kernel: [   25.388354] usb 1-2: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   25.512337] usb 3-1: new full speed USB device using uhci_hcd and address 2
Dec 23 07:22:52 schoolbook kernel: [   25.521363] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 07:22:52 schoolbook kernel: [   25.522302] ata1.00: ATA-7: Hitachi HTS541616J9SA00, SB4OC70P, max UDMA/100
Dec 23 07:22:52 schoolbook kernel: [   25.522306] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (not used)
Dec 23 07:22:52 schoolbook kernel: [   25.523407] ata1.00: configured for UDMA/100
Dec 23 07:22:52 schoolbook kernel: [   25.551732] ata2: SATA link down (SStatus 0 SControl 300)
Dec 23 07:22:52 schoolbook kernel: [   25.566747] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 23 07:22:52 schoolbook kernel: [   25.580745] ata3: SATA link down (SStatus 0 SControl 300)
Dec 23 07:22:52 schoolbook kernel: [   25.581002] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5
Dec 23 07:22:52 schoolbook kernel: [   25.581485] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 21
Dec 23 07:22:52 schoolbook kernel: [   25.581622] scsi3 : ata_piix
Dec 23 07:22:52 schoolbook kernel: [   25.581821] scsi4 : ata_piix
Dec 23 07:22:52 schoolbook kernel: [   25.583368] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 23 07:22:52 schoolbook kernel: [   25.583372] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 23 07:22:52 schoolbook kernel: [   25.592290] Driver 'sd' needs updating - please use bus_type methods
Dec 23 07:22:52 schoolbook kernel: [   25.594741] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 23 07:22:52 schoolbook kernel: [   25.594758] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 07:22:52 schoolbook kernel: [   25.594786] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 23 07:22:52 schoolbook kernel: [   25.594849] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Dec 23 07:22:52 schoolbook kernel: [   25.594863] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 07:22:52 schoolbook kernel: [   25.594890] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 23 07:22:52 schoolbook kernel: [   25.594894]  sda:<3>usb 3-1: device descriptor read/64, error -71
Dec 23 07:22:52 schoolbook kernel: [   25.898946] ata4.00: ATAPI: HL-DT-ST DVDRAM GSA-T20N, WA03, max UDMA/33
Dec 23 07:22:52 schoolbook kernel: [   25.985468] usb 3-1: new full speed USB device using uhci_hcd and address 4
Dec 23 07:22:52 schoolbook kernel: [   26.004350]  sda1 sda2 < sda5 >
Dec 23 07:22:52 schoolbook kernel: [   26.022963] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 23 07:22:52 schoolbook kernel: [   26.028611] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 23 07:22:52 schoolbook kernel: [   26.069787] ata4.00: configured for UDMA/33
Dec 23 07:22:52 schoolbook kernel: [   26.073476] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-T20N  WA03 PQ: 0 ANSI: 5
Dec 23 07:22:52 schoolbook kernel: [   26.073570] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Dec 23 07:22:52 schoolbook kernel: [   26.086307] Driver 'sr' needs updating - please use bus_type methods
Dec 23 07:22:52 schoolbook kernel: [   26.103539] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Dec 23 07:22:52 schoolbook kernel: [   26.103543] Uniform CD-ROM driver Revision: 3.20
Dec 23 07:22:52 schoolbook kernel: [   26.272091] Attempting manual resume
Dec 23 07:22:52 schoolbook kernel: [   26.319132] kjournald starting.  Commit interval 5 seconds
Dec 23 07:22:52 schoolbook kernel: [   26.319164] EXT3-fs: mounted filesystem with ordered data mode.
Dec 23 07:22:52 schoolbook kernel: [   26.440120] usb 3-1: new full speed USB device using uhci_hcd and address 5
Dec 23 07:22:52 schoolbook kernel: [   27.087723] usb 5-1: new full speed USB device using uhci_hcd and address 2
Dec 23 07:22:52 schoolbook kernel: [   27.256857] usb 5-1: configuration #1 chosen from 1 choice
Dec 23 07:22:52 schoolbook kernel: [   39.755068] input: PC Speaker as /devices/platform/pcspkr/input/input2
Dec 23 07:22:52 schoolbook kernel: [   39.783061] iTCO_vendor_support: vendor-support=0
Dec 23 07:22:52 schoolbook kernel: [   39.800543] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Dec 23 07:22:52 schoolbook kernel: [   39.800680] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x0860)
Dec 23 07:22:52 schoolbook kernel: [   39.800746] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Dec 23 07:22:52 schoolbook kernel: [   39.862171] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 23 07:22:52 schoolbook kernel: [   39.911017] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 23 07:22:52 schoolbook kernel: [   40.022886] Linux agpgart interface v0.102
Dec 23 07:22:52 schoolbook kernel: [   40.085674] agpgart: Detected an Intel 965GM Chipset.
Dec 23 07:22:52 schoolbook kernel: [   40.088494] agpgart: Detected 7676K stolen memory.
Dec 23 07:22:52 schoolbook kernel: [   40.103388] agpgart: AGP aperture is 256M @ 0xd0000000
Dec 23 07:22:52 schoolbook kernel: [   40.165007] input: Power Button (FF) as /devices/virtual/input/input3
Dec 23 07:22:52 schoolbook kernel: [   40.229754] ACPI: Power Button (FF) [PWRF]
Dec 23 07:22:52 schoolbook kernel: [   40.229842] input: Lid Switch as /devices/virtual/input/input4
Dec 23 07:22:52 schoolbook kernel: [   40.250337] ACPI: Lid Switch [LID0]
Dec 23 07:22:52 schoolbook kernel: [   40.250432] input: Power Button (CM) as /devices/virtual/input/input5
Dec 23 07:22:52 schoolbook kernel: [   40.317710] ACPI: Power Button (CM) [PWRB]
Dec 23 07:22:52 schoolbook kernel: [   40.581582] sdhci: Secure Digital Host Controller Interface driver
Dec 23 07:22:52 schoolbook kernel: [   40.581586] sdhci: Copyright(c) Pierre Ossman
Dec 23 07:22:52 schoolbook kernel: [   40.581633] sdhci: SDHCI controller found at 0000:01:04.1 [1524:0750] (rev 0)
Dec 23 07:22:52 schoolbook kernel: [   40.581658] ACPI: PCI Interrupt 0000:01:04.1[A] -> GSI 16 (level, low) -> IRQ 16
Dec 23 07:22:52 schoolbook kernel: [   40.581731] mmc0: SDHCI at 0xfddff400 irq 16 DMA
Dec 23 07:22:52 schoolbook kernel: [   40.581744] sdhci: SDHCI controller found at 0000:01:04.3 [1524:0751] (rev 0)
Dec 23 07:22:52 schoolbook kernel: [   40.581765] ACPI: PCI Interrupt 0000:01:04.3[A] -> GSI 16 (level, low) -> IRQ 16
Dec 23 07:22:52 schoolbook kernel: [   40.581778] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 23 07:22:52 schoolbook kernel: [   40.581821] mmc1: SDHCI at 0xfddffc00 irq 16 DMA
Dec 23 07:22:52 schoolbook kernel: [   40.825920] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
Dec 23 07:22:52 schoolbook kernel: [   40.882359] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Dec 23 07:22:52 schoolbook kernel: [   41.220185] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 22
Dec 23 07:22:52 schoolbook kernel: [   41.277268] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
Dec 23 07:22:52 schoolbook kernel: [   41.306322] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
Dec 23 07:22:52 schoolbook kernel: [   41.379708] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Dec 23 07:22:52 schoolbook kernel: [   41.379712] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Dec 23 07:22:52 schoolbook kernel: [   41.379830] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 18
Dec 23 07:22:52 schoolbook kernel: [   41.379881] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
Dec 23 07:22:52 schoolbook kernel: [   41.386138] ACPI: Battery Slot [BAT1] (battery present)
Dec 23 07:22:52 schoolbook kernel: [   41.387033] ACPI: AC Adapter [ADP1] (on-line)
Dec 23 07:22:52 schoolbook kernel: [   41.473879] Bluetooth: Core ver 2.11
Dec 23 07:22:52 schoolbook kernel: [   41.476980] NET: Registered protocol family 31
Dec 23 07:22:52 schoolbook kernel: [   41.476983] Bluetooth: HCI device and connection manager initialized
Dec 23 07:22:52 schoolbook kernel: [   41.476988] Bluetooth: HCI socket layer initialized
Dec 23 07:22:52 schoolbook kernel: [   41.510497] Bluetooth: HCI USB driver ver 2.9
Dec 23 07:22:52 schoolbook kernel: [   41.512793] usbcore: registered new interface driver hci_usb
Dec 23 07:22:52 schoolbook kernel: [   42.947683] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Dec 23 07:22:52 schoolbook kernel: [   43.162535] udev: renamed network interface wlan0 to eth1
Dec 23 07:22:52 schoolbook kernel: [   43.168917] lp: driver loaded but no devices found
Dec 23 07:22:52 schoolbook kernel: [   43.186714] snd-bt-sco revision 1.19 $
Dec 23 07:22:52 schoolbook kernel: [   43.186736] snd-bt-sco: snd-bt-scod thread starting
Dec 23 07:22:52 schoolbook kernel: [   43.619020] Adding 6056464k swap on /dev/sda5.  Priority:-1 extents:1 across:6056464k
Dec 23 07:22:52 schoolbook kernel: [   44.079457] EXT3 FS on sda1, internal journal
Dec 23 07:22:52 schoolbook kernel: [   44.332595] device-mapper: uevent: version 1.0.3
Dec 23 07:22:52 schoolbook kernel: [   44.332630] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
Dec 23 07:22:52 schoolbook kernel: [   45.577443] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 23 07:22:52 schoolbook kernel: [   47.146052] No dock devices found.
Dec 23 07:22:55 schoolbook kernel: [   50.224945] NET: Registered protocol family 10
Dec 23 07:22:55 schoolbook kernel: [   50.225187] lo: Disabled Privacy Extensions
Dec 23 07:22:56 schoolbook kernel: [   50.831134] ppdev: user-space parallel port driver
Dec 23 07:22:56 schoolbook kernel: [   50.841220] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:22:56 schoolbook kernel: [   50.841224] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:22:56 schoolbook kernel: [   50.842480] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:22:56 schoolbook kernel: [   50.842483] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:22:56 schoolbook kernel: [   51.363625] audit(1230042176.827:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5434 profile="/usr/sbin/cupsd" namespace="default"
Dec 23 07:22:56 schoolbook kernel: [   51.418319] apm: BIOS not found.
Dec 23 07:22:57 schoolbook kernel: [   51.739336] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:22:57 schoolbook kernel: [   51.739340] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:22:57 schoolbook kernel: [   51.740595] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:22:57 schoolbook kernel: [   51.740598] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:22:57 schoolbook kernel: [   52.115842] [drm] Initialized drm 1.1.0 20060810
Dec 23 07:22:57 schoolbook kernel: [   52.190769] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Dec 23 07:22:57 schoolbook kernel: [   52.190819] [drm] Initialized i915 1.6.0 20060119 on minor 0
Dec 23 07:22:58 schoolbook kernel: [   52.539272] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:22:58 schoolbook kernel: [   52.539277] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:22:58 schoolbook kernel: [   52.540119] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:22:58 schoolbook kernel: [   52.540123] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:22:58 schoolbook kernel: [   53.170320] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:22:58 schoolbook kernel: [   53.170324] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:22:58 schoolbook kernel: [   53.171581] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:22:58 schoolbook kernel: [   53.171584] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:23:03 schoolbook dhcdbd: Started up.
Dec 23 07:23:05 schoolbook kernel: [   59.603339] ADDRCONF(NETDEV_UP): eth1: link is not ready
Dec 23 07:23:05 schoolbook kernel: [   59.703203] r8169: eth0: link down
Dec 23 07:23:05 schoolbook kernel: [   59.707533] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 07:23:05 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 23 07:23:05 schoolbook kernel: [   59.843627] Bluetooth: L2CAP ver 2.9
Dec 23 07:23:05 schoolbook kernel: [   59.843635] Bluetooth: L2CAP socket layer initialized
Dec 23 07:23:05 schoolbook kernel: [   59.949659] Bluetooth: RFCOMM socket layer initialized
Dec 23 07:23:05 schoolbook kernel: [   59.949678] Bluetooth: RFCOMM TTY layer initialized
Dec 23 07:23:05 schoolbook kernel: [   59.949682] Bluetooth: RFCOMM ver 1.8
Dec 23 07:23:05 schoolbook kernel: [   59.978518] usb 3-1: new full speed USB device using uhci_hcd and address 6
Dec 23 07:23:06 schoolbook kernel: [   60.596183] usb 3-1: new full speed USB device using uhci_hcd and address 7
Dec 23 07:23:07 schoolbook kernel: [   61.158670] usb 3-1: new full speed USB device using uhci_hcd and address 8
Dec 23 07:23:07 schoolbook kernel: [   61.166401] NET: Registered protocol family 17
Dec 23 07:23:07 schoolbook kernel: [   61.677360] usb 3-1: new full speed USB device using uhci_hcd and address 9
Dec 23 07:23:09 schoolbook kernel: [   63.252649] vmmon: module license 'unspecified' taints kernel.
Dec 23 07:23:09 schoolbook kernel: [   63.745835] bridge-eth1: already up
Dec 23 07:23:09 schoolbook kernel: [   63.749714] bridge-eth0: already up
Dec 23 07:23:34 schoolbook kernel: [   69.485778] usb 3-1: new full speed USB device using uhci_hcd and address 10
Dec 23 07:23:35 schoolbook kernel: [   69.508821] usb 3-1: new full speed USB device using uhci_hcd and address 11
Dec 23 07:23:35 schoolbook kernel: [   69.528910] usb 3-1: new full speed USB device using uhci_hcd and address 12
Dec 23 07:23:36 schoolbook kernel: [   69.543860] usb 3-1: new full speed USB device using uhci_hcd and address 13
Dec 23 07:24:34 schoolbook kernel: [   98.545039] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:593: hda_intel: azx_get_response timeout, switching to polling mode: last cmd=0x006f000a
Dec 23 07:25:00 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Dec 23 07:25:05 schoolbook kernel: [  128.529319] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Dec 23 07:25:13 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Dec 23 07:25:13 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Dec 23 07:25:13 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Dec 23 07:25:13 schoolbook dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Dec 23 07:25:22 schoolbook kernel: [  145.745909] atkbd.c: Unknown key pressed (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:25:22 schoolbook kernel: [  145.745915] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:25:22 schoolbook kernel: [  145.747170] atkbd.c: Unknown key released (translated set 2, code 0xf7 on isa0060/serio0).
Dec 23 07:25:22 schoolbook kernel: [  145.747174] atkbd.c: Use 'setkeycodes e077 <keycode>' to make it known.
Dec 23 07:40:31 schoolbook kernel: [  433.094103] atkbd.c: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:40:31 schoolbook kernel: [  433.094113] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:40:31 schoolbook kernel: [  433.095371] atkbd.c: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
Dec 23 07:40:31 schoolbook kernel: [  433.095382] atkbd.c: Use 'setkeycodes e078 <keycode>' to make it known.
Dec 23 07:49:52 schoolbook kernel: [  628.781013] usb 3-1: new full speed USB device using uhci_hcd and address 14
Dec 23 07:49:52 schoolbook kernel: [  628.957058] usb 3-1: new full speed USB device using uhci_hcd and address 15
Dec 23 07:49:53 schoolbook kernel: [  629.117478] usb 3-1: new full speed USB device using uhci_hcd and address 16
Dec 23 07:49:53 schoolbook kernel: [  629.267039] usb 3-1: new full speed USB device using uhci_hcd and address 17
Dec 23 07:52:27 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 23 08:02:52 schoolbook -- MARK --
Dec 23 08:22:52 schoolbook -- MARK --
Dec 23 08:42:52 schoolbook -- MARK --
Dec 23 09:02:52 schoolbook -- MARK --
Dec 23 09:22:52 schoolbook -- MARK --
Dec 23 09:28:03 schoolbook kernel: [ 2109.763556] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:03 schoolbook kernel: [ 2109.763566] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:04 schoolbook kernel: [ 2109.795699] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:04 schoolbook kernel: [ 2109.795708] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:09 schoolbook kernel: [ 2111.157565] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:09 schoolbook kernel: [ 2111.157574] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:10 schoolbook kernel: [ 2111.196650] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:10 schoolbook kernel: [ 2111.196659] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:12 schoolbook kernel: [ 2111.894767] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:12 schoolbook kernel: [ 2111.894778] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:13 schoolbook kernel: [ 2111.932047] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:13 schoolbook kernel: [ 2111.932059] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:15 schoolbook kernel: [ 2112.425413] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:15 schoolbook kernel: [ 2112.425425] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:15 schoolbook kernel: [ 2112.473266] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:15 schoolbook kernel: [ 2112.473276] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:42:52 schoolbook -- MARK --
Dec 23 10:02:52 schoolbook -- MARK --
Dec 23 10:13:13 schoolbook kernel: [ 2800.970458] usb 3-1: new full speed USB device using uhci_hcd and address 18
Dec 23 10:13:14 schoolbook kernel: [ 2801.078374] usb 3-1: new full speed USB device using uhci_hcd and address 19
Dec 23 10:13:15 schoolbook kernel: [ 2801.178915] usb 3-1: new full speed USB device using uhci_hcd and address 20
Dec 23 10:13:15 schoolbook kernel: [ 2801.297297] usb 3-1: new full speed USB device using uhci_hcd and address 21
Dec 23 10:20:02 schoolbook kernel: [ 2923.782229] usb 7-1: new high speed USB device using ehci_hcd and address 8
Dec 23 10:20:03 schoolbook kernel: [ 2924.229187] usb 7-1: new high speed USB device using ehci_hcd and address 9
Dec 23 10:20:04 schoolbook kernel: [ 2924.562440] usb 3-1: new full speed USB device using uhci_hcd and address 22
Dec 23 10:20:04 schoolbook kernel: [ 2924.774623] usb 3-1: new full speed USB device using uhci_hcd and address 23
Dec 23 10:20:05 schoolbook kernel: [ 2925.014165] usb 3-1: new full speed USB device using uhci_hcd and address 24
Dec 23 10:20:05 schoolbook kernel: [ 2925.211599] usb 3-1: new full speed USB device using uhci_hcd and address 25
Dec 23 10:39:11 schoolbook kernel: [ 3248.194707] audit(1230053951.407:3): type=1503 operation="capable" name="dac_override" pid=20799 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Dec 23 10:39:11 schoolbook kernel: [ 3248.194725] audit(1230053951.407:4): type=1503 operation="capable" name="dac_read_search" pid=20799 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"

```

/var/log/syslog:
```
Dec 23 07:52:27 schoolbook syslogd 1.5.0#1ubuntu1: restart.
Dec 23 07:52:27 schoolbook anacron[6003]: Job `cron.daily' terminated
Dec 23 07:52:27 schoolbook anacron[6003]: Normal exit (1 job run)
Dec 23 08:00:02 schoolbook /USR/SBIN/CRON[9678]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 08:09:01 schoolbook /USR/SBIN/CRON[10276]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 08:17:01 schoolbook /USR/SBIN/CRON[10810]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 08:20:01 schoolbook /USR/SBIN/CRON[11006]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 08:39:01 schoolbook /USR/SBIN/CRON[12258]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 08:40:01 schoolbook /USR/SBIN/CRON[12331]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 09:00:01 schoolbook /USR/SBIN/CRON[13648]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 09:09:01 schoolbook /USR/SBIN/CRON[14293]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 09:17:01 schoolbook /USR/SBIN/CRON[14940]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 09:20:01 schoolbook /USR/SBIN/CRON[15137]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 09:28:03 schoolbook kernel: [ 2109.763556] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:03 schoolbook kernel: [ 2109.763566] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:04 schoolbook kernel: [ 2109.795699] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:04 schoolbook kernel: [ 2109.795708] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:09 schoolbook kernel: [ 2111.157565] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:09 schoolbook kernel: [ 2111.157574] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:10 schoolbook kernel: [ 2111.196650] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:10 schoolbook kernel: [ 2111.196659] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:12 schoolbook kernel: [ 2111.894767] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:12 schoolbook kernel: [ 2111.894778] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:13 schoolbook kernel: [ 2111.932047] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:13 schoolbook kernel: [ 2111.932059] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:15 schoolbook kernel: [ 2112.425413] atkbd.c: Unknown key pressed (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:15 schoolbook kernel: [ 2112.425425] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:28:15 schoolbook kernel: [ 2112.473266] atkbd.c: Unknown key released (translated set 2, code 0xe4 on isa0060/serio0).
Dec 23 09:28:15 schoolbook kernel: [ 2112.473276] atkbd.c: Use 'setkeycodes e064 <keycode>' to make it known.
Dec 23 09:39:01 schoolbook /USR/SBIN/CRON[16402]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 09:40:01 schoolbook /USR/SBIN/CRON[16471]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 10:00:01 schoolbook /USR/SBIN/CRON[17811]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 10:09:01 schoolbook /USR/SBIN/CRON[18412]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 10:13:13 schoolbook kernel: [ 2800.970458] usb 3-1: new full speed USB device using uhci_hcd and address 18
Dec 23 10:13:14 schoolbook kernel: [ 2800.998223] usb 3-1: device descriptor read/64, error -71
Dec 23 10:13:14 schoolbook kernel: [ 2801.039015] usb 3-1: device descriptor read/64, error -71
Dec 23 10:13:14 schoolbook kernel: [ 2801.078374] usb 3-1: new full speed USB device using uhci_hcd and address 19
Dec 23 10:13:14 schoolbook kernel: [ 2801.095032] usb 3-1: device descriptor read/64, error -71
Dec 23 10:13:14 schoolbook kernel: [ 2801.141908] usb 3-1: device descriptor read/64, error -71
Dec 23 10:13:15 schoolbook kernel: [ 2801.178915] usb 3-1: new full speed USB device using uhci_hcd and address 20
Dec 23 10:13:15 schoolbook kernel: [ 2801.268200] usb 3-1: device not accepting address 20, error -71
Dec 23 10:13:15 schoolbook kernel: [ 2801.297297] usb 3-1: new full speed USB device using uhci_hcd and address 21
Dec 23 10:13:15 schoolbook kernel: [ 2801.376068] usb 3-1: device not accepting address 21, error -71
Dec 23 10:17:01 schoolbook /USR/SBIN/CRON[18943]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 10:20:01 schoolbook /USR/SBIN/CRON[19140]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec 23 10:20:02 schoolbook kernel: [ 2923.782229] usb 7-1: new high speed USB device using ehci_hcd and address 8
Dec 23 10:20:03 schoolbook kernel: [ 2924.229187] usb 7-1: new high speed USB device using ehci_hcd and address 9
Dec 23 10:20:04 schoolbook kernel: [ 2924.562440] usb 3-1: new full speed USB device using uhci_hcd and address 22
Dec 23 10:20:04 schoolbook kernel: [ 2924.607262] usb 3-1: device descriptor read/64, error -71
Dec 23 10:20:04 schoolbook kernel: [ 2924.694683] usb 3-1: device descriptor read/64, error -71
Dec 23 10:20:04 schoolbook kernel: [ 2924.774623] usb 3-1: new full speed USB device using uhci_hcd and address 23
Dec 23 10:20:04 schoolbook kernel: [ 2924.818543] usb 3-1: device descriptor read/64, error -71
Dec 23 10:20:05 schoolbook kernel: [ 2924.915639] usb 3-1: device descriptor read/64, error -71
Dec 23 10:20:05 schoolbook kernel: [ 2925.014165] usb 3-1: new full speed USB device using uhci_hcd and address 24
Dec 23 10:20:05 schoolbook kernel: [ 2925.167458] usb 3-1: device not accepting address 24, error -71
Dec 23 10:20:05 schoolbook kernel: [ 2925.211599] usb 3-1: new full speed USB device using uhci_hcd and address 25
Dec 23 10:20:06 schoolbook kernel: [ 2925.366409] usb 3-1: device not accepting address 25, error -71
Dec 23 10:32:12 schoolbook kernel: [ 3130.138724] /dev/vmmon[20215]: Module vmmon: unloaded
Dec 23 10:32:12 schoolbook kernel: [ 3130.485140] bridge-eth1: down
Dec 23 10:32:12 schoolbook kernel: [ 3130.485155] bridge-eth1: detached
Dec 23 10:32:14 schoolbook avahi-daemon[5403]: Interface vmnet1.IPv4 no longer relevant for mDNS.
Dec 23 10:32:14 schoolbook avahi-daemon[5403]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 192.168.189.1.
Dec 23 10:32:14 schoolbook avahi-daemon[5403]: Withdrawing address record for fe80::250:56ff:fec0:1 on vmnet1.
Dec 23 10:32:14 schoolbook avahi-daemon[5403]: Withdrawing address record for 192.168.189.1 on vmnet1.
Dec 23 10:32:16 schoolbook kernel: [ 3131.213817] bridge-eth0: down
Dec 23 10:32:16 schoolbook kernel: [ 3131.213839] bridge-eth0: detached
Dec 23 10:32:19 schoolbook avahi-daemon[5403]: Interface vmnet8.IPv4 no longer relevant for mDNS.
Dec 23 10:32:19 schoolbook avahi-daemon[5403]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 192.168.100.1.
Dec 23 10:32:19 schoolbook avahi-daemon[5403]: Withdrawing address record for fe80::250:56ff:fec0:8 on vmnet8.
Dec 23 10:32:19 schoolbook avahi-daemon[5403]: Withdrawing address record for 192.168.100.1 on vmnet8.
Dec 23 10:39:01 schoolbook /USR/SBIN/CRON[20778]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 23 10:39:11 schoolbook kernel: [ 3248.194707] audit(1230053951.407:3): type=1503 operation="capable" name="dac_override" pid=20799 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Dec 23 10:39:11 schoolbook kernel: [ 3248.194725] audit(1230053951.407:4): type=1503 operation="capable" name="dac_read_search" pid=20799 profile="/usr/lib/cups/backend/cups-pdf" namespace="default"
Dec 23 10:40:01 schoolbook /USR/SBIN/CRON[20857]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

```

---

### Post by thomasaaron on 2008-12-23
Interesting. You have a ton of phantom keypress errors. Are you using
acpi=noirq as a kernel option in your menu.lst? If you don't know, post your /boot/grub/menu.lst file.

I'm not seeing the tell-tale errors that would indicate your touchpad is going bad. However, that doesn't look like all of your syslog either.

---

### Post by imhavoc on 2008-12-23
hrmm... acpi=noirq must have gotten dropped during some previous wrestling with the system...

I've added it to defoptions=... , and I'll reboot and test.

If that fails, I'll repost my my syslog (without trying to cheat this time).

brb.

---

### Post by imhavoc on 2008-12-23
adding it to defoptions didn't do anything.

I appended it to the kernel line, and rebooted. *viola!*

thanks, Thomas! Merry Christmas! Safe Travels.

---

### Post by imhavoc on 2008-12-30
It's up after one boot and down again after the next. Here are my syslog and messages log.

---

### Post by thomasaaron on 2008-12-30
OK, here's my hunch: I don't think it is hardware. I've seen the touchpads go bad on DarU2 notebooks, and I'm familiar with the errors that indicate the failure. You don't have them.

However, you have a lot of "setkeycode" errors that indicate your keymapping might be hosed. It could be that this is disabling your touchpad somewhat randomly.

Here are some thoughts and things to try, which will either confirm my hunch or... blow it out of the water. 

1. See if it happens when booting from a live CD. If it does, it's hardware. If not, it's configuration-related.

2. Go to System > Preferences > Keyboard > Layout and tell me how your keyboard is configured. Is it the standard U.S. layout?

3. Have you installed any touchpad controlling software? Gsynaptics? Others? If you have more than one installed, they could be conflicting.

4. If your keyboard is set to the standard U.S. layout, you might try clicking the 'keyboard model' button and then, in the lower text area that appears, select 'EvDev Managed Keyboard' to see if that fixes it. If not, go back to the U.S. layout. You'll probably need to reboot after changing it.

---

### Post by imhavoc on 2009-01-02
Looks like the mouse is suffering intermittent failure. The first time I booted with a boot disc, it worked fine. Tonight, however, it failed.

Bummer. I'm going to pick up a mouse tomorrow. We're in Albuquerque this weekend, so at least I'll have some decent choices.

---

### Post by imhavoc on 2009-01-02
Thomas, can you post a known-working, clean, video-accelerated xorg.conf for the daru2?

---

### Post by thomasaaron on 2009-01-02
I can do that when I return to work on Monday.

---

### Post by imhavoc on 2009-01-16
bump (xorg.conf)

---

### Post by thomasaaron on 2009-01-16
Oops! Sorry, I forgot.

I'm imaging one now. Stand by...

(Note: You said it did it from a live CD. That probably points to hardware.)

---

### Post by imhavoc on 2009-01-16
I picked up a Logitech notebook VX mouse. It's actually an improvement. I just wouldn't have laid out the cash for one without having a broekn touchpad, so it works out okay overall.

I'm just pretty convinced that my xorg.conf is reflective of "minced meat," and I'd like something more coherent.

---

### Post by thomasaaron on 2009-01-16
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

