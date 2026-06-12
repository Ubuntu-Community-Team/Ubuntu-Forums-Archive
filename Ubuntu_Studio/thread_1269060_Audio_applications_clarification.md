---
title: "Audio applications clarification"
date: 2009-09-17
forum: Ubuntu Studio
---

### Post by inadaze on 2009-09-17
Hi all,
I am trying to grasp the different levels of applications that go into the input and output sound in Hardy.  I am having some issues with the setup of a USB audio card, and I am lost.

Could someone explain how alsa, pulseaudio and jack work together?  What does each do in conjunction with each other?  do I need one or all?

I am trying to troubleshoot my audio device but I don't know where to begin.  Pulse shows it and alsa doesn't.  I can hear sound but can't record it...  grrr

thanks
Jay

---

### Post by thorgal on 2009-09-18
hello,

ALSA is two things:
1- a kernel layer : provides a driver for your hardware
2- a userspace library that abstracts communication to the driver. It allows userspace applications (like a simple audio player app) to communicate to the hardware via the kernel driver in a consistent fashion. So this userspace API makes it easier for application developers.

JACK: it is a userspace sound server that streams audio data from one application to another, including your hardware. It can do so because it has a backend that can communicate with the ALSA layer. So your h/w becomes an entity (or client) with input and output ports just like a software application that also exposes jack input and output ports. 
The cool thing about jack is that the streaming is sample accurate and has other very interesting features, e.g. the jack transport mode: all applications that are connected to the jack graph can be started and stopped by one single event - mouse click or whatever - OSC, MIDI, etc. This meansthat you can create a complete virtual studio and have all apps responding to one common transport control. JACK is not dealing with the kernel level. It leaves this to ALSA (or OSS or freebob / ffado). JACK is also very configurable so you can decide at which latency you want to work (the time between e.g. the audio entering your PC, treated by the CPU, and leaving your PC).
You can do much more with JACK by combining other machines on a fast network (netjack).


PULSEAUDIO: it is another userspace sound server for generic desktop usage.  It also has a backend that communicates with eg. ALSA (the ALSA userspace lib I mentioned above). Pulseaudio aims at replacing all former desktop sound servers as there were some confusion and also limitations in those. But practice showed that while the objective was nice, it created even more confusion.

SO, conclusion:
- ALSA is the low level layer: kernel driver. It also exposes a userspace API for userspace apps that want to communicate with the kernel driver. 

These userspace apps are for example Jack and pulseaudio.

However, once one app has a grip on your h/w, it tends to be exclusive. So if you run pulseaudio, you will not be able to run jack, unless you trick it to do so. This issue is being taken care of in the actual development of PA so that if one starts jack while pulseaudio is running, PA gives up its grip on the "audio device".  

One can say the same thing about jack. If it runs and has thereby a grip on your "audio device", you will not be able to run audio apps that do not use Jack for their audio io protocol.


- About ALSA;
if you have more than one real devices, and each has an ALSA driver, ALSA will ceate as many "hw" as your PC contains. An audio app that can use the ALSA lib (like mplayer, zine, amarok, etc) can b configured to use one of these "hw: x" (x being 0, 1, etc).

Jack, being an app that can talk via the ALSA lib to the driver, is no exception. If you have an onboard sound chip and an external device (e.g. USB) and all are supported by ALSA, you will have a hw: 0 (onboard chip, most likely) and hw: 1. So If you want to use jack on hw:1 (USB device in this example), you have to configure jack to do so (see other discussion threads in these forums).

If pulseaudio is already busy with it, you have to close it (either by brute force or by issuing this command in a terminal: 
pulseaudio -k 
There might be graphical tools for that, I don't know anything about PA so I cannot help you more at this stage).

Hope this helps.

---

### Post by cooper77z on 2009-09-18
This is just a guess, but if you want to use audio in ubuntu I suspect that the audio must be in a digital format. Like DAT or MIDI or MP3/2 or some other digital format I am missing. Just feed it to the system in a digital format and all should be fine. I think.

Even in Final Cut Pro, on a MAC, all the media has to be digital. So don't feel like Linux is to blame.

---

### Post by raboofje on 2009-09-19
> **cooper77z said:**
> This is just a guess, but if you want to use audio in ubuntu I suspect that the audio must be in a digital format. Like DAT or MIDI or MP3/2 or some other digital format I am missing. Just feed it to the system in a digital format and all should be fine. I think.

Uh, sound cards tend to have these fancy things called A/D and D/A converters, which convert from analog to digital and back again for you :).

As for the original topic: we should document this 'layering' somewhere, for example at [http://wiki.linuxaudio.org/wiki/newbie](http://wiki.linuxaudio.org/wiki/newbie)

---

### Post by trulan on 2009-09-19
I think thorgal just did a pretty good job of documenting this stuff. ;)

Pulse Audio and Jack are often portrayed as enemies.  They don't play together very well.  Some people completely remove Pulse Audio by brute force.  In my limited experience, Jack has always been able to push Pulse Audio out of the way.  If you use Jack Control (qjackctl) to control Jack, it suspends Pulse so it won't interfere with Jack doing its thing.

Here's another thorough documentation, including diagrams, of how audio is set up in linux.
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)
I don't understand all of it and as such I'm ot sure how accurate it is.  But it is interesting reading nonetheless.

---

### Post by raboofje on 2009-09-20
I started [http://wiki.linuxaudio.org/wiki/audio_layers_overview](http://wiki.linuxaudio.org/wiki/audio_layers_overview) , feel free to extend/improve on it.

---

