---
title: "ksoftirqd/0 high CPU load"
date: 2010-01-27
forum: Server Platforms
---

### Post by danep on 2010-01-27
Hi all- I just installed Karmic on a new Dell Poweredge 200 server and have noticed that ksoftirqd/0 is eating up an unreasonable amount of CPU time, averaging 5-10% but spiking to 100% occasionally and inexplicably. This is my first experience with an "enterprise" server, but I'm assuming that this is not normal. I have seen similar threads on this issue but they all focused around TV tuner cards, which obviously I don't have.

The only thing that I suspect could be related is Dell's OMSA software - the dsm_sa_datamgr32d and dsm_sa_snmp32d processes average about 1% load. Powertop shows each of these as the top causes for wakeups, almost 1000 times  / sec (note, however, that this data is from a period of low ksoftirqd activity, as luck would have it). Below is my output from /proc/interrupts.

Does anyone have any idea what might be causing this, or at least how I might go about investigating/confirming the cause? Thanks in advance.
```

           CPU0       CPU1       
  0:        297        270   IO-APIC-edge      timer
  1:          0          2   IO-APIC-edge      i8042
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          2          2   IO-APIC-edge      i8042
 16:     183518     183564   IO-APIC-fasteoi   ioc0
 20:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 21:         13         12   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb4
 23:          0          0   IO-APIC-fasteoi   ata_piix
 28:     176162     176119   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:  169282142  132710989   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:       1532       1981   Rescheduling interrupts
CAL:         34         51   Function call interrupts
TLB:      16873       9516   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:        544        544   Machine check polls
ERR:          0
MIS:          0
```

---

