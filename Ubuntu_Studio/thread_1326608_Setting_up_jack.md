---
title: "Setting up jack"
date: 2009-11-14
forum: Ubuntu Studio
---

### Post by Depressure on 2009-11-14
Hi all.

This might be a long shot but it's always worth a try =) I'm doing some sound editing for a friend of mine (drums and guitars), and has done it with audacity which is by all means a nice app. But I want to try working with ardour. However "aptitude install ardour" does not do the magic thing for me and after some reading i found out bout JACK. So how do I set up jack so its working on my system and what can I read to understand how it's set up and used?

I'm running ubuntu 9.10 64bit and want to keep it that way, know bout ubuntu studio but i dont need all those apps....

---

### Post by trulan on 2009-11-14
Here's a good place to start reading:
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")
There are a number of good Jack how-to's out there, hopefully that page will at least get you pointed in the right direction so you can do some informed web searching.

Most guides will recommend Ubuntu Studio and the real time kernel.  If you are working with tracks that have already been recorded this will be no benefit at all.  Just use the generic Ubuntu kernel and be sure to de-select the real time option in Jack.

---

### Post by Depressure on 2009-11-14
> **trulan said:**
> Here's a good place to start reading:
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")
There are a number of good Jack how-to's out there, hopefully that page will at least get you pointed in the right direction so you can do some informed web searching.

Most guides will recommend Ubuntu Studio and the real time kernel.  If you are working with tracks that have already been recorded this will be no benefit at all.  Just use the generic Ubuntu kernel and be sure to de-select the real time option in Jack.

Thank you so much, the tracks are pre recorded yes, so thank you for the tips =)

---

### Post by sgx on 2009-11-14
If recording in audacity from a jackd routed source, you must start recording, then press pause, then go to your connections gui, qjackctl, qjackconnect, patchage, whatever you use, and the audacity portaudio icon should now be visible, connect to it, and press pause again to resume recording. 
This may be new to the various how-to, as audacity gets lots of updates

To begin, you can start jackd first, with garden-variety settings

jackd -d alsa -r 44100

Then start qjackctl, and begin connecting things. Might save you a few minutes tonight.

timemachine for qick onebutton recoding
zynaddsubfx softsynth
hydrogen drum machine
fluidsynth soundfont player
linuxsampler  .gig file player 

Cheers

---

### Post by trulan on 2009-11-14
I think he's working things the other way - using tracks that somebody else recorded with Audacity and putting them together in Ardour.  But that's some good tips for using Audacity with Jack nonetheless.

---

