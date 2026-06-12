---
title: "EMU Tracker USB not appearing in Patchage"
date: 2011-06-07
forum: Ubuntu Studio
---

### Post by skipkent on 2011-06-07
Greetings!

I've connected my EMU Tracker USB audio device to my laptop running the latest (June 2011) Ubuntu Studio.  I ran the System/Preferences/Sound utility and the Tracker showed up along with the laptop's internal sound.  I set the Tracker as the default in/out and could see a level when I strummed a guitar on input 1.  I couldn't hear anything, however.  When I did the speaker tests, I got sound from the EMU just fine.

I then ran Patchage and started up Rakarrak, and saw the system/capture_1 in Patchage make the connection.

Question 1:  Should I see the EMU in Patchage somewhere?  I poked around but it doesn't appear to be in there.

I enabled effects on Rakarrak and strummed a bit but no sound.  When I boosted the input and output on Rakarrak, I got some sound (ambient, no guitar) out of the laptop speakers, so it was clearly using the system (laptop) sound and not the EMU.

Can anyone help point me in the right direction here?  I'm thinking I need to configure JACK somehow to recognize the EMU, and then that will in turn cause the EMU to appear in Patchage, but I'm not sure.  

Thanks in advance for any help anyone can offer!

-skent

---

### Post by Pablo_F on 2011-06-07
Hi, 

You have to tell jack what audio card to use. The normal way of configuring the jack audio server (jackd) is via qjackctl (Jack Control). In the interface field, select the audio card you want. 

Note that the audio hardware will be named "system" in any case. So, it is essential that you know what audio card jack is using.

Sound preferences is a pulseaudio frontend. Pulseaudio is the default audio server. rakarrack, ardour, qtractor, etc, depend on jack, not pulseaudio. Patchage has nothing to do with pulseaudio either. You can use patchage or you can use the Connections window of qjackctl (audio tab) to make audio connections between jack clients (audio card, aka "system", and applications).

---

### Post by skipkent on 2011-06-07
Pablo,

I opened qjackctrl but I don't see the EMU listed as an option in the Interface drop-down.

What I see is this:

(default)
plughw:0
/dev/audio
hw:0
/dev/dsp

I'll experiment with each of them, but if you could offer any ideas as to which might refer to the EMU that would be great.

Thanks very much for your help with this!

-skent

---

### Post by skipkent on 2011-06-07
NEVER MIND!

I got it.  I clicked the little '<' icon next to the Interfaces drop-down and that showed the EMU.  Getting sounds now.  

:D

Thanks again for your help!

---

