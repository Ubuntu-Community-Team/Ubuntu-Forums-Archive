---
title: "ffado driver with 2.6.28-3-rt?"
date: 2009-04-26
forum: Ubuntu Studio
---

### Post by _nate on 2009-04-26
Has anyone been able to get this working without a bunch of xruns or crashing?

---

### Post by Stochastic on 2009-04-26
Yes, it works fine for me.

---

### Post by _nate on 2009-04-27
Did you have to configure anything manually?  I am using a Presonus Firebox 

Here is what my syslog is showing:

Apr 26 22:00:40 ubuntu kernel: [  348.094747] doh, someone wants to mess with state set
Apr 26 22:00:40 ubuntu kernel: [  348.414534] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Apr 26 22:00:40 ubuntu kernel: [  348.414551] ieee1394: Node reactivated: ID:BUS[0-00:1023]  GUID[000a9200d7011288]
Apr 26 22:00:48 ubuntu kernel: [  356.546372] ohci1394: fw-host0: IR DMA error - OHCI error code 0x1d
Apr 26 22:00:48 ubuntu kernel: [  356.546374] 
Apr 26 22:01:17 ubuntu kernel: [  385.669022] ohci1394: fw-host0: IR DMA error - OHCI error code 0x1d
Apr 26 22:01:17 ubuntu kernel: [  385.669025] 
Apr 26 22:01:22 ubuntu kernel: [  390.385953] ohci1394: fw-host0: IR DMA error - OHCI error code 0x1d
Apr 26 22:01:22 ubuntu kernel: [  390.385956] 
Apr 26 22:01:22 ubuntu kernel: [  390.386064] jackd[4541]: segfault at 7f276105c000 ip 00007f275fafe11b sp 00007f2759807ba8 error 4 in libc-2.9.so[7f275fa7a000+168000]

---

### Post by _nate on 2009-04-27
Here is what my interrupts show.  I am not sure what this means but I read somewhere that two devices shouldn't have the same id of something.

cat /proc/interrupts
           CPU0       CPU1       
  0:       1387     389404   IO-APIC-edge      timer
  1:          0          8   IO-APIC-edge      i8042
  4:          0          2   IO-APIC-edge    
  7:          1          0   IO-APIC-edge      parport0
  8:          0          1   IO-APIC-edge      rtc0
  9:          0          1   IO-APIC-fasteoi   acpi
 12:         21       1519   IO-APIC-edge      i8042
 14:          5        710   IO-APIC-edge      pata_atiixp
 15:          0          0   IO-APIC-edge      pata_atiixp
 16:         40       4681   IO-APIC-fasteoi   ohci_hcd:usb2, HDA Intel
 17:          1        161   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb5
 18:          0          0   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb6
 19:          4        540   IO-APIC-fasteoi   radeon@pci:0000:01:05.0
 20:          5        687   IO-APIC-fasteoi   ehci_hcd:usb1
 22:        119      12490   IO-APIC-fasteoi   ahci
 23:          1         85   IO-APIC-fasteoi   ohci1394, yenta
2301:          5       1451   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     220954      34598   Local timer interrupts
RES:      27115      15156   Rescheduling interrupts
CAL:         61         55   Function call interrupts
TLB:       1113        923   TLB shootdowns
SPU:          0          0   Spurious interrupts
ERR:          1
MIS:          0

---

