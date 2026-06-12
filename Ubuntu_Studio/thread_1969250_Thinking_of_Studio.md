---
title: "Thinking of Studio"
date: 2012-04-29
forum: Ubuntu Studio
---

### Post by TheMTtakeover on 2012-04-29
I am a music producer, and I have recently switched to Ubuntu. I am looking at trying out Ubuntu studio I have been told that some of the programs may not be able to offer me a full replacement of my FL Studio set up, but I am more curious than anything. I had a few questions

Does Ubuntu Studio work good as an OS even if I find I don't like the music programs in it?

Where is the best places to get VSTs and Synthesizers at?

Are any of the programs fully featured DAWs?

---

### Post by sgx on 2012-04-30
Hi, no 'full' daw yet, but between qtractor, ardour, timemachine,
audacity, and plugins, there is little that can't be done.

Reaper works well with wine and wineasio, and even your FLS may work, given compatible hardware. Install wine and wineasio for that.
Run command regsvr32 wineasio.dll
choose wineasio in the host, and

wine name-of-installer.exe  to run installers.

Synaptic is your linux software installer, you'll want to press its reload button to update the list, then install
zynaddsubfx, its modern cousin, yoshimi, phasex, hexter, whysynth, calf monosynth (part of the calf plugins package) qsynth for soundfonts playback, hydrogen for drum machine and sample playback
in patterns, and for fx, guitarix2,
rakarrack, invada and MDA plugins, all LV2 and ladspa plugins
tap, caps, amb, swf,vco

Don't get flustered, there is a lot to learn, it took years
for microsoft to screw things up so bad.

youtube for
ubuntu studio, qjackctl, ardour, hydrogen, rakarrack, guitarix
it will bring good luck.
Cheers

---

### Post by jejeman on 2012-04-30
> **TheMTtakeover said:**
> Does Ubuntu Studio work good as an OS even if I find I don't like the music programs in it?

Where is the best places to get VSTs and Synthesizers at?

Are any of the programs fully featured DAWs?1. Yes, ubuntustudio is good as ubuntu is.

2. You have synths in reposotires.

3. What is fully featured DAW?

---

### Post by sgx on 2012-04-30
Full featured daw is for example
Sonar
Cubase
Logic
FLStudio
Ableton
Studio One

These ship with sample and plugin content, comprehensive recording
options, midi and audio editing, tempo and pitch editing, complete session management, and some include bundled extras from business
partners and license holders. Some are bundled with hardware
devices. How well the features integrate, or succeed, is the
subject of many enjoyable fan wars.

To me, linux is itself, a daw, the sum of the parts need
not be huge, yet can be very effective. The release/business model
is of course different than commercial products, and each has
advantages and flaws, worthy of being inclusive,
rather than exclusive. Neither makes for a good religion,
yet zealotry is all too abundant these days.
Cheers

---

### Post by TheMTtakeover on 2012-04-30
Thanks for the replies. and Yes FL does run in Linux when using crossover. I haven't tried just wine but I'm sure it would run the same. When I had FL in Crossover on 11.10 there was a very noticeable lag of when sounds should be hitting, will the studio Kernal help with this at all? Because I run FL on my mac with Crossover and I've had no issues like that with it.

---

### Post by sgx on 2012-04-30
Was crossover using wineasio? That might account for some slowness.
If it has the same type of winecfg, choosingjackd instead of alsa,
may be an issue. There is a lllloooonnnnnggggg topic here, where people worked hard to get FLS working,  

[http://ubuntuforums.org/showthread.php?t=1260057&highlight=fl+studio](http://ubuntuforums.org/showthread.php?t=1260057&highlight=fl+studio)

---

