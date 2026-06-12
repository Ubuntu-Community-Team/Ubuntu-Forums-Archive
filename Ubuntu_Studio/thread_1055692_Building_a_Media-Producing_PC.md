---
title: "Building a Media-Producing PC"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by ShinHadoken on 2009-01-31
What I would like to look into is building a PC completely dedicated to media production, specifically audio recording and editing. I am basing this project on Ubuntu Studio. What sort of hardware would I need, within the PC and outside it (such as soundboards, mixers, etc)? 

Thanks so much for your input!

- Shin Hadoken

---

### Post by ShinHadoken on 2009-01-31
BUMP (in a polite way)

---

### Post by ShinHadoken on 2009-01-31
> **ShinHadoken said:**
> BUMP (in a polite way)
Ditto

---

### Post by ShinHadoken on 2009-02-01
Sorry, don't mean to be a nag here, but I understand how these things can get lost in the shuffle.

---

### Post by thorgal on 2009-02-01
software-wise:
realtime kernel 
audio server: jack audio connection kit -> [http://jackaudio.org](http://jackaudio.org)
multitrack record / editor and more (DAW): Ardour -> [http://www.ardour.org](http://www.ardour.org)
(there are others but less "professional" like e.g. audacity)
sound editors: audacity, rezound, etc. Have a look at [www.linux-sound.org](www.linux-sound.org)
drum machine : Hydrogen -> [www.hydrogen-music.org](www.hydrogen-music.org)
mastering : Jamin
plugins: LADSPA, LV2, DSSI, VST (that one requires WIne, the windows "emulator")
MIDI stuff: Rosegarden, Muse, Qtractor are sequencers.
Sampler: linuxsampler

there is much much more, look again at linux-sound.org

hardware-wise: it all depends on your needs. Many IOs ? The MAudio Delta PCI cards (envy24 chip) are a goood choice. The very pricy but excellent choice (I use one of those) is the RME Hammerfall DSP serie (PCI or PCIe).

Then it's really up to you (mixer board, preamps, h/w effects, filters, etc). Really, you can start first with the PC stuff. Once you're done with the PC part, you can expand with h/w if you feel you need it. That's the cheapest path :)

---

### Post by ShinHadoken on 2009-02-01
Ok, cool. I think what I could do is put a few nice hardrives in there in a RAID 5 array, and then water-cool everything. As far as a sound card goes, I suppose I could do some browsing, just as long as I had one Line In, because I could run everything through a mixer/soundboard. Then it's just a matter of software. I'll do some poking at linux-sound.org, but AFAIK, most everything I'll need is prepackaged in Ubuntu Studio. Thanks for your input thorgal, anyone else?

---

### Post by thorgal on 2009-02-02
I forgot to add:

- linux-sound.org does not replace your package repos. It is just for information, inspiration, etc. Once you spot an app that seems interesting in there, you just apt-get it. It's just that before you apt-get an app, it's nice to read about it on its official website :)

- h/w inside your PC: for pro audio, it is recommended to have your signal converters outside the PC. My RME system uses the IO box called Multiface II, which hosts the converters. It is not subject to interferences with the PC guts (mobo).

- as for cooling, a big Zalman CPU cooler (CNPS9700-Cu or the like) will do the job. It is noiseless, especially inside a well crafted case like the Antech Sonota III. It can accomodate a microATX board. I think ATX would be possible but very tight. The case also comes with an Earthwatts PSU which is very smart and silent. My PC is basically noiseless. Of course, if you want to water-cool your CPU, that's even better. But isn't it a bit pricy ? I'd rather spend the bucks in good mikes, preamps and converters :)

by the way, my DAW specs are posted here (with pics):
[http://linuxmusicians.com/viewtopic.php?f=18&t=101](http://linuxmusicians.com/viewtopic.php?f=18&t=101)

It works nicely. I've been running it for 1.5 year, no problems, very stable and reliable.

---

