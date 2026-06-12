---
title: "Delta 44 audio artefact"
date: 2010-02-16
forum: Ubuntu Studio
---

### Post by Stason on 2010-02-16
My Delta 44 output gets choppy with intensive audio streams. It sounds that the stutter affects only 1-2kHz band, but this is subjective. 

I killed Gutsy 7.10 and installed Lucid 10.04 A2 to get the latest kernel and alsa drivers. It did not help. Tried to tweak those pulseaudio "fragment" settings, put it into high priority. Nothing worked - the audio still stutters.

At this point I am seriously considering throwing away the Delta card.

Is there anything I can try to fix this? Any directions on where to look would be appreciated.

---

### Post by Stason on 2010-02-18
bump

---

### Post by Stason on 2010-02-19
Weirdly enough, one of the following actually put things in order (I did it simultaneously - therefore I don't know which one helped):

1. Change PCI slot the card is installed into
2. Enable built-in audio! Yes, it works when the built-in chip is set to AUTO rather than to Disabled.

---

