---
title: "Roland UA-25EX: Problems getting it working in JACK"
date: 2010-08-11
forum: Ubuntu Studio
---

### Post by brelic on 2010-08-11
I've read in so many places, including here, that the Roland UA-25EX just works out of the box with newer kernels.

I'm running Ubuntu 9.10 with kernel 2.6.31-rt.

Here's some output that might help...

FWIW, here's the jack output:

```


19:21:43.711 Startup script...
19:21:43.712 artsshell -q terminate
sh: artsshell: not found
19:21:44.115 Startup script terminated with exit status=32512.
19:21:44.115 JACK is starting...
19:21:44.115 /usr/bin/jackd -R -dalsa -dhw:1 -r48000 -p512 -n3
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:1|hw:1|512|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
19:21:44.146 JACK was started with PID=8229.
configuring for 48000Hz, period = 512 frames (10.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
19:21:44.486 JACK was stopped successfully.
19:21:44.486 Post-shutdown script...
19:21:44.486 killall jackd
jackd: no process found
19:21:44.900 Post-shutdown script terminated with exit status=256.
19:21:46.173 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

```

Here's the lsusb output:

```

vince@zeno:~$ lsusb
Bus 002 Device 003: ID 064e:c107 Suyin Corp. 
Bus 002 Device 004: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0582:00e6 Roland Corp. 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And here's the cat /proc/asound/cards output:


```

vince@zeno:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdb100000 irq 36
 1 [UA25EX         ]: USB-Audio - UA-25EX
                      EDIROL UA-25EX at usb-0000:00:1a.0-1.1, full speed

```

Here's aplay -l:

```

vince@zeno:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: UA25EX [UA-25EX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

These is the "groups" output:

```

vince@zeno:~$ groups
vince adm dialout cdrom audio plugdev lpadmin admin sambashare

```


Any obvious reason why it wouldn't work?

---

### Post by AutoStatic on 2010-08-12
Hello Vince,

```
DRIVER NT: could not start driver
cannot start driver
```

Didn't see this one before but this could indicate the following:
[LIST]
[*]Bad USB cable, so check your USB cable with which you connect the UA-25EX, it should be a USB2 cable.
[*]Crowded USB port, the Edirol is on port/bus 3 according to lsusb and it shares that port with another device (Suyin Corp.). You could try another port for the Edirol, port 2 seems to be free.
[*]A buggy USB controller and unfortunately I fear that that's the cause in your case. ID 8087:0020 is an Intel 5 or 3400 Series Chipset and those are buggy: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html)
[/LIST]

So could you post the output of lspci?

---

### Post by brelic on 2010-08-12
> **AutoStatic said:**
> Hello Vince,

```
DRIVER NT: could not start driver
cannot start driver
```

Didn't see this one before but this could indicate the following:
[LIST]
[*]Bad USB cable, so check your USB cable with which you connect the UA-25EX, it should be a USB2 cable.
[*]Crowded USB port, the Edirol is on port/bus 3 according to lsusb and it shares that port with another device (Suyin Corp.). You could try another port for the Edirol, port 2 seems to be free.
[*]A buggy USB controller and unfortunately I fear that that's the cause in your case. ID 8087:0020 is an Intel 5 or 3400 Series Chipset and those are buggy: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html)
[/LIST]

So could you post the output of lspci?

I will post the output as soon as I get home.

In the meantime, I really hope it's not a buggy USB controller... but from that link you posted, it seems as though it should still work, albeit with possible clicks and pops. Currently, I can't even get jack to recognize it.

---

### Post by AutoStatic on 2010-08-12
What kind of machine is it? If it's a desktop and it does have this buggy controller than you could consider buying a PCIe USB card.

---

### Post by brelic on 2010-08-12
> **AutoStatic said:**
> What kind of machine is it? If it's a desktop and it does have this buggy controller than you could consider buying a PCIe USB card.

It's an HP Pavillion dv7-3170 laptop. I do have a desktop for audio as well (though quite old in computer years) but was hoping this laptop could be a mobile solution when I go over to some friends' houses to record and jam.

Here's the output of lspci:

```
vince@zeno:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.7 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 8 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a28 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
```

So, if it's a buggy controller, does that mean I'm screwed as long as I have this laptop? It works fine in Windows, but it would be ideal if it would work in Linux too.

I've been using Linux near exclusively at home for about 10 years now... the only exception is gaming and audio. It's just extremely frustrating that if it's not the soundcard, it's the usb controller, or it's the firewire chipset, or it's the nvidia chipset, and on and on.

---

### Post by AutoStatic on 2010-08-13
> **brelic said:**
> Here's the output of lspci:Thanks, the HP has this dreaded USB controller, but maybe you could figure out which chipset revision it has. It's probably B2, hence your issues. No idea how to figure that out though.

> **brelic said:**
> So, if it's a buggy controller, does that mean I'm screwed as long as I have this laptop? It works fine in Windows, but it would be ideal if it would work in Linux too.If it works in Windows then it should in work in Linux too as this has got nothing to do with the OS but with the hardware. Did you also check your cabling and using a free USB port? And how did you test it in Windows?

More information on the Intel® 5 Series Chipset and Intel® 3400 Series Chipset: [http://www.intel.com/Assets/PDF/specupdate/322170.pdf](http://www.intel.com/Assets/PDF/specupdate/322170.pdf)

---

### Post by brelic on 2010-08-13
> **AutoStatic said:**
> Thanks, the HP has this dreaded USB controller, but maybe you could figure out which chipset revision it has. It's probably B2, hence your issues. No idea how to figure that out though.

If it works in Windows then it should in work in Linux too as this has got nothing to do with the OS but with the hardware. Did you also check your cabling and using a free USB port? And how did you test it in Windows?

The cabling must be fine as it works in Windows. And I have tried a different port, but this was before I knew that I should address the device explicitly as hw:UA25EX, so I will try again tonight.

In Windows, I have tried it out with Reaper, recording several audio tracks, using EZDrummer for drum tracks, and real time effects on guitar and bass with no audible latency. With the Roland/Cakewalk drivers for the device, I can get 10ms which is low enough to avoid audible delay. No clicks, no pops, everything seems to be working fine.

Thanks for the link to the PDF document. I will look it over and see if there is anything I can do.

---

### Post by Joan Quintana on 2010-09-06
Same problem here in my new laptop (everything was perfect in my old laptop with the same interface and cable).

I discovered:
*JACK starts as usual with only playback. So the problem is 'Only record' or 'duplex mode'
*aplay and arecord works as usual, so is a JACK issue.

I remember the message:
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver

Joan Quintana

---

### Post by AutoStatic on 2010-09-06
> **Joan Quintana said:**
> *aplay and arecord works as usual, so is a JACK issue.If you have the same USB controller then it's probably a hardware problem, not a JACK problem.

---

### Post by Joan Quintana on 2010-09-06
So it seems that I have this buggy chipset

$lspci
...
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
...
The problem was fixed in chip revision B3. My revision is 06? Is older or newer??

So, what can I do now? Try to have my money back? Is it possible to use a USB_2_ExpressCard converter?

Joan Q

---

### Post by AutoStatic on 2010-09-07
@Joan Quintana, Clemens Ladisch replied to your mail on the LAU mailinglist. And he's the authority when it comes to USB soundcards. Apparently things are a bit different than I thought. I have to test it out myself too, I have an Edirol UA-25 and the new multimedia machines at work have that USB controller too.

---

### Post by Joan Quintana on 2010-09-09
I tested the UA-25EX relating with this problems and I can say:

*JACK starts in with Edirol in normal mode (switch), duplex mode (JACK settings) and without mouse
*with the mouse plugged is not possible to connect JACK (same conditions). It means that the USB bus is not so fast??
*with the mouse plugged and advanced mode, I can connect JACK with 'only playback' JACK settings.
*I tweak the different options in JACK setupt and nothing to say that change things.

So, in resume, I can't start the UA25EX in normal mode and mouse. I disconnect the mouse, and I connect.

Of course, I have the UA25EX and the optical mouse in the same bus ($ lsusb). But all my USB physical entries are in the same bus (but I have another bus listed in lsusb). Is it possible to change that?

My last chance. I ordered a ExpressCard to USB 2.0, with two USB ports, they say Linux compatible. Can I have chances in this case? I hope.

Joan Q

---

### Post by Pablo_F on 2010-09-10
Hi Joan, 

A well configured rtirq script might help.

What is the output of 

cat /proc/interrupts

lsusb

with both the mouse and the card connected, and then without the mouse, lsusb again?

Cheers! Pablo

---

### Post by Joan Quintana on 2010-09-13
Here is my output.

Ubuntu Studio 10.04 Lucid Lynx
Processor: i5
RAM: 4GB

without Edirol UA25-EX plugged in

$ lsusb
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6406 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:        142          0          0          0   IO-APIC-edge      timer
  1:         86         30         77         24   IO-APIC-edge      i8042
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:        130        188        139        189   IO-APIC-fasteoi   acpi
 12:        498         39        482         34   IO-APIC-edge      i8042
 16:         19         20         18         17   IO-APIC-fasteoi   ehci_hcd:usb1, ohci1394
 17:        117         70        109         78   IO-APIC-fasteoi   mmc0, HDA Intel
 22:        532        147        528        156   IO-APIC-fasteoi   HDA Intel
 23:        118       1073        118       1111   IO-APIC-fasteoi   ehci_hcd:usb2
 24:          0          0          0          0  HPET_MSI-edge      hpet2
 25:          0          0          0          0  HPET_MSI-edge      hpet3
 26:          0          0          0          0  HPET_MSI-edge      hpet4
 27:          0          0          0          0  HPET_MSI-edge      hpet5
 35:        925       3033        932       3038   PCI-MSI-edge      ahci
 36:         14         19        315         18   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      26951      20996      21254      21757   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        331        371        331        437   Rescheduling interrupts
CAL:         99        106         92        121   Function call interrupts
TLB:        200        327        398        479   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          2          2          2          2   Machine check polls
ERR:          3
MIS:          0



Now I plug the USB interface: Edirol UA25EX

$ lsusb
Bus 002 Device 004: ID 0582:00e7 Roland Corp. 
Bus 002 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6406 Microdia 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ cat /proc/interrupts
           CPU0       CPU1       CPU2       CPU3       
  0:        142          0          0          0   IO-APIC-edge      timer
  1:        150         67        131         68   IO-APIC-edge      i8042
  8:          0          0          0          1   IO-APIC-edge      rtc0
  9:        194        285        204        290   IO-APIC-fasteoi   acpi
 12:       1033        255       1021        250   IO-APIC-edge      i8042
 16:         19         20         18         17   IO-APIC-fasteoi   ehci_hcd:usb1, ohci1394
 17:        117         70        109         78   IO-APIC-fasteoi   mmc0, HDA Intel
 22:        532        147        528        156   IO-APIC-fasteoi   HDA Intel
 23:        588       3097        567       3159   IO-APIC-fasteoi   ehci_hcd:usb2
 24:          1          0          0          0  HPET_MSI-edge      hpet2
 25:          0          0          0          0  HPET_MSI-edge      hpet3
 26:          0          0          0          0  HPET_MSI-edge      hpet4
 27:          0          0          0          0  HPET_MSI-edge      hpet5
 35:        925       4715        932       4752   PCI-MSI-edge      ahci
 36:         14         19        785         18   PCI-MSI-edge      eth0
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      40491      35835      30650      29723   Local timer interrupts
SPU:          0          0          0          0   Spurious interrupts
PMI:          0          0          0          0   Performance monitoring interrupts
PND:          0          0          0          0   Performance pending work
RES:        375        413        518        488   Rescheduling interrupts
CAL:        104        109         98        125   Function call interrupts
TLB:        212        374        430        558   TLB shootdowns
TRM:          0          0          0          0   Thermal event interrupts
THR:          0          0          0          0   Threshold APIC interrupts
MCE:          0          0          0          0   Machine check exceptions
MCP:          3          3          3          3   Machine check polls
ERR:          3
MIS:          0

I'm going to get documentation about rtirq and try to priorize my USB bus. As you can see, the mouse and the Edirol share the bus #2. But all my three physical USB ports seem to be attached to the usb #2 bus.

TIA,
Joan Quintana

---

### Post by AutoStatic on 2010-09-13
What does **ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq"** with the UA-25EX connected output?
I'm taking my UA-25 with me to work tomorrow. I'm upgrading our multimedia room and the new PC's also have this USB controller chipset.

---

### Post by Joan Quintana on 2010-09-13
$ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq" 
    4  TS      -  19   0 [ksoftirqd/0]
    7  TS      -  19   0 [ksoftirqd/1]
   10  TS      -  19   0 [ksoftirqd/2]
   13  TS      -  19   0 [ksoftirqd/3]
 1116  TS      -  19   0 /usr/sbin/irqbalance$ sudo nano /etc/default/rtirq
 1962  TS      -  19   0 grep --color=auto -i irq

$ cat /proc/interrupts | grep usb
 16:         17         16         19         18   IO-APIC-fasteoi   ehci_hcd:usb1, ohci1394
 23:       2264        261       2173        265   IO-APIC-fasteoi   ehci_hcd:usb2

To tweak my rtirq script I'm following this link
*[http://semicorchux.blogspot.com/2010/05/el-script-rtirq-en-ubuntustudio.html](http://semicorchux.blogspot.com/2010/05/el-script-rtirq-en-ubuntustudio.html) (sorry, Spanish)

It is supposed that I must increase the priority of the USB irqs (now 19) up to 80-90. But I edit rtirq and nothing happens:

$ sudo nano /etc/default/rtirq

#RTIRQ_NAME_LIST="rtc snd usb i8042"
RTIRQ_NAME_LIST="rtc usb snd i8042"


# Highest priority.
RTIRQ_PRIO_HIGH=90

# Priority decrease step.
RTIRQ_PRIO_DECR=5

$ sudo /etc/init.d/rtirq start

and nothing changes. Priority is still 19.

My system is a fresh Ubuntu Studio 10.04, but I tested before with Ubuntu 10.04 (preparation Ubuntu Studio)

Joan Q

---

### Post by AutoStatic on 2010-09-14
> **Joan Quintana said:**
> $ ps -eLo pid,cls,rtprio,pri,nice,cmd | grep -i "irq" 
    4  TS      -  19   0 [ksoftirqd/0]
    7  TS      -  19   0 [ksoftirqd/1]
   10  TS      -  19   0 [ksoftirqd/2]
   13  TS      -  19   0 [ksoftirqd/3]
 1116  TS      -  19   0 /usr/sbin/irqbalance$ sudo nano /etc/default/rtirq
 1962  TS      -  19   0 grep --color=auto -i irqYou're not running a realtime kernel so rtirq won't work. What does **uname -a** return?

---

### Post by Joan Quintana on 2010-09-14
Uau! that's true!
 
I'm using Ubuntu Studio 10.04, but my kernel is preempt:

uname -a
Linux joan 2.6.32-21-preempt #32-Ubuntu SMP PREEMPT Fri Apr 16 10:23:59 UTC 2010 x86_64 GNU/Linux

I'm using the 64 bits version. When I downloaded this version from Ubuntu Studio, I remember saying 'preempted' thinking that it was similar to rt.

I needed to choose the 64 bits version in order that my 4GB are recognized (Ubuntu 32 bits only see 2.9GB).

Joan Q

---

### Post by AutoStatic on 2010-09-14
The preempt kernel is indeed very similar but it lacks the [tasklet API]("http://subversion.ffado.org/wiki/IrqPriorities") that the real-time kernel provides.
I'm about to hook up my UA-25 to a PC with a 5 Series/3400 Series Chipset in it, let's see if it works or not.

---

### Post by AutoStatic on 2010-09-14
```
studio@audiopc:~$ lspci | grep USB2
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
```

```
studio@audiopc:~$ cat /proc/asound/cards && aplay -l
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf7ff8000 irq 22
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbdfc000 irq 16
 2 [UA25           ]: USB-Audio - UA-25
                      EDIROL UA-25 at usb-0000:00:1d.0-1.6, full speed
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: UA25 [UA-25], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

When I start JACK with Advanced mode on and a sample rate of 48Khz:```
studio@audiopc:~$ /usr/bin/jackd -v -P69 -t2000 -dalsa -dhw:UA25 -r48000 -p128 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6115326
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x9b9d00 fd = -1
apparent rate = 48000
creating alsa driver ... hw:UA25|hw:UA25|128|3|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
new buffer size 128
resizing port buffer segment for type 0, one buffer = 512 bytes
resizing port buffer segment for type 1, one buffer = 512 bytes
registered port system:capture_1, offset = 512
registered port system:capture_2, offset = 1024
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
-- jack_rechain_graph()
-- jack_sort_graph
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'
```
ALSA refuses to output to the card also:```
studio@audiopc:~$ aqualung -o alsa -d hw:UA25
alsa_init: unable to open 32 bit output, falling back to 16 bit...
alsa_init: unable to open 16 bit output, exiting.
```
And with Advanced mode off ALSA works:```
studio@audiopc:~$ aqualung -o alsa -d hw:UA25alsa_init: unable to open 32 bit output, falling back to 16 bit...
```
But JACK still refuses to work:```
studio@audiopc:~$ /usr/bin/jackd -v -P69 -t2000 -dalsa -dhw:UA25 -r44100 -p1024 -n2 -S
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6115326
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x22a6d00 fd = -1
apparent rate = 44100
creating alsa driver ... hw:UA25|hw:UA25|1024|2|44100|0|0|nomon|swmeter|-|16bit
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
new buffer size 1024
resizing port buffer segment for type 0, one buffer = 4096 bytes
resizing port buffer segment for type 1, one buffer = 4096 bytes
registered port system:capture_1, offset = 4096
registered port system:capture_2, offset = 8192
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
-- jack_rechain_graph()
-- jack_sort_graph
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver
server thread back from poll
unloading driver
freeing shared port segments
stopping server thread
stopping watchdog thread
last xrun delay: 0.000 usecs
max delay reported by backend: 0.000 usecs
freeing engine shared memory
max usecs: 0.000, engine deleted
cleaning up shared memory
cleaning up files
unregistering server `default'

```
But if I enable Advanced mode and only use the playback ports it does work:```
studio@audiopc:~$ /usr/bin/jackd -v -P69 -t2000 -dalsa -dhw:UA25 -r48000 -p64 -n3 -P
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    6115326
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
new client: alsa_pcm, id = 1 type 1 @ 0x769d00 fd = -1
apparent rate = 48000
creating alsa driver ... hw:UA25|-|64|3|48000|0|0|nomon|swmeter|-|32bit
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 3 periods
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
new buffer size 64
resizing port buffer segment for type 0, one buffer = 256 bytes
resizing port buffer segment for type 1, one buffer = 256 bytes
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
-- jack_rechain_graph()
-- jack_sort_graph
8197 waiting for signals
load = 0.1500 max usecs: 4.000, spare = 1329.000
load = 0.2251 max usecs: 4.000, spare = 1329.000
load = 0.2626 max usecs: 4.000, spare = 1329.000
load = 0.2813 max usecs: 4.000, spare = 1329.000
load = 0.2907 max usecs: 4.000, spare = 1329.000
load = 0.2954 max usecs: 4.000, spare = 1329.000
load = 0.2977 max usecs: 4.000, spare = 1329.000
server thread back from poll
new client: aqualung, id = 2 type 2 @ 0x7fdf59cda000 fd = 11
start poll on 4 fd's
server thread back from poll
new client aqualung using 12 for events
start poll on 4 fd's
server thread back from poll
registered port aqualung:out_L, offset = 256
start poll on 4 fd's
server thread back from poll
registered port aqualung:out_R, offset = 512
start poll on 4 fd's
server thread back from poll
```
So duplex doesn't work. When monitoring dmesg this is what I see when I execute **/usr/bin/jackd -v -P69 -t2000 -dalsa -dhw:UA25 -r48000 -p64 -n3**:
```
[ 6894.097634] usb 1-1.4: new full speed USB device using ehci_hcd and address 14
[ 6894.195761] usb 1-1.4: configuration #1 chosen from 1 choice
[ 6930.941407] cannot submit datapipe for urb 0, error -28: not enough bandwidth
```
So apparently there's not enough bandwidth to run the soundcard in duplex mode.

---

### Post by Joan Quintana on 2010-09-15
Thanks Jeremy for your help.
I'm following the thread in LAU, and the discussion has a high level that is difficult for me to contribute.

Just to say that I can work with Duplex mode with this stupid trick... as you know, I can start JACK in duplex mode without the mouse. Then, JACK started, if I plug the mouse nothing happens and I can work (!?).

I'm testing with JACK + fluidsynth + vkeybd, but I also recorded a track with Ardour. Because I have a nice cpu and RAM, I can work without XRUNs at all, indeed when I work in duplex mode with this trick.

So I'm wondering... why I don't have any XRUNs if this USB hasn't enough bandwith?

(all that I'm saying is with UA25EX in normal mode. No way to work with advanced mode and duplex)

thanks again,
Joan Q

---

### Post by yuhong on 2010-09-26
> **Joan Quintana said:**
> So it seems that I have this buggy chipset

$lspci
...
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
...
The problem was fixed in chip revision B3. My revision is 06? Is older or newer??

In generate, to translate, look at the spec update for the chipset in the Identification Information section. In this case, the spec update is here:
[http://www.intel.com/assets/pdf/specupdate/322170.pdf](http://www.intel.com/assets/pdf/specupdate/322170.pdf)
There is a table under this section which you can use to translate.

---

### Post by Svictor on 2011-02-18
Hello everyone,
I seem to have a similar problem on my Asus UL30JT. Lspci -vv says : 
```
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06) (prog-if 20 [EHCI])
    Subsystem: ASUSTeK Computer Inc. Device 1017
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 23
    Region 0: Memory at d7407000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

```I'm not sure how to read the "specification update" from Intel. They say that "B3 rev id" is 06h. So if I see 06 in the output of lspci, does it mean that i have the b3 model ? This would mean that my problem is not with the hardware controller (although the symptoms seem the same as those described in this thread) ...

@Joan : what is the thread in LAU you refer to ? The one [here]("http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html") ends on a rather pessimistic note. Did anyone find a workaround for the bugged controller ?

Thanks in advance for your help,
Victor

---

### Post by blablack on 2011-04-24
Hi all,

Facing the exact same problem with an HP Envy 17 and the Edirol UA25-EX...


```
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 144d
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d610a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
```

Did anyone ever found a solution?

---

### Post by raboofje on 2011-04-26
> **Joan Quintana said:**
> as you know, I can start JACK in duplex mode without the mouse. Then, JACK started, if I plug the mouse nothing happens and I can work (!?).

Strange... I guess the mouse reserves a certain amount of bandwidth even though it doesn't really need it or something?

I solved this problem by getting a cheap PCMCIA (or whatever it's called these days) USB card :(

---

### Post by blablack on 2011-05-10
Is this problem only raising if you plug a USB 1 soundcard (like the UA25) into a EHCI USB port, or even upgrading to a USB 2 Sound Card wouldn't fix it?

---

