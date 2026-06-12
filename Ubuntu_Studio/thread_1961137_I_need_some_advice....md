---
title: "I need some advice..."
date: 2012-04-18
forum: Ubuntu Studio
---

### Post by jmate24 on 2012-04-18
On what sound-card I should get for my Casio WK-200 for Ubuntu Studio so far I have had no luck with getting the keyboard to play through the USB connection and to my monitor speakers I am using OS version 12.04. Also I would like to find a guide to get this all up and running that is current to the 12.04 Release of Ubuntu Studio.

---

### Post by jejeman on 2012-04-18
Plug in casio via usb, and issue this commands
```
lsusb
amidi -l
```
then, paste here the output.

---

### Post by sgx on 2012-04-18
> **jmate24 said:**
> On what sound-card I should get for my Casio WK-200 for Ubuntu Studio so far I have had no luck with getting the keyboard to play through the USB connection and to my monitor speakers I am using OS version 12.04. Also I would like to find a guide to get this all up and running that is current to the 12.04 Release of Ubuntu Studio.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

the 4th and 8th link at the wiki have screenshots and info to
get your keyboard and soundcard connected in qjackctl,
and then running with the zynaddsubfx softsynth.

The connections are the same, regardless of which versions
are installed. In the Alsa tab, connect zyn on the right,
to your midi device on the left.

In the Audio tab, connect system on the right, to zyn on the left.

Some instruments can use a2jmidid, which makes a midi port in
qjackctl midid tab.

install a2jmidid and run command

a2jmidid -j default.

For audio processing and recording, connect the Casio headphone
output to the soundcard line input. It will be on the qjackctl
Audio tab on the left. Start a recording software like timemachine, it will be in the audio tab on the right, connect them, press record, and begin playing. Press the button again to stop. A file beginning with tm, and ending with .w64 will be your music. Audio, not midi.

qjackctl setup page, 

Input Device >
Output device >

click the > and see if the Casio midi keyboard is there to choose.
Cheers

---

### Post by jmate24 on 2012-04-22
I'm just looking for a sound card that I can adjust the midi settings on a little easier I have an available 32-bit PCI slot and I am wondering what I should buy from newegg.com.

because it seems that the midi settings are out of whack I cannot get it to record or play midi audio but I will post the outputs.


```
justin@justin-MS-7596:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 003: ID 0402:7108 ALi Corp. 
Bus 002 Device 002: ID 125f:312b A-DATA Technology Co., Ltd. 
Bus 004 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 005: ID 05ac:024f Apple, Inc. 
Bus 001 Device 006: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 003 Device 002: ID 07cf:6803 Casio Computer Co., Ltd
justin@justin-MS-7596:~$ amidi -l
Dir Device    Name
IO  hw:2,0,0  CASIO USB-MIDI MIDI 1
justin@justin-MS-7596:~$ a2jmidid -j default
Directory "/home/justin/.log/a2j" does not exist. Creating...
Directory "/home/justin/.config/a2j" does not exist. Creating...
JACK MIDI <-> ALSA sequencer MIDI bridge, version 7 (b169fb6b8e9e11ce1488d1964649aabedbb89ddf) built on Wed Dec 31 17:00:00 1969
Copyright 2006,2007 Dmitry S. Baikov
Copyright 2007,2008,2009,2011 Nedko Arnaudov

Bridge starting...
Using JACK server 'default'
Hardware ports will not be exported.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
ERROR: a2j_jack_client_create: Cannot create jack client
ERROR: a2j_start: a2j_new() failed.

```

---

### Post by sgx on 2012-04-23
try starting jackd with this

jackd -d alsa -r 44100

then run

a2jmidid -j default

look in the midi tab of qjackctl for an icon

open a synth, phasex, zynaddsubfx, calf monosynth etc
An icon should appear in the Audio tab, and maybe in the Alsa tab.
Make connections by selecting the desired item on each side,
and press the connect button on this panel, not the one
on the main panel.

If that fails, reboot with the keyboard unplugged.
Plug it in, turn its power on, and run the commands and
start an instrument again.
Phasex autoconnects in the Audio tab, so connect midi in
the alsa or midi tabs, or both.

An maudio audiophile delta 24/96 pci card works and sounds great, hassle free setup in
almost all cases. I use one fpr 5 years already!
ice1712 is its kernel module, envy24control
is a dedicated mixer-control app. google those terms to see
what users report. $99 or less online
Cheers
[http://www.ebay.com/itm/ws/eBayISAPI.dll?ViewItem&item=270912286786+&item=270912286786&lgeo=1&vectorid=229466](http://www.ebay.com/itm/ws/eBayISAPI.dll?ViewItem&item=270912286786+&item=270912286786&lgeo=1&vectorid=229466)

---

### Post by emma157 on 2012-04-23
i think you need to change your driver.

---

### Post by jejeman on 2012-04-23
Your Casio keyboard is recognized as midi device, so you should be able to use it as midi controler if that was what you wanted by saying
> getting the keyboard to play through the USB connection and to my monitor speakers
So you don't need different sound card.

---

### Post by birdie_in_texas on 2012-04-24
From what I read, it looks like he is trying to use the on-board Casio tones as if he was just using the PC as an amplifier, and he does not realize he cannot do this without an interface..but to use the keyboard as a midi controller, he needs to load a soft-synth so that the PC can assign the Casio to control that and he must use the software to pick a "sound"..

---

### Post by sgx on 2012-04-24
That may be the case, if so, connect the headphone or
line-out to the motherboard line-in.

Cheers

---

### Post by jmate24 on 2012-04-25
tried connecting to line-in and to no avail the pc does not recognize it as a microphone it says that it exists but the synth is way off I also tried setting the keyboard to MIDI and no luck. I guess I will try buying a card and or a proper input device from my local music store they also said that it could be the midi settings of my sound card or the driver.

---

### Post by sgx on 2012-04-25
aplay -l
cat /proc/asound/cards

the output of these commands should have a soundcard or chipset name
within brackets. In qjackctl, setup page,

Input Device >
Output Device > click the > widget and look for something similar to
what is in the brackets, and select it.

If its not there, replace whatever hw:0,0 hw:1 etc are there with the
text inside the brackets. You can type it in the change, then stop
and restart qjackctl.

The headphone out of the keyboard can go to the line in.
Ideally, you would have some preamped source to boost
electric guitar levels for that line input.

In qjackctl, press Connect on the main screen, the line in will be in the Audio tab, left side,
labelled 'System', with a widget to expand the display for
stereo and multiple input/output.

The soundcard/chip output, will be System on the right side.

The alsa tab has the midi connections, when you start a synth like phasex, zynaddsubfx, whysynth, calf monosynth, it will be listed
on the right side, select it, and a midi port on left side,
and press the connect button

to see if Casio is found by midi, use the commands

aconnect -i and
aconnect -o
Cheers

---

