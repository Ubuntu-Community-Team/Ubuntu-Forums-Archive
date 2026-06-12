---
title: "Making music in Ubuntu"
date: 2007-05-31
forum: The Cafe
---

### Post by hoboken on 2007-05-31
OK, guys. I play guitar but am in love with music of all kinds, and I'd like to start making music digitally on my PC, which includes recording singing and guitar bits. I started fiddling around with FLstudio in windows, but it kinda left me wanting something more versatile - not just for making synth and beats and stuff, but for adding recorded tracks, sounds, mixing, creating full songs, etc. I have ideas but I just don't know what tools I need to get them out of my head and onto my hard disk. So - can any of you musically minded people point me to programs, guides, and anything else I might need? Other questions:

-jackd? What is it, what is it for?

-Is there any decent virtual guitar amp, to add effects to my guitar parts?

-Ubuntu studio? would you reccomend it? Do I have to do a clean install to get it running properly, and lose all my programs and settings I have on Ubuntu?

THANKS - I promise I'll post my groovalicious tunes on here when I'm done ;)

---

### Post by hoboken on 2007-05-31
bump. There must be some Ubuntu musicians out there.

---

### Post by Xzallion on 2007-05-31
Audacity will be a good tool to record small sounds and add effects to the sounds.  For laying down your tracks you will probably want LMMS (Linux Music Making Studio or something like that).  LMMS is a lot like FruityLoops, with some differences.  I haven't tried rosegarden but have heard its a good program also, and I have no experience with ubuntu studio so I can't say yay or nay there.

Give audacity and LMMS a try though.

---

### Post by maniacmusician on 2007-05-31
As of right now, music recording and editing in Linux really isn't all that great, but if you want to use Ubuntu, your best bet is probably UbuntuStudio. A fresh install of it is not required, but it is recommended. You can install on top of Feisty Fawn if you want to.

This should answer your questions about JACK [http://ardour.org/jack](http://ardour.org/jack)

I don't really know about any virtual amps, I like working with my pedals :) Have fun.

---

### Post by firedancer on 2007-05-31
i did  a 'upgrade' from ubuntu feisty about settings i'm not sure 

make sure you have a compatible soundcard , that's my problem at the moment , but it seems ok 


i also did some stuff with the dynebolic livecd 


i had to put everythimg away , waiting to see how to get me a maudio 1010 or something less expensive (poor graduate student without studyloan and no time to work for some money)


in the threads you can find out how to 

;)

---

### Post by icechen1 on 2007-05-31
> **hoboken said:**
> e

-Ubuntu studio? would you reccomend it? Do I have to do a clean install to get it running properly, and lose all my programs and settings I have on Ubuntu? 
Yes,i heard you can install everything in Ubuntu studio to your normal Ubuntu installation(i forgot the link,do a forum search)including themes,etc.

---

### Post by stmiller on 2007-05-31
Hey yeah jack creates internal audio routing for Linux. So you can literally press play in Rosegarden and press record in Audacity and record your project internally on your computer with jack.

Jack also lets you route midi to different programs, as well as audio.

Just install every audio program out there (or try ubuntu studio) and start messing around with everything. You can do quite a bit in Linux.

I'm a commercial music composer as my day job. I created [this]("http://www.scottmillercomposer.com/music/05-News_Intro.mp3") for a local tv news station with Cecilia / Csound and Audacity in Linux, along with some sounds from a non-free program Reaktor (OS X).


Check out these mailing lists for some serious Linux audio users:

[http://ccrma-mail.stanford.edu/pipermail/planetccrma/](http://ccrma-mail.stanford.edu/pipermail/planetccrma/)

[http://music.columbia.edu/pipermail/linux-audio-user/](http://music.columbia.edu/pipermail/linux-audio-user/)

[http://music.columbia.edu/pipermail/linux-audio-dev/](http://music.columbia.edu/pipermail/linux-audio-dev/)

---

### Post by The Mekon on 2007-05-31
> **icechen1 said:**
> Yes,i heard you can install everything in Ubuntu studio to your normal Ubuntu installation(i forgot the link,do a forum search)including themes,etc.

I think this is the link.[http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/]("http://www.ubustu.com/globe/2007/05/23/add-ubuntu-studio-to-an-existing-ubuntu-install/")

Brian

---

### Post by thisllub on 2007-05-31
Ardour is the most powerful recording interface in Linux although it is a little frustrating to learn compared to simpler interfaces.

Audacity is a good sound recorder editor but doesn't have the features of Ardour.

---

### Post by zettberlin on 2007-05-31
It is perfectly possible to do audio-work professional with fun under Linux. It takes quite little effort to set up the system, then you can do anything - though not with the same comfort as on Mac or Win but you can even use a lot of Win-Progs via Wine (with the wineasio-patch).

But in my experience you do not even need that - Linux and its set of free Audioapps will do, if you are ready to learn a bit about acoustics and the way audiosoftware works.

To be perfectly honest I cannot recomend Audacity, especially because its lack of realtime-FX and because the editing.features are not really great. Ardour is indeed a different kind of beast, but if you take the time to read the Doku on ardour.org and experiment a little with it, it can do everything you need to recrod, cut and arrange music and you can sync the midi-sequencer muse via jack to it so you can have synths and a drummachine in sync with your project.

To make Ardour and all the other pro-audiotools for Linux run OK  you need a special kernel and the audioserver jack. The latter connects audioprogs with each other and transports streams in near-realtime. Jack needs a so-called realtime-kernel. Such a thing is in the Ubunturepos under the name "kernel-lowlatency". 

Thanks to the Ubuntustudioproject all needed apps can be installed easily with synaptic.

Proprietary graphics-drivers may be needed to be reinstalled after the kernel-switch. But this is as simple as the first install of them. Just mark the respective packages for reinstallation in synaptic and all should be forgiven :-)

Here on my Audio Workstation Boxes (2 AMD 64, 1 Pentium IV) the kernel runs very very good and on the AMDs the NVIDIA-Drivers work like a charm.

---

### Post by sinaen on 2007-07-15
anyone tried to run fruityloops via wine or such in linux??

hmm.. lmms is really poor every time i start it up it damages my ears throug the headphones distorted sound i do think its something about the audiodriver thou i cannot find out what. cause the sound works in all other cases.. :(

---

