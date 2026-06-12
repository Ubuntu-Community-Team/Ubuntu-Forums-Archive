---
title: "xen-hypervisor-4.1-amd64 update (March 21,2013) breaks AMD-Vi ?"
date: 2013-03-26
forum: Virtualisation
---

### Post by blistovmhz on 2013-03-26
Update on March 21 broke my Xen :(
Package xen-hypervisor-4.1-amd64:amd64 (4.1.2-2ubuntu2.5, 4.1.2-2ubuntu2.6) was updated March 21, 2013.  I didn't reboot till today so didn't notice till now.
AMD-Vi fails to load with the following:
**(XEN) Initing memory sharing.**
**(XEN) IVHD Error: Invalid IO-APIC 0xff**
**(XEN) AMD-Vi: Error initialization**
**(XEN) I/O virtualisation disabled**



xm dmesg (full output): 
(XEN) Xen version 4.1.2 (Ubuntu 4.1.2-2ubuntu2.6) (stefan.bader@canonical.com) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) Mon Feb  4 16:41:16 UTC 2013
(XEN) Bootloader: GRUB 1.99-21ubuntu3.9
(XEN) Command line: pci_msitranslate=0 xen-pciback=passthrough xen-pciback.hide=(06:00.0)(06.00.1)
(XEN) Video information:
(XEN)  VGA is text mode 80x25, font 8x16
(XEN)  VBE/DDC methods: V2; EDID transfer time: 1 seconds
(XEN) Disc information:
(XEN)  Found 7 MBR signatures
(XEN)  Found 6 EDD information structures
(XEN) Xen-e820 RAM map:
(XEN)  0000000000000000 - 000000000009e800 (usable)
(XEN)  000000000009e800 - 00000000000a0000 (reserved)
(XEN)  00000000000e0000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 00000000bab4f000 (usable)
(XEN)  00000000bab4f000 - 00000000baf83000 (reserved)
(XEN)  00000000baf83000 - 00000000baf93000 (ACPI data)
(XEN)  00000000baf93000 - 00000000bbcfa000 (ACPI NVS)
(XEN)  00000000bbcfa000 - 00000000bca4f000 (reserved)
(XEN)  00000000bca4f000 - 00000000bca50000 (usable)
(XEN)  00000000bca50000 - 00000000bcc56000 (ACPI NVS)
(XEN)  00000000bcc56000 - 00000000bd083000 (usable)
(XEN)  00000000bd083000 - 00000000bd7f4000 (reserved)
(XEN)  00000000bd7f4000 - 00000000bd800000 (usable)
(XEN)  00000000f8000000 - 00000000fc000000 (reserved)
(XEN)  00000000fec00000 - 00000000fec01000 (reserved)
(XEN)  00000000fec10000 - 00000000fec11000 (reserved)
(XEN)  00000000fec20000 - 00000000fec21000 (reserved)
(XEN)  00000000fed00000 - 00000000fed01000 (reserved)
(XEN)  00000000fed61000 - 00000000fed71000 (reserved)
(XEN)  00000000fed80000 - 00000000fed90000 (reserved)
(XEN)  00000000fef00000 - 0000000100000000 (reserved)
(XEN)  0000000100001000 - 000000043f000000 (usable)
(XEN) ACPI: RSDP 000F0490, 0024 (r2 ALASKA)
(XEN) ACPI: XSDT BAF89070, 005C (r1 ALASKA    A M I  1072009 AMI     10013)
(XEN) ACPI: FACP BAF90BF8, 010C (r5 ALASKA    A M I  1072009 AMI     10013)
(XEN) ACPI Warning (tbfadt-0232): FADT (revision 5) is longer than ACPI 2.0 version, truncating length 0x10C to 0xF4 [20070126]
(XEN) ACPI Warning (tbfadt-0444): Optional field "Pm2ControlBlock" has zero address or length: 0000000000000000/1 [20070126]
(XEN) ACPI: DSDT BAF89168, 7A8A (r2 ALASKA    A M I        0 INTL 20051117)                                                                                                                                                                  
(XEN) ACPI: FACS BBCF4F80, 0040                                                                                                                                                                                                              
(XEN) ACPI: APIC BAF90D08, 009E (r3 ALASKA    A M I  1072009 AMI     10013)                                                                                                                                                                  
(XEN) ACPI: FPDT BAF90DA8, 0044 (r1 ALASKA    A M I  1072009 AMI     10013)                                                                                                                                                                  
(XEN) ACPI: MCFG BAF90DF0, 003C (r1 ALASKA    A M I  1072009 MSFT    10013)                                                                                                                                                                  
(XEN) ACPI: HPET BAF90E30, 0038 (r1 ALASKA    A M I  1072009 AMI         5)                                                                                                                                                                  
(XEN) ACPI: SSDT BAF90FC0, 1714 (r1 AMD    POWERNOW        1 AMD         1)
(XEN) ACPI: IVRS BAF90EC0, 0100 (r1  AMD     RD890S   202031 AMD         0)
(XEN) System RAM: 16287MB (16678040kB)
(XEN) Domain heap initialised
(XEN) ACPI: 32/64X FACS address mismatch in FADT - bbcf4f80/0000000000000000, using 32
(XEN) Processor #16 5:1 APIC version 16
(XEN) Processor #17 5:1 APIC version 16
(XEN) Processor #18 5:1 APIC version 16
(XEN) Processor #19 5:1 APIC version 16
(XEN) Processor #20 5:1 APIC version 16
(XEN) Processor #21 5:1 APIC version 16
(XEN) Processor #22 5:1 APIC version 16
(XEN) Processor #23 5:1 APIC version 16
(XEN) IOAPIC[0]: apic_id 9, version 33, address 0xfec00000, GSI 0-23
(XEN) IOAPIC[1]: apic_id 10, version 33, address 0xfec20000, GSI 24-55
(XEN) Enabling APIC mode:  Flat.  Using 2 I/O APICs
(XEN) Table is not found!
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Detected 3913.328 MHz processor.
(XEN) Initing memory sharing.
(XEN) IVHD Error: Invalid IO-APIC 0xff
(XEN) AMD-Vi: Error initialization
(XEN) I/O virtualisation disabled
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) Platform timer is 14.318MHz HPET
(XEN) Allocated console ring of 16 KiB.
(XEN) HVM: ASIDs enabled.
(XEN) SVM: Supported advanced features:
(XEN)  - Nested Page Tables (NPT)
(XEN)  - Last Branch Record (LBR) Virtualisation
(XEN)  - Next-RIP Saved on #VMEXIT
(XEN)  - VMCB Clean Bits
(XEN)  - Pause-Intercept Filter
(XEN) HVM: SVM enabled
(XEN) HVM: Hardware Assisted Paging detected.
(XEN) Brought up 8 CPUs
(XEN) *** LOADING DOMAIN 0 ***
(XEN)  Xen  kernel: 64-bit, lsb, compat32
(XEN)  Dom0 kernel: 64-bit, PAE, lsb, paddr 0x1000000 -> 0x234d000
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   0000000420000000->0000000428000000 (4047290 pages to be allocated)
(XEN)  Init. ramdisk: 000000043c817000->000000043efff800
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: ffffffff81000000->ffffffff8234d000
(XEN)  Init. ramdisk: ffffffff8234d000->ffffffff84b35800
(XEN)  Phys-Mach map: ffffffff84b36000->ffffffff86a6ad18
(XEN)  Start info:    ffffffff86a6b000->ffffffff86a6b4b4
(XEN)  Page tables:   ffffffff86a6c000->ffffffff86aa5000
(XEN)  Boot stack:    ffffffff86aa5000->ffffffff86aa6000
(XEN)  TOTAL:         ffffffff80000000->ffffffff86c00000
(XEN)  ENTRY ADDRESS: ffffffff81cf7210
(XEN) Dom0 has maximum 8 VCPUs
(XEN) Scrubbing Free RAM: .done.
(XEN) Xen trace buffers: disabled
(XEN) Std. Loglevel: Errors and warnings
(XEN) Guest Loglevel: Nothing (Rate-limited: Errors and warnings)
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type \047CTRL-a\047 three times to switch input to Xen)
(XEN) Freed 216kB init memory.
(XEN) traps.c:2432:d0 Domain attempted WRMSR 00000000c0010201 from 0x0000000000000000 to 0x000000000000ffff.
(XEN) physdev.c:162: dom0: wrong map_pirq type 3


Anyone else run into this yet?

This is running on an Asus Sabretooth 990fx R2.0 /  AMD FX-8120
No hardware nor configuration changes made.  Setup worked properly until update.

---

