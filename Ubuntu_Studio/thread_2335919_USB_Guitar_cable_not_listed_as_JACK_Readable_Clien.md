---
title: "USB Guitar cable not listed as JACK Readable Clients/Output Ports"
date: 2016-09-02
forum: Ubuntu Studio
---

### Post by furant2 on 2016-09-02
Hi all,
I'm pretty new to Ubuntu Studio and digital audio in Linux.  I just got a USB cable for my guitar in hopes of using Ardour, Rakarrack and Guitarix. I think I got JACK working now and want to know how to setup the Guitar as a Readable Client / Output Port.  In qjackctl's Connect dialog, I see Midi Through and Sound Fusion CS46xx in the ALSA tab Readable Clients/Output Ports.  The Audio tab shows system>capture_1 and capture_2.

cat /proc/asound/cards
```
 0 [CS46xx         ]: CS46xx - Sound Fusion CS46xx
                      Sound Fusion CS46xx at 0xfddff000/0xfdc00000, irq 20
 1 [Device         ]: USB-Audio - USB Audio Device
                      C-Media Electronics Inc. USB Audio Device at usb-0000:00:13.0-3, full speed
```

lsusb
```
Bus 005 Device 002: ID 0d8c:0014 C-Media Electronics, Inc.
```

In Audacity, if I set the Host to ALSA and Recording Device to: USB Audio Device: - (hw:1,0):Mic:0, I can record the guitar and play it back through my soundcard, but I don't hear it live in realtime.

Any idea what I might be doing wrong?

Thanks,
Joe

---

### Post by jejeman on 2016-09-03
JACK uses only one soundcard.
You have two of them.
Choose the one you want.

You can set two soundcards, one for capture, other for playback. It works, but it is not recommended.

---

