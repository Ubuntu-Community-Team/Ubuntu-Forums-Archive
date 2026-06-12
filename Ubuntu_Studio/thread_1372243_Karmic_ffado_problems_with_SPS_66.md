---
title: "Karmic ffado problems with SPS 66"
date: 2010-01-04
forum: Ubuntu Studio
---

### Post by halalkebabhut on 2010-01-04
Hi,

I've been finding that jack intermittently shuts down when I'm connected to my Sonar SPS 66 (same as edirol FA-60). I'm on Karmic Studio recently updated from a Jaunty install.

I can't see any pattern to when the connection times out and its quite inconsistent when trying to get it restarted.

I often get this error message in qjack's message window 


 

[html]

01874834422: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
 [0m01880090421: [31mError (configrom.cpp)[ 148] initialize: Could not parse config rom of node 0 on port 0
 [0mfirewire ERR: Error creating FFADO streaming device
 cannot load driver module firewire
 no message buffer overruns
 cannot continue execution of the processing graph (Broken pipe)
[/html]
Weirdly if I leave it alone for a while I can connect again ?

I'm most confused could anyone help ?

---

### Post by halalkebabhut on 2010-01-04
this is another one I get after restarting the machine

   [html]
00511708192:  (ffado.cpp)[  92] ffado_streaming_init: libffado 1.999.43 built Sep 17 2009 20:03:51
 17:30:42.112 Server configuration saved to "/home/simonkatan/.jackdrc".
 17:30:42.114 Statistics reset.
 17:30:42.188 Client activated.
 17:30:42.189 JACK connection change.
 17:30:42.193 JACK connection graph change.
 firewire ERR: Could not start streaming threads: -1
 DRIVER NT: could not start driver
 cannot start driver
[/html]

---

### Post by AutoStatic on 2010-01-04
Hello halalkebabhut, could you post the outcome of **lspci | grep 1394** and **cat /proc/interrupts** ?
You do have the same issue (a configrom error) as in the thread in which I claimed you could have a different problem.

---

### Post by halalkebabhut on 2010-01-04
here's my lspci | grep 1394

[HTML]

1a:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01)[/HTML]

here's my cat /proc/interrupts 

 [HTML]0:        128          3   IO-APIC-edge      timer
  1:        154        155   IO-APIC-edge      i8042
  8:          0          1   IO-APIC-edge      rtc0
  9:       2197       2184   IO-APIC-fasteoi   acpi
 12:         60         46   IO-APIC-edge      i8042
 16:         49         44   IO-APIC-fasteoi   uhci_hcd:usb3, ohci1394, mmc0
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb8, eth1
 19:       5551       5484   IO-APIC-fasteoi   ehci_hcd:usb1, uhci_hcd:usb5, uhci_hcd:usb7
 21:       2117       2112   IO-APIC-fasteoi   uhci_hcd:usb4
 22:        774        798   IO-APIC-fasteoi   HDA Intel
 23:         11         14   IO-APIC-fasteoi   ehci_hcd:usb2, uhci_hcd:usb6
 30:       8328       8388   PCI-MSI-edge      ahci
 31:       1288       1279   PCI-MSI-edge      i915
 32:        284        307   PCI-MSI-edge      eth0
NMI:          0          0   Non-maskable interrupts
LOC:     719277     717892   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:       1849       2691   Rescheduling interrupts
CAL:       7203       5678   Function call interrupts
TLB:        316        413   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          3          3   Machine check polls
ERR:          0
MIS:          0
[/HTML]

many thanks

---

### Post by AutoStatic on 2010-01-04
I think it's your controller: [http://www.ffado.org/?q=node/251](http://www.ffado.org/?q=node/251)

> So far, in order of preference (best to worst) according to developers:
Texas Instruments, VIA, NEC, O2 Micro (all are OHCI controllers)

Do you have a desktop or a notebook? And could you post the contents of */home/simonkatan/.jackdrc* ?

---

### Post by halalkebabhut on 2010-01-04
Oh bother it's at the bottom end of the list ! 

I have a dell laptop - vostro 1520

I had a quick look into TI express bus controllers but apparently this is not the same as has having native TI firewire. I guess I bought the wrong laptop .. doh

Is there anything I can do with the settings ? (higher latency i guess though I'm not getting Xruns or suchlike)
For my current purposes higher latencies are tolerable but timeouts aren't. 

heres the .jackdrc

[html]/usr/bin/jackd -R -P60 -p128 -dfirewire -r48000 -p128 -n2[/html]


many thanks for your help

---

### Post by AutoStatic on 2010-01-04
Does it work with Windows? And unfortunately you can't replace an onboard Firewire controller, if your notebook has an ExpressCard slot you could try a Firewire ExpressCard with a better supported chipset/controller.
Your .jackdrc looks good. You could try tweaking your system a bit more with the help of rtirq: [http://ubuntuforums.org/showthread.php?t=1328175](http://ubuntuforums.org/showthread.php?t=1328175)
Also there's an USB port and a cardreader that shares an IRQ with the Firewire controller, are those in use? What does **lsusb** in a terminal say?

---

### Post by halalkebabhut on 2010-01-04
It doesn't really work with windows. Starts out fine but intermittently becomes very distorted. I don't use windows for sound at the moment though.

I note that the USB busses change every time you reboot so trying to avoid sharing ports requires an lsusb and if necessary change usb ports on every occasion.

The link was useful though and I've followed that advice. I'll see how it goes and post some news soon. If things don't improve I'll try a Firewire express card (any suggestions)

One last thing, is there a quick way of resetting the device once it has timed out. At the moment my workaround is unplug it and wait 5 minutes which seems to solve the problem but would be highly stressful on a gig.

---

### Post by AutoStatic on 2010-01-04
> **halalkebabhut said:**
> It doesn't really work with windows. Starts out fine but intermittently becomes very distorted.The I fear it's your Firewire controller almost for sure.

> **halalkebabhut said:**
> I note that the USB busses change every time you reboot so trying to avoid sharing ports requires an lsusb and if necessary change usb ports on every occasion.that's weird, didn't know that, I thought USB ports were statically linked to an IRQ. I could be wrong though :)

> **halalkebabhut said:**
> The link was useful though and I've followed that advice. I'll see how it goes and post some news soon. If things don't improve I'll try a Firewire express card (any suggestions)That would be great, if it works it saves you from investing in an ExpressCard. if you have to get one, make sure it has a Texas Instruments (TI) chipset. I read somewhere you can get them from about $25,-

> **halalkebabhut said:**
> One last thing, is there a quick way of resetting the device once it has timed out. At the moment my workaround is unplug it and wait 5 minutes which seems to solve the problem but would be highly stressful on a gig.Hmm, realized I forgot to ask something, does the Edirol come with an external power supply? And does your notebook have a 4-pin (small) or 6-pin (big) Firewire connection?
To answer your question, you could try a **sudo modprobe -r ohci1394**, that removes the Firewire driver/kernel module, and then reload it again with **sudo modprobe ohci1394**. Maybe that works, not sure though.

---

### Post by halalkebabhut on 2010-01-05
I found out about the USB ports here

[http://subversion.ffado.org/wiki/IrqPriorities](http://subversion.ffado.org/wiki/IrqPriorities)

My firewire interface has external mains supply and plugs from a large pin at interface side to small on my laptop

thanks for the great advice

---

### Post by AutoStatic on 2010-01-05
> **halalkebabhut said:**
> My firewire interface has external mains supply and plugs from a large pin at interface side to small on my laptopAnd you use the external power supply I reckon?

---

### Post by halalkebabhut on 2010-01-05
yes it doesn't work without it

been running this morning -it still times out ... usually after long periods of inactivity

 **sudo modprobe -r ohci1394 **returns 

FATAL: Module ohci1394 is in use.

---

### Post by AutoStatic on 2010-01-05
> **halalkebabhut said:**
>  **sudo modprobe -r ohci1394 **returns 

FATAL: Module ohci1394 is in use.Yes, that's right, then it's still in use by your soundcard. You could try switching the Edirol off and then unload the ohci1394 module. But there's probably a better way to quickly reset it I'm not yet aware of.

---

