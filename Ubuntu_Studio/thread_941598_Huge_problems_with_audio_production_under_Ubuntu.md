---
title: "Huge problems with audio production under Ubuntu"
date: 2008-10-08
forum: Ubuntu Studio
---

### Post by teel on 2008-10-08
Hi there!
First of all: I've been using Linux since 1999 and I'm familiar with it quite well (at home only Linux). Apart from being an IT engineer I also play music on my own, since 1992. Being both amateur musician and IT engineer cannot accept what people say that Linux is usable as music production environment.

Ok, so what's the problem? Installed Ubuntu Studio to have a full environment. Hardware: 1.6GHz Athlon, Audigy2 ZS, 1.5GB RAM.

First of all: latencies are killing me!!! I set up JACK with or without RealTime option, nothing. 100ms of latency playing a piano (MIDI keyboard) is way too much.
Ok, screw latencies. But the JACK lots of times causes my computer to total freeze, nothing but hardware reset helps.
If it works like don't freeze it doesn't work: something stops the daemon.

Rosegarden is maybe a good software but a month is not enough to set up a STABLE environment.

Ok, next: simple software synthesizers or SoundFonts are not clean at all. Something causes you can hear distinct statics (cracks, crancles, hard to call it ;).

Ok, yesterday I just gave up. 10 years of using only Linux!!!!! 10 years of laughing on M$ users with their slavery to Window$ and what I have finished like?
I took my wife's laptop (Celeron, 512MB RAM) with Windows XP Home, an ordinary china-production-low-end sound card (sound MAX or sth like that, who cares), downloaded FL Studio 8 Demo and what? Perfect clean sound, no crancles, no cracks, just a beautiful Grand Piano sounds. Latencies? What are they? Just like playing real piano. Stability: 100%.

Sorry guys, Linux sucks when it comes to sound (don't know nothing about other multimedia applications). Still have Ubuntu exclusively installed at my desktop PC and love it, but probably I have finished lying to myself that it's good for music production. I't obviously not and I'm not happy with it.

Regards,
teel

---

### Post by thorgal on 2008-10-08
in the end, you can produce your music, that's what counts. However, I have an experience that is 180 deg from yours, my linux DAW really works, is stable, latency is nothing, and I can do what I want, which depends on the music style I am developing (rock). If it was not so, I would look for an alternative. But as much as you are disappointed about linux audio, I must say I am fully satisfied by my setup :) So the world is not black and white ;)

---

### Post by Prefader on 2008-10-08
I'm going to venture a guess that your computer that gave you so much trouble with audio is housing a VIA chipset.

Twice in my life I've tried to use VIA chipsets in DAWs, both running Windows XP, and both times ended in utter and complete failure - dropouts, pops/clicks, and hard crashes.  I'm now using an NVidia (nforce4) chipset in my desktop, and an Intel (855) chipset in my laptop, and everything is fantastic.

Linux may not be the problem here, but you probably don't have enough data to rule it out yet.

---

### Post by teel on 2008-10-08
> **thorgal said:**
> in the end, you can produce your music, that's what counts. However, I have an experience that is 180 deg from yours, my linux DAW really works, is stable, latency is nothing, and I can do what I want, which depends on the music style I am developing (rock). If it was not so, I would look for an alternative. But as much as you are disappointed about linux audio, I must say I am fully satisfied by my setup :) So the world is not black and white ;)

Great to hear, really. Could you please share the info about your DAW setup? What computer, soundcard, how did you set up the JACK, what drivers (ALSA, OSS, some other?), what applications? 

I also play rock and what I basically need is:
- SoundFont (SF2) support
- stage piano support (working actually as a midi keyboard)
- drummachine (Hydrogen: nothing more needed, if each application was so incredible..)
- multitrack recording (Ardour seems to be more that I need).

The main problem I see is not the application itself, it's the basic sound setup which I was talking about.

Regards,
teel

---

### Post by thorgal on 2008-10-08
you can find a description of my setup here :

[http://linuxmusicians.com/viewtopic.php?f=18&t=101](http://linuxmusicians.com/viewtopic.php?f=18&t=101)

I am using a debian sid OS, compiled my own RT kernel (2.6.24.3-rt3), set up the security for RT access, disabled a lot of useless things (graphical 3D acc, even 2D acc, some services that are irrelevant, etc), tweaked the IRQ thread priorities, among other things. Just kept what was needed for the OS to function and the audio to have the priority over other stuff (network, graphics, USB, whatever). It's a DAW, nothing else. And I invested in RME gears, very good investment!

by the way, I am of course using jackd with the alsa backend. The alsa driver is snd-hdsp. I have nothing to do with OSS, disabled the OSS emulation. I sometimes use oss2jack as a fooling trick for oss aware apps that don't understand jack natively (flash player, or gwc, the gnome-wav-cleaner) but I rarely do that. It's just a jack. 
I have saved a few different setups in qjackctl : 
RT mode with 64 frames / period, 2 periods per buffer which I use sort of rarely, I don't use dynamic software FX in realtime
Lazy mode : 1024 frames / period, 2 periods / buffer which I most of the time use (no need of low latency, I have h/w monitoring with the RME TotalMix mixer)
A medium setup at 256 frames / period, good compromise between real RT and lazy.

All this at a sample rate of 96kHz, so the latency reported is half the one at 48kHz. The lazy mode gives me 10.7ms. Honestly, low latency is only used when I play the piano. I use a VSTi called Pianoteq for that (great stuff!), and the medium mode is good enough for realtime feel.

---

### Post by cb951303 on 2008-10-08
for me it works great. I can play my guitar through it and record dry signal. but to process the signal I need to switch to windows since all the great modeling softwares (AT, RV, GR3) are for win and mac :/

---

### Post by teel on 2008-10-08
> **cb951303 said:**
> for me it works great. I can play my guitar through it and record dry signal. but to process the signal I need to switch to windows since all the great modeling softwares (AT, RV, GR3) are for win and mac :/

Yes, they are. And guess why: because Linux has tons of libraries, interfaces and so on. Besides we as Linux users are unfortunately circa 5% or even less of grand total computer users. No one wants to spend money fighting with APIs they don't have traversed, they prefer areas they have already been and this is not strange.

Regards,
teel

---

### Post by cb951303 on 2008-10-09
> **teel said:**
> Yes, they are. And guess why: because Linux has tons of libraries, interfaces and so on. Besides we as Linux users are unfortunately circa 5% or even less of grand total computer users. No one wants to spend money fighting with APIs they don't have traversed, they prefer areas they have already been and this is not strange.

Regards,
teel

All the softwares I mentioned before come also as VST plugins. Linux supports VST natively. All they need to do is to use a cross-platform GUI toolkit. ReValver uses wxWidgets for example. But still there is no native linux version. All I'm saying, since these software companies already do cross-platform dev (MAC and WIN) it shouldn't be very hard for them to support linux. But I agree with you on the user population argument. They probably don't see linux users as potential clients.

PS: I would like to share some programming ideas of mine about modeling softwares for linux if there is audio engineers around here. (Since I don't know much about audio engineering I would like to ask them a few questions before making stupid statements :))

---

### Post by eye208 on 2008-10-09
> **teel said:**
> First of all: latencies are killing me!!! I set up JACK with or without RealTime option, nothing. 100ms of latency playing a piano (MIDI keyboard) is way too much.
Ok, screw latencies. But the JACK lots of times causes my computer to total freeze, nothing but hardware reset helps.
If it works like don't freeze it doesn't work: something stops the daemon.
I think there is a problem with your Jack configuration. My latency is 8ms with a standard HDA onboard audio device. No freezes, no crashes, no glitches.

I agree with you regarding the quality of audio applications. Rosegarden looks promising but lacks basic features such as plugin automation. Ardour's MIDI support is still in development. LMMS is crash-prone. None of them can replace Cubase, Logic or Sonar.

However the foundation (ALSA/Jack) is solid. What we need is support from commercial application developers.

---

### Post by teel on 2008-10-09
> **eye208 said:**
> I think there is a problem with your Jack configuration. My latency is 8ms with a standard HDA onboard audio device. No freezes, no crashes, no glitches.

Could you please share your exact JACK settings?

teel

---

### Post by cb951303 on 2008-10-09
this is achieved with an on board card: [http://ubuntuforums.org/attachment.php?attachmentid=70166&stc=1&thumb=1&d=1210852675](http://ubuntuforums.org/attachment.php?attachmentid=70166&stc=1&thumb=1&d=1210852675)

this one is achieved with a cheap usb behringer card: [http://ubuntuforums.org/attachment.php?attachmentid=71520&stc=1&thumb=1&d=1211718505](http://ubuntuforums.org/attachment.php?attachmentid=71520&stc=1&thumb=1&d=1211718505)

see the 2nd post in this thread. I explain exactly what to do to set up jack properly: [http://ubuntuforums.org/showthread.php?t=806730&highlight=jack](http://ubuntuforums.org/showthread.php?t=806730&highlight=jack)

---

### Post by teel on 2008-10-09
> **cb951303 said:**
> this is achieved with an on board card: [http://ubuntuforums.org/attachment.php?attachmentid=70166&stc=1&thumb=1&d=1210852675](http://ubuntuforums.org/attachment.php?attachmentid=70166&stc=1&thumb=1&d=1210852675)

this one is achieved with a cheap usb behringer card: [http://ubuntuforums.org/attachment.php?attachmentid=71520&stc=1&thumb=1&d=1211718505](http://ubuntuforums.org/attachment.php?attachmentid=71520&stc=1&thumb=1&d=1211718505)

see the 2nd post in this thread. I explain exactly what to do to set up jack properly: [http://ubuntuforums.org/showthread.php?t=806730&highlight=jack](http://ubuntuforums.org/showthread.php?t=806730&highlight=jack)

Thumbnails are too small to see anything, could you please send bigger ones?

---

### Post by cb951303 on 2008-10-09
oops sorry about that 

behringer sound card: [http://ubuntuforums.org/attachment.php?attachmentid=71520&d=1211718505](http://ubuntuforums.org/attachment.php?attachmentid=71520&d=1211718505)

onboard one: [http://ubuntuforums.org/attachment.php?attachmentid=70166&d=1210852675](http://ubuntuforums.org/attachment.php?attachmentid=70166&d=1210852675)

---

### Post by eye208 on 2008-10-09
> **teel said:**
> Could you please share your exact JACK settings?
See attachment.

---

### Post by teel on 2008-10-09
> **eye208 said:**
> See attachment.

Thanks all of you, I'll try it and see the results.

teel

---

### Post by teel on 2008-10-13
Great news, Linux does not suck so much :)

I've found the source of my problems: lmms application. It is not mature enough to be used yet, so for SF2 support I use fluidsynth+qsynth.

But not everything works right. I still hear crancles and other audio artifacts while playing. It is connected with those messages ofjack:

**** alsa_pcm: xrun of at least 5.396 msecs
00:05:52.760 XRUN callback (1 skipped).
**** alsa_pcm: xrun of at least 5.073 msecs
**** alsa_pcm: xrun of at least 9.708 msecs
**** alsa_pcm: xrun of at least 11.446 msecs
**** alsa_pcm: xrun of at least 10.558 msecs
**** alsa_pcm: xrun of at least 6.746 msecs
00:05:54.526 XRUN callback (72).
**** alsa_pcm: xrun of at least 5.385 msecs
**** alsa_pcm: xrun of at least 11.741 msecs
00:05:54.765 XRUN callback (6 skipped).
**** alsa_pcm: xrun of at least 6.706 msecs
**** alsa_pcm: xrun of at least 10.969 msecs
00:05:56.828 XRUN callback (76).
**** alsa_pcm: xrun of at least 77.328 msecs
00:05:57.030 XRUN callback (2 skipped).
00:05:58.907 XRUN callback (77).
**** alsa_pcm: xrun of at least 68.197 msecs

Each time the crancle is emited I get this "xrun of at least 68.197 msecs" notice. I wonder how to get rid of it. Do you gyus have any idea?

Regards,
Tomek

---

### Post by teel on 2008-10-13
OK, almost found what it's going all about: [http://alsa.opensrc.org/index.php/Xruns](http://alsa.opensrc.org/index.php/Xruns)
This is what I really get, now I have to find the soulution.

Tomek

---

### Post by robeast on 2008-10-13
I was a mere novice user when I started fiddling with Linux audio apps--now I'm a novice++. It took me a very long time to 
a) figure out what I even needed 
b) resolve dependencies
c) get any sound
d) get high quality sound with a low latency
e) patch things together
f) learn ~10 different programs
g) find my favorite LADSPA plugins
h) switch to 64studio because it is more stable for computer...of course this warranted doing some of the list over again.

Multimedia production seems much less developed than other areas of Linux and I don't find it at all surprising that a seasoned linuxair would be perturbed by its hurdles. I have found that it is well worth the patience required to find the right setup. Once you get a stable recording environment you will be having a great time discovering its capabilities. Don't get too caught up in it though, because then you won't be spending any time recording!

---

### Post by robeast on 2008-10-13
> **teel said:**
> OK, almost found what it's going all about: [http://alsa.opensrc.org/index.php/Xruns](http://alsa.opensrc.org/index.php/Xruns)
This is what I really get, now I have to find the soulution.
Tomek

Ah yes, I am well acquanted with those...have you tried messing around with your frames/periods and period/buffer? I've read what they technically do, but that did not help me understand how their relationships affect my sound quality, so it's been pretty much guess and check for me. Also try 41000 for the sample rate, maybe your sound card is just crap on 48000? You didn't mention if you are running a realtime kernel...are you?

---

### Post by teel on 2008-10-14
> **robeast said:**
> Ah yes, I am well acquanted with those...have you tried messing around with your frames/periods and period/buffer? I've read what they technically do, but that did not help me understand how their relationships affect my sound quality, so it's been pretty much guess and check for me. Also try 41000 for the sample rate, maybe your sound card is just crap on 48000? You didn't mention if you are running a realtime kernel...are you?

Yes, the distro is UbuntuStudio 8.04 with realtime kernel. Soundcard is SoundBlaster Audigy 2 ZS (SB0350) ([http://www.digit-life.com/articles2/creative-audigy2-zs/index.html](http://www.digit-life.com/articles2/creative-audigy2-zs/index.html)) wchich is maybe not a studio card but not a crappy one.

---

### Post by cb951303 on 2008-10-14
you can avoid xruns with properly setting frames and periods. also unchecking "monitor" might help (if you don't need it)

---

### Post by babarosa on 2008-10-14
Hi teel and the others!

Every time i hear problems with jack (latencies and crackling sound) i give the following advice, please forgive me if you already checked the following suggestions:

I am using Xubuntu, so if you use Ubuntu replace "mousepad" with "gedit":

sudo mousepad etc/security/limits.conf

add to the end of the file:

@yourname - rtprio 70
@yourname - memlock 700000
@yourname - nice -10 

In the settings menu of qjackctl do NOT set priority value (let the (default)-value).
Start with 64 Frames/Period, 44.1 KHZ and 4 Buffers, then try to reduce values.
Additionally consider to compile jack and qjackctl by yourself.

_My personal opinion is:_
I started to work with linux 1 1/2 year ago so i am not very experienced, but i am a professional user of computer music products (music production for tv and radio shows, advertising industry, cultural events).
Linux is in the state as windows was 1995 (cakewalk 9 era) but the development is immense.
I miss system exklusive administration (sound editors like sounddiver) and general stability of programs (i compile them all by myself).
Additionaly i use a firewire interface which works very well thanks pieter palmer's ffado but every now and then i face problems until ffado works again.
it is not possible to use linux neither if a customer sits besides you waiting for his production nor on live recording sessions.

BUT I LIKE IT VERY MUCH (appearance, ...)

Regards, Michael

---

### Post by rybec on 2008-10-14
I have two computers with rosegarden and other audio applications.  My laptop works fine, but my desktop has major issues.  I think the problem is either with jack and the sound card, or the combination of soundcard/motherboard and/or other components(some hardware combinations don't play friendly).

With high sensitivity applications (like real-time audio for instance), issues like this can arise that would never have made a difference with less intensive applications.  That said, one of these days I am going to boot my desktop from a dyne:bolic live cd and see how it fares.  It might just be how the OS is setup.

My laptop is using regular Ubuntu, with the realtime kernel as a boot option (I only use it for audio production, because I have other software on the computer that fights with the realtime kernel).  The desktop (the one with the problems) is running Debian 4.0 with KDE.  It works good for everything, except Jack.

I would recommend trying a live cd for another media distro.  (I like dyne:bolic for this, because it is made to run exclusively from the CD.)  If the other distro works fine, then the problem is either a general configuration problem (good luck figuring that out) or a problem with the kernel build configuration.

Anyway, I hope this offers a decent explanation of the cause of the problem, as well as a possible solution (or at least a diagnosis).

---

### Post by rayj on 2008-10-19
Forgive me if you already know and are doing this, but starting your applications via the terminal will give you all the information you will likely need to hunt down your issue. I'm a relative newbie to linux, but have managed to solve numerous problems through the debugging data you get in the terminal. This *might* be one of the things that make linux great...

---

