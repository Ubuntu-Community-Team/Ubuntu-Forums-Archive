---
title: "Gazelle Value Support: keyboard, memory"
date: 2008-02-11
forum: System76 Support
---

### Post by ldoolitt on 2008-02-11
Happy owner of a Gazelle Value (not sure of the version).

I recently put a fresh install (dual boot) of Gutsy Gibbon and Debian Etch, everything works great out-of-the box.  I have not installed System76 "drivers".  Debian still has some issues with suspend-to-RAM, but I know it can work.

I got some dirt in my keyboard, and then I scared myself by having the NumLk on without noticing it -- I thought my keyboard was hosed, trying to type the alphabet resulted in abcdefgh51230n6*qrst4vwxyz.  Anyway, I finally found the magic Google phrase, and got the SW1 hardware manual, with instructions for keyboard removal: [http://www.asimobile.com/notebook_files/sw1/guides/sw1_disassembly.pdf](http://www.asimobile.com/notebook_files/sw1/guides/sw1_disassembly.pdf) I got a lot of dust and hair out of the machine that way.

I start to lust after more RAM.  I don't see any for sale on the System76 site, but that's OK, I live close to a Fry's.  Without opening up the case, I thought I could check to see what speed SO-DIMM is in the machine now.  So I fired up sensors-config.  I poked at its results for a while, but never found any readout of the RAM.  Don't those modules have an ID ROM on them?

There was one I2C interface chip recognized, but for which lm-sensors (even the 3.0.1 development version) has no driver: a `Nat. Semi. PC87591 Super IO'.  Do y'all have an lm-sensors driver for this chip tucked away somewhere?  Are there any I2C devices attached to it?  Like the RAM, perhaps?

Keep up the good work!

   - Larry

---

### Post by thomasaaron on 2008-02-11
The SW1 could take a maximum of 2GB of 400, 533, 0r 667 MHz DDR2 RAM.
Unfortunately, I can't look up which speed was used on your computer.

You'll need to pull the bottom off and have a lookie-see.

---

### Post by ldoolitt on 2008-02-18
> You'll need to pull the bottom off and have a lookie-see.

It would have saved me some time if your answer were more constructive. It's not enough to pull the bottom off.  I also had to remove the RAM from its socket to see the side with the label, and even then most of the informative label is covered up with another sticker -- I can just barely make out the "5300" suffix that tells me the speed.

On the other hand, there is a nice program "decode-dimms" that is part of the the lm-sensors project, that tells me exactly what I want to know without removing any covers.  Unfortunately, the version of lm-sensors in Gutsy (2.10.4) is too old to include decode-dimms, and even the newest (3.0.1) release doesn't handle DDR2 modules correctly.  The latest trac copy works fine:
 [http://www.lm-sensors.org/browser/i2c-tools/trunk/eeprom/decode-dimms.pl?format=raw](http://www.lm-sensors.org/browser/i2c-tools/trunk/eeprom/decode-dimms.pl?format=raw)

In the Gazelle Value, the SO-DIMM eeprom is electrically behind the Intel 82801 interface chip.  So once decode-dimms is installed, do:

sudo modprobe i2c-i801 eeprom
decode-dimms

The results of which are:

```

Memory Serial Presence Detect Decoder
By Philip Edelbrock, Christian Zuckschwerdt, Burkart Lingner,
Jean Delvare and others


Decoding EEPROM: /sys/bus/i2c/drivers/eeprom/0-0050
Guessing DIMM is in                             bank 1

---=== SPD EEPROM Information ===---
EEPROM Checksum of bytes 0-62                   OK (0xDF)
# of bytes written to SDRAM EEPROM              128
Total number of bytes in EEPROM                 256
Fundamental Memory type                         DDR2 SDRAM
SPD Revision                                    1.2

---=== Memory Characteristics ===---
Maximum module speed                            666MHz (PC2-5300)
Size                                            512 MB
tCL-tRCD-tRP-tRAS                               5-5-5-15
Supported CAS Latencies                         5, 4, 3
Minimum Cycle Time (CAS 5)                      3 ns
Maximum Access Time (CAS 5)                     0.45 ns
Minimum Cycle Time (CAS 4)                      3.75 ns
Maximum Access Time (CAS 4)                     0.5 ns
Minimum Cycle Time (CAS 3)                      5 ns
Maximum Access Time (CAS 3)                     0.6 ns

---=== Manufacturing Information ===---
Manufacturer                                    Undefined
Part Number                                     NS5108E32-667P000
Manufacturing Date                              2006-W40
Assembly Serial Number                          0xEC170611

Number of SDRAM DIMMs detected and decoded: 1

```

P.S. I find this forum editor distinctly un-friendly.  Speaking as someone who has used Linux (and vi) pretty much exclusively since 1993, this is precisely the kind of too-helpful mouse-intensive interface I tried to avoid when I ditched Microsoft.

---

### Post by thomasaaron on 2008-02-18
Sorry my answer wasn't constructive enough. I shall endeavor to make my next answer a masterpiece! :guitar:

---

