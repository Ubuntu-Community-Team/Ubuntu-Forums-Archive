---
title: "cluster recording using one control interface"
date: 2012-11-21
forum: Ubuntu Studio
---

### Post by FishRCynic on 2012-11-21
have searched but have not found an answer to/for this.

would like a control interface on one machine that would start the recordings simultaneously on the others.

what i am doing:
multi track record (rather than mix down to stereo on one computer) on a cluster of amd64 machines (up to 5).
for example vocal, acoustic mike, electric guitar, electric bass
and mixed down drum kit recorded simultaneously on separate
computers handling each track separately.
allows a live performance to be mixed after that fact

i can do this manually but syncing after the fact is a little annoying.

the tracks would then be moved to one machine for post editing
and mixing with the sync being trivial

---

### Post by Takanakathehacker on 2012-11-22
> **FishRCynic said:**
> have searched but have not found an answer to/for this.

would like a control interface on one machine that would start the recordings simultaneously on the others.

what i am doing:
multi track record (rather than mix down to stereo on one computer) on a cluster of amd64 machines (up to 5).
for example vocal, acoustic mike, electric guitar, electric bass
and mixed down drum kit recorded simultaneously on separate
computers handling each track separately.
allows a live performance to be mixed after that fact

i can do this manually but syncing after the fact is a little annoying.

the tracks would then be moved to one machine for post editing
and mixing with the sync being trivial

Dude you certainly seem to be approaching this in a complicated way.

If it was me, i'd just get an external soundcard/interface with multiple line/xlr ins/outs, (can be used in standalone mode as well as hooked up to computer) I'm familiar with a sapphire pro/focusrite 8-track personally, (probs need a firewire/usb 3.0 port is all), and record from your multiple sources that way. 

Ideally into windows/cubase, but i suspect with a bit of research/tatting it can be done on audacity. 

But yeah if you have 5 computers dude, sell 4 and get a half-decent soundcard lol. ;)

Getting an AD convertor which is in essence what the saffire pro is (or motu 828 or whatever ya want ;), is useful because as you say it allows you to take each channel as a seperate entity when using your DAW (need a half-decent machine if your gonna go all out with high-def audio/plug-ins e.t.c) and you can do whatever effects/process on each individual track.

But yeah defo look into external soundcards like the saffire pro or motu imho dude.

---

### Post by CrocoDuck on 2012-11-22
Hi. I think that a way to do what you have in mind probably exist, but probably is one of the hardest ways to record simultaneously a lot of tracks (and probably is practicable without losing in general audio quality only if you have all the 5 computer's audio performances fully identical). I recommend to follow the Takanakathehacker's advice, here a suggestion for a soundcard you may like:

[http://www.m-audio.com/products/en_us/Delta1010LT.html](http://www.m-audio.com/products/en_us/Delta1010LT.html)

It should be compatible with ALSA [http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio) and work under linux. Sometimes a way to use multiple devices exists, as the ALSA driver is deeply configurable. Here some info to use 2 delta 1010 ([http://www.m-audio.com/products/en_us/Delta1010.html](http://www.m-audio.com/products/en_us/Delta1010.html)) [http://www.ilovemyjournal.com/?action=view_entry&eid=4773](http://www.ilovemyjournal.com/?action=view_entry&eid=4773). As always, buy new hardware only if you are basically sure about his compatibility or if you have a concrete idea on how to workaround possible issues.

---

### Post by FishRCynic on 2012-11-22
thanks i thought as much

---

### Post by bumBumBUM on 2012-11-22
actually it is possible if the computers are networked and running jack thanks to the 'netjack' function.

[http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack](http://trac.jackaudio.org/wiki/WalkThrough/User/NetJack)

latency isn't necessarily an issue if you have a fast enough network apparently (the link i provide suggests only 2Mbit/sec bandwidth per 48khz channel)... For multiple connections you just need a router but to connect two computers you only need a cross over cable (modified ethernet cable). It should even work with an apple computer as long as they have jack running and it's configured with the correct parameters. You have one master and several slaves so there is really only one audio interface that provides the metering - as I understand it, the signal from the slaves is taken as it comes and is delivered in a buffered stream. The slave's signal should then appear as a regular input in qjackctl's connections window on the master. Sounds pretty cool I think.

Anyway, my band is too poor to buy extra equipment so I have been looking into stuff like this. I can't recommend it or not myself as I'm still learing about it and have yet to implement it but it is possible (may be a bit complicated/technical for some though). Plenty of people can afford a cheap netbook but not dedicated recording equipment so I like the idea that each musician can be in charge of there own sound with their computer and instrument, then they just send their signal to the master.

If you can afford it though, perhaps the easy route of buying the hardware is best :D

PS> If you do go for it 'manually', you can probably sync the tracks by making sure every one plays a synchronized marker sound at the start and at the end of the track. Then you can line up the tracks more easily and guage how much they are squashed or stretched by the different metering from each interface by comparing the end sound. Sounds like too much work to me though.

---

