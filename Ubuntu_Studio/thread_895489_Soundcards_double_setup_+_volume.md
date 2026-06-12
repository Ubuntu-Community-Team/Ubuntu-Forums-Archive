---
title: "Soundcards double setup + volume"
date: 2008-08-20
forum: Ubuntu Studio
---

### Post by Wtrz on 2008-08-20
Hi all,

I wish to build a computer setup with two soundcards with ubuntu running mixxx. I have two questions. 
At this moment my dj mixing setup is connected like this:

[LIST]
[*]Ubuntu computer with one onboard soundcard
[*]soundcard output
[*]line in - mixer (3 phono in, 2 line in)
[*]amplifier
[/LIST]

I also have a dualcdplayer connected to the line in seperated - mixer. So one channel now has input from the dualcdplayer & the computer. The output volume of the soundcard is very low, while I ensured that every mixer setting is correct maxed out. (I also tried it with Windows XP, max volume stays the same) I tried to set the alsamixer volume higher but it will distort the sound. I think the max output of the soundcard has been reached, but it's volume-amount is nothing compared to the output volume of the dualcdplayer. 
[B]
Question 1: Can I use the onboard soundcard to achieve higher output volume? [/B]

Okay, now for my future setup I would like:

[LIST]
[*]Ubuntu computer with two soundcards
[*]Both Soundcards outputs
[*]Seperated channels (phono in prefered) - mixer
[*]amplifier
[/LIST]
[B]
Question 2: Before buying any soundcard, how can I ensure that the max volume of the soundcards are equal (or higher) to the dualcdplayer? [/B]

Any help is appreciated:)

---

### Post by Chainek on 2008-08-20
I am not familiar with audio setups in linux very much yet. I've always used windows until now.

One thing I can point out though.. Most of the pro audio soundcards have an option in their drivers to switch the input jack between line-level input and amplified input.

If their is a problem with the volume from the alsa mixer though then this means nothing.

I would look into some Darla soundcards. I currently use an Echo Darla. I havn't set it up for recording in linux yet. But I did notice that there is a specialized inferface written for the Darla soundcards in the add/remove programs link in the applications menu. It appears to include some drivers as well.

---

### Post by markbuntu on 2008-08-20
If you want to use two soundcards, you should be aware of a few issues. Sound cards use their own clocks and they will become unsynchronized rather quickly and drift apart. There are a few pro cards that allow clock sharing, Hammerfall and the m-audio 1010 are a couple I have heard about that can do this. Another way involves extensive hardware hacking to physically wire two identical cards together. 

A third way involves using pulseaudio which will correct the clock drifting at some expense in latency. I don't know how you can do this with jack or alsa.

---

### Post by Stochastic on 2008-08-21
> **Wtrz said:**
> Hi all,

I wish to build a computer setup with two soundcards with ubuntu running mixxx. 
<snip>
Okay, now for my future setup I would like:

[LIST]
[*]Ubuntu computer with two soundcards
[*]Both Soundcards outputs
[*]Seperated channels (phono in prefered) - mixer
[*]amplifier
[/LIST]


Why is it that you need two soundcards?  Usually this is only needed for multiple output channels, and for any mixxx setup you can get all the outs you need on a multiple-channel soundcard that will cost you much less than two decent sound cards - and cause you much fewer headaches (a single card won't go out of sync).

> **Wtrz said:**
> 
[B]
Question 2: Before buying any soundcard, how can I ensure that the max volume of the soundcards are equal (or higher) to the dualcdplayer? [/B]

Any help is appreciated:)

Check the info on your soundcard at either the alsa website [www.alsa-project.org](www.alsa-project.org) or the ffado website (for firewire cards) [www.ffado.org](www.ffado.org)

---

### Post by Wtrz on 2008-08-21
Thanks for the replies, 

Stochastic, great wake-up call. I just haven't thought about a single multi-channel soundcard setup. <stupid!>

First gonna check out some multi-channel soundcards, any recommendations/experiences with ubuntu + multi-channel soundcard?

---

### Post by jocheem67 on 2008-08-21
My m-audio delta 1010lt does the job...got plenty in's and out's, with acceptable volume.

By the way, I've been playing around with mixxx too lately. Already got some help too from the above posters. My idea? Why not buying a dj controller with inbuilt soundcard? My Hercules RMX has 4 outputs, is recognized by ubuntu/mixxx as such, and works well enough.
Ofcourse there are other ones, lots of 'm working well with mixxx.
A better than average soundcard is I think in the same pricerange as a djcontroller, and a controller is way more fun, you can carry it around to your friends and show off yor skills
:popcorn:
As a matter of fact, my beautiful m-audio is sitting still at the moment, as the built-in RMX soundcard does provide in all my audio needs. You can easily configure this through alsaconf. Pulse is not my thing yet, I'm using jack for low latency.

---

### Post by Wtrz on 2008-08-21
The Hercules RMX indeed seems to be a nice controller. But in my case, I already have a mixer that I want to put to use.

An hour ago I tried connecting the output of the soundcard to a phono-input of the mixer and the volume is much, much better. The volume now matches the dualcdplayer's volume. Although I have to equalize the bass a notch down in mixxx and there is a light, but hearable 'buzz'. 

As I'm just rolling into mixxx, I would like to try it out a little before purchasing 'expensive' equipment. Searching for a multichannel soundcard below 30 euro. Wonder if some card like this:  [http://www.maplin.co.uk/Module.aspx?ModuleNo=44583&doy=21m8&C=SO&U=strat15](http://www.maplin.co.uk/Module.aspx?ModuleNo=44583&doy=21m8&C=SO&U=strat15) 

could be configured to use in my setup. (assign deck A to front out and assign deck B to rear out for example)

---

