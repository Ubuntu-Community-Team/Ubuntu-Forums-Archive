---
title: "edirol UA 25 - jack issue"
date: 2010-07-26
forum: Ubuntu Studio
---

### Post by boeszyslak on 2010-07-26
Hello
I'm trying to use my Edirol UA-25 soundcard with jack
If I turn the "Advanced mode" switch off it works.
If I set it to on (to use the midi in) the jackd server does not start.
it says
ALSA: could not start playback (Broken pipe)
 DRIVER NT: could not start driver
 cannot start driver


Can you help me?
Thanks. 

Michele.

---

### Post by AutoStatic on 2010-07-26
Hello Michele,

The error message indicates something is interfering with the UA-25.
Could you post the output of the terminal command **lsusb** ?
And what kind of USB cable are you using? You really need a decent USB2.0 cable for the UA-25 (even though it's a USB1 device).

---

### Post by boeszyslak on 2010-07-27
this is the output of lsusb

Bus 002 Device 007: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 002 Device 006: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by AutoStatic on 2010-07-27
> **boeszyslak said:**
> this is the output of lsusb

Bus 002 Device 007: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 002 Device 006: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubThanks! Two USB ports and everything is on port/bus 002. Could you try plugging the UA-25 into another USB port and try **lsusb** again? You need to get the UA-25 on port/bus 001.

---

### Post by boeszyslak on 2010-07-27
i moved the soundcard to another usb card.
this is the new output of lsusb

Bus 002 Device 006: ID 03f0:231d Hewlett-Packard 
Bus 002 Device 003: ID 0408:03f1 Quanta Computer, Inc. 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I

---

### Post by AutoStatic on 2010-07-27
Looks good! Bus/port 001 is completely free so the UA-25 should work now. I have an UA-25 also and best settings for me are:
[LIST]
[*]Frames/Period: 64 (but maybe try starting with 256)
[*]Sample Rate: 48000
[*]Periods/Buffer: 3
[/LIST]

---

### Post by boeszyslak on 2010-07-27
it still does not work...
this is the complete output of jack

jackd -v -r -dalsa -dhw:2 -r48000 -p64 -n3
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details


Memory locking is unlimited - this is dangerous. You should probably alter the line:
     @audio   -  memlock    unlimited
in your /etc/limits.conf to read:
     @audio   -  memlock    3038154
getting driver descriptor from /usr/lib/jack/jack_dummy.so
getting driver descriptor from /usr/lib/jack/jack_net.so
getting driver descriptor from /usr/lib/jack/jack_oss.so
getting driver descriptor from /usr/lib/jack/jack_firewire.so
no message buffer overruns
getting driver descriptor from /usr/lib/jack/jack_alsa.so
JACK compiled with System V SHM support.
server `default' registered
registered builtin port type 32 bit float mono audio
registered builtin port type 8 bit raw midi
clock source = system clock via clock_gettime
loading driver ..
start poll on 3 fd's
SSE2 detected
apparent rate = 48000
creating alsa driver ... hw:2|hw:2|64|3|48000|0|0|nomon|swmeter|-|32bit
control device hw:2
new client: alsa_pcm, id = 1 type 1 @ 0x17c40c0 fd = -1
configuring for 48000Hz, period = 64 frames (1.3 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 24bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 24bit little-endian
ALSA: use 3 periods for playback
new buffer size 64
registered port system:capture_1, offset = 256
registered port system:capture_2, offset = 512
registered port system:playback_1, offset = 0
registered port system:playback_2, offset = 0
++ jack_sort_graph
++ jack_rechain_graph():
+++ client is now alsa_pcm active ? 1
client alsa_pcm: internal client, execution_order=0.
-- jack_rechain_graph()
-- jack_sort_graph
ALSA: could not start playback (Broken pipe)
DRIVER NT: could not start driver
cannot start driver
starting server engine shutdown
stopping driver

---

### Post by AutoStatic on 2010-07-27
And what kind of USB cable are you using now? Advanced mode is on? Sample rate on the UA-25 itself is set to 48000 also? And maybe you could try *-dhw:UA25* instead of *-dhw:2*.

---

### Post by boeszyslak on 2010-07-27
Advanced mode is on (if i turn it off it works)
the sample rate on the soundcard is set to 48000
I tried 2 different usb cables, but it still does not work...

---

### Post by AutoStatic on 2010-07-27
Could you post the output of **lspci** ?

---

### Post by boeszyslak on 2010-07-27
lspci
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
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 230M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
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

---

### Post by AutoStatic on 2010-07-27
Thanks!

```
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
```

You have a buggy controller chipset, USB soundcards won't properly work with them: [http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html](http://lists.linuxaudio.org/pipermail/linux-audio-user/2010-June/070353.html)

---

### Post by boeszyslak on 2010-07-27
Damn , there isn't a workaround.
I have to use another pc.

Thanks for helping me.

---

### Post by AutoStatic on 2010-07-27
You're welcome. That buggy controller is a real bummer, but maybe you could get yourself a PCIe USB card? Those are fairly cheap and allow you to use the UA-25 nonetheless.

---

