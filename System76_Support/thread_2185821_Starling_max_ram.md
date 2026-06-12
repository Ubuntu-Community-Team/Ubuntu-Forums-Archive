---
title: "Starling max ram?"
date: 2013-11-04
forum: System76 Support
---

### Post by Carleas on 2013-11-04
I have a Starling (the sticker on the bottom calls it a Bonobo Performance Bonp4; model # M1110Q) that currently has 2 GB of ram.  Another computer of mine recently stopped working, and I'm looking to canabalize parts.  This other computer had 16gb of ram, 2 8gb sticks.  Will these work in my Starling?  I know I have at least 1 empty slot, but if I could use both sticks that would be rad.  Might that work?

---

### Post by isantop on 2013-11-07
The maximum RAM that the Starling's motherboard will support is 2 GB.

---

### Post by Carleas on 2013-11-08
Thanks for your response, not what I was hoping for, but good to know.  I have a followup question:  When I run  "dmidecode -q | less", I get two listings for "Memory Device:

> Memory Device
        Total Width: 72 bits
        Data Width: 64 bits
        Size: 2048 MB
        Form Factor: SODIMM
        Set: 1
        Locator: J6G1
        Bank Locator: DIMM 0
        Type: DDR3
        Type Detail: Synchronous
        Speed: 667 MHz
        Manufacturer: 48spaces                                        
        Serial Number: 01234567
        Asset Tag: 01234567
        Part Number: 012345678901234567890123456789012345
        Rank: Unknown

Memory Device
        Total Width: Unknown
        Data Width: Unknown
        Size: No Module Installed
        Form Factor: SODIMM
        Set: 1
        Locator: J6G2
        Bank Locator: DIMM 1
        Type: DDR3
        Type Detail: Synchronous
        Speed: 667 MHz
        Manufacturer: 48spaces                                        
        Serial Number: 01234567
        Asset Tag: 01234567
        Part Number: 012345678901234567890123456789012345
        Rank: Unknown
What's the second one that says "no module installed"?  I poked around inside and didn't see any open slots.

---

### Post by isantop on 2013-11-08
The chipset has firmware to handle another slot (which is what you're seeing here), but the slot isn't physically present.

---

