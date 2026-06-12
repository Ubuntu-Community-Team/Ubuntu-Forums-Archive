---
title: "90's Atari ST Cubase User - now totally confused"
date: 2012-10-25
forum: Ubuntu Studio
---

### Post by layolayo on 2012-10-25
Hi, I've decided to get back in to my music and get all my old synths back out. Got myself a new MIDI keyboard (Casio CDP-120) and a USB-MIDI converter  (Roland UM-ONE).

My Old Synths: 
DrSynth DS330 - MIDI Channels 1-16
DrRhythm DR660 - MIDI Channel 10
Novation BassStation - Midi Channel 16
Yamaha TX81Z - Midi Channel 15
Roland TB303 - with the Kenton MIDI Conversion - Midi Channel 14

All synths are connected up to a MIDI expander unit, except the new Casio which has a direct USB connection.

I have loaded up Rosegarden (the nearest I can find to Cubase) - and things seemed OK...

Generally I had the DS330 accepting all 16 MIDI channels and I individually set the sound level of channels I was using for the other synths to 0. 

Unfortunately - things are not as easy as they used to be... I used to choose a channel and enter sequence data and voila - everything worked. There was a certain separation between the device settings and the Atari. Now it would seem that Rosegarden wants to control the settings of my devices..?

The DS330 and DR660 keep going back to standard settings. And I cannot get the BassStation to play from the track data, but will from the midi-thru data.

The opposite seems true of the TX81Z which has 16 preset channels - I cannot get it to play from the keyboard input, but it will automatically switch to the particular channel that I select on Rosegarden, but so do the other synths...?

It's doing my head in! This used to be so easy! 

It nearly looks like I need a USB-MIDI adapter for every synth! But that cannot be right, surely!

I hope someone out there can help me out with this - I am hoping it is just a simple setting I am missing.

Cheers

Layolayo

---

### Post by desktorp on 2012-10-25
I've never used Rosegarden, but I wonder: how much JACK is involved in this setup?

The last time I had a problem with multiple devices, MIDI, USB and ALSA, it was something I was doing wrong with JACK.

Sorry - I know that's not helping anything.

Mostly wanted to praise your decision and your great gear and to wish you good luck.  If you don't find help here, try the forums at KVRaudio.com .. they seem to solve a lot of complicated problems.  Hopefully this won't become any more complicated for you ;)
..and remember, no acid until you've cleaned your room.  Puh puh puh puh puh:guitar:

---

### Post by sgx on 2012-10-26
Hi, another thing to sort, is that usb midi does not always
play correctly, when 5-pin midi ports are also used. I would
get a soundcard with 5 pin midi ports, or a usb device
with multiple 5-pin connectors.

The expander midi ports should appear in the Alsa tab of qjackctl
connection panel, the Audio tab is for souncard and
software i/o. The Midi 

In the meantime, verify that each piece of gear works
individually with the Roland, and when using the expander,
that it shows it's ports in qjackctl

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

in this wiki, link 4 is for jackd, and link 8 for qjackctl,
the gui for jackd, to connect all your hardware and software.
It is crucial to set this up correctly. In the qjackctl
setup page, the Periods/Buffer setting should be 3 for us midi
device like the Roland. (And 'MIDI Driver' box should read 'none'
since midi is handled separately by alsa)

Be patient, and enjoy the gear. The analog outs can all be
recorded in timemachine, ardour, and audacity, as you get
familiar with linux midi.

---

### Post by jejeman on 2012-10-26
It seams to me that Rosegarden sends program change message. Try to turn it off.
If you just do MIDI sequencing, maybe Seq24 is better for you. Its simpler program than Rosegarden, and it's closer to pure sequencers.

---

### Post by layolayo on 2012-10-26
Thanks, quick update -

I have given up with Rosegarden for the moment and tried QTractor - I have managed to get communication with each device on each MIDI Channel set to it (whoo hoo!)

This is playing with the CDP-120 and from QTractor - good news.

There is still a problem with the Dr-Synth resetting itself and/or giving a Error Message everytime QTractor goes back to the beginning of Segment [Time Sector 00:00] although this seems to be intermittent.

I'll have to play around with getting the SysEx commands set-up, so the DrSynth and DrRhythm can be configured on start-up (I seem to remember this was essential back in the day!)

sgx - I have configured QJackctl as recommended.

There also seems to be a stability problem with my system as QTractor can just crash out on playing or stopping a track.

_Rosegarden_
This software looks great - maybe I will have to persevere, and get a full on midi card for my machine. There is some great advantage of configuring everything from the desktop - it just seems a little alien from my 'old skool' method!

Although I maybe missing something and QTractor can do all this as well.

(In QTractor - I do miss drawing the velocity curves with the pen tool)

---

### Post by layolayo on 2012-10-26
Now coming up against not been able to dump SysEx data into QTractor - looks like I need an Instrument set-up. But you need an instrument file .ins or .sf2 first ???

would getting a larger scale midi input/output device help here. I have seen the MidiSport 8x8 shown on a few sites but cannot locate one to buy. They now do a 2x2 version for £40, don't want to spend more money if this isn't going to solve the problem.

With respect to jejeman - I reckon you're on the money there. I just wish I could locate where and how this data is transferred. The manuals for RoseGarden and Qtractor are limited in this area - or I am too stupid to understand/find the data... :(

---

### Post by sgx on 2012-10-26
There is in qjackctl Setup page, 'Timeout (Msec)'
You might increase this to 1000, or 2000 to see if
the crashes stop, then back your way down to a sweet spot.

A file  /rtc/security/limits.conf
has a line near the bottom:

@audio          -       rtprio           99


When 99 is the setting, the qjackctl Setup page priority
can be increased to 89, for maximum audio performance,
relative to other more mundane system functions.

Maybe the omni on/off on the hardware can be toggled, or a master/slave sync established with qtractor?
Glad good progress is happening!

---

### Post by jejeman on 2012-10-26
I'm not that deep in MIDI, but I do have hardware synths which I have used only accasionaly, so far.
Also I use MusE, not Rosegarden so I can't help you that much with that.
In MusE you can define completly your hardware instrument - programs, contorlers and SysEx.
I don't know how your DS330 and DR660 resets, but I have notice on my synths that when makeing new project they change to first program. After that, because I have made definitions for my synths (which are now included in MusE - FLOSS :guitar:), I choose for each midi track a program to be played.
Also I think I saw in the settings of my synths something like MIDI filters, so you can look for it in the manuals of your hardware for something like that.
At the moment I'm not by my synths to check on that.

---

### Post by layolayo on 2012-10-27
Hi jejeman - just downloaded Muse, it looks pretty neat (and with pen tool for velocity ramps! :) )

I see what you mean about resetting the synths on start-up, it is a similar effect that I had in Rosegarden. Can you offer any advice on configuring this - as everytime I change it on the left to a new instrument, when I restart the track they all go back to the basic settings?

---

