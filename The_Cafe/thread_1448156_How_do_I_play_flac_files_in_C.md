---
title: "How do I play flac files in C?"
date: 2010-04-06
forum: The Cafe
---

### Post by dragos240 on 2010-04-06
I'm making a simple program that writes the lyrics of "still alive" in a terminal in sync with the song, and so far it's a HUGE SUCCESS..... it's pretty hard to overstate my satisfaction...... anyway, how can I play flac files in C? What headers do I have to import, and how do I signal it to play?

---

### Post by falconindy on 2010-04-06
looks like you'll need to import FLAC/stream_decoder.h (and who knows what else). To play the stream once its decoded, just find the user's audio device (maybe /dev/dsp?) and write to it. Maybe look at MPD's code for ideas?

---

### Post by Laterix on 2010-04-06
I suggest to use gstreamer framework. Makes it a whole lot easier.

---

### Post by schauerlich on 2010-04-06
First result in google search for "flac c library":

[http://flac.sourceforge.net/api/index.html](http://flac.sourceforge.net/api/index.html)

---

