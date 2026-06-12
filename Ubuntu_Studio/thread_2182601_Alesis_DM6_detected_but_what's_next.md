---
title: "Alesis DM6 detected but what's next?"
date: 2013-10-21
forum: Ubuntu Studio
---

### Post by 33Nicolas on 2013-10-21
I have an Alesis DM6 detected but what's next? How do I use it with anything?

Thanks

---

### Post by jejeman on 2013-10-21
Detected as what?
Give
```
lsusb
arecord -l
amidi -l
```

---

### Post by 33Nicolas on 2013-10-24
I'm trying to use my Alesis DM6, ideally to record myself.  Any idea how  can do that?  Thanks.

---

### Post by cub on 2013-10-25
What have you tried already? Does it recognize the it when you connect the usb?

---

### Post by 33Nicolas on 2013-10-25
Yes, not sure what to do with it.

I saw it show up in something.  Either a midi path editor or something similar.

---

### Post by Bucky Ball on 2013-10-25
***Threads Merged***

*_Do not_* post duplicate threads, please. It dilutes community effort, confuses users and potential helpers, wastes time and energy, lessens your chances of getting help, and a heap of other not good things. Thanks.

You posted a second thread without having replied to jejeman's request for output in the second post of this one. You seem to have ignored it:

```
lsusb
arecord -l
amidi -l
```

If you want help, respond to helpers rather than posting another thread. If you don't understand something, ask. ;)

---

### Post by 33Nicolas on 2013-10-25
Sorry about that.  I just noticed.  I don't know how.

---

### Post by Bucky Ball on 2013-10-25
All good. What is the output of those commands so people can have a shot? Can you open Ardour and see it as a usable instrument? Not sure what the DM6 is (device type, that is) ...

If you are new to UStudio you might want to do some research and read up on jack, etc. ;)

---

### Post by 33Nicolas on 2013-10-30
Thanks, I will do reading.  Alesis is an electronic drumset and shows up e-drum.  It has a USB output and is midi.  Ardour doesn't see it. 

lsusb
Bus 001 Device 005: ID 05ac:021d Apple, Inc. Aluminum Mini Keyboard (ANSI)
Bus 001 Device 004: ID 05ac:1005 Apple, Inc. 
Bus 001 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: XFi [Creative X-Fi], device 0: ctxfi [Front/WaveIn]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC9200 Analog [STAC9200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


amidi -l
Dir Device    Name
IO  hw:2,0,0  e-drum MIDI 1



Hopes that helps.

Basically, what programs can I use to listen and record the Alesis drum set.  Thanks, Nicolas

---

### Post by jejeman on 2013-10-30
Before when you executed the "lsusb" command did you plugin the drum set? I guess you used the MIDI port on your sound card, or something else, because it doesn't show as USB device, at least it is not obvious. Does this Alesis DM6 has USB connection?

It shows as MIDI I/O device. So, you can use it as MIDI input device (record notes etc.) or player via hardware sound modul if this DM6 has one.
> Basically, what programs can I use to listen and record the Alesis drum set. Thanks, NicolasSince this is only MIDI device you can record MIDI data in any program that does that, like MusE, Seq24, Ardour3, Qtractor etc.
If it has sound module, you can only connect it's audio output to you sound card audio input and monitor it.

I don't use Hydrogen but I can tell you general workflow with MIDI devices.

1. We saw that DM6 is recognized as MIDI device - first step is good.

2. Launch JACK e.g. via Qjackctl

3. Launch hydrogen

4. Open connect window in Qjacktl, Check if Hydrogen has registered Audio ports in Audio tab. Connect Hydrogren outputs to System inputs to hear sound from it on your hardware speakers via soundcard. Switch to ALSA tab to see MIDI ports. It should have both Hydrogen MIDI ports and e-drum ports. Connect e-drum outputs to Hydrogen inputs in order to receive MIDI data in Hydrogen from the e-drum. And vice versa, connect hydrogen outputs to e-drum inputs to control DM6 with hydrogen (this only make sens if DM6 has sound module). If there is no Hydrogen MIDI ports in ALSA tab, check the (JACK)MIDI tab. If they are there, than you need to find a way to bridge ALSA MIDI to JACK MIDI. Or see in Hydrogen if there is option to use ALSA MIDI instead.

5. Load drum kit in Hydrogen and try to play notes on DM6. You should here samples form Hydrogen playing. Now, you need to check the MIDI drum map to match the MIDI notes to play corresponding samples e.g. bass drum note to play bass drum sample etc. You can remap ether in Hydrogen or on the DM6 if it has drum map presets etc. Also check if the Hydrogen is listening to MIDI channel on witch DM6 is sending the MIDI notes. Usualy for drums it is Ch 10.

This is general workflow with MIDI.

---

### Post by 33Nicolas on 2013-10-31
Wow, thanks Jejeman.  It works!

---

