---
title: "Many xruns on Ubuntu Studio 13.04 Beta on Toshiba Satellite P870"
date: 2013-04-19
forum: Ubuntu Studio
---

### Post by darwincommarts on 2013-04-19
i have Ubuntu Studio 13.04 Beta 2 on a Toshiba Satellite P870. with Jack, I get xruns at anything less than 256 frames/period (Sample Rate: 48000, Periods/Buffer: 3). Its a decently-specified machine (i7, 16Gb RAM, 1Tb HD, etc), bought two weeks go. But I'm getting better performance from less well-specified, older machines, running Ubuntu Studio 13.04 Beta 1, and Ubuntu Studio 12.04. Any suggestions to improve performance/reduce latency appreciated.

---

### Post by jejeman on 2013-04-19
Why 3 periods? USB card?
What's your
```
cat /proc/interrupts
```

---

### Post by darwincommarts on 2013-04-20
Thanks, Jejeman.

I use a USB card too (Alesis iO2 or Samson G-Track) and the performance improves a little bit, but I still have xruns at 256/

Here's the output of cat /proc/interrupts, without the USB card:

```


           CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       CPU6       CPU7       
  0:         71          0          0          0          0          0          0          0   IO-APIC-edge      timer
  1:         69          0          0          2          2          6          0          1   IO-APIC-edge      i8042
  8:          0          0          0          0          0          1          0          0   IO-APIC-edge      rtc0
  9:          0          1          0          0          0          0          0          0   IO-APIC-fasteoi   acpi
 12:      18677        269        210        507        168        561        158        541   IO-APIC-edge      i8042
 16:        157         14          5         43         16         14         24          4   IO-APIC-fasteoi   ehci_hcd:usb1, nouveau
 17:         77         21         20        468          9         28          3         11   IO-APIC-fasteoi   rtlwifi
 23:         16          3          0          0          0          1         10          3   IO-APIC-fasteoi   ehci_hcd:usb2
 41:          0          0          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 42:         11          5          1         12          0          1          1          2   PCI-MSI-edge      rtsx_pci
 43:       2523        596        259       2972       1529        307        359        855   PCI-MSI-edge      ahci
 44:          4          9          0          0          1          1          0          0   PCI-MSI-edge      mei
 45:          3          2          2          1          1          2          0          2   PCI-MSI-edge      i915
 46:         71        243         40         35         38         64          3         18   PCI-MSI-edge      snd_hda_intel
 47:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0
 48:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-TR-0
 49:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-TR-1
 50:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-TR-2
 51:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-TR-3
 52:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-R-4
 53:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-R-5
 54:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-R-6
 55:          0          0          0          0          0          0          0          0   PCI-MSI-edge      eth0-R-7
NMI:          3          1          4          1          5          1          5          1   Non-maskable interrupts
LOC:       5453       2859       6365       3318       8468       2853       6639       2846   Local timer interrupts
SPU:          0          0          0          0          0          0          0          0   Spurious interrupts
PMI:          3          1          4          1          5          1          5          1   Performance monitoring interrupts
IWI:          0          0          0          0          0          0          0          0   IRQ work interrupts
RTR:          7          0          0          0          0          0          0          0   APIC ICR read retries
RES:       3603       1050        379       1126        585        199        291        257   Rescheduling interrupts
CAL:        691        637        677        700        681        669        659        701   Function call interrupts
TLB:        160        240        163        305        149        237        123        236   TLB shootdowns
TRM:          0          0          0          0          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0          0          0          0          0   Machine check exceptions
MCP:          2          2          2          2          2          2          2          2   Machine check polls
ERR:          0
MIS:          0



```

---

### Post by jejeman on 2013-04-20
USB1 bus is sharing with VGA. Try the USB2 bus.

---

### Post by darwincommarts on 2013-04-20
Thanks, Jejeman.

By USB2, I take it you mean that the sound card should use the USB 2 bus? If so, I checked with lsusb and it looks like the card is on USB 2.

```


Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 003: ID 08bb:2904 Texas Instruments PCM2904 Audio Codec
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0930:021d Toshiba Corp. 
Bus 001 Device 004: ID 064e:d283 Suyin Corp. 
Bus 001 Device 005: ID 1164:1ee9 YUAN High-Tech Development Co., Ltd 


```

Cheers

---

### Post by darwincommarts on 2013-04-21
It was the wifi. Takin a cue from you, I saw that rtlwifi shares with usb1 and usb2. i turned off wifi (and networking altogether), and no more xruns, even at 64 frames. thanks, Jejeman!

---

### Post by jejeman on 2013-04-21
Yes, on laptops it is always good to turn off wifi. It is the same for my laptop too.

---

