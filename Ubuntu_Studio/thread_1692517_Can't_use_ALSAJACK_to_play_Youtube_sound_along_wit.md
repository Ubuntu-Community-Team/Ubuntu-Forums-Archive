---
title: "Can't use ALSA/JACK to play Youtube sound along with virtual instruments"
date: 2011-02-21
forum: Ubuntu Studio
---

### Post by windeguy on 2011-02-21
In Ubuntus Studio 10.04, when I start JACK I cannot hear sound from a Youtube video.  I am trying to play along with some of these videos using Qsynth and other virtual instruments. 

I can play the Virtual Instruments using Jack, just not together with a streaming sound source such as Youtube. 

I have attempted to remove all traces of PulseAudio from my system and strictly use JACK/ALSA. 
When I go to System - Preferences - Sound I get the message "Waiting for Sound System to Respond" without ever seeing it respond.
   
Any suggestions?

---

### Post by Pablo_F on 2011-02-21
The problem is that the flash player is not jack-aware by default. 

There are other tricks, but I personally prefer [this one]("http://www.linuxmusicians.com/viewtopic.php?f=4&t=2323").

The drawback is that you _must_ have jack up and running to hear to youtube videos, myspace, etc. 

For more info and alternatives, google for "jack plugin flash player" and see jackaudio.org faq.

Cheers, Pablo

EDIT: 
> 
I have attempted to remove all traces of PulseAudio from my system and strictly use JACK/ALSA.
When I go to System - Preferences - Sound I get the message "Waiting for Sound System to Respond" without ever seeing it respond.

Then, the link I gave you is the way to go. Sound preferences is a pulseaudio frontend for the gnome desktop. The same happens to me when jack is running (and pulseaudio is dead).

---

### Post by beefheartvliet on 2011-02-21
I have a suggestion for you. It's a little lame, in as much as I didn't solve how to do it in Ubuntu Studio. I Have Dreamlinux. Which is based on Ubuntu. The good thing is, is that that Jack and Pulseaudio run together.  IE: You can watch and listen to a vid on youtube, while playing a synth etc.  I'm sure some more experienced users will be able to help you solve the problem with your existing installation. All I'm saying is, is works for me.  I'm using an M-audio Audiophile 24/96. I hope it helps in some way. Just to say, you can still download from the Ununtu repositories, and do everything else you can do with Ubuntu studio. But with that added Dream of pulse and Jack running together.    It's been a while since I posted here. I'm sure if I was to look at my earlier posts, then they would besound related issues.  Maybe  the next release of Ubuntu Studio should consider adding a 'PulseAudio Jack Sink'. Maybe it will? :-)

---

### Post by windeguy on 2011-02-21
Thank you once again Pablo. Excellent. 
I can now play virtual instruments along with the Youtube/FLash player. 

AND I can also play a YouTube video and hear the audio without having to remember to start JACK. It is true that JACK needs to be running, I checked and JACK is running, but it starts "in the background automagically" when I start a Youtube video.

So far this seems to be a very acceptable situation.

---

### Post by windeguy on 2011-02-21
> **beefheartvliet said:**
> I have a suggestion for you. It's a little lame, in as much as I didn't solve how to do it in Ubuntu Studio. I Have Dreamlinux. Which is based on Ubuntu. The good thing is, is that that Jack and Pulseaudio run together.  IE: You can watch and listen to a vid on youtube, while playing a synth etc.  I'm sure some more experienced users will be able to help you solve the problem with your existing installation. All I'm saying is, is works for me.  I'm using an M-audio Audiophile 24/96. I hope it helps in some way. Just to say, you can still download from the Ununtu repositories, and do everything else you can do with Ubuntu studio. But with that added Dream of pulse and Jack running together.    It's been a while since I posted here. I'm sure if I was to look at my earlier posts, then they would besound related issues.  Maybe  the next release of Ubuntu Studio should consider adding a 'PulseAudio Jack Sink'. Maybe it will? :-)

Thank you also for the response.  For the moment, Pablo's suggestion is working for me.  I had read a lot of threads about Pulse audio eating up CPU cycles and causing delays so I tend to stay with ALSA only solutions if possible.  That said, there may come a time that I am loving a hybrid ALSA/Pulse Audio solution.

---

