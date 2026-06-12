---
title: "pulseaudio or ALSA?"
date: 2008-09-19
forum: Ubuntu Studio
---

### Post by kakyoism on 2008-09-19
For multimedia production usage,
do you guys prefer pulseaudio or ALSA as audio driver?
why?

---

### Post by Stochastic on 2008-09-19
Don't you mean Pulse Audio or ESD?

Or are you asking about ALSA vs. OSS?

These are two distinct audio driver layers - Pulse Audio feeds into ALSA, but some people who have issues with their Pulse Audio setups choose to bypass it and go straight into ALSA.

I personally like the features Pulse Audio adds to my setup.

---

### Post by kakyoism on 2008-09-19
Thanks for the clarification.
So do you mean that I can still modify ALSA and pulseaudio won't prevent me from doing this, or should I always do it through pulseaudio according to its mechanism?

---

### Post by Bios Element on 2008-09-19
Only one device can use a sound device at a time. PulseAudio manages the mixing of several audio streams. So if you 'do' use pure alsa it will be the only thing able to use the soud device while your using it.

---

### Post by eye208 on 2008-09-20
> **Bios Element said:**
> Only one device can use a sound device at a time. PulseAudio manages the mixing of several audio streams. So if you 'do' use pure alsa it will be the only thing able to use the soud device while your using it.
That's nonsense.

---

### Post by thorgal on 2008-09-20
yes, it is not correct. My linux DAW has two soundcards :
- RME HDSP system with external Multiface II IO box
- onboard soundchip that I disabled in the bios because useless

But when the onboard sound was not disabled, I could use both soundcards, e.g. by plugging the output of the onboard card to inputs in the RME Multiface IO box. it was a useful setup at that time because I used the onboard device for flash, system sounds, etc and the RME stuff was using jack for pro audio work. It trimed my DAW later on because I only made it less reliable for pro work with the onboard chip sharing IRQ with the RME card.

The conclusion is : as soon as ALSA supports your devices, they will all available at the same time. Pulseaudio is a sound server layer that (I think) can be configured so that you don't need to see the hardware layer specifics, unlike pure ALSA. But as Stochastic said, pulseaudio NEEDS an audio backend (e.g. ALSA or OSS) that talks to the kernel and your hardware device.

---

### Post by eye208 on 2008-09-20
Bios Element was talking about several applications using **one** soundcard at the same time. This was impossible with OSS, the original sound system of Linux, but it became possible with ALSA. I guess Bios Element was confusing these two.

In fact there is **nothing** in PulseAudio that cannot be done with ALSA and Jack.

---

### Post by markbuntu on 2008-09-21
> **eye208 said:**
> 

In fact there is **nothing** in PulseAudio that cannot be done with ALSA and Jack.

Actually, there is. Pulseaudio will keep two different sound cards in sync. To do that with ALSA and Jack you would need to physically wire their clocks together or buy a pair of Hammersmith or M-Audio 1010 cards.

---

### Post by Stochastic on 2008-09-22
> **eye208 said:**
> In fact there is **nothing** in PulseAudio that cannot be done with ALSA and Jack.
can ALSA be configured to send the audio to a different machine?  Pulse Audio can.

edit: pulse audio also has a sink to send audio out to the jack server (and another that will take inputs from the jack server) - alsa can't do that can it?
edit#2: pulse audio even has a LADSPA sink that will allow any source (i.e. Totem) to be processed through a LADSPA effect before being sent to the output - I'd be quite surprised if alsa has that trick up its sleeve!

---

### Post by Ape3000 on 2008-09-22
I prefer pure ALSA over Pulseaudio.

There is some good sides on Pulseaudio like **OSS-support**, **transfer sound to another Pulse server**, **per application volume manager**, etc, etc..

But there is also bad sides about using Pulseaudio. It has **problems with some applications**, **in some cases the sound quality suffers** and it always **adds a little latency**.

---

### Post by MindFlayer on 2008-09-22
> **Ape3000 said:**
> But there is also bad sides about using Pulseaudio. It has **problems with some applications**, **in some cases the sound quality suffers** and it always **adds a little latency**.

Ditto. I couldn't play any OpenAL games (Alien Arena, Frozen Bubble, etc..) without horrible stutter. SDL games and emulators had way too much latency. Java couldn't play a thing out on my pulseaudio setup. My mic didn't work. Even 5.1 digital audio seemed like too much of a hassle on pulseaudio. Configuring Pulseaudio felt like hell because it's yet another layer on ALSA and OSS which both still had to be tweaked for my purposes. Also, Wine doesn't natively support Pulseaudio so it had to be used via padsp (an OSS wrapper)!

After I switched to ALSA, all of my above problems went away and I'm happily using Ubuntu again! :)

---

### Post by Stochastic on 2008-09-22
Hmm strange that the issue of latency comes up as this is a quote from Pulse Audio's documentation > PulseAudio is intended to provide lower latency than the software mixers dmix and esd.

Am I wrong in assuming that those who have uninstalled pulse audio have then re-installed esd?  (and therefore the latency would theoretically be worse - provided the above quote is true)

Personally I don't game so latency in 'everyday' multimedia viewers isn't an issue, and any time latency would be an issue (recording audio, performances, etc...) I switch to JACK.

I know not every app works perfectly with Pulse Audio yet - it is the new guy on the block still - but with Ubuntu, Fedora, and Mandriva all using it as a default, I'm sure devs on those particular apps are working hard to repair their code.

---

### Post by eye208 on 2008-09-22
> **markbuntu said:**
> Pulseaudio will keep two different sound cards in sync. To do that with ALSA and Jack you would need to physically wire their clocks together or buy a pair of Hammersmith or M-Audio 1010 cards.
No. All I need to do is run Jack on hw:0 (master), then run alsa_client (from the NetJack package) on hw:1 (slave). This will make both cards available in Jack. The slave(s) will be resampled to sync with the master clock.

> **Stochastic said:**
> can ALSA be configured to send the audio to a different machine?  Pulse Audio can.
NetJack can connect two (or more) instances of Jack running on remote machines.

> edit: pulse audio also has a sink to send audio out to the jack server (and another that will take inputs from the jack server) - alsa can't do that can it?
Yes it can. In fact there are two possible ways to do it: using the ALSA Jack sink (which ironically uses the same plugin interface as the ALSA Pulse sink) or using ALSA's loopback driver (snd-aloop).

> edit#2: pulse audio even has a LADSPA sink that will allow any source (i.e. Totem) to be processed through a LADSPA effect before being sent to the output - I'd be quite surprised if alsa has that trick up its sleeve!
See above. Once the audio is in Jack, you can route it through Jack-Rack to apply LADSPA effects.

---

### Post by Stochastic on 2008-09-22
> **eye208 said:**
> Yes it can. In fact there are two possible ways to do it: using the ALSA Jack sink (which ironically uses the same plugin interface as the ALSA Pulse sink) or using ALSA's loopback driver (snd-aloop).
<snip> Once the audio is in Jack, you can route it through Jack-Rack to apply LADSPA effects.

Wow, sounds like it might be easier and more intuitive (maybe even faster) to add the effects ahead of time via audacity, then play them in totem. :)

I'm going to stop myself now, as my bias is clearly showing and I'm getting a little too cheeky.

How long has alsa-jack been around?  I've heard very little about it before now.  Can you post any good explanation sites on the matter?

---

### Post by markbuntu on 2008-09-22
Many people have tried the alsa-jack sink. The biggest complaint was that not all their applications could use it. The pulse-jack sink seems to work with more applications. 

The netjack workaround seems to make two sound cards available for jack but how do you switch applications between the cards and how do you get one application to use one card and another app to use the other card?

I route my players through the jack sink to ardour then into jack rack and back through ardour so I can more easily control the mixing of the original and the effects.

This has become a good exchange of information here. I will try testing some of these things soon and if they work without too much difficulty, I will add them to my guide. Does anyone know if the new alsa version adds any functionality to these items we are discussing?

---

### Post by thorgal on 2008-09-22
> **markbuntu said:**
> 
I route my players through the jack sink to ardour then into jack rack and back through ardour so I can more easily control the mixing of the original and the effects.


you could avoid the overhead of jack-rack (GUI) by using ardour sends ;)

---

### Post by markbuntu on 2008-09-22
> **thorgal said:**
> you could avoid the overhead of jack-rack (GUI) by using ardour sends ;)

I suppose I could, but I have barely scratched the surface of ardour. Next time I have it setup that way, I will try to figure that out but I kind of like having the jackrack gui hanging around so I can fool with stuff.

---

### Post by kakyoism on 2008-09-22
Wow, this post has been so informative to a newbie like me...
Sorry for asking another stupid question.
What is sink?
Is it, quoted from Wikipedia at
[http://en.wikipedia.org/wiki/Sink_(disambiguation)]("http://en.wikipedia.org/wiki/Sink_(disambiguation)")
this:
 sink (computing), in software engineering, an object implementing the event interface to receive incoming events

Meaning that pulseaudio or other similar servers prepare a sink for any audio applications that send requests to them?

---

### Post by markbuntu on 2008-09-22
Yes, that's exactly what they do.

---

### Post by Stochastic on 2008-09-25
> **Stochastic said:**
> How long has alsa-jack been around?  I've heard very little about it before now.  Can you post any good explanation sites on the matter?

Anyone? 
(to clarify, I was referring to the ALSA Jack sink that eye208 mentioned)

I find it ironic that google pointed me to: [http://ubuntuforums.org/showthread.php?t=158758](http://ubuntuforums.org/showthread.php?t=158758) on the matter (a search for alsa-jack).

---

### Post by eye208 on 2008-09-25
> **Stochastic said:**
> Anyone? 
(to clarify, I was referring to the ALSA Jack sink that eye208 mentioned)

I find it ironic that google pointed me to: [http://ubuntuforums.org/showthread.php?t=158758](http://ubuntuforums.org/showthread.php?t=158758) on the matter (a search for alsa-jack).
[http://alsa.opensrc.org/index.php/Jack_%28plugin%29](http://alsa.opensrc.org/index.php/Jack_%28plugin%29)

The Jack plugin for ALSA has been around for a long time, but it has been deliberately left out of Ubuntu because, you know, there was no room left on the discs. Interestingly, when PulseAudio came along, all disc space problems suddenly vanished.

Compare these:
[http://packages.debian.org/etch/libasound2-plugins](http://packages.debian.org/etch/libasound2-plugins)
[http://packages.ubuntu.com/hardy/libasound2-plugins](http://packages.ubuntu.com/hardy/libasound2-plugins)

---

### Post by Stochastic on 2008-09-25
> **eye208 said:**
> [http://alsa.opensrc.org/index.php/Jack_%28plugin%29](http://alsa.opensrc.org/index.php/Jack_%28plugin%29)

The Jack plugin for ALSA has been around for a long time, but it has been deliberately left out of Ubuntu because, you know, there was no room left on the discs. Interestingly, when PulseAudio came along, all disc space problems suddenly vanished.

Compare these:
[http://packages.debian.org/etch/libasound2-plugins](http://packages.debian.org/etch/libasound2-plugins)
[http://packages.ubuntu.com/hardy/libasound2-plugins](http://packages.ubuntu.com/hardy/libasound2-plugins)

Hmm, am I correct in understanding that this needs a new configuration file (or at least a revision) every time the plugin is turned on/off (i.e. everytime jack starts/stops)?  That alsa site really doesn't speak english, it speaks alsa.

It's not left out of the libasound2-plugins in ubuntu, just take a look at the source of that package.  At first you led me to think it was simply because the libjack dependency listing isn't in the ubuntu package, but the plugin is in the tar.gz file.

---

### Post by eye208 on 2008-09-25
> **Stochastic said:**
> Hmm, am I correct in understanding that this needs a new configuration file (or at least a revision) every time the plugin is turned on/off (i.e. everytime jack starts/stops)?  That alsa site really doesn't speak english, it speaks alsa.
The Jack plugin works just like the Pulse plugin. So I guess whatever happens to the ALSA-Pulse sink when PulseAudio is suspended will happen to the ALSA-Jack sink when Jack is not running.

The good thing about ALSA is that most of its configuration resides in $HOME. You can use asoundconf-gtk to switch between configurations.

> It's not left out of the libasound2-plugins in ubuntu, just take a look at the source of that package.
The source is available, but the binary is not. See bug [#84900](https://bugs.launchpad.net/ubuntu/+bug/84900).

---

