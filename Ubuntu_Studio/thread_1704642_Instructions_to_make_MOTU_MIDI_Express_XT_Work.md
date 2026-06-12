---
title: "Instructions to make MOTU MIDI Express XT Work?"
date: 2011-03-10
forum: Ubuntu Studio
---

### Post by bbarton11 on 2011-03-10
Hi All,

I've installed Ubuntu Studio on my machine and I'm trying to get my MOTU MIDI Express XT to work.  I saw an entry for it on ALSA [http://alsa-project.org/main/index.php/Matrix:Module-mtpav](http://alsa-project.org/main/index.php/Matrix:Module-mtpav) but it looks completely foreign to me.  I don't even know if that's for my device - the instructions look like they're for a soundcard and my device is a MIDI I/O.

Please let me know if there's a way it will work in Ubuntu Studio.

Thanks,
Brian

---

### Post by Pablo_F on 2011-03-11
Hi Brian,

Please, give the terminal output of these informative commands:

lsusb
cat /proc/asound/cards
cat /proc/asound/modules
arecordmidi -l
aplaymidi -l

Cheers, Pablo

---

### Post by bbarton11 on 2011-03-11
Thanks for the info, Pablo.  It looks like those commands are providing info for the USB devices that are connected.  My device is actually connected via parallel port.  Is there a similar set of instructions for parallel?

Brian

> **Pablo_F said:**
> Hi Brian,

Please, give the terminal output of these informative commands:

lsusb
cat /proc/asound/cards
cat /proc/asound/modules
arecordmidi -l
aplaymidi -l

Cheers, Pablo

---

### Post by bbarton11 on 2011-03-12
*bump*

---

### Post by bbarton11 on 2011-03-16
Hi Pablo, here is the info you were asking about:

**lsusb**
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 019: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 004 Device 003: ID 413c:2011 Dell Computer Corp. Multimedia Pro Keyboard
Bus 004 Device 002: ID 0557:8021 ATEN International Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 005: ID 0763:0196 Midiman Oxygen 49
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

** cat1**
 0 [Audigy         ]: Audigy - SB Audigy 1 [SB0090]
                      SB Audigy 1 [SB0090] (rev.3, serial:0x511102) at 0xb800, irq 17
 1 [U49            ]: USB-Audio - USB Oxygen 49
                      M-Audio USB Oxygen 49 at usb-0000:00:1d.7-1.2, full speed

**cat2**
 0 snd_emu10k1
 1 snd_usb_audio

**arecordmidi**
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    SB Audigy 1 [SB0090]             Audigy MPU-401 (UART)
 16:32   SB Audigy 1 [SB0090]             Audigy MPU-401 #2
 20:0    USB Oxygen 49                    USB Oxygen 49 MIDI 1

**aplaymidi**
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    SB Audigy 1 [SB0090]             Audigy MPU-401 (UART)
 16:32   SB Audigy 1 [SB0090]             Audigy MPU-401 #2
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3
 20:0    USB Oxygen 49                    USB Oxygen 49 MIDI 1

Let me know if you need anything else.

Thanks!
Brian

---

### Post by sgx on 2011-03-18
This is a complex unit, If you need those features, you may find some are implemented in Ardour, various jackd compatible utilities, and
video related utilities. MOTU are not recognized as linux friendly.

For testing, I would get rid of all the other usb peripherals, and remove soundcards that have any midi chips or ports.

If you just need basic midi i/o, E-mu make a dandy 2x2 midi interface that shows up ready for duties.

Cheers

---

### Post by Pablo_F on 2011-03-20
Hi Brian

Yes I thought it was a USB device. Now, I have no idea... I made a google search (linux MOTU MIDI Express XT) and your device is mentioned in the linux audio user mailing list. 

Cheers, Pablo

---

### Post by sgx on 2011-03-20
If your unit was made for Mac, I found this:

"I spent quite a while trying to the the Midi Express XT to work with XP and it would not communicate with the computer. Finally, after searching for a long time on the net, found mention of a ROM upgrade required to have the unit work with PC. Purchased the ROM upgrade from motu and the unit works flawlessly. Get the ROM if you are having trouble."

and in general:

"Resolved! - Reset to factory defaults with the Panic button held in on boot, and then select User Mode, not Factory mode and it works! Woohoo! Thanks for the help!"


Also. the battery may need replacing.

The above are 'windows fixes' but still may help

Have you tested with both the serial/paralell and usb midi cables
connected at the same time? 

kaconnect is a nice midi port app, worth having around.

Cheers

---

