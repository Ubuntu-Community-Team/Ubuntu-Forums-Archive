---
title: "Server randomly becomes unresponsive - how to find fault?"
date: 2014-01-05
forum: Server Platforms
---

### Post by martinmcanespie on 2014-01-05
For the last week my dedicated Ubuntu LAMP server has randomly become unresponsive when accessed remotely such as trying to connect to the website it hosts.

Each time it happens it goes down for approx 30 mins and then comes back to life, however i can reboot the server or restart the Apache service and it comes back to life instantly

It happened today and i noticed i couldn't access the server from the external website address & the mail client wasn't working either, however when using internal ip addresses to connect i could access webmin, ispconfig, FTP & Telnet without any issues

So from what i can gather its a fault stopping external connections. I've ran the HP diagnostics which has no hardware faults in the logs and i've ran hardware diagnostics which have come back ok

I've checked the main logs and cant find anything, the only thing i've noticed is some these 'No host group' errors in the logwatch report (the server had just been rebooted):

```
    Banned services with Fail2Ban:                                                  Bans:Unbans
      apache-w00tw00t:                                        [  1:1  ]
         103.245.197.202                                         1:1  
      sasl:                                                   [  2:1  ]
         116.11.252.198                                          1:1  
         85.105.141.50 (85.105.141.50.static.ttnet.com.tr)       1:0  
   
   3 faulty iptables invocation(s):
   2014-01-04 17:22:10,011 fail2ban.actions.action: ERROR  iptables -n -L INPUT | grep -q fail2ban-apache-w00tw00t returned 100
   2014-01-04 17:22:10,040 fail2ban.actions.action: ERROR  iptables -D fail2ban-apache-w00tw00t -s 103.245.197.202 -j DROP returned 100
   2014-01-04 17:22:16,701 fail2ban.actions.action: ERROR  iptables -n -L INPUT | grep -q fail2ban-sasl returned 100
   2014-01-04 17:22:16,741 fail2ban.actions.action: ERROR  iptables -D fail2ban-sasl -s 116.11.252.198 -j DROP returned 100
   
   2 fail2ban rules reinitialization(s)
   **Unmatched Entries**
   2014-01-04 17:22:09,283 fail2ban.server : INFO   Stopping all jails
   2014-01-04 17:41:12,790 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
   2014-01-04 17:41:12,947 fail2ban.jail   : INFO   Jail 'ssh-ddos' uses Gamin
   2014-01-04 17:41:12,957 fail2ban.jail   : INFO   Jail 'apache' uses Gamin
   2014-01-04 17:41:12,985 fail2ban.jail   : INFO   Jail 'apache-multiport' uses Gamin
   2014-01-04 17:41:12,994 fail2ban.jail   : INFO   Jail 'apache-noscript' uses Gamin
   2014-01-04 17:41:13,005 fail2ban.jail   : INFO   Jail 'apache-overflows' uses Gamin
   2014-01-04 17:41:13,015 fail2ban.jail   : INFO   Jail 'pure-ftpd' uses Gamin
   2014-01-04 17:41:13,025 fail2ban.jail   : INFO   Jail 'postfix' uses Gamin
   2014-01-04 17:41:13,047 fail2ban.jail   : INFO   Jail 'sasl' uses Gamin
   2014-01-04 17:41:13,057 fail2ban.jail   : INFO   Jail 'dovecot' uses Gamin
   2014-01-04 17:41:13,067 fail2ban.jail   : INFO   Jail 'apache-phpmyadmin' uses Gamin
   2014-01-04 17:41:13,070 fail2ban.filter : ERROR  No 'host' group in '[[]client []] File does not exist: /var/www/(?:PMA|phpmyadmin|myadmin|mysql|mysqladmin|sqladmin|mypma|admin|xampp|mysqldb|mydb|db|pmadb|phpmyadmin1|phpmyadmin2)'
   2014-01-04 17:41:13,077 fail2ban.jail   : INFO   Jail 'fail2ban' uses Gamin
   2014-01-04 17:41:13,092 fail2ban.jail   : INFO   Jail 'http-get-dos' uses Gamin
   2014-01-04 17:41:13,099 fail2ban.jail   : INFO   Jail 'pureftpd' uses Gamin
   2014-01-04 17:41:13,130 fail2ban.jail   : INFO   Jail 'dovecot-pop3imap' uses Gamin
   2014-01-04 17:41:13,137 fail2ban.jail   : INFO   Jail 'webmin' uses Gamin
   2014-01-04 17:41:13,148 fail2ban.jail   : INFO   Jail 'apache-badbots' uses Gamin
   2014-01-04 17:41:13,214 fail2ban.jail   : INFO   Jail 'apache-nohome' uses Gamin
   2014-01-04 17:41:13,225 fail2ban.jail   : INFO   Jail 'php-url-fopen' uses Gamin
   2014-01-04 17:41:13,235 fail2ban.jail   : INFO   Jail 'exim' uses Gamin
   2014-01-04 17:41:13,244 fail2ban.jail   : INFO   Jail 'apache-w00tw00t' uses Gamin
   2014-01-04 17:41:13,248 fail2ban.filter : ERROR  No 'host' group in '# Option: ignoreregex'
   2014-01-04 17:41:13,249 fail2ban.filter : ERROR  No 'host' group in '# Notes.: regex to ignore. If this regex matches, the line is ignored.'
   2014-01-04 17:41:13,249 fail2ban.filter : ERROR  No 'host' group in '# Values: TEXT'
   2014-01-04 17:41:13,250 fail2ban.filter : ERROR  No 'host' group in 'ignoreregex ='
   2014-01-04 17:41:13,256 fail2ban.jail   : INFO   Jail 'apache-myadmin' uses Gamin
  

```

and i also have kernal errors which is unusual but could be present due to the server rebooting?

```
 WARNING:  Kernel Errors Present
    ACPI Error: Field [CDW3] at ...:  1 Time(s)
    ACPI Error: Method parse/ex ...:  1 Time(s)
    ERST: Failed to get Error Log Address Rang ...:  1 Time(s)
    EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)
 
 1 Time(s): , receive & transmit flow control ON
 1 Time(s): ... bit width:              40
 1 Time(s): ... event mask:             0000000700000003
 1 Time(s): ... fixed-purpose events:   3
 1 Time(s): ... generic registers:      2
 1 Time(s): ... max period:             000000007fffffff
 1 Time(s): ... value mask:             000000ffffffffff
 1 Time(s): ... version:                2
 1 Time(s): ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
 1 Time(s): 0 base 00E0000000 mask 0FE0000000 uncachable
 1 Time(s): 00000-9FFFF write-back
 1 Time(s): 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
 1 Time(s): 1 disabled
 1 Time(s): 2 disabled
 1 Time(s): 3 disabled
 1 Time(s): 4 disabled
 1 Time(s): 5 disabled
 1 Time(s): 6 disabled
 1 Time(s): 7 disabled
 1 Time(s): A0000-BFFFF uncachable
 1 Time(s): ACPI BIOS Bug: Warning: Invalid length for FADT/Pm1aControlBlock: 32, using default 16 (20121018/tbfadt-648)
 1 Time(s): ACPI BIOS Bug: Warning: Invalid length for FADT/Pm2ControlBlock: 32, using default 8 (20121018/tbfadt-648)
 1 Time(s): ACPI Warning: 0x0000000000000928-0x000000000000092f SystemIO conflicts with Region \SGPE 1 (20121018/utaddress-251)
 1 Time(s): ACPI Warning: For \_SB_.PCI0.PT02._PRT: Return Package has no elements (empty) (20121018/nspredef-463)
 1 Time(s): ACPI: (supports S0 S4 S5)
 1 Time(s): ACPI: ACPI bus type pnp unregistered
 1 Time(s): ACPI: APIC 00000000dfe54480 0009E (v01 HP     ProLiant 00000002      00000000)
 1 Time(s): ACPI: Added _OSI(3.0 _SCP Extensions)
 1 Time(s): ACPI: Added _OSI(Module Device)
 1 Time(s): ACPI: Added _OSI(Processor Aggregator Device)
 1 Time(s): ACPI: Added _OSI(Processor Device)
 1 Time(s): ACPI: BERT 00000000dfe546c0 00030 (v01 HP     ProLiant 00000001   Ò? 0000162E)
 1 Time(s): ACPI: Core revision 20121018
 1 Time(s): ACPI: DSDT 00000000dfe54940 02A24 (v01 HP         DSDT 00000001 INTL 20061109)
 8 Time(s): ACPI: Dynamic OEM Table Load:
 1 Time(s): ACPI: EC: Look up EC in DSDT
 1 Time(s): ACPI: ERST 00000000dfe54280 001D0 (v01 HP     ProLiant 00000001   Ò? 0000162E)
 1 Time(s): ACPI: FACP 00000000dfe54840 000F4 (v03 HP     ProLiant 00000002   Ò? 0000162E)
 1 Time(s): ACPI: FACS 00000000dfe54100 00040
 1 Time(s): ACPI: FFFF 00000000dfe54540 00176 (v01 HP     ProLiant 00000001   Ò? 0000162E)
 1 Time(s): ACPI: HEST 00000000dfe54700 000BC (v01 HP     ProLiant 00000001   Ò? 0000162E)
 1 Time(s): ACPI: HPET 00000000dfe54200 00038 (v01 HP     ProLiant 00000002   Ò? 0000162E)
 1 Time(s): ACPI: HPET id: 0x8086a201 base: 0xfed00000
 1 Time(s): ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
 1 Time(s): ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
 1 Time(s): ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
 1 Time(s): ACPI: IOAPIC (id[0x09] address[0xfec80000] gsi_base[24])
 1 Time(s): ACPI: IRQ0 used by override.
 1 Time(s): ACPI: IRQ2 used by override.
 1 Time(s): ACPI: IRQ9 used by override.
 1 Time(s): ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
 1 Time(s): ACPI: Interpreter enabled
 1 Time(s): ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
 1 Time(s): ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
 1 Time(s): ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
 2 Time(s): ACPI: Local APIC address 0xfee00000
 1 Time(s): ACPI: MCFG 00000000dfe541c0 0003C (v01 HP     ProLiant 00000001      00000000)
 1 Time(s): ACPI: No dock devices found.
 1 Time(s): ACPI: PCI Interrupt Link [LNKA] (IRQs *5 7 10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *7 10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 *10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKE] (IRQs 5 7 10 11) *0, disabled.
 1 Time(s): ACPI: PCI Interrupt Link [LNKF] (IRQs *5 7 10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 *10 11)
 1 Time(s): ACPI: PCI Interrupt Link [LNKH] (IRQs 5 *7 10 11)
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IP2P._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPTA._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT02.IPE4.IPE1._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT02.IPE4.IPE2._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT02.IPE4._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT02.PEX2._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT02._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT04._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT05.EEPB.EPPB._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT05.EEPB._PRT]
 1 Time(s): ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
 1 Time(s): ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7f])
 1 Time(s): ACPI: PM-Timer IO Port: 0x908
 1 Time(s): ACPI: Power Button [PWRF]
 1 Time(s): ACPI: RSDP 00000000000f4f00 00024 (v02 HP    )
 1 Time(s): ACPI: SPCR 00000000dfe54140 00050 (v01 HP     SPCRRBSU 00000001   Ò? 0000162E)
 1 Time(s): ACPI: SPMI 00000000dfe54240 00040 (v05 HP     ProLiant 00000001   Ò? 0000162E)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU0CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU1CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU2CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU3CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU4CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU5CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU6CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT           (null) 000AD (v01 HP      CPU7CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe59000 00C85 (v01 HP        SSDTP 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5f800 000AD (v01 HP      CPU0CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5f900 000AD (v01 HP      CPU1CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5fa00 000AD (v01 HP      CPU2CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5fb00 000AD (v01 HP      CPU3CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5fc00 000AD (v01 HP      CPU4CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5fd00 000AD (v01 HP      CPU5CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5fe00 000AD (v01 HP      CPU6CST 00000001 INTL 20061109)
 1 Time(s): ACPI: SSDT 00000000dfe5ff00 000AD (v01 HP      CPU7CST 00000001 INTL 20061109)
 1 Time(s): ACPI: Thermal Zone [THM0] (8 C)
 1 Time(s): ACPI: Using IOAPIC for interrupt routing
 1 Time(s): ACPI: XSDT 00000000dfe547c0 0007C (v01 HP     ProLiant 00000002   Ò? 0000162E)
 1 Time(s): ACPI: acpi_idle registered with cpuidle
 1 Time(s): ACPI: bus type pci registered
 1 Time(s): ACPI: bus type pnp registered
 1 Time(s): ACPI: bus type scsi registered
 1 Time(s): ACPI: bus type usb registered
 1 Time(s): AMD AuthenticAMD
 1 Time(s): Adding 5242876k swap on /dev/mapper/MYSERVER--vg-swap_1.  Priority:-1 extents:1 across:5242876k
 1 Time(s): AppArmor: AppArmor Filesystem Enabled
 1 Time(s): AppArmor: AppArmor initialized
 1 Time(s): Asymmetric key parser 'x509' registered
 1 Time(s): BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
 1 Time(s): BIOS-e820: [mem 0x0000000000000000-0x000000000009ebff] usable
 1 Time(s): BIOS-e820: [mem 0x000000000009ec00-0x000000000009ffff] reserved
 1 Time(s): BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
 1 Time(s): BIOS-e820: [mem 0x0000000000100000-0x00000000dfe53fff] usable
 1 Time(s): BIOS-e820: [mem 0x00000000dfe54000-0x00000000dfe5bfff] ACPI data
 1 Time(s): BIOS-e820: [mem 0x00000000dfe5c000-0x00000000dfe5cfff] usable
 1 Time(s): BIOS-e820: [mem 0x00000000dfe5d000-0x00000000efffffff] reserved
 1 Time(s): BIOS-e820: [mem 0x00000000fec00000-0x00000000fecfffff] reserved
 1 Time(s): BIOS-e820: [mem 0x00000000fee00000-0x00000000fee0ffff] reserved
 1 Time(s): BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
 1 Time(s): BIOS-e820: [mem 0x0000000100000000-0x00000001dfffefff] usable
 1 Time(s): Base memory trampoline at [ffff880000098000] 98000 size 24576
 1 Time(s): Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
 1 Time(s): Bluetooth: BNEP (Ethernet Emulation) ver 1.3
 1 Time(s): Bluetooth: BNEP filters: protocol multicast
 1 Time(s): Bluetooth: BNEP socket layer initialized
 1 Time(s): Bluetooth: Core ver 2.16
 1 Time(s): Bluetooth: HCI device and connection manager initialized
 1 Time(s): Bluetooth: HCI socket layer initialized
 1 Time(s): Bluetooth: L2CAP socket layer initialized
 1 Time(s): Bluetooth: RFCOMM TTY layer initialized
 1 Time(s): Bluetooth: RFCOMM socket layer initialized
 1 Time(s): Bluetooth: RFCOMM ver 1.11
 1 Time(s): Bluetooth: SCO socket layer initialized
 1 Time(s): Booting paravirtualized kernel on bare hardware
 1 Time(s): Brought up 8 CPUs
 1 Time(s): Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1805794
 1 Time(s): C0000-FFFFF write-protect
 1 Time(s): CPU0: Thermal monitoring enabled (TM2)
 1 Time(s): CPU: Physical Processor ID: 1
 1 Time(s): CPU: Processor Core ID: 0
 1 Time(s): Calgary: Unable to locate Rio Grande table in EBDA - bailing!
 1 Time(s): Calgary: detecting Calgary via BIOS EBDA area
 1 Time(s): Calibrating delay loop (skipped), value calculated using timer frequency.. 5000.18 BogoMIPS (lpj=10000364)
 1 Time(s): Centaur CentaurHauls
 1 Time(s): Checking aperture...
 1 Time(s): Command line: BOOT_IMAGE=/vmlinuz-3.8.0-35-generic root=/dev/mapper/MYSERVER--vg-root ro
 1 Time(s): Console: colour dummy device 80x25
 1 Time(s): Console: switching to colour frame buffer device 240x67
 1 Time(s): Copyright (c) 1999-2008 LSI Corporation
 1 Time(s): DMA      [mem 0x00010000-0x00ffffff]
 1 Time(s): DMA zone: 3912 pages, LIFO batch:0
 1 Time(s): DMA zone: 6 pages reserved
 1 Time(s): DMA zone: 64 pages used for memmap
 1 Time(s): DMA32    [mem 0x01000000-0xffffffff]
 1 Time(s): DMA32 zone: 14266 pages used for memmap
 1 Time(s): DMA32 zone: 898715 pages, LIFO batch:31
 1 Time(s): DMI: HP ProLiant ML350 G5, BIOS D21 05/12/2009
 1 Time(s): Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
 1 Time(s): Disabling lock debugging due to kernel taint
 1 Time(s): Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
 1 Time(s): EDAC MC0: Giving out device to 'i5000_edac.c' 'I5000': DEV 0000:00:10.0
 1 Time(s): EDAC MC: Ver: 3.0.0
 1 Time(s): EDAC PCI0: Giving out device to module 'i5000_edac' controller 'EDAC PCI controller': DEV '0000:00:10.0' (POLLED)
 1 Time(s): EDD information not available.
 1 Time(s): EFI Variables Facility v0.08 2004-May-17
 1 Time(s): EVM: security.SMACK64
 1 Time(s): EVM: security.capability
 1 Time(s): EVM: security.selinux
 1 Time(s): EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
 1 Time(s): Early memory node ranges
 1 Time(s): Extended CMOS year: 2000
 1 Time(s): Faking a node at [mem 0x0000000000000000-0x00000001dfffefff]
 2 Time(s): Floppy drive(s): fd0 is 1.44M
 1 Time(s): Freeing SMP alternatives: 24k freed
 1 Time(s): Freeing initrd memory: 16448k freed
 1 Time(s): Freeing unused kernel memory: 1004k freed
 1 Time(s): Freeing unused kernel memory: 1016k freed
 1 Time(s): Freeing unused kernel memory: 952k freed
 1 Time(s): Fusion MPT SPI Host driver 3.04.20
 1 Time(s): Fusion MPT base driver 3.04.20
 1 Time(s): GHES: APEI firmware first mode is enabled by WHEA _OSC.
 1 Time(s): HEST: Table parsing has been initialized.
 1 Time(s): HP CISS Driver (v 3.6.26)
 1 Time(s): HPET: 3 timers in total, 0 timers will be used for per-cpu timer
 1 Time(s): Hierarchical RCU implementation.
 1 Time(s): HugeTLB registered 2 MB page size, pre-allocated 0 pages
 1 Time(s): IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
 1 Time(s): IOAPIC[1]: apic_id 9, version 32, address 0xfec80000, GSI 24-47
 1 Time(s): IPMI System Interface driver.
 1 Time(s): IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 2 Time(s): IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
 1 Time(s): ISO 9660 Extensions: Microsoft Joliet Level 3
 1 Time(s): ISO 9660 Extensions: RRIP_1991A
 1 Time(s): Initialise module verification
 1 Time(s): Initializing cgroup subsys blkio
 1 Time(s): Initializing cgroup subsys cpu
 1 Time(s): Initializing cgroup subsys cpuacct
 1 Time(s): Initializing cgroup subsys cpuset
 1 Time(s): Initializing cgroup subsys devices
 1 Time(s): Initializing cgroup subsys freezer
 1 Time(s): Initializing cgroup subsys hugetlb
 1 Time(s): Initializing cgroup subsys memory
 1 Time(s): Initializing cgroup subsys perf_event
 1 Time(s): Initmem setup node 0 [mem 0x00000000-0x1dfffefff]
 1 Time(s): Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
 1 Time(s): Intel GenuineIntel
 1 Time(s): Intel PMU driver.
 1 Time(s): KERNEL supported cpus:
 1 Time(s): Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-35-generic root=/dev/mapper/MYSERVER--vg-root ro
 1 Time(s): Kernel logging (proc) stopped.
 1 Time(s): Key type asymmetric registered
 1 Time(s): Key type dns_resolver registered
 1 Time(s): Key type encrypted registered
 1 Time(s): Key type trusted registered
 1 Time(s): Last level dTLB entries: 4KB 256, 2MB 0, 4MB 32
 1 Time(s): Last level iTLB entries: 4KB 128, 2MB 4, 4MB 4
 1 Time(s): Linux agpgart interface v0.103
 1 Time(s): Linux version 3.8.0-35-generic (buildd@allspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 (Ubuntu 3.8.0-35.50~precise1-generic 3.8.13.13)
 1 Time(s): Loading module verification certificates
 1 Time(s): MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 26d22696497e0146aec821b3bfa3dd9972acd4d9'
 1 Time(s): MTRR default type: write-back
 1 Time(s): MTRR fixed ranges enabled:
 1 Time(s): MTRR variable ranges enabled:
 1 Time(s): Memory: 7123912k/7864316k available (7176k kernel code, 526452k absent, 213952k reserved, 6067k data, 1016k init)
 1 Time(s): Mount-cache hash table entries: 256
 1 Time(s): Movable zone start for each node
 1 Time(s): NET: Registered protocol family 1
 1 Time(s): NET: Registered protocol family 10
 1 Time(s): NET: Registered protocol family 16
 1 Time(s): NET: Registered protocol family 17
 1 Time(s): NET: Registered protocol family 2
 1 Time(s): NET: Registered protocol family 31
 1 Time(s): NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
 1 Time(s): NODE_DATA [mem 0x1dfffa000-0x1dfffefff]
 1 Time(s): NR_IRQS:16640 nr_irqs:1152 16
 1 Time(s): NX (Execute Disable) protection: active
 1 Time(s): NetLabel:  domain hash size = 128
 1 Time(s): NetLabel:  protocols = UNLABELED CIPSOv4
 1 Time(s): NetLabel:  unlabeled traffic allowed by default
 1 Time(s): NetLabel: Initializing
 2 Time(s): No AGP bridge found
 1 Time(s): No NUMA configuration found
 1 Time(s): Normal   [mem 0x100000000-0x1dfffefff]
 1 Time(s): Normal zone: 14336 pages used for memmap
 1 Time(s): Normal zone: 903167 pages, LIFO batch:31
 1 Time(s): On node 0 totalpages: 1834466
 1 Time(s): P0 P2 IDE IDE ]
 1 Time(s): PCI host bridge to bus 0000:00
 1 Time(s): PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
 1 Time(s): PCI: CLS 64 bytes, default 64
 1 Time(s): PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
 1 Time(s): PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
 1 Time(s): PCI: Using ACPI for IRQ routing
 1 Time(s): PCI: Using configuration type 1 for base access
 1 Time(s): PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
 1 Time(s): PCI: pci_cache_line_size set to 64 bytes
 1 Time(s): PERCPU: Embedded 28 pages/cpu @ffff8801dfc00000 s84928 r8192 d21568 u262144
 1 Time(s): PID hash table entries: 4096 (order: 3, 32768 bytes)
 1 Time(s): PM: Registered nosave memory: 000000000009e000 - 000000000009f000
 1 Time(s): PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
 1 Time(s): PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
 1 Time(s): PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
 1 Time(s): PM: Registered nosave memory: 00000000dfe54000 - 00000000dfe5c000
 1 Time(s): PM: Registered nosave memory: 00000000dfe5d000 - 00000000f0000000
 1 Time(s): PM: Registered nosave memory: 00000000f0000000 - 00000000fec00000
 1 Time(s): PM: Registered nosave memory: 00000000fec00000 - 00000000fed00000
 1 Time(s): PM: Registered nosave memory: 00000000fed00000 - 00000000fee00000
 1 Time(s): PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
 1 Time(s): PM: Registered nosave memory: 00000000fee10000 - 00000000ffc00000
 1 Time(s): PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
 1 Time(s): PPP generic driver version 2.4.2
 1 Time(s): Performance Events: PEBS fmt0+, 4-deep LBR, Core2 events, Broken BIOS detected, complain to your hardware vendor.
 1 Time(s): Policy zone: Normal
 1 Time(s): RAMDISK: [mem 0x35fd0000-0x36fdffff]
 1 Time(s): RCU dyntick-idle grace-period acceleration is enabled.
 1 Time(s): RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
 1 Time(s): SCSI subsystem initialized
 1 Time(s): SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
 1 Time(s): SMBIOS 2.4 present.
 1 Time(s): Security Framework initialized
 1 Time(s): Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
 1 Time(s): Switching to clocksource hpet
 1 Time(s): TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
 1 Time(s): TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
 1 Time(s): TCP: Hash tables configured (established 65536 bind 65536)
 1 Time(s): TCP: cubic registered
 1 Time(s): TCP: reno registered
 1 Time(s): Trying to unpack rootfs image as initramfs...
 1 Time(s): UDP hash table entries: 4096 (order: 5, 131072 bytes)
 1 Time(s): UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
 1 Time(s): Using ACPI (MADT) for SMP configuration information
 1 Time(s): VFS: Disk quotas dquot_6.5.2
 1 Time(s): Write protecting the kernel read-only data: 12288k
 1 Time(s): Yama: becoming mindful.
 1 Time(s): Zone ranges:
 1 Time(s): [Firmware Bug]: the BIOS has corrupted hw-PMU resources (MSR 186 is 43003c)
 1 Time(s): [TTM] Initializing DMA pool allocator
 1 Time(s): [TTM] Initializing pool allocator
 1 Time(s): [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
 1 Time(s): [TTM] Zone  kernel: Available graphics memory: 3571678 kiB
 1 Time(s): [drm]     CRT1: INTERNAL_DAC1
 1 Time(s): [drm]     CRT2: INTERNAL_DAC2
 1 Time(s): [drm]    pitch is 1920
 1 Time(s): [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
 1 Time(s): [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
 2 Time(s): [drm]   Encoders:
 1 Time(s): [drm]   VGA-1
 1 Time(s): [drm]   VGA-2
 1 Time(s): [drm] Connector 0:
 1 Time(s): [drm] Connector 1:
 1 Time(s): [drm] Detected VRAM RAM=128M, BAR=128M
 1 Time(s): [drm] Driver supports precise vblank timestamp query.
 1 Time(s): [drm] GART: num cpu pages 131072, num gpu pages 131072
 1 Time(s): [drm] Initialized drm 1.1.0 20060810
 1 Time(s): [drm] Initialized radeon 2.29.0 20080528 for 0000:01:03.0 on minor 0
 1 Time(s): [drm] Loading R100 Microcode
 1 Time(s): [drm] No TV DAC info found in BIOS
 1 Time(s): [drm] PCI GART of 512M enabled (table at 0x0000000036A00000).
 1 Time(s): [drm] RAM width 16bits DDR
 1 Time(s): [drm] Radeon Display Connectors
 1 Time(s): [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
 1 Time(s): [drm] fb depth is 8
 1 Time(s): [drm] fb mappable at 0xF0040000
 1 Time(s): [drm] ib test succeeded in 0 usecs
 1 Time(s): [drm] initializing kernel modesetting (RV100 0x1002:0x515E 0x103C:0x31FB).
 1 Time(s): [drm] radeon defaulting to kernel modesetting.
 1 Time(s): [drm] radeon kernel modesetting enabled.
 1 Time(s): [drm] radeon: 32M of VRAM memory ready
 1 Time(s): [drm] radeon: 512M of GTT memory ready.
 1 Time(s): [drm] radeon: irq initialized.
 1 Time(s): [drm] radeon: ring at 0x00000000D0001000
 1 Time(s): [drm] register mmio base: 0xF9FF0000
 1 Time(s): [drm] register mmio size: 65536
 1 Time(s): [drm] ring test succeeded in 1 usecs
 1 Time(s): [drm] size 2076672
 1 Time(s): [drm] vram apper at 0xF0000000
 1 Time(s): [ffffea0000000000-ffffea00077fffff] PMD -> [ffff8801d8600000-ffff8801df5fffff] on node 0
 1 Time(s): [mem 0x00000000-0xdfdfffff] page 2M
 1 Time(s): [mem 0x100000000-0x1dfdfffff] page 2M
 1 Time(s): [mem 0x1dfe00000-0x1dfffefff] page 4k
 1 Time(s): [mem 0xdfe00000-0xdfe5cfff] page 4k
 1 Time(s): __ex_table already sorted, skipping sort
 1 Time(s): allocated 29360128 bytes of page_cgroup
 1 Time(s): ashmem: initialized
 1 Time(s): ata1.00: ATAPI: HL-DT-ST DVD-RAM GH40L, LA00, max UDMA/100
 1 Time(s): ata1.00: configured for UDMA/100
 1 Time(s): ata1.01: NODEV after polling detection
 1 Time(s): ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x500 irq 14
 1 Time(s): ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x508 irq 15
 1 Time(s): ata_piix 0000:00:1f.2: MAP [
 1 Time(s): ata_piix 0000:00:1f.2: setting latency timer to 64
 1 Time(s): ata_piix 0000:00:1f.2: version 2.13
 1 Time(s): audit: initializing netlink socket (disabled)
 1 Time(s): bio: create slab <bio-0> at 0
 1 Time(s): bio: create slab <bio-1> at 1
 1 Time(s): bnx2 0000:03:00.0 eth0: Broadcom NetXtreme II BCM5708 1000Base-T (B2) PCI-X 64-bit 133MHz found at mem fa000000, IRQ 16, node addr 00:26:55:7e:6e:36
 1 Time(s): bnx2 0000:03:00.0 eth0: NIC Copper Link is Up, 1000 Mbps full duplex
 1 Time(s): bnx2 0000:03:00.0 eth0: using MSI
 1 Time(s): bnx2 0000:03:00.0: irq 70 for MSI/MSI-X
 1 Time(s): bnx2: Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.2.3 (June 27, 2012)
 1 Time(s): brd: module loaded
 1 Time(s): cciss 0000:06:00.0: cciss0: <0x3230> at PCI 0000:06:00.0 IRQ 65 using DAC
 1 Time(s): cciss 0000:06:00.0: irq 65 for MSI/MSI-X
 1 Time(s): cciss 0000:06:00.0: irq 66 for MSI/MSI-X
 1 Time(s): cciss 0000:06:00.0: irq 67 for MSI/MSI-X
 1 Time(s): cciss 0000:06:00.0: irq 68 for MSI/MSI-X
 1 Time(s): cciss 0000:13:08.0: cciss1: <0x3238> at PCI 0000:13:08.0 IRQ 69 using DAC
 1 Time(s): cciss 0000:13:08.0: irq 69 for MSI/MSI-X
 1 Time(s): cciss/c0d0: p1 p2 < p5 >
 1 Time(s): cdrom: Uniform CD-ROM driver Revision: 3.20
 1 Time(s): console [tty0] enabled
 1 Time(s): cpuidle: using governor ladder
 1 Time(s): cpuidle: using governor menu
 1 Time(s): device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
 1 Time(s): device-mapper: uevent: version 1.0.3
 1 Time(s): devtmpfs: initialized
 1 Time(s): e820: BIOS-provided physical RAM map:
 1 Time(s): e820: [mem 0xf0000000-0xfebfffff] available for PCI devices
 1 Time(s): e820: last_pfn = 0x1dffff max_arch_pfn = 0x400000000
 1 Time(s): e820: last_pfn = 0xdfe5d max_arch_pfn = 0x400000000
 1 Time(s): e820: remove [mem 0x000a0000-0x000fffff] usable
 1 Time(s): e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
 1 Time(s): e820: reserve RAM buffer [mem 0x1dffff000-0x1dfffffff]
 1 Time(s): e820: reserve RAM buffer [mem 0xdfe54000-0xdfffffff]
 1 Time(s): e820: reserve RAM buffer [mem 0xdfe5d000-0xdfffffff]
 1 Time(s): e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
 1 Time(s): ehci-pci 0000:00:1d.7: EHCI Host Controller
 1 Time(s): ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
 1 Time(s): ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
 1 Time(s): ehci-pci 0000:00:1d.7: debug port 1
 1 Time(s): ehci-pci 0000:00:1d.7: irq 16, io mem 0xf9df0000
 1 Time(s): ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
 1 Time(s): ehci-pci 0000:00:1d.7: setting latency timer to 64
 1 Time(s): ehci-pci: EHCI PCI platform driver
 1 Time(s): ehci-platform: EHCI generic platform driver
 1 Time(s): ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
 1 Time(s): fbcon: radeondrmfb (fb0) is primary device
 2 Time(s): floppy0: no floppy controllers found
 1 Time(s): found SMP MP-table at [mem 0x000f4f80-0x000f4f8f] mapped at [ffff8800000f4f80]
 1 Time(s): ftrace: allocating 29399 entries in 115 pages
 1 Time(s): fuse init (API version 7.20)
 1 Time(s): gpio_ich: ACPI BAR is unavailable, GPI 0 - 15 unavailable
 1 Time(s): gpio_ich: GPIO from 206 to 255 on gpio_ich
 1 Time(s): hid-generic 0003:03F0:1027.0002: input,hidraw1: USB HID v1.01 Keyboard [HP Virtual Keyboard] on usb-0000:01:04.4-1/input0
 1 Time(s): hid-generic 0003:03F0:1027.0003: input,hidraw2: USB HID v1.01 Mouse [HP Virtual Keyboard] on usb-0000:01:04.4-1/input1
 1 Time(s): hid-generic 0003:045E:0040.0001: input,hidraw0: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.2-1/input0
 1 Time(s): hpet clockevent registered
 1 Time(s): hpet0: 3 comparators, 64-bit 14.318180 MHz counter
 1 Time(s): hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
 1 Time(s): hpwdt 0000:01:04.0: HP Watchdog Timer Driver: 1.3.1, timer margin: 30 seconds (nowayout=0).
 1 Time(s): hpwdt 0000:01:04.0: HP Watchdog Timer Driver: NMI decoding initialized, allow kernel dump: ON (default = 0/OFF)
 1 Time(s): hub 1-0:1.0: 8 ports detected
 1 Time(s): hub 1-0:1.0: USB hub found
 1 Time(s): hub 2-0:1.0: 2 ports detected
 1 Time(s): hub 2-0:1.0: USB hub found
 1 Time(s): hub 3-0:1.0: 2 ports detected
 1 Time(s): hub 3-0:1.0: USB hub found
 1 Time(s): hub 4-0:1.0: 2 ports detected
 1 Time(s): hub 4-0:1.0: USB hub found
 1 Time(s): hub 5-0:1.0: 2 ports detected
 1 Time(s): hub 5-0:1.0: USB hub found
 1 Time(s): hub 6-0:1.0: 2 ports detected
 1 Time(s): hub 6-0:1.0: USB hub found
 1 Time(s): i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
 1 Time(s): imklog 5.8.6, log source = /proc/kmsg started.
 1 Time(s): init_memory_mapping: [mem 0x00000000-0xdfe5cfff]
 1 Time(s): init_memory_mapping: [mem 0x100000000-0x1dfffefff]
 1 Time(s): initial memory mapped: [mem 0x00000000-0x1fffffff]
 1 Time(s): input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
 1 Time(s): input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.0/input/input3
 1 Time(s): input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.1/input/input4
 1 Time(s): input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1:1.0/input/input2
 1 Time(s): input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
 1 Time(s): intel_idle: does not run on family 6 model 23
 1 Time(s): intel_rng: FWH not detected
 1 Time(s): io scheduler cfq registered
 1 Time(s): io scheduler deadline registered (default)
 1 Time(s): io scheduler noop registered
 1 Time(s): ioc0: LSI53C1020A A1: Capabilities={Initiator,Target}
 1 Time(s): ip6_tables: (C) 2000-2006 Netfilter Core Team
 1 Time(s): ip_tables: (C) 2000-2006 Netfilter Core Team
 1 Time(s): ipmi message handler version 39.2
 1 Time(s): ipmi_si 0000:01:04.6: Found new BMC (man_id: 0x00000b, prod_id: 0x2000, dev_id: 0x11)
 1 Time(s): ipmi_si 0000:01:04.6: IPMI kcs interface initialized
 1 Time(s): ipmi_si 0000:01:04.6: Using irq 21
 1 Time(s): ipmi_si 0000:01:04.6: [mem 0xf9ef0000-0xf9ef00ff] regsize 1 spacing 1 irq 21
 1 Time(s): ipmi_si 0000:01:04.6: probing via PCI
 1 Time(s): ipmi_si 00:01: [io  0x0ca2-0x0ca3] regsize 1 spacing 1 irq 0
 1 Time(s): ipmi_si: Adding ACPI-specified kcs state machine
 1 Time(s): ipmi_si: Adding PCI-specified kcs state machine
 1 Time(s): ipmi_si: Adding SMBIOS-specified kcs state machine duplicate interface
 1 Time(s): ipmi_si: Adding SPMI-specified kcs state machine duplicate interface
 1 Time(s): ipmi_si: SMBIOS: io 0xca2 regsize 1 spacing 1 irq 0
 1 Time(s): ipmi_si: SPMI: io 0xca2 regsize 2 spacing 2 irq 0
 1 Time(s): ipmi_si: Trying PCI-specified kcs state machine at mem address 0xf9ef0000, slave address 0x0, irq 21
 1 Time(s): ipmi_si: probing via ACPI
 1 Time(s): ipmi_si: probing via SMBIOS
 1 Time(s): ipmi_si: probing via SPMI
 1 Time(s): kernel direct mapping tables up to 0x1dfffefff @ [mem 0xdfe4e000-0xdfe53fff]
 1 Time(s): kernel direct mapping tables up to 0xdfe5cfff @ [mem 0x1fffa000-0x1fffffff]
 7 Time(s): kvm: disabled by bios
 1 Time(s): ledtrig-cpu: registered to indicate activity on CPUs
 1 Time(s): libata version 3.00 loaded.
 1 Time(s): libphy: Fixed MDIO Bus: probed
 1 Time(s): loop: module loaded
 1 Time(s): lp: driver loaded but no devices found
 1 Time(s): lpc_ich: Resource conflict(s) found affecting gpio_ich
 1 Time(s): mce: CPU supports 6 MCE banks
 1 Time(s): microcode: CPU0 sig=0x10676, pf=0x40, revision=0x60c
 1 Time(s): microcode: CPU1 sig=0x1067a, pf=0x40, revision=0xa07
 1 Time(s): microcode: CPU2 sig=0x1067a, pf=0x40, revision=0xa07
 1 Time(s): microcode: CPU3 sig=0x10676, pf=0x40, revision=0x60c
 1 Time(s): microcode: CPU4 sig=0x1067a, pf=0x40, revision=0xa07
 1 Time(s): microcode: CPU5 sig=0x10676, pf=0x40, revision=0x60c
 1 Time(s): microcode: CPU6 sig=0x1067a, pf=0x40, revision=0xa07
 1 Time(s): microcode: CPU7 sig=0x10676, pf=0x40, revision=0x60c
 1 Time(s): microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
 1 Time(s): mousedev: PS/2 mouse device common for all mice
 1 Time(s): mptbase: ioc0: Initiating bringup
 1 Time(s): msgmni has been set to 13946
 2 Time(s): mtrr: your BIOS has configured an incorrect mask, fixing it.
 1 Time(s): nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
 1 Time(s): nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
 1 Time(s): node   0: [mem 0x00010000-0x0009dfff]
 1 Time(s): node   0: [mem 0x00100000-0xdfe53fff]
 1 Time(s): node   0: [mem 0x100000000-0x1dfffefff]
 1 Time(s): node   0: [mem 0xdfe5c000-0xdfe5cfff]
 1 Time(s): nr_irqs_gsi: 64
 1 Time(s): ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
 1 Time(s): osst :I: $Id: osst.c,v 1.73 2005/01/01 21:13:34 wriede Exp $
 1 Time(s): osst :I: Tape driver with OnStream support version 0.99.4
 1 Time(s): pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:00.0: [8086:25d0] type 00 class 0x060000
 2 Time(s): pci 0000:00:02.0:   bridge window [io  0x4000-0x5fff]
 1 Time(s): pci 0000:00:02.0:   bridge window [mem 0xf8000000-0xf81fffff pref]
 2 Time(s): pci 0000:00:02.0:   bridge window [mem 0xfda00000-0xfdefffff]
 1 Time(s): pci 0000:00:02.0: BAR 15: assigned [mem 0xf8000000-0xf81fffff pref]
 2 Time(s): pci 0000:00:02.0: PCI bridge to [bus 04-0e]
 1 Time(s): pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:02.0: [8086:25f7] type 01 class 0x060400
 2 Time(s): pci 0000:00:03.0: PCI bridge to [bus 17-19]
 1 Time(s): pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:03.0: [8086:25e3] type 01 class 0x060400
 2 Time(s): pci 0000:00:04.0: PCI bridge to [bus 0f-11]
 1 Time(s): pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:04.0: [8086:25e4] type 01 class 0x060400
 2 Time(s): pci 0000:00:05.0:   bridge window [io  0x6000-0x6fff]
 1 Time(s): pci 0000:00:05.0:   bridge window [mem 0xf8200000-0xf82fffff pref]
 2 Time(s): pci 0000:00:05.0:   bridge window [mem 0xfdf00000-0xfdffffff]
 1 Time(s): pci 0000:00:05.0: BAR 15: assigned [mem 0xf8200000-0xf82fffff pref]
 2 Time(s): pci 0000:00:05.0: PCI bridge to [bus 12-16]
 1 Time(s): pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:05.0: [8086:25e5] type 01 class 0x060400
 1 Time(s): pci 0000:00:10.0: [8086:25f0] type 00 class 0x060000
 1 Time(s): pci 0000:00:10.1: [8086:25f0] type 00 class 0x060000
 1 Time(s): pci 0000:00:10.2: [8086:25f0] type 00 class 0x060000
 1 Time(s): pci 0000:00:11.0: [8086:25f1] type 00 class 0x060000
 1 Time(s): pci 0000:00:13.0: [8086:25f3] type 00 class 0x060000
 1 Time(s): pci 0000:00:15.0: [8086:25f5] type 00 class 0x060000
 1 Time(s): pci 0000:00:16.0: [8086:25f6] type 00 class 0x060000
 1 Time(s): pci 0000:00:1c.0:   bridge window [mem 0xf8300000-0xf83fffff pref]
 2 Time(s): pci 0000:00:1c.0:   bridge window [mem 0xfa000000-0xfbffffff]
 1 Time(s): pci 0000:00:1c.0: BAR 15: assigned [mem 0xf8300000-0xf83fffff pref]
 2 Time(s): pci 0000:00:1c.0: PCI bridge to [bus 02-03]
 1 Time(s): pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1c.0: [8086:2690] type 01 class 0x060400
 1 Time(s): pci 0000:00:1d.0: [8086:2688] type 00 class 0x0c0300
 1 Time(s): pci 0000:00:1d.0: reg 20: [io  0x1000-0x101f]
 1 Time(s): pci 0000:00:1d.1: [8086:2689] type 00 class 0x0c0300
 1 Time(s): pci 0000:00:1d.1: reg 20: [io  0x1020-0x103f]
 1 Time(s): pci 0000:00:1d.2: [8086:268a] type 00 class 0x0c0300
 1 Time(s): pci 0000:00:1d.2: reg 20: [io  0x1040-0x105f]
 1 Time(s): pci 0000:00:1d.3: [8086:268b] type 00 class 0x0c0300
 1 Time(s): pci 0000:00:1d.3: reg 20: [io  0x1060-0x107f]
 1 Time(s): pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:00:1d.7: [8086:268c] type 00 class 0x0c0320
 1 Time(s): pci 0000:00:1d.7: reg 10: [mem 0xf9df0000-0xf9df03ff]
 1 Time(s): pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
 1 Time(s): pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
 2 Time(s): pci 0000:00:1e.0:   bridge window [io  0x2000-0x3fff]
 1 Time(s): pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
 2 Time(s): pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf7ffffff 64bit pref]
 1 Time(s): pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
 2 Time(s): pci 0000:00:1e.0:   bridge window [mem 0xf9e00000-0xf9ffffff]
 1 Time(s): pci 0000:00:1e.0: PCI bridge to [bus 01]
 1 Time(s): pci 0000:00:1e.0: PCI bridge to [bus 01] (subtractive decode)
 1 Time(s): pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
 1 Time(s): pci 0000:00:1e.0: setting latency timer to 64
 1 Time(s): pci 0000:00:1f.0: [8086:2670] type 00 class 0x060100
 1 Time(s): pci 0000:00:1f.0: rerouting interrupts for [8086:2670]
 1 Time(s): pci 0000:00:1f.2: PME# supported from D3hot
 1 Time(s): pci 0000:00:1f.2: [8086:2680] type 00 class 0x010180
 1 Time(s): pci 0000:00:1f.2: reg 10: [io  0x01f0-0x01f7]
 1 Time(s): pci 0000:00:1f.2: reg 14: [io  0x03f4-0x03f7]
 1 Time(s): pci 0000:00:1f.2: reg 18: [io  0x0170-0x0177]
 1 Time(s): pci 0000:00:1f.2: reg 1c: [io  0x0374-0x0377]
 1 Time(s): pci 0000:00:1f.2: reg 20: [io  0x0500-0x050f]
 1 Time(s): pci 0000:01:03.0: BAR 6: assigned [mem 0xf9e00000-0xf9e1ffff pref]
 1 Time(s): pci 0000:01:03.0: Boot video device
 1 Time(s): pci 0000:01:03.0: [1002:515e] type 00 class 0x030000
 1 Time(s): pci 0000:01:03.0: reg 10: [mem 0xf0000000-0xf7ffffff pref]
 1 Time(s): pci 0000:01:03.0: reg 14: [io  0x3000-0x30ff]
 1 Time(s): pci 0000:01:03.0: reg 18: [mem 0xf9ff0000-0xf9ffffff]
 1 Time(s): pci 0000:01:03.0: reg 30: [mem 0x00000000-0x0001ffff pref]
 1 Time(s): pci 0000:01:03.0: supports D1 D2
 1 Time(s): pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:01:04.0: [0e11:b203] type 00 class 0x088000
 1 Time(s): pci 0000:01:04.0: reg 10: [io  0x2800-0x28ff]
 1 Time(s): pci 0000:01:04.0: reg 14: [mem 0xf9fe0000-0xf9fe01ff]
 1 Time(s): pci 0000:01:04.2: BAR 6: assigned [mem 0xf9e20000-0xf9e2ffff pref]
 1 Time(s): pci 0000:01:04.2: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:01:04.2: [0e11:b204] type 00 class 0x088000
 1 Time(s): pci 0000:01:04.2: reg 10: [io  0x3400-0x34ff]
 1 Time(s): pci 0000:01:04.2: reg 14: [mem 0xf9fd0000-0xf9fd07ff]
 1 Time(s): pci 0000:01:04.2: reg 18: [mem 0xf9fc0000-0xf9fc3fff]
 1 Time(s): pci 0000:01:04.2: reg 1c: [mem 0xf9f00000-0xf9f7ffff]
 1 Time(s): pci 0000:01:04.2: reg 30: [mem 0x00000000-0x0000ffff pref]
 1 Time(s): pci 0000:01:04.4: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:01:04.4: [103c:3300] type 00 class 0x0c0300
 1 Time(s): pci 0000:01:04.4: reg 20: [io  0x3800-0x381f]
 1 Time(s): pci 0000:01:04.6: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:01:04.6: [103c:3302] type 00 class 0x0c0701
 1 Time(s): pci 0000:01:04.6: reg 10: [mem 0xf9ef0000-0xf9ef00ff]
 1 Time(s): pci 0000:02:00.0:   bridge window [mem 0xf8300000-0xf83fffff pref]
 2 Time(s): pci 0000:02:00.0:   bridge window [mem 0xfa000000-0xfbffffff]
 1 Time(s): pci 0000:02:00.0: BAR 15: assigned [mem 0xf8300000-0xf83fffff pref]
 2 Time(s): pci 0000:02:00.0: PCI bridge to [bus 03]
 1 Time(s): pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:02:00.0: [1166:0103] type 01 class 0x060400
 1 Time(s): pci 0000:02:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 1 Time(s): pci 0000:03:00.0: BAR 6: assigned [mem 0xf8300000-0xf831ffff pref]
 1 Time(s): pci 0000:03:00.0: PME# supported from D3hot D3cold
 1 Time(s): pci 0000:03:00.0: [14e4:164c] type 00 class 0x020000
 1 Time(s): pci 0000:03:00.0: reg 10: [mem 0xfa000000-0xfbffffff 64bit]
 1 Time(s): pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
 2 Time(s): pci 0000:04:00.0:   bridge window [io  0x4000-0x5fff]
 1 Time(s): pci 0000:04:00.0:   bridge window [mem 0xf8000000-0xf81fffff pref]
 2 Time(s): pci 0000:04:00.0:   bridge window [mem 0xfdb00000-0xfdefffff]
 1 Time(s): pci 0000:04:00.0: BAR 15: assigned [mem 0xf8000000-0xf81fffff pref]
 2 Time(s): pci 0000:04:00.0: PCI bridge to [bus 05-0b]
 1 Time(s): pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:04:00.0: [8086:3500] type 01 class 0x060400
 1 Time(s): pci 0000:04:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 2 Time(s): pci 0000:04:00.3: PCI bridge to [bus 0c-0e]
 1 Time(s): pci 0000:04:00.3: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:04:00.3: [8086:350c] type 01 class 0x060400
 2 Time(s): pci 0000:05:00.0:   bridge window [io  0x4000-0x4fff]
 1 Time(s): pci 0000:05:00.0:   bridge window [mem 0xf8000000-0xf80fffff pref]
 2 Time(s): pci 0000:05:00.0:   bridge window [mem 0xfdb00000-0xfdcfffff]
 1 Time(s): pci 0000:05:00.0: BAR 15: assigned [mem 0xf8000000-0xf80fffff pref]
 2 Time(s): pci 0000:05:00.0: PCI bridge to [bus 06-08]
 1 Time(s): pci 0000:05:00.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:05:00.0: [8086:3510] type 01 class 0x060400
 2 Time(s): pci 0000:05:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 2 Time(s): pci 0000:05:01.0:   bridge window [io  0x5000-0x5fff]
 1 Time(s): pci 0000:05:01.0:   bridge window [mem 0xf8100000-0xf81fffff pref]
 2 Time(s): pci 0000:05:01.0:   bridge window [mem 0xfdd00000-0xfdefffff]
 1 Time(s): pci 0000:05:01.0: BAR 15: assigned [mem 0xf8100000-0xf81fffff pref]
 2 Time(s): pci 0000:05:01.0: PCI bridge to [bus 09-0b]
 1 Time(s): pci 0000:05:01.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:05:01.0: [8086:3514] type 01 class 0x060400
 1 Time(s): pci 0000:06:00.0: BAR 6: assigned [mem 0xf8000000-0xf803ffff pref]
 1 Time(s): pci 0000:06:00.0: [103c:3230] type 00 class 0x010400
 1 Time(s): pci 0000:06:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 1 Time(s): pci 0000:06:00.0: reg 10: [mem 0xfdc00000-0xfdcfffff 64bit]
 1 Time(s): pci 0000:06:00.0: reg 18: [io  0x4000-0x40ff]
 1 Time(s): pci 0000:06:00.0: reg 1c: [mem 0xfdbf0000-0xfdbf0fff 64bit]
 1 Time(s): pci 0000:06:00.0: reg 30: [mem 0x00000000-0x0003ffff pref]
 1 Time(s): pci 0000:06:00.0: supports D1
 2 Time(s): pci 0000:09:00.0:   bridge window [io  0x5000-0x5fff]
 1 Time(s): pci 0000:09:00.0:   bridge window [mem 0xf8100000-0xf81fffff pref]
 2 Time(s): pci 0000:09:00.0:   bridge window [mem 0xfde00000-0xfdefffff]
 1 Time(s): pci 0000:09:00.0: BAR 15: assigned [mem 0xf8100000-0xf81fffff pref]
 2 Time(s): pci 0000:09:00.0: PCI bridge to [bus 0a]
 1 Time(s): pci 0000:09:00.0: PME# supported from D0 D3hot
 1 Time(s): pci 0000:09:00.0: [10b5:8114] type 01 class 0x060400
 1 Time(s): pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 1 Time(s): pci 0000:09:00.0: reg 10: [mem 0xfddf0000-0xfddf1fff]
 1 Time(s): pci 0000:0a:08.0: BAR 6: assigned [mem 0xf8100000-0xf81fffff pref]
 1 Time(s): pci 0000:0a:08.0: [1000:0030] type 00 class 0x010000
 1 Time(s): pci 0000:0a:08.0: reg 10: [io  0x5000-0x50ff]
 1 Time(s): pci 0000:0a:08.0: reg 14: [mem 0xfdee0000-0xfdefffff 64bit]
 1 Time(s): pci 0000:0a:08.0: reg 1c: [mem 0xfdec0000-0xfdedffff 64bit]
 1 Time(s): pci 0000:0a:08.0: reg 30: [mem 0x00000000-0x000fffff pref]
 1 Time(s): pci 0000:0a:08.0: supports D1 D2
 2 Time(s): pci 0000:12:00.0:   bridge window [io  0x6000-0x6fff]
 1 Time(s): pci 0000:12:00.0:   bridge window [mem 0xf8200000-0xf82fffff pref]
 2 Time(s): pci 0000:12:00.0:   bridge window [mem 0xfdf00000-0xfdffffff]
 1 Time(s): pci 0000:12:00.0: BAR 15: assigned [mem 0xf8200000-0xf82fffff pref]
 2 Time(s): pci 0000:12:00.0: PCI bridge to [bus 13-16]
 1 Time(s): pci 0000:12:00.0: PME# supported from D0 D3hot D3cold
 1 Time(s): pci 0000:12:00.0: [1166:0103] type 01 class 0x060400
 1 Time(s): pci 0000:12:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
 2 Time(s): pci 0000:13:04.0: PCI bridge to [bus 14-16]
 1 Time(s): pci 0000:13:04.0: [1166:0104] type 01 class 0x060400
 1 Time(s): pci 0000:13:08.0: BAR 6: assigned [mem 0xf8200000-0xf8203fff pref]
 1 Time(s): pci 0000:13:08.0: [103c:3238] type 00 class 0x010400
 1 Time(s): pci 0000:13:08.0: reg 10: [mem 0xfdf80000-0xfdffffff 64bit]
 1 Time(s): pci 0000:13:08.0: reg 18: [io  0x6000-0x60ff]
 1 Time(s): pci 0000:13:08.0: reg 1c: [mem 0xfdf70000-0xfdf77fff]
 1 Time(s): pci 0000:13:08.0: reg 30: [mem 0x00000000-0x00003fff pref]
 1 Time(s): pci 0000:13:08.0: supports D1
 1 Time(s): pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
 1 Time(s): pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
 1 Time(s): pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
 1 Time(s): pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
 1 Time(s): pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
 1 Time(s): pci_bus 0000:00: resource 7 [mem 0xf0000000-0xfebfffff]
 1 Time(s): pci_bus 0000:00: root bus resource [bus 00-7f]
 1 Time(s): pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
 1 Time(s): pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
 1 Time(s): pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
 1 Time(s): pci_bus 0000:00: root bus resource [mem 0xf0000000-0xfebfffff]
 1 Time(s): pci_bus 0000:01: resource 0 [io  0x2000-0x3fff]
 1 Time(s): pci_bus 0000:01: resource 1 [mem 0xf9e00000-0xf9ffffff]
 1 Time(s): pci_bus 0000:01: resource 2 [mem 0xf0000000-0xf7ffffff 64bit pref]
 1 Time(s): pci_bus 0000:01: resource 4 [io  0x0000-0x0cf7]
 1 Time(s): pci_bus 0000:01: resource 5 [io  0x0d00-0xffff]
 1 Time(s): pci_bus 0000:01: resource 6 [mem 0x000a0000-0x000bffff]
 1 Time(s): pci_bus 0000:01: resource 7 [mem 0xf0000000-0xfebfffff]
 1 Time(s): pci_bus 0000:02: resource 1 [mem 0xfa000000-0xfbffffff]
 1 Time(s): pci_bus 0000:02: resource 2 [mem 0xf8300000-0xf83fffff pref]
 1 Time(s): pci_bus 0000:03: resource 1 [mem 0xfa000000-0xfbffffff]
 1 Time(s): pci_bus 0000:03: resource 2 [mem 0xf8300000-0xf83fffff pref]
 1 Time(s): pci_bus 0000:04: resource 0 [io  0x4000-0x5fff]
 1 Time(s): pci_bus 0000:04: resource 1 [mem 0xfda00000-0xfdefffff]
 1 Time(s): pci_bus 0000:04: resource 2 [mem 0xf8000000-0xf81fffff pref]
 1 Time(s): pci_bus 0000:05: resource 0 [io  0x4000-0x5fff]
 1 Time(s): pci_bus 0000:05: resource 1 [mem 0xfdb00000-0xfdefffff]
 1 Time(s): pci_bus 0000:05: resource 2 [mem 0xf8000000-0xf81fffff pref]
 1 Time(s): pci_bus 0000:06: resource 0 [io  0x4000-0x4fff]
 1 Time(s): pci_bus 0000:06: resource 1 [mem 0xfdb00000-0xfdcfffff]
 1 Time(s): pci_bus 0000:06: resource 2 [mem 0xf8000000-0xf80fffff pref]
 1 Time(s): pci_bus 0000:09: resource 0 [io  0x5000-0x5fff]
 1 Time(s): pci_bus 0000:09: resource 1 [mem 0xfdd00000-0xfdefffff]
 1 Time(s): pci_bus 0000:09: resource 2 [mem 0xf8100000-0xf81fffff pref]
 1 Time(s): pci_bus 0000:0a: resource 0 [io  0x5000-0x5fff]
 1 Time(s): pci_bus 0000:0a: resource 1 [mem 0xfde00000-0xfdefffff]
 1 Time(s): pci_bus 0000:0a: resource 2 [mem 0xf8100000-0xf81fffff pref]
 1 Time(s): pci_bus 0000:12: resource 0 [io  0x6000-0x6fff]
 1 Time(s): pci_bus 0000:12: resource 1 [mem 0xfdf00000-0xfdffffff]
 1 Time(s): pci_bus 0000:12: resource 2 [mem 0xf8200000-0xf82fffff pref]
 1 Time(s): pci_bus 0000:13: resource 0 [io  0x6000-0x6fff]
 1 Time(s): pci_bus 0000:13: resource 1 [mem 0xfdf00000-0xfdffffff]
 1 Time(s): pci_bus 0000:13: resource 2 [mem 0xf8200000-0xf82fffff pref]
 1 Time(s): pci_hotplug: PCI Hot Plug PCI Core version: 0.5
 1 Time(s): pciehp: PCI Express Hot Plug Controller Driver version: 0.4
 1 Time(s): pcieport 0000:00:1c.0: irq 64 for MSI/MSI-X
 1 Time(s): pcpu-alloc: [0] 0 1 2 3 4 5 6 7
 1 Time(s): pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
 1 Time(s): pid_max: default: 32768 minimum: 301
 1 Time(s): platform rtc_cmos: registered platform RTC device (no PNP device found)
 1 Time(s): please try 'cgroup_disable=memory' option if you don't want memory cgroups
 1 Time(s): pnp 00:01: Plug and Play ACPI device, IDs IPI0001 (active)
 1 Time(s): pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
 1 Time(s): pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
 1 Time(s): pnp 00:03: [dma 7]
 1 Time(s): pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
 1 Time(s): pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
 1 Time(s): pnp 00:06: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)
 1 Time(s): pnp 00:07: Plug and Play ACPI device, IDs PNP0a06 (active)
 1 Time(s): pnp 00:08: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
 1 Time(s): pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (disabled)
 1 Time(s): pnp: PnP ACPI init
 1 Time(s): pnp: PnP ACPI: found 10 devices
 1 Time(s): ppdev: user-space parallel port driver
 1 Time(s): process: using mwait in idle threads
 1 Time(s): radeon 0000:01:03.0: GTT: 512M 0x00000000D0000000 - 0x00000000EFFFFFFF
 1 Time(s): radeon 0000:01:03.0: VRAM: 128M 0x00000000F0000000 - 0x00000000F7FFFFFF (32M used)
 1 Time(s): radeon 0000:01:03.0: WB disabled
 1 Time(s): radeon 0000:01:03.0: fb0: radeondrmfb frame buffer device
 1 Time(s): radeon 0000:01:03.0: fence driver on ring 0 use gpu addr 0x00000000d0000000 and cpu addr 0xffff880036850000
 1 Time(s): radeon 0000:01:03.0: registered panic notifier
 1 Time(s): registered taskstats version 1
 1 Time(s): regulator-dummy: no parameters
 1 Time(s): rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
 1 Time(s): rtc_cmos rtc_cmos: RTC can wake from S4
 1 Time(s): rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
 1 Time(s): rtc_cmos rtc_cmos: setting system clock to 2014-01-04 17:40:23 UTC (1388857223)
 1 Time(s): scsi 0:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH40L    LA00 PQ: 0 ANSI: 5
 1 Time(s): scsi 4:0:2:0: Attached scsi generic sg1 type 1
 1 Time(s): scsi 4:0:2:0: Sequential-Access TANDBERG TS400            0376 PQ: 0 ANSI: 3
 1 Time(s): scsi target4:0:2: Beginning Domain Validation
 1 Time(s): scsi target4:0:2: Domain Validation skipping write tests
 1 Time(s): scsi target4:0:2: Ending Domain Validation
 1 Time(s): scsi target4:0:2: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 126)
 1 Time(s): scsi0 : ata_piix
 1 Time(s): scsi1 : ata_piix
 1 Time(s): scsi2 : cciss
 1 Time(s): scsi3 : cciss
 1 Time(s): scsi4 : ioc0: LSI53C1020A A1, FwRev=01032700h, Ports=1, MaxQ=255, IRQ=17
 1 Time(s): serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
 1 Time(s): serio: i8042 AUX port at 0x60,0x64 irq 12
 1 Time(s): serio: i8042 KBD port at 0x60,0x64 irq 1
 1 Time(s): setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
 1 Time(s): shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
 1 Time(s): smpboot: Allowing 8 CPUs, 0 hotplug CPUs
 1 Time(s): smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
 1 Time(s): smpboot: CPU0: Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz (fam: 06, model: 17, stepping: 06)
 1 Time(s): smpboot: Total of 8 processors activated (40001.70 BogoMIPS)
 1 Time(s): software IO TLB [mem 0xdbe4e000-0xdfe4e000] (64MB) mapped at [ffff8800dbe4e000-ffff8800dfe4dfff]
 1 Time(s): sr 0:0:0:0: Attached scsi CD-ROM sr0
 1 Time(s): sr 0:0:0:0: Attached scsi generic sg0 type 5
 1 Time(s): sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
 1 Time(s): st 4:0:2:0: Attached scsi tape st0
 1 Time(s): st 4:0:2:0: st0: try direct i/o: yes (alignment 512 B)
 1 Time(s): st: Version 20101219, fixed bufsize 32768, s/g segs 256
 1 Time(s): system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
 1 Time(s): system 00:00: [io  0x02f8-0x02ff] has been reserved
 1 Time(s): system 00:00: [io  0x0408-0x040f] has been reserved
 1 Time(s): system 00:00: [io  0x04d0-0x04d1] has been reserved
 1 Time(s): system 00:00: [io  0x0700-0x071f] has been reserved
 1 Time(s): system 00:00: [io  0x0800-0x083f] has been reserved
 1 Time(s): system 00:00: [io  0x0900-0x097f] has been reserved
 1 Time(s): system 00:00: [io  0x0c80-0x0c83] has been reserved
 1 Time(s): system 00:00: [io  0x0ca0-0x0ca1] has been reserved
 1 Time(s): system 00:00: [io  0x0ca4-0x0ca5] has been reserved
 1 Time(s): system 00:00: [io  0x0cd4-0x0cd7] has been reserved
 1 Time(s): system 00:00: [io  0x0f50-0x0f58] has been reserved
 1 Time(s): system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
 1 Time(s): system 00:00: [mem 0xfe000000-0xfebfffff] has been reserved
 1 Time(s): thermal LNXTHERM:00: registered as thermal_zone0
 1 Time(s): tlb_flushall_shift: -1
 1 Time(s): tsc: Detected 2500.091 MHz processor
 1 Time(s): tsc: Fast TSC calibration using PIT
 1 Time(s): tsc: Marking TSC unstable due to TSC halts in idle
 1 Time(s): tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
 1 Time(s): tun: Universal TUN/TAP device driver, 1.6
 1 Time(s): uhci_hcd 0000:00:1d.0: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.0: irq 16, io base 0x00001000
 1 Time(s): uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
 1 Time(s): uhci_hcd 0000:00:1d.0: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.1: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.1: irq 17, io base 0x00001020
 1 Time(s): uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
 1 Time(s): uhci_hcd 0000:00:1d.1: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.2: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001040
 1 Time(s): uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
 1 Time(s): uhci_hcd 0000:00:1d.2: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:00:1d.3: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:00:1d.3: irq 19, io base 0x00001060
 1 Time(s): uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
 1 Time(s): uhci_hcd 0000:00:1d.3: setting latency timer to 64
 1 Time(s): uhci_hcd 0000:01:04.4: UHCI Host Controller
 1 Time(s): uhci_hcd 0000:01:04.4: irq 22, io base 0x00003800
 1 Time(s): uhci_hcd 0000:01:04.4: new USB bus registered, assigned bus number 6
 1 Time(s): uhci_hcd 0000:01:04.4: port count misdetected? forcing to 2 ports
 1 Time(s): uhci_hcd: USB Universal Host Controller Interface driver
 1 Time(s): usb 4-1: Manufacturer: Microsoft
 1 Time(s): usb 4-1: New USB device found, idVendor=045e, idProduct=0040
 1 Time(s): usb 4-1: New USB device strings: Mfr=1, Product=3, SerialNumber=0
 1 Time(s): usb 4-1: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
 1 Time(s): usb 4-1: new low-speed USB device number 2 using uhci_hcd
 1 Time(s): usb 6-1: Manufacturer: HP
 1 Time(s): usb 6-1: New USB device found, idVendor=03f0, idProduct=1027
 1 Time(s): usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
 1 Time(s): usb 6-1: Product: Virtual Keyboard
 1 Time(s): usb 6-1: new full-speed USB device number 2 using uhci_hcd
 1 Time(s): usb usb1: Manufacturer: Linux 3.8.0-35-generic ehci_hcd
 1 Time(s): usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
 1 Time(s): usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb1: Product: EHCI Host Controller
 1 Time(s): usb usb1: SerialNumber: 0000:00:1d.7
 1 Time(s): usb usb2: Manufacturer: Linux 3.8.0-35-generic uhci_hcd
 1 Time(s): usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
 1 Time(s): usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb2: Product: UHCI Host Controller
 1 Time(s): usb usb2: SerialNumber: 0000:00:1d.0
 1 Time(s): usb usb3: Manufacturer: Linux 3.8.0-35-generic uhci_hcd
 1 Time(s): usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
 1 Time(s): usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb3: Product: UHCI Host Controller
 1 Time(s): usb usb3: SerialNumber: 0000:00:1d.1
 1 Time(s): usb usb4: Manufacturer: Linux 3.8.0-35-generic uhci_hcd
 1 Time(s): usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
 1 Time(s): usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb4: Product: UHCI Host Controller
 1 Time(s): usb usb4: SerialNumber: 0000:00:1d.2
 1 Time(s): usb usb5: Manufacturer: Linux 3.8.0-35-generic uhci_hcd
 1 Time(s): usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
 1 Time(s): usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb5: Product: UHCI Host Controller
 1 Time(s): usb usb5: SerialNumber: 0000:00:1d.3
 1 Time(s): usb usb6: Manufacturer: Linux 3.8.0-35-generic uhci_hcd
 1 Time(s): usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
 1 Time(s): usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
 1 Time(s): usb usb6: Product: UHCI Host Controller
 1 Time(s): usb usb6: SerialNumber: 0000:01:04.4
 1 Time(s): usbcore: registered new device driver usb
 1 Time(s): usbcore: registered new interface driver hub
 1 Time(s): usbcore: registered new interface driver usbfs
 1 Time(s): usbcore: registered new interface driver usbhid
 1 Time(s): usbhid: USB HID core driver
 1 Time(s): vgaarb: bridge control possible 0000:01:03.0
 1 Time(s): vgaarb: device added: PCI:0000:01:03.0,decodes=io+mem,owns=io+mem,locks=none
 1 Time(s): vgaarb: loaded
 1 Time(s): x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
 

```

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Server Platforms**.*

Please use [code] tags. I have changed this one for you. ;)

---

### Post by martinmcanespie on 2014-01-06
It appears that the magento website log on the server became too big so i deleted it and so far today the server has been fine!

---

### Post by SeijiSensei on 2014-01-07
Add the log to the list in /etc/logrotate.d/rsyslog, and it will be automatically rotated for you.  Or you can create a custom definition for magento and place it in /etc/logrotate.d/.  Use the rsyslog file as a template.

---

