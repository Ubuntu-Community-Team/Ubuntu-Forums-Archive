---
title: "physical MIDI ports and jack"
date: 2009-03-04
forum: Ubuntu Studio
---

### Post by rafafredd on 2009-03-04
Hi. I have a RME DIGI9636 card, and I want to know how can I make my physical MIDI ports in the card appear in the ALSA tab of Qjackctl, so that I can actually connect it to the sequencers and synths. I read I should use "seq" for midi driver in jack configuration, but nothing changes no matter if I use seq, raw or (none) as a MIDI driver in the jack setup window... The physical MIDI ports of my sound card only appears in the MIDI tab of jack, not in the ALSA tab, so I can't really connect it to any synth or sequencer in my system...

How should I proceed? Searched a lot, and nothing yet...

How do you guys actually use MIDI keyboards and other external MIDI devices/peripherals in linux???

By the way, Hardy Heron here, and alsa working with my RME soundcard just fine. I can even record 18 channels of simutaneous audio tracks in Ardour with low latency (like 4ms) in my very old Athlon 1700+ system. :D Only can't connect (to and from) any of the physical MIDI ports in my card...

Any help VERY appreciated...

---

### Post by thorgal on 2009-03-04
you got the logic reversed:

the seq option is for jack, not ALSA, so what you see is an expected correct behavior of qjackctl. 

For ALSA, make sure you have modules loaded:

lsmod | grep seq

if something pops up, you should be fine. Otherwise, you'll have to load these kernel modules

---

### Post by raboofje on 2009-03-04
> **rafafredd said:**
> The physical MIDI ports of my sound card only appears in the MIDI tab of jack, not in the ALSA tab, so I can't really connect it to any synth or sequencer in my system...

To connect JACK MIDI and ALSA MIDI applications/ports you can use [http://home.gna.org/a2jmidid/](http://home.gna.org/a2jmidid/)

---

### Post by Steve H on 2009-03-07
I'm having a similar problem getting an Audiophile 2496 to play nice with a generic MIDI keyboard. It doesn't seem to connect and no matter what I do I can't use my physical keyboard. I've tested it with the virtual MIDI keyboard and it works, as soon as I connect it to the Audiophile , nothing.

There must be a way round this...

:(

---

