---
title: "jack stutters/xruns when using onboard alsa/ALC887 but not with external USB sound"
date: 2012-11-13
forum: Ubuntu Studio
---

### Post by ubnewbie2 on 2012-11-13
I have a Gigabyte GA-MA74GMT-S2 motherboard with onboard ALC887 sound.  When I select the analog ALC887 as jack's interface, the sound stutters every couple of seconds and there are plenty of xruns, no matter how large I set the frames/period or periods/buffer.  When I set jack to use my external USB Yamaha Audiogram6, it works fine.  If I set the system up to use Pulseaudio instead of jack, then sound works fine with the ALC887.

My processor is an AMD phenom x4 945, and I have 8GB ram. Video card is Geforce GTX550 Ti.  I am wondering how to make the onboard sound work properly (for when I don't have the Yamaha plugged in).

Any suggestions? Could this be a hardware conflict or something?  I really need to use jack as I need some of the filters etc that I can run in jackrack.

---

### Post by bumBumBUM on 2012-11-13
perhaps your sound card is working ok with pulseaudio but it can't keep up with jack in realtime mode.

You can first try running jack without realtime enabled to see if that works a bit better.

also put... ```
cat /proc/interrupts
```... into a terminal and post the output here. This command will reveal if there are any irq conflicts. 

As an example for you: my wireless card shares an irq with my onboard sound card and whilst both work fine together with pulseaudio, they don't work so well with the lower latencies set in jack. However, If I disable my wireless card then I can get decent latencies with my onboard sound card.

this is what I get from my interrupts file:

```
cat /proc/interrupts
           CPU0       CPU1       
  0:        149          0   IO-APIC-edge      timer
  1:         20        772   IO-APIC-edge      i8042
  7:          1          0   IO-APIC-edge    
  8:          0          1   IO-APIC-edge      rtc0
  9:          9       2456   IO-APIC-fasteoi   acpi
 12:       3453     362444   IO-APIC-edge      i8042
 16:     465672        849   IO-APIC-fasteoi   eth1, snd_hda_intel
 17:          5         96   IO-APIC-fasteoi   ehci_hcd:usb1, ehci_hcd:usb2, ehci_hcd:usb3
 18:          3        104   IO-APIC-fasteoi   ohci_hcd:usb4, ohci_hcd:usb5, ohci_hcd:usb6
 19:         25      15008   IO-APIC-fasteoi   ahci
 23:          0          0   IO-APIC-edge      lis3lv02d
 40:          0          0   PCI-MSI-edge      pciehp
 41:          0          0   PCI-MSI-edge      eth0
 42:       1762     367001   PCI-MSI-edge      radeon
 43:          0         59   PCI-MSI-edge      snd_hda_intel
NMI:         84         91   Non-maskable interrupts
LOC:    1027219    1001529   Local timer interrupts
SPU:          0          0   Spurious interrupts
PMI:         84         91   Performance monitoring interrupts
IWI:          0          0   IRQ work interrupts
RTR:          0          0   APIC ICR read retries
RES:     973038     862564   Rescheduling interrupts
CAL:        417        308   Function call interrupts
TLB:      12578      10551   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          6          6   Machine check polls
ERR:          1
MIS:          0

```from this you can see that eth1 (my wireless card) shares IRQ 16 with snd_hda_intel (my onboard soundcard).

hope that helps

---

### Post by ubnewbie2 on 2012-11-14
Turning off realtime seems to make no difference.  My soundcard seems to show up twice.  Is that because of analog and digital?  Anyway, it shares with various USBs.   Is there a way to change it.  I am not sure how to identify which USBs are which, nor how to disable them.



```
$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:         91          0         33          0   IO-APIC-edge      timer
  1:       7112        884         29          0   IO-APIC-edge      i8042
  6:          0          0          3          0   IO-APIC-edge      floppy
  7:          1          0          0          0   IO-APIC-edge    
  8:          0          0          1          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 14:      44363          0       9611          1   IO-APIC-edge      pata_atiixp
 15:          0          0          0          0   IO-APIC-edge      pata_atiixp
 16:      30455          0        770          4   IO-APIC-fasteoi   ohci_hcd:usb3, ohci_hcd:usb4, snd_hda_intel
 17:      31759          0       1238          0   IO-APIC-fasteoi   ehci_hcd:usb1
 18:    2937428       1135        219          1   IO-APIC-fasteoi   ohci_hcd:usb5, ohci_hcd:usb6, ohci_hcd:usb7, nvidia
 19:          5          0        227          0   IO-APIC-fasteoi   ehci_hcd:usb2, snd_hda_intel
 22:     313032          2      22872         14   IO-APIC-fasteoi   ahci
 42:     944097          0        104          0   PCI-MSI-edge      eth2
NMI:         65         62         59         58   Non-maskable interrupts
LOC:    3052515    2985365    3401809    3117324   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:         65         62         59         58   Performance monitoring interrupts
IWI:          0          0          0          0   IRQ work interrupts
RES:    4157903    4478977    4229452    4255661   Rescheduling interrupts
CAL:       6232       7823       6951       7709   Function call interrupts
TLB:     108948     127699     133712     134177   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:         84         83         83         83   Machine check polls
ERR:          1
MIS:          0

```

---

### Post by ubnewbie2 on 2012-11-14
Well I figured out why I have 2 soundcards. One is the one I am trying to use, the other is the Geforce video card's HDMI.  So it'd the IRQ16 one that I need to changes as it's sharing with USB3 and USB4

```
  *-multimedia            
       description: Audio device
       product: GF116 High Definition Audio Controller
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:19 memory:fbffc000-fbffffff
  *-multimedia
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:16 memory:fe024000-fe027fff

```

---

### Post by ubnewbie2 on 2012-11-14
I think the interrupt sharing was a red herring.   I just found, I hope, a solution.

I added the line
```
options snd-hda-intel model=generic
```
to /etc/modprobe.d/alsa-base.conf


I don't know what the side effects of doing this might be, but for now, it seems to be playing properly with jack.  I guess this implies it was an alsa/driver issue?

---

### Post by bumBumBUM on 2012-11-14
> **ubnewbie2 said:**
> I think the interrupt sharing was a red herring

It would appear so. Specifically since:

> Turning off realtime seems to make no differenceAt least you now know that some of your usb ports share interrupts with your soundcard though which may be useful information to know for the future.

>   I am not sure how to identify which USBs are which, nor how to disable them. With usb devices attached putting...

```
lsusb
```... into the terminal should let you figure out what's what by comparing the output to your interrupts file. You can disable stuff in BIOS usually or by blacklisting modules in linux but for the usb ports it might be enough to just avoid using them when jack is running in realtime.

> I don't know what the side effects of doing this might be, but for now,  it seems to be playing properly with jack.  I guess this implies it was  an alsa/driver issue? I don't know either but I'm sure you'll soon be able to tell whether or not there are any ill effects. I took a look at this page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which would suggest that there shouldn't be any problems if your module option corresponds adequately with your card... It seems to be more of a case of pointing the module in the right direction more than anything.

I also have HDMI sound and it is annoyingly picked as the default sound device in most linux distros. When using jack you can specify exactly which sound card to be used in qjactl - I assume that you were doing this and not inadvertantly selecting the HDMI sound device for jack? If the HDMI is the defaul HW 0,0 then your actual soundcard might be HW 1,0.

I would have thought that there would be more of a conflict caused by the HDMI sound rather than driver/module but I don't honestly know. Either way, your solution is interesting so thanks for sharing .

glad it worked out


PS. Also looking at the output message from qjackctl and posting it here would have been a good way of debugging your problem ('messages' button).

---

### Post by ubnewbie2 on 2012-11-15
> **bumBumBUM said:**
> 

I don't know either but I'm sure you'll soon be able to tell whether or not there are any ill effects. I took a look at this page:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which would suggest that there shouldn't be any problems if your module option corresponds adequately with your card... It seems to be more of a case of pointing the module in the right direction more than anything.



Well I have discovered that the 'generic' setting leaves me with nothing in the mixer to control input levels (line vs microphone) or hardly anything.  All the alsamixer has is Headphones, PCM, front, capture and digital. Very basic.

The problem with finding an option that works is that the HD-Audio-Models file does not list the Realtek 887, and any other option I guess at - such as 3stack, 6stack, even basic, results in the stuttering.  Still trying, but nothing seems obvious.

---

### Post by ubnewbie2 on 2012-11-15
Well, after an hour of rebooting and testing, I have found one which works, and has the mixer in a semi-useable state. Some controls don't make sense, but the majority seem to sort of work. The model is actually for an ALC882/883/885/888/889  (they left out 887?)

The one I am now using is
```
options snd-hda-intel model=3stack-6ch-intel
```

One drawback is that Audacity (connected to jack) can't seem to find an input level control to use (I have to set recording levels in the Alsamixer)

What's the story with all these models, are they something that can be configured/corrected by users?

---

