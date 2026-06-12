---
title: "MCE entries in dmesg"
date: 2007-04-28
forum: Server Platforms
---

### Post by chrroessner on 2007-04-28
Hi,

I have seen errors in my dmesg log on a dual AMD Opteron server running XEN:

```

 __  __            _____  ___   _____     ___  
 \ \/ /___ _ __   |___ / / _ \ |___ /    / _ \ 
  \  // _ \ '_ \    |_ \| | | |  |_ \ __| | | |
  /  \  __/ | | |  ___) | |_| | ___) |__| |_| |
 /_/\_\___|_| |_| |____(_)___(_)____/    \___/ 
                                               
 http://www.cl.cam.ac.uk/netos/xen
 University of Cambridge Computer Laboratory

 Xen version 3.0.3-0 (buildd@buildd) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) Thu Oct 19 02:31:23 UTC 2006
 Latest ChangeSet: unavailable 

(XEN) Command line: /xen-3.0-i386-pae.gz
(XEN) Physical RAM map:
(XEN)  0000000000000000 - 000000000009fc00 (usable)
(XEN)  000000000009fc00 - 00000000000a0000 (reserved)
(XEN)  00000000000e8000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 000000007fff0000 (usable)
(XEN)  000000007fff0000 - 000000007ffff000 (ACPI data)
(XEN)  000000007ffff000 - 0000000080000000 (ACPI NVS)
(XEN)  00000000ff780000 - 0000000100000000 (reserved)
(XEN) System RAM: 2047MB (2096700kB)
(XEN) Xen heap: 10MB (10344kB)
(XEN) PAE enabled, limit: 16 GB
(XEN) found SMP MP-table at 000ff780
(XEN) DMI 2.3 present.
(XEN) Using APIC driver default
(XEN) ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9870
(XEN) ACPI: RSDT (v001 A M I  OEMRSDT  0x05000622 MSFT 0x00000097) @ 0x7fff0000
(XEN) ACPI: FADT (v002 A M I  OEMFACP  0x05000622 MSFT 0x00000097) @ 0x7fff0200
(XEN) ACPI: MADT (v001 A M I  OEMAPIC  0x05000622 MSFT 0x00000097) @ 0x7fff0380
(XEN) ACPI: OEMB (v001 A M I  OEMBIOS  0x05000622 MSFT 0x00000097) @ 0x7ffff040
(XEN) ACPI: SRAT (v001 A M I  OEMSRAT  0x05000622 MSFT 0x00000097) @ 0x7fff38d0
(XEN) ACPI: DSDT (v001  H8DA8 H8DA8010 0x00000000 INTL 0x02002026) @ 0x00000000
(XEN) ACPI: Local APIC address 0xfee00000
(XEN) ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
(XEN) Processor #0 15:5 APIC version 16
(XEN) ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
(XEN) Processor #1 15:5 APIC version 16
(XEN) ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
(XEN) ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
(XEN) ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
(XEN) IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
(XEN) ACPI: IOAPIC (id[0x03] address[0xfebfe000] gsi_base[24])
(XEN) IOAPIC[1]: apic_id 3, version 17, address 0xfebfe000, GSI 24-27
(XEN) ACPI: IOAPIC (id[0x04] address[0xfebff000] gsi_base[28])
(XEN) IOAPIC[2]: apic_id 4, version 17, address 0xfebff000, GSI 28-31
(XEN) ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
(XEN) ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
(XEN) ACPI: IRQ0 used by override.
(XEN) ACPI: IRQ2 used by override.
(XEN) Enabling APIC mode:  Flat.  Using 3 I/O APICs
(XEN) Using ACPI (MADT) for SMP configuration information
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Initializing CPU#0
(XEN) Detected 1994.343 MHz processor.
(XEN) CPU0: AMD Flush Filter disabled
(XEN) CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
(XEN) CPU: L2 Cache: 1024K (64 bytes/line)
(XEN) Intel machine check architecture supported.
(XEN) Intel machine check reporting enabled on CPU#0.
(XEN) CPU0: AMD Opteron(tm) Processor 246 stepping 01
(XEN) Booting processor 1/1 eip 90000
(XEN) Initializing CPU#1
(XEN) CPU1: AMD Flush Filter disabled
(XEN) CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
(XEN) CPU: L2 Cache: 1024K (64 bytes/line)
(XEN) AMD: Disabling C1 Clock Ramping Node #0
(XEN) AMD: Disabling C1 Clock Ramping Node #1
(XEN) Intel machine check architecture supported.
(XEN) Intel machine check reporting enabled on CPU#1.
(XEN) CPU1: AMD Opteron(tm) Processor 246 stepping 01
(XEN) Total of 2 processors activated.
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) ..TIMER: vector=0xF0 apic1=0 pin1=2 apic2=0 pin2=0
(XEN) checking TSC synchronization across 2 CPUs: passed.
(XEN) Platform timer is 1.193MHz PIT
(XEN) Brought up 2 CPUs
(XEN) Machine check exception polling timer started.
(XEN) *** LOADING DOMAIN 0 ***
(XEN) Domain 0 kernel supports features = { 0000001f }.
(XEN) Domain 0 kernel requires features = { 00000000 }.
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   000000007c000000->000000007e000000 (477073 pages to be allocated)
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: c0100000->c0480734
(XEN)  Init. ramdisk: c0481000->c1261c00
(XEN)  Phys-Mach map: c1262000->c143be44
(XEN)  Start info:    c143c000->c143c46c
(XEN)  Page tables:   c143d000->c144e000
(XEN)  Boot stack:    c144e000->c144f000
(XEN)  TOTAL:         c0000000->c1800000
(XEN)  ENTRY ADDRESS: c0100000
(XEN) Dom0 has maximum 2 VCPUs
(XEN) Initrd len 0xde0c00, start at 0xc0481000
(XEN) Scrubbing Free RAM: .....................done.
(XEN) Xen trace buffers: disabled
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen).
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: d410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: d410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d400400000000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: d000400000000863
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9420400100000813
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9000400000000863
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9000400000000863
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 0: 8410400000000833
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 0: 8410400000000833
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 4: 9410400000000a13
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 0: 8408400000000833
(XEN) MCE: The hardware reports a non fatal, correctable incident occurred on CPU 1.
(XEN) Bank 2: 9000400000000863

```

So I googled around, but could not really find an answer, what these errors really mean and what could have caused them. The only thing I found out was to not just ignore them, because the server wants to tell me something.

The same machine sometimes crashes its DomU. And I did not find the real answer, yet, why the DomU crashed. I first thought of the NETTX(k)-4GB bug (and currently do still think), but maybe the MCE stuff is a problem, too.

The Dom0 is running on Ubuntu Edgy Eft, the DomU is running with Ubuntu Dapper Drake.

If anybody would have any idea (and might it be as little as can be), I really would be happy about it.

Thanks in advance

Christian

---

