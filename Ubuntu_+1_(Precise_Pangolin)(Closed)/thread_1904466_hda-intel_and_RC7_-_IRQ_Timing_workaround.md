---
title: "hda-intel and RC7 - IRQ Timing workaround"
date: 2012-01-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2012-01-04
```

$ cat /var/log/syslog | grep hda-intel
Jan  4 21:49:24 localhost, kernel: [773271.958001] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
$ cat /proc/asound/cards
  0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf9ef4000 irq 16
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe67c000 irq 19

```This is ALC892 at #0 and NVidia GTS450 at #1, running the latest dkms. 
I don't get this one using previous RCs. Anyone else seeing some interesting / new / similar hda-intel messages with RC7?

I can't find a specific symptom, despite the message.

---

### Post by xyzzyman on 2012-01-04
Can you post the output of cat /proc/interrupts. Maybe something is now sharing the same IRQ when you use the RC7 kernel, and causing the hda-intel driver to use the fail-safe timing workaround.

---

### Post by effenberg0x0 on 2012-01-04
```
$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       CPU4       CPU5       
  0:        410       3330       1574       6283     121857  226439983   IO-APIC-edge      timer
  1:      14665          0          0          0          0         45   IO-APIC-edge      i8042
  4:          0          0          0          0          0          4   IO-APIC-edge    
  7:          1          0          0          0          0          0   IO-APIC-edge    
  8:          0          0          0          0          0          1   IO-APIC-edge      rtc0
  9:          0          0          0          0          0          2   IO-APIC-fasteoi   acpi
 16:          0    5539915          0          0          7        718   IO-APIC-fasteoi   snd_hda_intel
 17:     152898          0          0          0          1        257   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3
 18:          9   19809169          0          0          2         56   IO-APIC-fasteoi   ahci, ohci_hcd:usb4, ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7, nvidia
 19:    2469945          0          0          0          1        976   IO-APIC-fasteoi   pata_jmicron, snd_hda_intel, nvidia
 21:          0          0          0          0          0          0   IO-APIC-fasteoi   sata_sil
 40:          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
 41:          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
 42:          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
 43:          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
 44:          0          0          0          0          0          0   PCI-MSI-edge      PCIe PME
 45:   88364124          1          0          1         45      11885   PCI-MSI-edge      ahci
 46:          0          0          0          0          0          1   PCI-MSI-edge      xhci_hcd
 47:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 48:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 49:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 50:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 51:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 52:          0          0          0          0          0          0   PCI-MSI-edge      xhci_hcd
 53:   42483731          0          0          0          3        347   PCI-MSI-edge      eth0
NMI:        986        807        481        458        451        924   Non-maskable interrupts
LOC:   46763022   39708788   42292486   42427402   42767099    2095827   Local timer interrupts
SPU:          0          0          0          0          0          0   Spurious interrupts
PMI:        986        807        481        458        451        924   Performance monitoring interrupts
IWI:          0          0          0          0          0          0   IRQ work interrupts
RES:   16750196   23082953   18301230   18084231   17704550   17014867   Rescheduling interrupts
CAL:   21495364    6032248   21112401   21628100   21638985   21801383   Function call interrupts
TLB:     442305     417149     480866     410807     374257     443637   TLB shootdowns
TRM:          0          0          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0          0          0   Machine check exceptions
MCP:       2614       2614       2614       2614       2614       2614   Machine check polls
ERR:          1
MIS:          0

```

---

### Post by xyzzyman on 2012-01-04
It sounds like you have non-RC7 kernels still installed. Maybe you can run that same command under one of those? Your media reader might not be sharing the same IRQ under those. Usually people wind up with random audio stalls, etc when they get that error. If you're not having a problem then idk, but there is an hda-intel switch to use if it becomes an issue.

---

### Post by effenberg0x0 on 2012-01-04
I did a little reading on it... it looks like an open bug since 2008, with many duplicates (triaged / not-triaged). Triagers keep pushing it back and forth between pulseaudio and kernel (clocksource, the "increasing delta" / hpet old friend). Amazing proposed solutions include disabling audio.

I won't report it or investigate it any further, it's useless.

Thanks guys.

---

### Post by xyzzyman on 2012-01-04
If you do wind up having any issues try adding

options snd-hda-intel enable_msi=1

to /etc/modprobe.d/alsa-base.conf.

3.2 is released now so no more RC's. :)

---

