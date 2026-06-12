---
title: "Where's my MIDI Keyboard in Jack ?"
date: 2011-05-01
forum: Ubuntu Studio
---

### Post by aredcat66 on 2011-05-01
Hi All.
Recently I've upgraded my system with a new MB and a Multi core Processor(Phenom II Black Edition 4 Core) in the hope of reducing the frequency of xrun in Jack and improving audio performances. I've installed the last version of ubuntu studio but I've a big problem.
In the connect windows of the Jack Audio Connection kit I cannot find my Master Keyboard (Roland PC-200 MK II) so It is not possible to connect the midi input to other devices. 
The Keyboard works in windows XP so I think probably it's not an HW issue.
Moreover frequently jack hangs.
Hope someone can help.
Thanks in advance.

> miciogatto@ubuntumicio:~$ aplay -l 
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Mia [Mia], dispositivo 0: PCM [Mia]
  Sottoperiferiche: 7/8
  Sottoperiferica #0: subdevice #0
  Sottoperiferica #1: subdevice #1
  Sottoperiferica #2: subdevice #2
  Sottoperiferica #3: subdevice #3
  Sottoperiferica #4: subdevice #4
  Sottoperiferica #5: subdevice #5
  Sottoperiferica #6: subdevice #6
  Sottoperiferica #7: subdevice #7
miciogatto@ubuntumicio:~$ sudo lshw -C multimedia

SCSI                      



  *-multimedia     
       description: Multimedia controller
       product: DSP56361 Digital Signal Processor
       vendor: Motorola
       physical id: 5
       bus info: pci@0000:03:05.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Echoaudio Mia latency=192
       resources: irq:20 memory:fbf00000-fbffffff


---

### Post by Pablo_F on 2011-05-01
Hi, 

Do you plug your MIDI keyboard via USB or via MIDI cable to a MIDI input device? In any case, what is the terminal output of

**arecordmidi -l && aplaymidi -l**

If the MIDI keyboard is connected to USB, show also the output of

**lsusb**



Cheers, Pablo

---

### Post by aredcat66 on 2011-05-03
Hola Pablo
thank you for your answer

> **Pablo_F said:**
> Hi,
Do you plug your MIDI keyboard via USB or via MIDI cable to a MIDI input device?


The keyboard is connected via MIDI cable to the MIDI input of the soundcard

> **Pablo_F said:**
> 
 In any case, what is the terminal output of

**arecordmidi -l && aplaymidi -l**


The output is : 

  [PHP]Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    Mia                                   Mia
 Port    Client name                        Port name
 14:0    Midi Through                      Midi Through Port-0
 16:0    Mia                                    Mia[/PHP]

---

### Post by Tux Toledo on 2011-07-27
I'm having the same problem with my USB MIDI (Oxygen 25). Here's the output of lsusb:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 009: ID 0763:2026 Midiman 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0bda:0182 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 13b1:0020 Linksys WUSB54GC v1 802.11g Adapter [Ralink RT73]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It doesn't show up as a MIDI device in the JACK connection manager.

---

### Post by Pablo_F on 2011-07-27
Hi, 

For clarification, the MIDI tab in qjackctl refers to JACK MIDI and the ALSA tab refers to ALSA MIDI. So, both are MIDI. 

Normally, hardware MIDI devices should appear in the ALSA tab. Whenever there is a need to bridge a hardware midi device to JACK MIDI, the recommended way to do it is running "ajmidid -e" (tip: put "ajmidid -e &" as a post-start script in qjackctl setup, options tab).

So, does it appear in the ALSA tab?

Cheers, Pablo

---

