---
title: "MusE doesn´t start: Config file might be corrupted. Unkown shortcut: toggle_mi"
date: 2011-05-19
forum: Ubuntu Studio
---

### Post by Troubadix-der-Barde on 2011-05-19
I open a new topic, as my problem changed:

Ubuntu Studio 11.04, lowlatency-kernel.

I was able to start MusE using jackd1. But then it was not able to create a Jack-Midi-in port. I tried that several times (turning on and off Jack) and after a few trys neither MusE did want to start: 

"Config file might be corrupted. Unkown shortcut: toggle_mi"

I really would prefer MusE, as it gives full Jack-Midi-support and my system makes incredible noises using Alsa-Midi (Rosegarden doesn´t seem to be an option because of that). So would be happy for any suggestion.

Saludos

---

### Post by Troubadix-der-Barde on 2011-05-20
Ok, an update:
I reeinstalled the hole system. It's able to reproduce the crashing MusE.

Means: When I try to create a Jack-MIDI-Port (just MIDI-in is the problem, Jack-MIDI-out works) MusE crashes.


Jack says: 

"subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
11:31:19.487 XRUN callback (2).
11:42:24.905 XRUN callback (3).
11:43:15.286 Schaubild der JACK-Verbindungen geändert.
11:43:15.384 JACK-Verbindung geändert.
11:47:31.536 Schaubild der JACK-Verbindungen geändert.
subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
subgraph starting at MusE timed out (subgraph_wait_fd=36, status = 0, state = Triggered, pollret = 0 revents = 0x0)
11:47:31.603 Schaubild der ALSA-Verbindungen geändert.
11:47:31.655 JACK-Verbindung geändert.
11:47:31.656 ALSA-Verbindung geändert.
11:47:32.341 XRUN callback (4).
11:49:54.248 Schaubild der ALSA-Verbindungen geändert.
11:49:54.271 ALSA-Verbindung geändert.
11:49:54.424 Schaubild der JACK-Verbindungen geändert.
11:49:54.492 JACK-Verbindung geändert."


And in the MusE-Terminal:

"MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
MidiJackDevice::queueEvent #1: buffer overflow, event lost
Speicherzugriffsfehler"


Now I'm afraid of trying to create a Jack-MIDI-out-port, because maybe it will destroy again this MusE config file.


Saludos

---

### Post by Pablo_F on 2011-05-20
Hi, 

Try to find the configuration file. 

sudo updatedb
(wait...)
locate MusE

In my system it is ~/.MusE

So, edit it:

gedit ~/.MusE

Try to see if there is something wrong there. 

If you can't figure out, just delete it and start again.

Maybe you should update to Muse 2 Beta.

Cheers, Pablo

---

### Post by Troubadix-der-Barde on 2011-05-20
You mean, that you don´t have problems to create a Jack-MIDI-In-Device? 

Did read about similar problem, but just with the dummy-driver, and seems as if they fixed it. I have it with alsa- and with firewire-driver.

How I said: I reinstalled Ubuntu 11.04 and still have the same problem. Create in MusE-Settings a Jack-Midi-In-Device let crash MusE.

Before 11.04 I used 10.10 wich just offered MusE1.0 in repositorie, so I installed MusE1.1 out of source. That didn´t make this problem with Jack-MIDI-In. But now I try to install it out of repositorie and have the problem with the Jack-MIDI-In.

Already thought about installing MusE2.0. But still am very new in Linux, so installing stuff, wich is not in the repositorie still is kind of mess for me.

I will try your advise, when I come home.

Saludos.

---

