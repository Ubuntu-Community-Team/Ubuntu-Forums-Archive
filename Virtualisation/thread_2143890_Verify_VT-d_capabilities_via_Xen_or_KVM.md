---
title: "Verify VT-d capabilities via Xen or KVM?"
date: 2013-05-10
forum: Virtualisation
---

### Post by MaOs on 2013-05-10
Hi,

I am currently trying to figure out if my desktop machine (Dell XPS 8500) supports Intel's VT-d.

The processor is a Core i7 3770 and the chipset is a H77 PantherPoint.

I installed Xen 4.1 and did a 

```
xm dmesg
```

Now, the output is:

```
(XEN) Xen version 4.1.2 (Ubuntu 4.1.2-2ubuntu2.8) (stefan.bader@canonical.com) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) Mon Apr 29 19:04:55 UTC 2013(XEN) Bootloader: GRUB 1.99-21ubuntu3.9
(XEN) Command line: placeholder
(XEN) Video information:
(XEN)  VGA is text mode 80x25, font 8x16
(XEN)  VBE/DDC methods: V2; EDID transfer time: 1 seconds
(XEN) Disc information:
(XEN)  Found 2 MBR signatures
(XEN)  Found 2 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN)  0000000000000000 - 000000000009d800 (usable)
(XEN)  000000000009d800 - 00000000000a0000 (reserved)
(XEN)  00000000000e0000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 00000000de19f000 (usable)
(XEN)  00000000de19f000 - 00000000de3b2000 (reserved)
(XEN)  00000000de3b2000 - 00000000de7f0000 (ACPI NVS)
(XEN)  00000000de7f0000 - 00000000dedeb000 (reserved)
(XEN)  00000000dedeb000 - 00000000dedec000 (usable)
(XEN)  00000000dedec000 - 00000000dee2f000 (ACPI NVS)
(XEN)  00000000dee2f000 - 00000000df5d7000 (usable)
(XEN)  00000000df5d7000 - 00000000df7f2000 (reserved)
(XEN)  00000000df7f2000 - 00000000df800000 (usable)
(XEN)  00000000f8000000 - 00000000fc000000 (reserved)
(XEN)  00000000fec00000 - 00000000fec01000 (reserved)
(XEN)  00000000fed00000 - 00000000fed04000 (reserved)
(XEN)  00000000fed1c000 - 00000000fed20000 (reserved)
(XEN)  00000000fee00000 - 00000000fee01000 (reserved)
(XEN)  00000000ff000000 - 0000000100000000 (reserved)
(XEN)  0000000100000000 - 000000021f000000 (usable)
(XEN) ACPI: RSDP 000F0490, 0024 (r2 DELL  )
(XEN) ACPI: XSDT DE7E2080, 007C (r1 DELL    FX09    20100118 AMI        97)
(XEN) ACPI: FACP DE7EAA50, 010C (r5 DELL    FX09    20100118 AMI        97)
(XEN) ACPI Warning (tbfadt-0232): FADT (revision 5) is longer than ACPI 2.0 version, truncating length 0x10C to 0xF4 [20070126]
(XEN) ACPI: DSDT DE7E2190, 88B9 (r2 DELL    FX09           0 INTL 20051117)
(XEN) ACPI: FACS DE7EE080, 0040
(XEN) ACPI: APIC DE7EAB60, 0092 (r3 DELL    FX09    20100118 AMI        97)
(XEN) ACPI: FPDT DE7EABF8, 0044 (r1 DELL    FX09    20100118 AMI        97)
(XEN) ACPI: MCFG DE7EAC40, 003C (r1   DELL     FX09 20100118 MSFT       97)
(XEN) ACPI: SLIC DE7EAC80, 0176 (r1 DELL    FX09    20100118 MSFT       97)
(XEN) ACPI: HPET DE7EADF8, 0038 (r1   DELL     FX09 20100118 AMI.        5)
(XEN) ACPI: SSDT DE7EAE30, 036D (r1 SataRe SataTabl     1000 INTL 20091112)
(XEN) ACPI: MSDM DE7EB1A0, 0055 (r3 DELL    FX09    20100118 AMI        97)
(XEN) ACPI: SSDT DE7EB1F8, 09AA (r1  PmRef  Cpu0Ist     3000 INTL 20051117)
(XEN) ACPI: SSDT DE7EBBA8, 0A92 (r1  PmRef    CpuPm     3000 INTL 20051117)
(XEN) ACPI: DMAR DE7EC640, 0080 (r1 INTEL      SNB         1 INTL        1)
(XEN) System RAM: 8152MB (8348620kB)
(XEN) Domain heap initialised
(XEN) ACPI: 32/64X FACS address mismatch in FADT - de7ee080/0000000000000000, using 32
(XEN) Processor #0 7:10 APIC version 21
(XEN) Processor #2 7:10 APIC version 21
(XEN) Processor #4 7:10 APIC version 21
(XEN) Processor #6 7:10 APIC version 21
(XEN) Processor #1 7:10 APIC version 21
(XEN) Processor #3 7:10 APIC version 21
(XEN) Processor #5 7:10 APIC version 21
(XEN) Processor #7 7:10 APIC version 21
(XEN) IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
(XEN) Enabling APIC mode:  Flat.  Using 1 I/O APICs
(XEN) Table is not found!
(XEN) Switched to APIC driver x2apic_cluster.
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 3392.355 MHz processor.
(XEN) Initing memory sharing.
(XEN) Intel VT-d Snoop Control not enabled.
(XEN) Intel VT-d Dom0 DMA Passthrough not enabled.
(XEN) Intel VT-d Queued Invalidation enabled.
(XEN) Intel VT-d Interrupt Remapping enabled.
(XEN) Intel VT-d Shared EPT tables not enabled.
(XEN) I/O virtualisation enabled
(XEN)  - Dom0 mode: Relaxed
(XEN) Enabled directed EOI with ioapic_ack_old on!
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using old ACK method
(XEN) Platform timer is 14.318MHz HPET
(XEN) Allocated console ring of 16 KiB.
(XEN) VMX: Supported advanced features:
(XEN)  - APIC MMIO access virtualisation
(XEN)  - APIC TPR shadow
(XEN)  - Extended Page Tables (EPT)
(XEN)  - Virtual-Processor Identifiers (VPID)
(XEN)  - Virtual NMI
(XEN)  - MSR direct-access bitmap
(XEN)  - Unrestricted Guest
(XEN) EPT supports 2MB super page.
(XEN) HVM: ASIDs enabled.
(XEN) HVM: VMX enabled
(XEN) HVM: Hardware Assisted Paging detected.
(XEN) Brought up 8 CPUs
(XEN) *** LOADING DOMAIN 0 ***
(XEN)  Xen  kernel: 64-bit, lsb, compat32
(XEN)  Dom0 kernel: 64-bit, PAE, lsb, paddr 0x1000000 -> 0x205f000
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   0000000210000000->0000000214000000 (1999193 pages to be allocated)
(XEN)  Init. ramdisk: 000000021c9ee000->000000021efffe00
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: ffffffff81000000->ffffffff8205f000
(XEN)  Init. ramdisk: ffffffff8205f000->ffffffff84670e00
(XEN)  Phys-Mach map: ffffffff84671000->ffffffff855e4b58
(XEN)  Start info:    ffffffff855e5000->ffffffff855e54b4
(XEN)  Page tables:   ffffffff855e6000->ffffffff85615000
(XEN)  Boot stack:    ffffffff85615000->ffffffff85616000
(XEN)  TOTAL:         ffffffff80000000->ffffffff85800000
(XEN)  ENTRY ADDRESS: ffffffff81cfc200
(XEN) Dom0 has maximum 8 VCPUs
(XEN) Scrubbing Free RAM: .done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen)
(XEN) Freed 216kB init memory.
(XEN) physdev.c:162: dom0: wrong map_pirq type 3

```

The VT-d related output confuses me. It says I/O virtualisation is enabled, however, DMA remapping is not enabled. DMA remapping is one essential feature of VT-d (which I need). Any idea how to enable this? I checked the BIOS and enabled "Intel Virtualization Technology".

Thanks for any help!

---

### Post by pqwoerituytrueiwoq on 2013-05-10
[http://ark.intel.com/products/65719/#infosectionadvancedtechnologies-scrollpane](http://ark.intel.com/products/65719/#infosectionadvancedtechnologies-scrollpane)
yes it does
it may need to be enabled it in your bios
if virtualbox can boot a 64bit OS it is working

---

### Post by MaOs on 2013-05-10
All it says in the BIOS is "Intel Virtualization Technology". Not specifically VT-x or VT-d.

---

### Post by heiko_s on 2013-05-12
> **MaOs said:**
> Hi,

I am currently trying to figure out if my desktop machine (Dell XPS 8500) supports Intel's VT-d.

The processor is a Core i7 3770 and the chipset is a H77 PantherPoint.

...

The VT-d related output confuses me. It says I/O virtualisation is enabled, however, DMA remapping is not enabled. DMA remapping is one essential feature of VT-d (which I need). Any idea how to enable this? I checked the BIOS and enabled "Intel Virtualization Technology".

Thanks for any help!

The output looks OK - I got very much the same and PCI and VGA passthrough work just fine with Xen (so should it work with kvm).

If there are any issues, have another look at the BIOS settings. My board (Asus Sabertooth X79) has a VT-x or "Intel Virtualization Technology" option, as well as a VT-d option. However, the VT-d section is under a different menu, you probably have to search for that.  Normally VT-d would be disabled on most boards.

If you try to get VGA passthrough working, you may find these how-tos helpful:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=112013]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013") - I'm the author, so you can blame me if it doesn't work ;)

[http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787]("http://www.overclock.net/t/1205216/guide-create-a-gaming-virtual-machine/600#post_19770787") - this is for kvm

Under Xen, in order to check if VT-d works, just pass through a USB controller (use the pciback script in the Xen how-to) and check with
```
sudo xm pci-list-assignable-devices
```
The PCI ID of the passed through device should be listed.

---

