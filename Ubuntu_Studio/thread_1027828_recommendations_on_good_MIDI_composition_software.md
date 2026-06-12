---
title: "recommendations on good MIDI composition software?"
date: 2009-01-01
forum: Ubuntu Studio
---

### Post by comet on 2009-01-01
Hey guys! Happy new years to you all! 

I just purchased an M Audio 88-key digital piano that has a built in USB MIDI interface. I've heard some good response on people using USB MIDI keyboards in Linux and thought I'd give it a shot.

I'm simply looking for a good MIDI program that will interact with my keyboard and give me the opportunity to use a notation editor and print out the sheet music.

I figure if I can at least get something to actually record the MIDI data, I could always use a different program as a notation editor and for printing the sheet music.

I've used Rosegarden in the past, but never had much luck with it, and had it crash very frequently. I'm open to any suggestions.

Thanks so much for your help!

---

### Post by barisurum on 2009-01-03
I use rosegarden (1.7.2 version from getdeb) for this purpose because it does:

Midi step recording
Midi realtime recording
Advanced quantization (can be frustrating at first but you get used to it)
Near WYSIWYG notation editing compatible with lilypond score engraver
Drum editor
Score editor
Matrix editor all with midi attribute automation

So believe me rosegarden is the software you want. If you want a good metronome (rosegarden doesn't have a built in metronome sound) plug ardour to rosegarden via midi, sync them (make ardour time master and select JACK as sync source in ardour) and use ardour's metronome.

---

