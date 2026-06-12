---
title: "Manually assigning IRQ"
date: 2009-03-09
forum: Ubuntu Studio
---

### Post by kiwidoc66 on 2009-03-09
Hi
I am running ubuntustudio 8.10 on a Dell Inspiron 8200 laptop. I would like to give the external soundcard (on usb) greater priority. Is there any way of forcing the usb to, say IRQ 3 or 4?

david@david-laptop:~$ cat /proc/interrupts
CPU0
0: 101298 XT-PIC-XT timer
1: 43 XT-PIC-XT i8042
2: 0 XT-PIC-XT cascade
3: 3 XT-PIC-XT
4: 4 XT-PIC-XT
5: 847 XT-PIC-XT Intel 82801CA-ICH3
6: 5 XT-PIC-XT floppy
7: 4 XT-PIC-XT parport0
8: 3 XT-PIC-XT rtc
9: 0 XT-PIC-XT acpi
10: 3 XT-PIC-XT
11: 5135 XT-PIC-XT uhci_hcd:usb1, uhci_hcd:usb2, ohci1394, yenta, yenta, eth0, nvidia
12: 1 XT-PIC-XT i8042
14: 9650 XT-PIC-XT libata
15: 0 XT-PIC-XT libata
NMI: 0 Non-maskable interrupts
LOC: 0 Local timer interrupts
RES: 0 Rescheduling interrupts
CAL: 0 function call interrupts
TLB: 0 TLB shootdowns
TRM: 0 Thermal event interrupts
SPU: 0 Spurious interrupts
ERR: 0
MIS: 0
david@david-laptop:~$

---

### Post by clubsoda on 2009-03-31
Best to let the kernel worry about IRQs, I think.  Maybe you can achieve the desired result by having the ALSA default device updated automatically.  This may help:-
[http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto)](http://alsa.opensrc.org/index.php/Hotplugging_USB_audio_devices_(Howto))

---

### Post by markbuntu on 2009-04-02
DO you just want to make it the default or are you having other issues?

---

