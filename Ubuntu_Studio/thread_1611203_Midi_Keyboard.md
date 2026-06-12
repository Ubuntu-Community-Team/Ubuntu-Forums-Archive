---
title: "Midi Keyboard"
date: 2010-11-01
forum: Ubuntu Studio
---

### Post by korsvanloon on 2010-11-01
Hi all,

I'm new to the forums :) and I want to start making music in Ubuntu Studio. So far I've managed to get Jack working: I can connect Virtual Keyboard with ZynAddSubFX and do something and I understand how that works. But now I want my physical midi keyboard which is connected to an M-Audio Fasttrack Pro to replace that.
Jack detects Fasttrack pro and Fasttrack pro is recieving events from my keyboard (the light flickers when I play), but when I make a connection (red line) with Fasttrack pro and ZynAddSubFX nothing happens. My keyboard shoupd send events to all channels.

What's wrong?

Kind regards from the Netherlands,

Kors

---

### Post by sgx on 2010-11-01
Hi, you press the Setup button in qjackctl, and on the right, you see

Input Device >
Output Device >

click the > and choose your soundcard in both, possibly ICE1712 for
m-Audio sound chips. It could be your motherboard soundchip is the unwanted default. 

There are two connections needed in qjackctl, press Connect
on the main qjackctl gui, the alsa tab is for your midi keyboard,
the audio tab is for you soundcard output.

If you run the lsmod command, it will list the kernel modules,
and be able to find the motherboard soundchip module. You can make a textfile called blacklist, put in the folder

/etc/modprobe.d

It will be just


blacklist name-of-unwanted-module

envy24control is a mixer for maudio souncards, use synaptic
to install it.

Cheers

---

### Post by korsvanloon on 2010-11-02
Thanks for your reply,

I can choose between (apart from hw 0's):
- hw1 fast track pro
- hw 1,1 USB audio #1
- hw 1,0 USB audio** {only in output}**
- hw 2 MPU-401 UART

I'm not sure if I tried all combinations, but I definitly tried fast track pro with and without some combinations and it doesn't work.

When I connect (in the alsa tab) fast track pro with Timidity I can hear the keyboard sound through my computer boxes. But when I connect it to ZynAddSubFX it doesn't do anything.

Also sometimes I don't hear any sound coming from ZynAddSubFX (if i click on those keys).

And I don't understand the last thing you are saying about the black list thing. What is it for?

---

### Post by AutoStatic on 2010-11-02
Hallo Kors en welkom!

Blacklisting is to tell your system not to load certain drivers. IMHO it's not necessary in your case.
Regarding ZynAddSubFX, did you connect both the audio ports (in the Audio tab) and the MIDI ports (in the ALSA tab)? So in the Audio tab the outputs of ZASFX should be connected to the capture ports of your soundcard and in the ALSA tab the MIDI out port should be connected to the MIDI in of your Fast Track Pro.

Groet,

Jeremy

---

