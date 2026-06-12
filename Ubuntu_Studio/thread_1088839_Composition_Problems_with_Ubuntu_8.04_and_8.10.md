---
title: "Composition Problems with Ubuntu 8.04 and 8.10"
date: 2009-03-06
forum: Ubuntu Studio
---

### Post by Gazok on 2009-03-06
I recently wiped XP off of my old computer and put Ubuntu on it instead. I've been pretty happy so far, but audio seems to be a major problem, and I don't know enough to even analyse it, let alone fix it.

Audio editors like Audacity and Audigy refuse to work without the JACK server running. Running the JACK server promptly breaks all sound output.

MuseScore will make sound now that I've installed the Ubuntu soundfont package through Synaptics, but for some reason I can't place notes.

Rosegarden refuses to output MIDI (I haven't tried audio, as it requires the JACK server), although I may just be doing something wrong.

I've installed linux-rt 2.6.24, because I was getting the System Timer Resolution too low on 8.10, but I've now reverted back to 8.04, so I don't know if it's necessary any more.

---

### Post by Gazok on 2009-03-08
Apologies for bump

---

### Post by thirdspace on 2009-03-09
The first step is to get the Jack audio server working. You cannot get far with music creation on Linux until Jack is solid on your hardware. Use qjackctl to experiment with different Jack settings. Search the web for advice on what works with your particular audio device. And for what it's worth, audacity on Ubuntu has never worked reliably for me, I use ardour even though I do not really like its user interface.

---

### Post by Gazok on 2009-03-09
Heh, funny thing: I meant Ardour, and it didn't work on 8.10 either, and I didn't try it on 8.04. It actually works :D.

Still no JACK audio server in Rosegarden, though. Audacity throws an error: "Error while opening sound device. Please check the output device settings and the project sample rate" at every sample rate, so I assume that's JACK related as well.

---

