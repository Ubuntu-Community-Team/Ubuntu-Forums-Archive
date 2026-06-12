---
title: "Fast track pro and jack in Duplex mode"
date: 2011-03-21
forum: Ubuntu Studio
---

### Post by tjajab on 2011-03-21
Hi,

first of all, thanks to all participating in this and other forums around, I been greatly helped already.

However, now I have trouble starting Jack with my Fast track pro card. I am using it on a normal Ubuntu 10.10 installation, and maybe that could be part of the problem, although I do not understand why.

I've tried just to put the interface to hw:Pro (or hw:1) but then I get playback only, so after searching in forums, I set Input Device to hw:1,1 and output device to hw:1 (which I guess would be the same as hw:Pro). I've got Frames/Period to 1024 and sample rate 44100, periods/buffer 3 and I've tried with or without "Force 16bit".

It works when I use another device as playback (Output Device: hw:2,0) or when I use Playback only or Capture only.

The output I get is:
```

17:35:23.528 JACK is starting...
17:35:23.528 /usr/bin/jackd -t5000 -dalsa -r44100 -p1024 -n3 -D -Chw:1,1 -Phw:1
17:35:23.539 JACK was started with PID=2472.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1,1|1024|3|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver USB-Audio running on card 1 - M-Audio FastTrack Pro at usb-0000:00:1a.0-1.1, full speed
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
ALSA: could not start playback (Broken pipe)
Cannot start driver
JackServer::Start() failed with -1
Released audio card Audio1
audio_reservation_finish
Failed to start server
17:35:23.717 JACK was stopped with exit status=255.

```

```
**** List of PLAYBACK Hardware Devices ****
aplay -l:
card 1: Pro [FastTrack Pro], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
arecord -l:
**** List of CAPTURE Hardware Devices ****
card 0: Q9000 [QuickCam Pro 9000], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Pro [FastTrack Pro], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Intel [HDA Intel], device 2: ALC889 Analog [ALC889 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

```

---

### Post by AutoStatic on 2011-03-21
Hello tjajab, could you post the outcome of **lsusb** and **lspci** ? The 'broken pipe' error is not a good sign though....

Best,

Jeremy

---

### Post by tjajab on 2011-03-21
Hi, thanks for your reply. Here it is:
```

lsusb:
Bus 002 Device 006: ID 0781:a7c1 SanDisk Corp. 
Bus 002 Device 005: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 003: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 003: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lspci:
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
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 5 Series/3400 Series Chipset 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GTS] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)

```

---

### Post by AutoStatic on 2011-03-21
> **tjajab said:**
> ```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
...
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
```Those two, especially the Rate Matching Hub, are probably causing your issues. Is this on a notebook or on a desktop PC?

Best,

Jeremy

---

### Post by tjajab on 2011-03-21
Hi again, and thanks for your help. It is a desktop PC, and I found your other posts on the topic. A bit unfortunate, I'm not into changing my motherboard at the moment :)

I actually got it running when I put all other stuff on the same bus (=hub?) and left the USB card alone on one bus, however, I just tested sound in - sound out, so I guess there could be some issues when using it more extensively.

Lucky for me, I will primarily use this card for recording OR playback, using the built in intel sound output while creating.

Thanks again for all your help - if you have more input on the issue it is very welcome.

Best regards,
Andreas

---

### Post by pinkwerther on 2011-04-05
no kidding? i should have thought about that before, but all the time i thought it was the hardware, today i got a behringer bcd3000 and duplex wouldn't work, so i tried another computer... and here i am.

so i have lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
43:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
44:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 06)
44:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 25)
44:06.2 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev bb)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```and lsusb:
```

Bus 002 Device 003: ID 1397:00bf BEHRINGER International GmbH 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b163 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 138a:0007 DigitalPersona, Inc 
Bus 001 Device 003: ID 03f0:231d Hewlett-Packard 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```in my fresh hp elitebook 2540p, i intended to use for audio production, live and recording a lot.
and as > jackd -d alsa -d -P hw:1 -C hw:1 -D says
```

jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:1
Using ALSA driver USB-Audio running on card 1 - Behringer BCD3000 at usb-0000:00:1d.0-1.2, full speed
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
ALSA: could not start playback (Broken pipe)
Cannot start driver
JackServer::Start() failed with -1
control device hw:1
Released audio card Audio1
audio_reservation_finish
control device hw:1
Failed to start server

```I strongly assume it will never work. Can anybody please tell me that I really can stop trying and it's the laptop that doesn't like me?

---

### Post by AutoStatic on 2011-04-06
> **pinkwerther said:**
> ]I strongly assume it will never work. Can anybody please tell me that I really can stop trying and it's the laptop that doesn't like me?You can stop trying, it is most probably the hardware that is the bottleneck :( Try getting a PCI ExpressCard USB2 card if you want your BCD3000 to work with your notebook.

Best,

Jeremy

---

### Post by tjajab on 2011-04-06
I have a stationary computer. Could it be that an USB3 card could work too? Those are much easier to find, and could be useful for other purposes as well.

Best,
Andreas

---

### Post by AutoStatic on 2011-04-06
Hello Andreas, no, USB3 cards won't work with USB sound cards. The XHCI audio driver doesn't function properly yet.

Best,

Jeremy

---

### Post by pinkwerther on 2011-04-08
> **AutoStatic said:**
> You can stop trying, it is most probably the hardware that is the bottleneck :( Try getting a PCI ExpressCard USB2 card if you want your BCD3000 to work with your notebook.


Thanks Jeremy. I have been thinking... Will it be comfortable with the expresscard then? Or will it be a mess, at least it'll be another device I need to carry around. So would it be better to get an expresscard, or to get rid of the laptop and get a macbook pro 13'?

What do you think?

lg,
pw

---

### Post by AutoStatic on 2011-04-08
[http://www.amazon.com/Best-Connectivity-SD-EXP20030-ExpressCard-Ports/dp/B003BYRO74](http://www.amazon.com/Best-Connectivity-SD-EXP20030-ExpressCard-Ports/dp/B003BYRO74)

vs

[http://store.apple.com/us/browse/home/shop_mac/family/macbook_pro?afid=p210](http://store.apple.com/us/browse/home/shop_mac/family/macbook_pro?afid=p210)

So $32 vs $1200,- ;)
I have no experience with USB2 ExpressCards but my bet is that it should work just fine.

Best,

Jeremy

---

### Post by pinkwerther on 2011-04-12
well, i got this laptop for music production mainly and it's very fresh, if the included usb doesn't do duplex, what's the point? so i'm thinking about getting a mac and sending the hp back, then i could also get

[http://www.friendlyhouse.at/geraete/dj-equipment/soundkarten--interfaces/fw/presonus-firestudio-mobile/PIDRklSRVNUVURJT01PQklMRQ==](http://www.friendlyhouse.at/geraete/dj-equipment/soundkarten--interfaces/fw/presonus-firestudio-mobile/PIDRklSRVNUVURJT01PQklMRQ==)

and don't worry about linux supporting or not, just double-boot. i mean macos is not that bad, anyway i'm surely not going to double-boot with windows... there doesn't seem to be a lot of support for the good interfaces, no blame on the community of course. but this interface would do exactly what i need, 2 mic/line combo + 6 line inputs, headphone and line out, compactness, price, anything like that available reported to work under linux?

---

