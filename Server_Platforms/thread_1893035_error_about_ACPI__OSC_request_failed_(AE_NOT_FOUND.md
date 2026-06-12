---
title: "error about ACPI _OSC request failed (AE_NOT_FOUND)"
date: 2011-12-09
forum: Server Platforms
---

### Post by yavuz.maslak on 2011-12-09
I have ubuntu server 11.10 64 bit 

I see an error in kernel.log. This error comes out  when the server reboot.

some port of grep APCI in kernel.log;
Dec  5 09:08:51 www kernel: [    0.588605]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec  5 09:08:51 www kernel: [    0.588667]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  5 09:08:51 www kernel: [    0.588746] ACPI _OSC control for PCIe not granted, disabling ASPM

Which hardware may be cause this error ? 

root@www:# grep -r ACPI /var/log/kern.log
Dec  5 09:08:51 www kernel: [    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf798000 (ACPI data)
Dec  5 09:08:51 www kernel: [    0.000000]  BIOS-e820: 00000000bf798000 - 00000000bf7dc000 (ACPI NVS)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: RSDP 00000000000fb1a0 00014 (v00 ACPIAM)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: RSDT 00000000bf780000 00040 (v01 022410 RSDT1405 20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: FACP 00000000bf780200 00084 (v01 022410 FACP1405 20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: DSDT 00000000bf7804b0 0C359 (v01  A1279 A1279001 00000001 INTL 20060113)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: FACS 00000000bf798000 00040
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: APIC 00000000bf780390 000D8 (v01 022410 APIC1405 20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: MCFG 00000000bf780470 0003C (v01 022410 OEMMCFG  20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: OEMB 00000000bf798040 00072 (v01 022410 OEMB1405 20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: HPET 00000000bf78f4b0 00038 (v01 022410 OEMHPET  20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: OSFR 00000000bf78f4f0 000B0 (v01 022410 OEMOSFR  20100224 MSFT 00000097)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: SSDT 00000000bf798fe0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec8a000] gsi_base[24])
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  5 09:08:51 www kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  5 09:08:51 www kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Dec  5 09:08:51 www kernel: [    0.009507] ACPI: Core revision 20110413
Dec  5 09:08:51 www kernel: [    0.499129] PM: Registering ACPI NVS region at bf798000 (278528 bytes)
Dec  5 09:08:51 www kernel: [    0.500749] ACPI: bus type pci registered
Dec  5 09:08:51 www kernel: [    0.502747] ACPI: EC: Look up EC in DSDT
Dec  5 09:08:51 www kernel: [    0.503788] ACPI: Executed 1 blocks of module-level executable AML code
Dec  5 09:08:51 www kernel: [    0.520435] ACPI: SSDT 00000000bf7980c0 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Dec  5 09:08:51 www kernel: [    0.520863] ACPI: Dynamic OEM Table Load:
Dec  5 09:08:51 www kernel: [    0.520990] ACPI: SSDT           (null) 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Dec  5 09:08:51 www kernel: [    0.521308] ACPI: Interpreter enabled
Dec  5 09:08:51 www kernel: [    0.521366] ACPI: (supports S0 S1 S3 S4 S5)
Dec  5 09:08:51 www kernel: [    0.521611] ACPI: Using IOAPIC for interrupt routing
Dec  5 09:08:51 www kernel: [    0.522622] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec  5 09:08:51 www kernel: [    0.554150] ACPI: No dock devices found.
Dec  5 09:08:51 www kernel: [    0.554267] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec  5 09:08:51 www kernel: [    0.555231] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec  5 09:08:51 www kernel: [    0.588224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  5 09:08:51 www kernel: [    0.588398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec  5 09:08:51 www kernel: [    0.588451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Dec  5 09:08:51 www kernel: [    0.588473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
Dec  5 09:08:51 www kernel: [    0.588492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Dec  5 09:08:51 www kernel: [    0.588512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Dec  5 09:08:51 www kernel: [    0.588540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
Dec  5 09:08:51 www kernel: [    0.588559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
Dec  5 09:08:51 www kernel: [    0.588579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
Dec  5 09:08:51 www kernel: [    0.588605]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec  5 09:08:51 www kernel: [    0.588667]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  5 09:08:51 www kernel: [    0.588746] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec  5 09:08:51 www kernel: [    0.597666] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12 14 *15)
Dec  5 09:08:51 www kernel: [    0.598142] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Dec  5 09:08:51 www kernel: [    0.598336] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
Dec  5 09:08:51 www kernel: [    0.598810] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
Dec  5 09:08:51 www kernel: [    0.599284] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 *14 15)
Dec  5 09:08:51 www kernel: [    0.599762] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
Dec  5 09:08:51 www kernel: [    0.600236] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
Dec  5 09:08:51 www kernel: [    0.600709] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
Dec  5 09:08:51 www kernel: [    0.601931] PCI: Using ACPI for IRQ routing
Dec  5 09:08:51 www kernel: [    0.628146] pnp: PnP ACPI init
Dec  5 09:08:51 www kernel: [    0.628211] ACPI: bus type pnp registered
Dec  5 09:08:51 www kernel: [    0.628417] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec  5 09:08:51 www kernel: [    0.628859] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  5 09:08:51 www kernel: [    0.628915] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec  5 09:08:51 www kernel: [    0.628951] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec  5 09:08:51 www kernel: [    0.628975] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Dec  5 09:08:51 www kernel: [    0.629004] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec  5 09:08:51 www kernel: [    0.629229] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  5 09:08:51 www kernel: [    0.629779] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  5 09:08:51 www kernel: [    0.629849] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Dec  5 09:08:51 www kernel: [    0.629901] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
Dec  5 09:08:51 www kernel: [    0.630030] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  5 09:08:51 www kernel: [    0.630254] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  5 09:08:51 www kernel: [    0.630304] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Dec  5 09:08:51 www kernel: [    0.630359] pnp 00:0d: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
Dec  5 09:08:51 www kernel: [    0.630492] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  5 09:08:51 www kernel: [    0.630986] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  5 09:08:51 www kernel: [    0.631078] pnp: PnP ACPI: found 16 devices
Dec  5 09:08:51 www kernel: [    0.631135] ACPI: ACPI bus type pnp unregistered
Dec  5 09:08:51 www kernel: [    0.726291] ACPI: Power Button [PWRB]
Dec  5 09:08:51 www kernel: [    0.726452] ACPI: Power Button [PWRF]
Dec  5 09:08:51 www kernel: [    0.726527] ACPI: acpi_idle yielding to intel_idle
Dec  7 21:45:22 www kernel: [    0.000000]  BIOS-e820: 00000000bf780000 - 00000000bf798000 (ACPI data)
Dec  7 21:45:22 www kernel: [    0.000000]  BIOS-e820: 00000000bf798000 - 00000000bf7dc000 (ACPI NVS)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: RSDP 00000000000fb1a0 00014 (v00 ACPIAM)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: RSDT 00000000bf780000 00040 (v01 022410 RSDT1405 20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: FACP 00000000bf780200 00084 (v01 022410 FACP1405 20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: DSDT 00000000bf7804b0 0C359 (v01  A1279 A1279001 00000001 INTL 20060113)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: FACS 00000000bf798000 00040
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: APIC 00000000bf780390 000D8 (v01 022410 APIC1405 20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: MCFG 00000000bf780470 0003C (v01 022410 OEMMCFG  20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: OEMB 00000000bf798040 00072 (v01 022410 OEMB1405 20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: HPET 00000000bf78f4b0 00038 (v01 022410 OEMHPET  20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: OSFR 00000000bf78f4f0 000B0 (v01 022410 OEMOSFR  20100224 MSFT 00000097)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: SSDT 00000000bf798fe0 00363 (v01 DpgPmm    CpuPm 00000012 INTL 20060113)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x86] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x87] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x88] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x89] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x8a] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x8b] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x8c] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x8d] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x8e] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x8f] disabled)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec8a000] gsi_base[24])
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec  7 21:45:22 www kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec  7 21:45:22 www kernel: [    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
Dec  7 21:45:22 www kernel: [    0.009505] ACPI: Core revision 20110413
Dec  7 21:45:22 www kernel: [    0.499203] PM: Registering ACPI NVS region at bf798000 (278528 bytes)
Dec  7 21:45:22 www kernel: [    0.500819] ACPI: bus type pci registered
Dec  7 21:45:22 www kernel: [    0.503121] ACPI: EC: Look up EC in DSDT
Dec  7 21:45:22 www kernel: [    0.504162] ACPI: Executed 1 blocks of module-level executable AML code
Dec  7 21:45:22 www kernel: [    0.520821] ACPI: SSDT 00000000bf7980c0 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Dec  7 21:45:22 www kernel: [    0.521247] ACPI: Dynamic OEM Table Load:
Dec  7 21:45:22 www kernel: [    0.521374] ACPI: SSDT           (null) 00F20 (v01 DpgPmm  P001Ist 00000011 INTL 20060113)
Dec  7 21:45:22 www kernel: [    0.521691] ACPI: Interpreter enabled
Dec  7 21:45:22 www kernel: [    0.521748] ACPI: (supports S0 S1 S3 S4 S5)
Dec  7 21:45:22 www kernel: [    0.521993] ACPI: Using IOAPIC for interrupt routing
Dec  7 21:45:22 www kernel: [    0.523002] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Dec  7 21:45:22 www kernel: [    0.554533] ACPI: No dock devices found.
Dec  7 21:45:22 www kernel: [    0.554649] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec  7 21:45:22 www kernel: [    0.555620] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec  7 21:45:22 www kernel: [    0.588224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec  7 21:45:22 www kernel: [    0.588398] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec  7 21:45:22 www kernel: [    0.588451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
Dec  7 21:45:22 www kernel: [    0.588473] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
Dec  7 21:45:22 www kernel: [    0.588492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Dec  7 21:45:22 www kernel: [    0.588512] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
Dec  7 21:45:22 www kernel: [    0.588540] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE1._PRT]
Dec  7 21:45:22 www kernel: [    0.588559] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE3._PRT]
Dec  7 21:45:22 www kernel: [    0.588579] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NPE7._PRT]
Dec  7 21:45:22 www kernel: [    0.588606]  pci0000:00: Requesting ACPI _OSC control (0x1d)
Dec  7 21:45:22 www kernel: [    0.588667]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
Dec  7 21:45:22 www kernel: [    0.588746] ACPI _OSC control for PCIe not granted, disabling ASPM
Dec  7 21:45:22 www kernel: [    0.597661] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 11 12 14 *15)
Dec  7 21:45:22 www kernel: [    0.598137] ACPI: PCI Interrupt Link [LNKB] (IRQs *5)
Dec  7 21:45:22 www kernel: [    0.598331] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 10 *11 12 14 15)
Dec  7 21:45:22 www kernel: [    0.598804] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 *10 11 12 14 15)
Dec  7 21:45:22 www kernel: [    0.599278] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12 *14 15)
Dec  7 21:45:22 www kernel: [    0.599756] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 6 7 10 11 12 14 15)
Dec  7 21:45:22 www kernel: [    0.600230] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 6 *7 10 11 12 14 15)
Dec  7 21:45:22 www kernel: [    0.600704] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 *4 6 7 10 11 12 14 15)
Dec  7 21:45:22 www kernel: [    0.601926] PCI: Using ACPI for IRQ routing
Dec  7 21:45:22 www kernel: [    0.624115] pnp: PnP ACPI init
Dec  7 21:45:22 www kernel: [    0.624179] ACPI: bus type pnp registered
Dec  7 21:45:22 www kernel: [    0.624382] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
Dec  7 21:45:22 www kernel: [    0.624821] system 00:01: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  7 21:45:22 www kernel: [    0.624875] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
Dec  7 21:45:22 www kernel: [    0.624911] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
Dec  7 21:45:22 www kernel: [    0.624933] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
Dec  7 21:45:22 www kernel: [    0.624962] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
Dec  7 21:45:22 www kernel: [    0.625186] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  7 21:45:22 www kernel: [    0.625733] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  7 21:45:22 www kernel: [    0.625803] pnp 00:08: Plug and Play ACPI device, IDs PNP0103 (active)
Dec  7 21:45:22 www kernel: [    0.625856] pnp 00:09: Plug and Play ACPI device, IDs INT0800 (active)
Dec  7 21:45:22 www kernel: [    0.625984] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  7 21:45:22 www kernel: [    0.626206] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  7 21:45:22 www kernel: [    0.626256] pnp 00:0c: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
Dec  7 21:45:22 www kernel: [    0.626312] pnp 00:0d: Plug and Play ACPI device, IDs PNP0f03 PNP0f13 (active)
Dec  7 21:45:22 www kernel: [    0.626445] system 00:0e: Plug and Play ACPI device, IDs PNP0c02 (active)
Dec  7 21:45:22 www kernel: [    0.626936] system 00:0f: Plug and Play ACPI device, IDs PNP0c01 (active)
Dec  7 21:45:22 www kernel: [    0.627027] pnp: PnP ACPI: found 16 devices
Dec  7 21:45:22 www kernel: [    0.627084] ACPI: ACPI bus type pnp unregistered
Dec  7 21:45:22 www kernel: [    0.722086] ACPI: Power Button [PWRB]
Dec  7 21:45:22 www kernel: [    0.722246] ACPI: Power Button [PWRF]
Dec  7 21:45:22 www kernel: [    0.722320] ACPI: acpi_idle yielding to intel_idle

---

### Post by RavanH on 2012-01-13
Getting the same fail:

```
...
[    0.333326]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.333329]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.333331] ACPI _OSC control for PCIe not granted, disabling ASPM
...
```

Disabling ASPM [http://www.lesswatts.org/projects/devices-power-management/pcie.php](http://www.lesswatts.org/projects/devices-power-management/pcie.php) seems a pitty on my Dell Latitude E6400 laptop :(

---

