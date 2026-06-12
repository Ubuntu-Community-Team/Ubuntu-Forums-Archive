---
title: "Apache2 does not star at boot after upgrade to fesity"
date: 2007-04-25
forum: Server Platforms
---

### Post by GoBieN on 2007-04-25
After upgrade to fesity, some services don't start at boot.
Apache2, webmin, ventrilo, proftpd they don't start at boot.

I've tried reinstalling apache2 and apache2-common. Webmin says the init.d script are ativated to start at boot time. What could be causing this ?

---

### Post by falcon15500 on 2007-04-25
Firstly, check to make sure the soft links from **/etc/rc.2** are pointing correctly to the scripts in **/etc/init.d**

If that's okay, I would try a:  ```
sudo /etc/init.d/apache2 start
```

And checkout the resulting output to stdin.  It may give you a clue?


falc

---

### Post by GoBieN on 2007-04-26
> stan@ARES:/etc/rc2.d$ ls -al S91apache2
lrwxrwxrwx 1 root root 17 2007-01-07 22:24 S91apache2 -> ../init.d/apache2

So the link is there. And "/etc/init.d/apache2 start" works fine thats what i use after i saw that apache2 wasn't up after boot.

So the link is there, apache works when manually started by "/etc/init.d/apache2"

Is rc2 the correct runlevel ? With the new upstart system and all ?

ps:
```
Apr 25 20:43:19 ares kernel: Inspecting /boot/System.map-2.6.20-15-server
Apr 25 20:43:19 ares kernel: Loaded 25134 symbols from /boot/System.map-2.6.20-15-server.
Apr 25 20:43:19 ares kernel: Symbols match kernel version 2.6.20.
Apr 25 20:43:19 ares kernel: No module symbols loaded - kernel modules not enabled. 
Apr 25 20:43:19 ares kernel: [    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
Apr 25 20:43:19 ares kernel: [    0.000000] BIOS-provided physical RAM map:
Apr 25 20:43:19 ares kernel: [    0.000000] sanitize start
Apr 25 20:43:19 ares kernel: [    0.000000] sanitize end
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f000 end: 000000000009f000 type: 1
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 000000000009f000 size: 0000000000001000 end: 00000000000a0000 type: 2
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 00000000000eac00 size: 0000000000015400 end: 0000000000100000 type: 2
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000002fef0000 end: 000000002fff0000 type: 1
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() type is E820_RAM
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 000000002fff0000 size: 000000000000fc00 end: 000000002ffffc00 type: 3
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 000000002ffffc00 size: 0000000000000400 end: 0000000030000000 type: 4
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Apr 25 20:43:19 ares kernel: [    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 00000000000eac00 - 0000000000100000 (reserved)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000002fff0000 (usable)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 000000002fff0000 - 000000002ffffc00 (ACPI data)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 000000002ffffc00 - 0000000030000000 (ACPI NVS)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Apr 25 20:43:19 ares kernel: [    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Apr 25 20:43:19 ares kernel: [    0.000000] 0MB HIGHMEM available.
Apr 25 20:43:19 ares kernel: [    0.000000] 767MB LOWMEM available.
Apr 25 20:43:19 ares kernel: [    0.000000] found SMP MP-table at 000f6f60
Apr 25 20:43:19 ares kernel: [    0.000000] Zone PFN ranges:
Apr 25 20:43:19 ares kernel: [    0.000000]   DMA             0 ->     4096
Apr 25 20:43:19 ares kernel: [    0.000000]   Normal       4096 ->   196592
Apr 25 20:43:19 ares kernel: [    0.000000]   HighMem    196592 ->   196592
Apr 25 20:43:19 ares kernel: [    0.000000] early_node_map[1] active PFN ranges
Apr 25 20:43:19 ares kernel: [    0.000000]     0:        0 ->   196592
Apr 25 20:43:19 ares kernel: [    0.000000] DMI 2.3 present.
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1208
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x03] enabled)
Apr 25 20:43:19 ares kernel: [    0.000000] Processor #3 6:8 APIC version 17
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Apr 25 20:43:19 ares kernel: [    0.000000] Processor #0 6:8 APIC version 17
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Apr 25 20:43:19 ares kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-15
Apr 25 20:43:19 ares kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec01000] gsi_base[16])
Apr 25 20:43:19 ares kernel: [    0.000000] IOAPIC[1]: apic_id 2, version 17, address 0xfec01000, GSI 16-31
Apr 25 20:43:19 ares kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 2 I/O APICs
Apr 25 20:43:19 ares kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 25 20:43:19 ares kernel: [    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
Apr 25 20:43:19 ares kernel: [    0.000000] Detected 1000.168 MHz processor.
Apr 25 20:43:19 ares kernel: [  108.169768] Built 1 zonelists.  Total pages: 195057
Apr 25 20:43:19 ares kernel: [  108.169777] Kernel command line: root=UUID=1a6601a5-a8de-23fe-d156-14228c51510e ro quiet splash
Apr 25 20:43:19 ares kernel: [  108.170209] Enabling fast FPU save and restore... done.
Apr 25 20:43:19 ares kernel: [  108.170215] Enabling unmasked SIMD FPU exception support... done.
Apr 25 20:43:19 ares kernel: [  108.170234] Initializing CPU#0
Apr 25 20:43:19 ares kernel: [  108.170317] PID hash table entries: 4096 (order: 12, 16384 bytes)
Apr 25 20:43:19 ares kernel: [  108.171938] Console: colour VGA+ 80x25
Apr 25 20:43:19 ares kernel: [  108.173304] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Apr 25 20:43:19 ares kernel: [  108.176028] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Apr 25 20:43:19 ares kernel: [  108.244725] Memory: 767004k/786368k available (2020k kernel code, 18812k reserved, 893k data, 328k init, 0k highmem)
Apr 25 20:43:19 ares kernel: [  108.244749] virtual kernel memory layout:
Apr 25 20:43:19 ares kernel: [  108.244751]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Apr 25 20:43:19 ares kernel: [  108.244754]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Apr 25 20:43:19 ares kernel: [  108.244758]     vmalloc : 0xf0800000 - 0xffbfe000   ( 243 MB)
Apr 25 20:43:19 ares kernel: [  108.244761]     lowmem  : 0xc0000000 - 0xefff0000   ( 767 MB)
Apr 25 20:43:19 ares kernel: [  108.244764]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
Apr 25 20:43:19 ares kernel: [  108.244767]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
Apr 25 20:43:19 ares kernel: [  108.244770]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
Apr 25 20:43:19 ares kernel: [  108.244777] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Apr 25 20:43:19 ares kernel: [  108.390120] Calibrating delay using timer specific routine.. 2001.05 BogoMIPS (lpj=10005277)
Apr 25 20:43:19 ares kernel: [  108.390207] Security Framework v1.0.0 initialized
Apr 25 20:43:19 ares kernel: [  108.390225] SELinux:  Disabled at boot.
Apr 25 20:43:19 ares kernel: [  108.390259] Mount-cache hash table entries: 512
Apr 25 20:43:19 ares kernel: [  108.390538] CPU: L1 I cache: 16K, L1 D cache: 16K
Apr 25 20:43:19 ares kernel: [  108.390544] CPU: L2 cache: 256K
Apr 25 20:43:19 ares kernel: [  108.390550] CPU serial number disabled.
Apr 25 20:43:19 ares kernel: [  108.390573] Compat vDSO mapped to ffffe000.
Apr 25 20:43:19 ares kernel: [  108.390589] Remapping vsyscall page to ffffe000
Apr 25 20:43:19 ares kernel: [  108.390608] Checking 'hlt' instruction... OK.
Apr 25 20:43:19 ares kernel: [  108.430262] SMP alternatives: switching to UP code
Apr 25 20:43:19 ares kernel: [  108.430909] Early unpacking initramfs... done
Apr 25 20:43:19 ares kernel: [  109.175390] ACPI: Core revision 20060707
Apr 25 20:43:19 ares kernel: [  109.176389] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Apr 25 20:43:19 ares kernel: [  109.179716] CPU0: Intel Pentium III (Coppermine) stepping 0a
Apr 25 20:43:19 ares kernel: [  109.179774] SMP alternatives: switching to SMP code
Apr 25 20:43:19 ares kernel: [  109.179960] Booting processor 1/0 eip 3000
Apr 25 20:43:19 ares kernel: [  109.190241] Initializing CPU#1
Apr 25 20:43:19 ares kernel: [  109.339237] Calibrating delay using timer specific routine.. 2000.15 BogoMIPS (lpj=10000766)
Apr 25 20:43:19 ares kernel: [  109.339267] CPU: L1 I cache: 16K, L1 D cache: 16K
Apr 25 20:43:19 ares kernel: [  109.339272] CPU: L2 cache: 256K
Apr 25 20:43:19 ares kernel: [  109.339277] CPU serial number disabled.
Apr 25 20:43:19 ares kernel: [  109.339577] CPU1: Intel Pentium III (Coppermine) stepping 0a
Apr 25 20:43:19 ares kernel: [  109.339622] Total of 2 processors activated (4001.20 BogoMIPS).
Apr 25 20:43:19 ares kernel: [  109.339946] ENABLING IO-APIC IRQs
Apr 25 20:43:19 ares kernel: [  109.340203] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
Apr 25 20:43:19 ares kernel: [  109.559048] checking TSC synchronization across 2 CPUs: passed.
Apr 25 20:43:19 ares kernel: [    0.009994] Brought up 2 CPUs
Apr 25 20:43:19 ares kernel: [    0.128562] migration_cost=887
Apr 25 20:43:19 ares kernel: [    0.129147] Booting paravirtualized kernel on bare hardware
Apr 25 20:43:19 ares kernel: [    0.129298] Time: 20:42:32  Date: 03/25/107
Apr 25 20:43:19 ares kernel: [    0.129372] NET: Registered protocol family 16
Apr 25 20:43:19 ares kernel: [    0.129554] EISA bus registered
Apr 25 20:43:19 ares kernel: [    0.129564] ACPI: bus type pci registered
Apr 25 20:43:19 ares kernel: [    0.130755] PCI: PCI BIOS revision 2.10 entry at 0xfd9e1, last bus=7
Apr 25 20:43:19 ares kernel: [    0.130761] PCI: Using configuration type 1
Apr 25 20:43:19 ares kernel: [    0.130765] Setting up standard PCI resources
Apr 25 20:43:19 ares kernel: [    0.139784] ACPI: Interpreter enabled
Apr 25 20:43:19 ares kernel: [    0.139794] ACPI: Using IOAPIC for interrupt routing
Apr 25 20:43:19 ares kernel: [    0.140558] ACPI: PCI Root Bridge [PCI0] (0000:00)
Apr 25 20:43:19 ares kernel: [    0.142429] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr 25 20:43:19 ares kernel: [    0.142432] * this clock source is slow. If you are sure your timer does not have
Apr 25 20:43:19 ares kernel: [    0.142436] * this bug, please use "acpi_pm_good" to disable the workaround
Apr 25 20:43:19 ares kernel: [    0.142470] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
Apr 25 20:43:19 ares kernel: [    0.142473] * this clock source is slow. If you are sure your timer does not have
Apr 25 20:43:19 ares kernel: [    0.142477] * this bug, please use "acpi_pm_good" to disable the workaround
Apr 25 20:43:19 ares kernel: [    0.142523] PCI: Firmware left 0000:00:02.0 e100 interrupts enabled, disabling
Apr 25 20:43:19 ares kernel: [    0.144388] ACPI: PCI Interrupt Link [LNKU] (IRQs 5) *10
Apr 25 20:43:19 ares kernel: [    0.144757] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.145129] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.145499] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.145883] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.146310] ACPI: PCI Interrupt Link [LNK4] (IRQs 9 *11)
Apr 25 20:43:19 ares kernel: [    0.146681] ACPI: PCI Interrupt Link [LNK5] (IRQs 9 11) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.147051] ACPI: PCI Interrupt Link [LNK6] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.147443] ACPI: PCI Interrupt Link [LNK7] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.147865] ACPI: PCI Interrupt Link [LNK8] (IRQs 3 4 *5 7 10 11 12 14 15)
Apr 25 20:43:19 ares kernel: [    0.148287] ACPI: PCI Interrupt Link [LNK9] (IRQs 3 4 5 7 10 11 12 14 15) *9
Apr 25 20:43:19 ares kernel: [    0.148661] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.149037] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.149411] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.149788] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.150181] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.150556] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.150821] ACPI: Blank IRQ resource
Apr 25 20:43:19 ares kernel: [    0.150909] ACPI: PCI Interrupt Link [LNKX] (IRQs) *0, disabled.
Apr 25 20:43:19 ares kernel: [    0.153586] ACPI: PCI Root Bridge [PCI1] (0000:05)
Apr 25 20:43:19 ares kernel: [    0.157731] Linux Plug and Play Support v0.97 (c) Adam Belay
Apr 25 20:43:19 ares kernel: [    0.157767] pnp: PnP ACPI init
Apr 25 20:43:19 ares kernel: [    0.164322] pnp: PnP ACPI: found 13 devices
Apr 25 20:43:19 ares kernel: [    0.164332] PnPBIOS: Disabled by ACPI PNP
Apr 25 20:43:19 ares kernel: [    0.164463] PCI: Using ACPI for IRQ routing
Apr 25 20:43:19 ares kernel: [    0.164471] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Apr 25 20:43:19 ares kernel: [    0.167671] NET: Registered protocol family 8
Apr 25 20:43:19 ares kernel: [    0.167677] NET: Registered protocol family 20
Apr 25 20:43:19 ares kernel: [    0.167696] NetLabel: Initializing
Apr 25 20:43:19 ares kernel: [    0.167700] NetLabel:  domain hash size = 128
Apr 25 20:43:19 ares kernel: [    0.167704] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 25 20:43:19 ares kernel: [    0.167734] NetLabel:  unlabeled traffic allowed by default
Apr 25 20:43:19 ares kernel: [    0.167933] pnp: 00:05: ioport range 0xf50-0xf58 has been reserved
Apr 25 20:43:19 ares kernel: [    0.167940] pnp: 00:05: ioport range 0x1100-0x111f could not be reserved
Apr 25 20:43:19 ares kernel: [    0.167947] pnp: 00:05: ioport range 0x1200-0x121f could not be reserved
Apr 25 20:43:19 ares kernel: [    0.168704] NET: Registered protocol family 2
Apr 25 20:43:19 ares kernel: [    0.269900] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Apr 25 20:43:19 ares kernel: [    0.270282] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Apr 25 20:43:19 ares kernel: [    0.274901] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Apr 25 20:43:19 ares kernel: [    0.277280] TCP: Hash tables configured (established 131072 bind 65536)
Apr 25 20:43:19 ares kernel: [    0.277289] TCP reno registered
Apr 25 20:43:19 ares kernel: [    0.310035] checking if image is initramfs... it is
Apr 25 20:43:19 ares kernel: [    1.719681] Freeing initrd memory: 8111k freed
Apr 25 20:43:19 ares kernel: [    1.720171] Simple Boot Flag at 0x35 set to 0x1
Apr 25 20:43:19 ares kernel: [    1.720737] audit: initializing netlink socket (disabled)
Apr 25 20:43:19 ares kernel: [    1.720765] audit(1177533753.960:1): initialized
Apr 25 20:43:19 ares kernel: [    1.721094] VFS: Disk quotas dquot_6.5.1
Apr 25 20:43:19 ares kernel: [    1.721142] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Apr 25 20:43:19 ares kernel: [    1.721267] io scheduler noop registered
Apr 25 20:43:19 ares kernel: [    1.721274] io scheduler anticipatory registered
Apr 25 20:43:19 ares kernel: [    1.721279] io scheduler deadline registered (default)
Apr 25 20:43:19 ares kernel: [    1.721312] io scheduler cfq registered
Apr 25 20:43:19 ares kernel: [    1.721815] isapnp: Scanning for PnP cards...
Apr 25 20:43:19 ares kernel: [    2.077673] isapnp: No Plug & Play device found
Apr 25 20:43:19 ares kernel: [    2.148662] Real Time Clock Driver v1.12ac
Apr 25 20:43:19 ares kernel: [    2.148764] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Apr 25 20:43:19 ares kernel: [    2.148989] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 25 20:43:19 ares kernel: [    2.149406] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 25 20:43:19 ares kernel: [    2.150785] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 25 20:43:19 ares kernel: [    2.151343] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Apr 25 20:43:19 ares kernel: [    2.151876] mice: PS/2 mouse device common for all mice
Apr 25 20:43:19 ares kernel: [    2.153187] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Apr 25 20:43:19 ares kernel: [    2.153706] input: Macintosh mouse button emulation as /class/input/input0
Apr 25 20:43:19 ares kernel: [    2.153788] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Apr 25 20:43:19 ares kernel: [    2.153797] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Apr 25 20:43:19 ares kernel: [    2.154181] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
Apr 25 20:43:19 ares kernel: [    2.158526] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 25 20:43:19 ares kernel: [    2.158542] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 25 20:43:19 ares kernel: [    2.158902] EISA: Probing bus 0 at eisa.0
Apr 25 20:43:19 ares kernel: [    2.158923] Cannot allocate resource for EISA slot 1
Apr 25 20:43:19 ares kernel: [    2.158930] Cannot allocate resource for EISA slot 2
Apr 25 20:43:19 ares kernel: [    2.158977] EISA: Detected 0 cards.
Apr 25 20:43:19 ares kernel: [    2.189365] TCP cubic registered
Apr 25 20:43:19 ares kernel: [    2.189393] NET: Registered protocol family 1
Apr 25 20:43:19 ares kernel: [    2.189450] Starting balanced_irq
Apr 25 20:43:19 ares kernel: [    2.189474] Using IPI No-Shortcut mode
Apr 25 20:43:19 ares kernel: [    2.189663] input: AT Translated Set 2 keyboard as /class/input/input1
Apr 25 20:43:19 ares kernel: [    2.189756] ACPI: (supports S0 S1 S5)
Apr 25 20:43:19 ares kernel: [    2.189847]   Magic number: 3:672:751
Apr 25 20:43:19 ares kernel: [    2.189856]   hash matches device ttyS2
Apr 25 20:43:19 ares kernel: [    2.190611] Freeing unused kernel memory: 328k freed
Apr 25 20:43:19 ares kernel: [    2.197957] Time: tsc clocksource has been installed.
Apr 25 20:43:19 ares kernel: [    3.682747] Capability LSM initialized
Apr 25 20:43:19 ares kernel: [    3.722847] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
Apr 25 20:43:19 ares kernel: [    4.142515] md: linear personality registered for level -1
Apr 25 20:43:19 ares kernel: [    4.152652] md: multipath personality registered for level -4
Apr 25 20:43:19 ares kernel: [    4.161112] md: raid0 personality registered for level 0
Apr 25 20:43:19 ares kernel: [    4.171399] md: raid1 personality registered for level 1
Apr 25 20:43:19 ares kernel: [    4.179643] raid5: automatically using best checksumming function: pIII_sse
Apr 25 20:43:19 ares kernel: [    4.226063]    pIII_sse  :  1991.600 MB/sec
Apr 25 20:43:19 ares kernel: [    4.226068] raid5: using function: pIII_sse (1991.600 MB/sec)
Apr 25 20:43:19 ares kernel: [    4.396023] raid6: int32x1    306 MB/s
Apr 25 20:43:19 ares kernel: [    4.565753] raid6: int32x2    357 MB/s
Apr 25 20:43:19 ares kernel: [    4.735645] raid6: int32x4    289 MB/s
Apr 25 20:43:19 ares kernel: [    4.905646] raid6: int32x8    258 MB/s
Apr 25 20:43:19 ares kernel: [    5.075282] raid6: mmxx1      908 MB/s
Apr 25 20:43:19 ares kernel: [    5.245150] raid6: mmxx2     1135 MB/s
Apr 25 20:43:19 ares kernel: [    5.414974] raid6: sse1x1     800 MB/s
Apr 25 20:43:19 ares kernel: [    5.584854] raid6: sse1x2    1126 MB/s
Apr 25 20:43:19 ares kernel: [    5.584858] raid6: using algorithm sse1x2 (1126 MB/s)
Apr 25 20:43:19 ares kernel: [    5.584867] md: raid6 personality registered for level 6
Apr 25 20:43:19 ares kernel: [    5.584872] md: raid5 personality registered for level 5
Apr 25 20:43:19 ares kernel: [    5.584876] md: raid4 personality registered for level 4
Apr 25 20:43:19 ares kernel: [    5.601108] SCSI subsystem initialized
Apr 25 20:43:19 ares kernel: [    5.638328] usbcore: registered new interface driver usbfs
Apr 25 20:43:19 ares kernel: [    5.638377] usbcore: registered new interface driver hub
Apr 25 20:43:19 ares kernel: [    5.638468] usbcore: registered new device driver usb
Apr 25 20:43:19 ares kernel: [    5.642041] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
Apr 25 20:43:19 ares kernel: [    5.642049] e100: Copyright(c) 1999-2006 Intel Corporation
Apr 25 20:43:19 ares kernel: [    5.642150] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 20 (level, low) -> IRQ 16
Apr 25 20:43:19 ares kernel: [    5.665853] e100: eth0: e100_probe: addr 0xfd100000, irq 16, MAC addr 00:E0:18:59:9F:0B
Apr 25 20:43:19 ares kernel: [    5.783210] Floppy drive(s): fd0 is 1.44M
Apr 25 20:43:19 ares kernel: [    5.793221] ACPI: PCI Interrupt 0000:05:05.0[A] -> GSI 24 (level, low) -> IRQ 17
Apr 25 20:43:19 ares kernel: [    5.946001] sym0: <896> rev 0x7 at pci 0000:05:05.0 irq 17
Apr 25 20:43:19 ares kernel: [    5.948200] sym0: Symbios NVRAM, ID 7, Fast-40, LVD, parity checking
Apr 25 20:43:19 ares kernel: [    5.948206] sym0: open drain IRQ line driver, using on-chip SRAM
Apr 25 20:43:19 ares kernel: [    5.948211] sym0: using LOAD/STORE-based firmware.
Apr 25 20:43:19 ares kernel: [    5.948215] sym0: handling phase mismatch from SCRIPTS.
Apr 25 20:43:19 ares kernel: [    5.955020] sym0: SCSI BUS has been reset.
Apr 25 20:43:19 ares kernel: [    5.955041] scsi0 : sym-2.2.3
Apr 25 20:43:19 ares kernel: [    5.955150] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011840 irq 14
Apr 25 20:43:19 ares kernel: [    5.955292] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011848 irq 15
Apr 25 20:43:19 ares kernel: [    5.955328] scsi1 : pata_serverworks
Apr 25 20:43:19 ares kernel: [    5.955364] ACPI: PCI Interrupt 0000:05:05.1[B] -> GSI 25 (level, low) -> IRQ 18
Apr 25 20:43:19 ares kernel: [    6.107718] sym1: <896> rev 0x7 at pci 0000:05:05.1 irq 18
Apr 25 20:43:19 ares kernel: [    6.107925] md: raid10 personality registered for level 10
Apr 25 20:43:19 ares kernel: [    6.109904] sym1: Symbios NVRAM, ID 7, Fast-40, LVD, parity checking
Apr 25 20:43:19 ares kernel: [    6.109910] sym1: open drain IRQ line driver, using on-chip SRAM
Apr 25 20:43:19 ares kernel: [    6.109915] sym1: using LOAD/STORE-based firmware.
Apr 25 20:43:19 ares kernel: [    6.109919] sym1: handling phase mismatch from SCRIPTS.
Apr 25 20:43:19 ares kernel: [    6.117386] sym1: SCSI BUS has been reset.
Apr 25 20:43:19 ares kernel: [    6.117401] scsi3 : sym-2.2.3
Apr 25 20:43:19 ares kernel: [    6.118232] FDC 0 is a National Semiconductor PC87306
Apr 25 20:43:19 ares kernel: [    6.185410] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 25 20:43:19 ares kernel: [    6.185422] ata1.00: ATA-6: WDC WD800JB-00ETA0, 77.07W77, max UDMA/100
Apr 25 20:43:19 ares kernel: [    6.185429] ata1.00: 156301488 sectors, multi 16: LBA48 
Apr 25 20:43:19 ares kernel: [    6.185652] ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
Apr 25 20:43:19 ares kernel: [    6.185659] ata1.01: ATA-7: Maxtor 4R160L0, RAMB1TU0, max UDMA/133
Apr 25 20:43:19 ares kernel: [    6.185665] ata1.01: 320173056 sectors, multi 16: LBA48 
Apr 25 20:43:19 ares kernel: [    6.215293] ata1.00: ata_hpa_resize 1: sectors = 156301488, hpa_sectors = 156301488
Apr 25 20:43:19 ares kernel: [    6.215300] ata1.00: configured for MWDMA2
Apr 25 20:43:19 ares kernel: [    6.244488] ata1.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
Apr 25 20:43:19 ares kernel: [    6.244494] ata1.01: configured for MWDMA2
Apr 25 20:43:19 ares kernel: [    6.244521] scsi2 : pata_serverworks
Apr 25 20:43:19 ares kernel: [    6.644085] ata2.00: ATAPI, max MWDMA2
Apr 25 20:43:19 ares kernel: [    6.644321] ata2.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
Apr 25 20:43:19 ares kernel: [    6.644332] ata2.01: ATA-7: Maxtor 4R160L0, RAMB1TU0, max UDMA/133
Apr 25 20:43:19 ares kernel: [    6.644339] ata2.01: 320173056 sectors, multi 16: LBA48 
Apr 25 20:43:19 ares kernel: [    6.843883] ata2.00: configured for MWDMA2
Apr 25 20:43:19 ares kernel: [    6.873894] ata2.01: ata_hpa_resize 1: sectors = 320173056, hpa_sectors = 320173056
Apr 25 20:43:19 ares kernel: [    6.873901] ata2.01: configured for MWDMA2
Apr 25 20:43:19 ares kernel: [    6.873929] scsi: waiting for bus probes to complete ...
Apr 25 20:43:19 ares kernel: [    8.965702] scsi 0:0:0:0: Direct-Access     HP 18.2G ST318406LW       HP04 PQ: 0 ANSI: 2
Apr 25 20:43:19 ares kernel: [    8.965722]  target0:0:0: tagged command queuing enabled, command queue depth 16.
Apr 25 20:43:19 ares kernel: [    8.965740]  target0:0:0: Beginning Domain Validation
Apr 25 20:43:19 ares kernel: [    8.966231]  target0:0:0: asynchronous
Apr 25 20:43:19 ares kernel: [    8.977085]  target0:0:0: wide asynchronous
Apr 25 20:43:19 ares kernel: [    8.981570]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 31)
Apr 25 20:43:19 ares kernel: [    8.987517]  target0:0:0: Domain Validation skipping write tests
Apr 25 20:43:19 ares kernel: [    8.987523]  target0:0:0: Ending Domain Validation
Apr 25 20:43:19 ares kernel: [   10.189233] scsi 0:0:5:0: Sequential-Access HP       C5683A           C911 PQ: 0 ANSI: 2
Apr 25 20:43:19 ares kernel: [   10.189268]  target0:0:5: Beginning Domain Validation
Apr 25 20:43:19 ares kernel: [   10.189569]  target0:0:5: asynchronous
Apr 25 20:43:19 ares kernel: [   10.195358]  target0:0:5: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 31)
Apr 25 20:43:19 ares kernel: [   10.197532]  target0:0:5: Domain Validation skipping write tests
Apr 25 20:43:19 ares kernel: [   10.197537]  target0:0:5: Ending Domain Validation
Apr 25 20:43:19 ares kernel: [   12.855191] SCSI device sda: 35566480 512-byte hdwr sectors (18210 MB)
Apr 25 20:43:19 ares kernel: [   12.856422] sda: Write Protect is off
Apr 25 20:43:19 ares kernel: [   12.858259] SCSI device sda: write cache: enabled, read cache: enabled, supports DPO and FUA
Apr 25 20:43:19 ares kernel: [   12.859275] SCSI device sda: 35566480 512-byte hdwr sectors (18210 MB)
Apr 25 20:43:19 ares kernel: [   12.860493] sda: Write Protect is off
Apr 25 20:43:19 ares kernel: [   12.862328] SCSI device sda: write cache: enabled, read cache: enabled, supports DPO and FUA
Apr 25 20:43:19 ares kernel: [   12.862335]  sda:<6>st: Version 20061107, fixed bufsize 32768, s/g segs 256
Apr 25 20:43:19 ares kernel: [   12.872262]  sda1
Apr 25 20:43:19 ares kernel: [   12.872394] sd 0:0:0:0: Attached scsi disk sda
Apr 25 20:43:19 ares kernel: [   12.873194] st 0:0:5:0: Attached scsi tape st0
Apr 25 20:43:19 ares kernel: [   12.873203] st 0:0:5:0: st0: try direct i/o: yes (alignment 512 B)
Apr 25 20:43:19 ares kernel: [   12.885891] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 25 20:43:19 ares kernel: [   12.885944] st 0:0:5:0: Attached scsi generic sg1 type 1
Apr 25 20:43:19 ares kernel: [   12.899022]  target0:0:5: FAST-20 SCSI 20.0 MB/s ST (50 ns, offset 31)
Apr 25 20:43:19 ares kernel: [   12.911675] st0: Block limits 1 - 16777215 bytes.
Apr 25 20:43:19 ares kernel: [   13.591188] scsi 1:0:0:0: Direct-Access     ATA      WDC WD800JB-00ET 77.0 PQ: 0 ANSI: 5
Apr 25 20:43:19 ares kernel: [   13.591359] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
Apr 25 20:43:19 ares kernel: [   13.591388] sdb: Write Protect is off
Apr 25 20:43:19 ares kernel: [   13.591429] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   13.591538] SCSI device sdb: 156301488 512-byte hdwr sectors (80026 MB)
Apr 25 20:43:19 ares kernel: [   13.591560] sdb: Write Protect is off
Apr 25 20:43:19 ares kernel: [   13.591597] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   13.591605]  sdb: sdb1 sdb2 sdb3 sdb4
Apr 25 20:43:19 ares kernel: [   13.626713] sd 1:0:0:0: Attached scsi disk sdb
Apr 25 20:43:19 ares kernel: [   13.626811] sd 1:0:0:0: Attached scsi generic sg2 type 0
Apr 25 20:43:19 ares kernel: [   13.627388] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 4R160L0   RAMB PQ: 0 ANSI: 5
Apr 25 20:43:19 ares kernel: [   13.629066] SCSI device sdc: 320173056 512-byte hdwr sectors (163929 MB)
Apr 25 20:43:19 ares kernel: [   13.629094] sdc: Write Protect is off
Apr 25 20:43:19 ares kernel: [   13.629134] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   13.629231] SCSI device sdc: 320173056 512-byte hdwr sectors (163929 MB)
Apr 25 20:43:19 ares kernel: [   13.629252] sdc: Write Protect is off
Apr 25 20:43:19 ares kernel: [   13.629290] SCSI device sdc: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   13.629298]  sdc: sdc1 sdc2
Apr 25 20:43:19 ares kernel: [   17.734270] sd 1:0:1:0: Attached scsi disk sdc
Apr 25 20:43:19 ares kernel: [   17.734356] sd 1:0:1:0: Attached scsi generic sg3 type 0
Apr 25 20:43:19 ares kernel: [   17.735816] scsi 2:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4120B 2.02 PQ: 0 ANSI: 5
Apr 25 20:43:19 ares kernel: [   17.735962] scsi 2:0:0:0: Attached scsi generic sg4 type 5
Apr 25 20:43:19 ares kernel: [   17.736842] scsi 2:0:1:0: Direct-Access     ATA      Maxtor 4R160L0   RAMB PQ: 0 ANSI: 5
Apr 25 20:43:19 ares kernel: [   17.737409] SCSI device sdd: 320173056 512-byte hdwr sectors (163929 MB)
Apr 25 20:43:19 ares kernel: [   17.737435] sdd: Write Protect is off
Apr 25 20:43:19 ares kernel: [   17.737475] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   17.737578] SCSI device sdd: 320173056 512-byte hdwr sectors (163929 MB)
Apr 25 20:43:19 ares kernel: [   17.737599] sdd: Write Protect is off
Apr 25 20:43:19 ares kernel: [   17.737636] SCSI device sdd: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 25 20:43:19 ares kernel: [   17.737644]  sdd: sdd1 sdd2 < sdd5 > sdd3 sdd4
Apr 25 20:43:19 ares kernel: [   21.812878] sd 2:0:1:0: Attached scsi disk sdd
Apr 25 20:43:19 ares kernel: [   21.812966] sd 2:0:1:0: Attached scsi generic sg5 type 0
Apr 25 20:43:19 ares kernel: [   21.813644] ACPI: PCI Interrupt Link [LNKU] enabled at IRQ 5
Apr 25 20:43:19 ares kernel: [   21.813669] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [LNKU] -> GSI 5 (level, low) -> IRQ 5
Apr 25 20:43:19 ares kernel: [   21.813704] ohci_hcd 0000:00:0f.2: OHCI Host Controller
Apr 25 20:43:19 ares kernel: [   21.813985] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
Apr 25 20:43:19 ares kernel: [   21.814023] ohci_hcd 0000:00:0f.2: irq 5, io mem 0xfd102000
Apr 25 20:43:19 ares kernel: [   21.881598] usb usb1: configuration #1 chosen from 1 choice
Apr 25 20:43:19 ares kernel: [   21.881677] hub 1-0:1.0: USB hub found
Apr 25 20:43:19 ares kernel: [   21.881700] hub 1-0:1.0: 2 ports detected
Apr 25 20:43:19 ares kernel: [   22.054061] sr0: scsi3-mmc drive: 0x/32x writer cd/rw xa/form2 cdda tray
Apr 25 20:43:19 ares kernel: [   22.054076] Uniform CD-ROM driver Revision: 3.20
Apr 25 20:43:19 ares kernel: [   23.281075] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   23.281098] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   33.009019] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Apr 25 20:43:19 ares kernel: [   35.033540] NET: Registered protocol family 17
Apr 25 20:43:19 ares kernel: [   35.075712] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
Apr 25 20:43:19 ares kernel: [   35.091793] Linux agpgart interface v0.102 (c) Dave Jones
Apr 25 20:43:19 ares kernel: [   35.105857] agpgart: agp_backend_initialize() failed.
Apr 25 20:43:19 ares kernel: [   35.105867] agpgart-serverworks: probe of 0000:00:00.0 failed with error -22
Apr 25 20:43:19 ares kernel: [   35.105892] agpgart: agp_backend_initialize() failed.
Apr 25 20:43:19 ares kernel: [   35.105899] agpgart-serverworks: probe of 0000:00:00.1 failed with error -22
Apr 25 20:43:19 ares kernel: [   35.317173] input: PC Speaker as /class/input/input2
Apr 25 20:43:19 ares kernel: [   35.907080] input: PS/2 Generic Mouse as /class/input/input3
Apr 25 20:43:19 ares kernel: [   36.226081] parport0: PC-style at 0x378 [PCSPP]
Apr 25 20:43:19 ares kernel: [   36.326326] lp0: using parport0 (polling).
Apr 25 20:43:19 ares kernel: [   36.412868] fuse init (API version 7.8)
Apr 25 20:43:19 ares kernel: [   36.820226] Adding 748432k swap on /dev/disk/by-uuid/df5aeee1-0517-46a3-8068-2e232717a440.  Priority:-1 extents:1 across:748432k
Apr 25 20:43:19 ares kernel: [   37.107241] EXT3 FS on sdb1, internal journal
Apr 25 20:43:19 ares kernel: [   37.516954] NET: Registered protocol family 10
Apr 25 20:43:19 ares kernel: [   37.517233] lo: Disabled Privacy Extensions
Apr 25 20:43:19 ares kernel: [   43.842632] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   43.843268] EXT3 FS on dm-2, internal journal
Apr 25 20:43:19 ares kernel: [   43.843285] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   43.856218] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   43.856854] EXT3 FS on dm-3, internal journal
Apr 25 20:43:19 ares kernel: [   43.856869] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   43.914416] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   43.915029] EXT3 FS on dm-9, internal journal
Apr 25 20:43:19 ares kernel: [   43.915045] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   43.936205] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   43.936689] EXT3 FS on dm-0, internal journal
Apr 25 20:43:19 ares kernel: [   43.936703] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   43.971022] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   43.971657] EXT3 FS on dm-5, internal journal
Apr 25 20:43:19 ares kernel: [   43.971673] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   44.014161] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   44.014679] EXT3 FS on dm-8, internal journal
Apr 25 20:43:19 ares kernel: [   44.014695] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   44.061877] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   44.062401] EXT3 FS on dm-7, internal journal
Apr 25 20:43:19 ares kernel: [   44.062416] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   44.093713] kjournald starting.  Commit interval 5 seconds
Apr 25 20:43:19 ares kernel: [   44.094290] EXT3 FS on dm-6, internal journal
Apr 25 20:43:19 ares kernel: [   44.094306] EXT3-fs: mounted filesystem with ordered data mode.
Apr 25 20:43:19 ares kernel: [   44.152671] Adding 748432k swap on /dev/disk/by-uuid/df5aeee1-0517-46a3-8068-2e232717a440.  Priority:-2 extents:1 across:748432k
Apr 25 20:43:19 ares kernel: [   45.867062] input: Power Button (FF) as /class/input/input4
Apr 25 20:43:19 ares kernel: [   45.867119] ACPI: Power Button (FF) [PWRF]
Apr 25 20:43:19 ares kernel: [   46.188051] Using specific hotkey driver
Apr 25 20:43:19 ares kernel: [   46.363868] No dock devices found.
Apr 25 20:43:19 ares kernel: [   46.459243] pcc_acpi: loading...
Apr 25 20:43:35 ares dhcdbd: Started up.
Apr 25 20:43:36 ares dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 25 20:43:36 ares dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Apr 25 20:43:37 ares hpiod: 1.7.3 accepting connections at 2208... 
Apr 25 20:43:38 ares kernel: [   66.034617] ppdev: user-space parallel port driver
Apr 25 20:43:38 ares kernel: [   66.380299] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Apr 25 20:43:38 ares kernel: [   66.380313] apm: disabled - APM is not SMP safe.
Apr 25 20:43:40 ares dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Apr 25 20:43:40 ares dhcdbd: dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 
Apr 25 20:43:40 ares dhcdbd: dhco_input_option: Value -1 cannot be converted to type L 
Apr 25 20:43:40 ares dhcdbd: dhco_parse_option_settings: bad option setting: old_dhcp_lease_time = -1 
Apr 25 20:43:40 ares dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Apr 25 20:43:40 ares dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Apr 25 20:43:57 ares kernel: [   85.696188] Bluetooth: Core ver 2.11
Apr 25 20:43:58 ares kernel: [   85.696353] NET: Registered protocol family 31
Apr 25 20:43:58 ares kernel: [   85.696360] Bluetooth: HCI device and connection manager initialized
Apr 25 20:43:58 ares kernel: [   85.696370] Bluetooth: HCI socket layer initialized
Apr 25 20:43:58 ares kernel: [   85.740450] Bluetooth: L2CAP ver 2.8
Apr 25 20:43:58 ares kernel: [   85.740462] Bluetooth: L2CAP socket layer initialized
Apr 25 20:43:58 ares kernel: [   85.829033] Bluetooth: RFCOMM socket layer initialized
Apr 25 20:43:58 ares kernel: [   85.829070] Bluetooth: RFCOMM TTY layer initialized
Apr 25 20:43:58 ares kernel: [   85.829075] Bluetooth: RFCOMM ver 1.8
Apr 25 20:43:58 ares nagios: Nagios 2.7 starting... (PID=6235)
Apr 25 20:43:58 ares nagios: LOG VERSION: 2.0 
Apr 25 20:43:58 ares nagios: Finished daemonizing... (New PID=6236) 
Apr 25 20:44:03 ares gconfd (stan-6325): (versie 2.18.0.1) gestart, pid 6325 gebruiker 'stan'
Apr 25 20:44:03 ares gconfd (stan-6325): Adres "xml:readonly:/etc/gconf/gconf.xml.mandatory" getraceerd naar een alleen-lezen configuratiebron op positie 0
Apr 25 20:44:03 ares gconfd (stan-6325): Adres "xml:readwrite:/home/stan/.gconf" getraceerd naar een schrijfbare configuratiebron op positie 1
Apr 25 20:44:03 ares gconfd (stan-6325): Adres "xml:readonly:/etc/gconf/gconf.xml.defaults" getraceerd naar een alleen-lezen configuratiebron op positie 2
Apr 25 20:44:03 ares gconfd (stan-6325): Adres "xml:readonly:/var/lib/gconf/debian.defaults" getraceerd naar een alleen-lezen configuratiebron op positie 3
Apr 25 20:44:03 ares gconfd (stan-6325): Adres "xml:readonly:/var/lib/gconf/defaults" getraceerd naar een alleen-lezen configuratiebron op positie 4
Apr 25 20:44:17 ares gconfd (stan-6325): Adres "xml:readwrite:/home/stan/.gconf" getraceerd naar een schrijfbare configuratiebron op positie 0
```

---

### Post by huygens on 2007-04-27
Perhaps this is completely, but did you try the following:
in Gnome menu: "System" -> "Administration" -> "Services"
There scroll to find the Apache entry. If it is not checked, check it. If it is checked, then uncheck it and check it again.
Now, why not trying to reboot to see if Apache is launch at start-up automatically?

You could try the same trick with other services.

---

### Post by GoBieN on 2007-04-29
> **huygens said:**
> Perhaps this is completely, but did you try the following:
in Gnome menu: "System" -> "Administration" -> "Services"
There scroll to find the Apache entry. If it is not checked, check it. If it is checked, then uncheck it and check it again.
Now, why not trying to reboot to see if Apache is launch at start-up automatically?

You could try the same trick with other services.

It was there and was checked, i have now unchecked it and then checked it again.

i'll reboot and see.

---

### Post by GoBieN on 2007-04-29
SO it started GREAT !

To bad my other supposed to boot daemons aren't listed there. Ventrilo etc .
I will try to find a way to add them to services.

---

### Post by GoBieN on 2007-04-30
What is the easiest way to make a /etc/init.d/ventrilo script start at boot ?

---

