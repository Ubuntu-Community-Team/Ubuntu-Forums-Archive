---
title: "Wonky MIDI - USB devices drawing too much power?"
date: 2017-04-08
forum: Ubuntu Studio
---

### Post by marseille2 on 2017-04-08
Hey all... I've been having MIDI connection problems and thought my keyboard was on the blink. But it's probably not true, and seems more like my USB devices are drawing too much power and causing wonky behavior. For instance, when I have my audio interface (USB 3.0), keyboard (class compliant), and an external CD ROM (class compliant) plugged in ... something always goes wrong (MIDI blinks out or CD drive can't read). 

But I just figured out that if I use a two-prong USB cord (in hopes of doubling power?) ... my cd drive starts working again. I only have one cords like this, and don't have an extra power pack for the keyboard (need to buy) ... and probably have to cut out extra MIDI controllers (I like using 3 but cut off 2 due to this issue). 

BTW ... My mobo has USB 2.0 and 3.0 ports and I guess they work fine. So my question is ... what can I do need to do to stop the MIDI from blinking out on me? Do I need a stronger computer power supply; or do I need to get separate power supplies for the midi devices (where I can ... at least one controller is USB only)... or is there a bigger problem?

```


$ lsusb

Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 03f0:5e07 Hewlett-Packard 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1235:0032 Focusrite-Novation 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0b05:17cb ASUSTek Computer, Inc. Broadcom BCM20702A0 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 1235:8202 Focusrite-Novation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

```

$ amidi -l

Dir Device    Name
IO  hw:1,0    Virtual Raw MIDI (16 subdevices)
IO  hw:1,1    Virtual Raw MIDI (16 subdevices)
IO  hw:1,2    Virtual Raw MIDI (16 subdevices)
IO  hw:1,3    Virtual Raw MIDI (16 subdevices)
IO  hw:4,0,0  Launchkey 61 MIDI 1
IO  hw:4,0,1  Launchkey 61 MIDI 2



```

---

### Post by Autodave on 2017-04-11
Since no one else has popped in here, let me try. The power supply could definitely be your problem: especially if it is the original one and/or getting old.  That said, getting some stuff onto their own power supplies would be my next step. That external CD ROM should have its own power supply: that is drawing way too much current to have it rely on the USB to power it.

---

### Post by marseille2 on 2017-04-12
Thanks for answering! This is a real headache, so much appreciated. ... I guess I better start ordering parts then.

---

### Post by mte2 on 2017-04-14
I might help if you get a powered USB hub and plug any power hungry devices in to it, even if you have open ports on the motherboard. A good hub that is also designed for charging can deliver more amps.
This should reduce any communications issues on the USB device serial lines.
I have blown the USB on a motherboard and even a hub on a different machine due to a wonky bitcoin miner. I use cheap powered hubs now which seems to save the motherboard.
Mark

---

### Post by yoshii on 2017-07-29
I vaguely remember a website about pro audio saying, "Don't use compound USB hubs; just use a minimum of USB devices; USB is somewhat fussy and not as easy as it seems because of device polling, power consumption, network congestion, power idling, etc."

If your laptop computer doesn't have enough USB ports, you may want to use a desktop computer instead.  They usually have a lot more USB ports, and you can disable any hardware you don't need in the UEFI/BIOS settings more easily.

---

