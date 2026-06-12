---
title: "no sound in new ubuntu studio 8.04 install"
date: 2009-02-01
forum: Ubuntu Studio
---

### Post by le_vainqueur on 2009-02-01
I just did a fresh install of Ubuntu Studio 8.04, and I performed all of the updates.  There is presently no sound coming out of my speakers, however.  I do not know if it was working before the updates or not since I didn't try at all.  

I want to use this machine to record audio in Audacity/Ardour, so my understanding is that I need to use ALSA to get this working properly.  When I test ALSA in the sound preferences I get the following error

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I couldn't find a solution in my searches.  If you could help me out, I would greatly appreciate it.


LV

---

### Post by le_vainqueur on 2009-02-01
UPDATE:

When I try to run the ALSA mixer, I get a window that says:

> alsamixer: function snd_ctl_open failed for default: No such file or directory

---

