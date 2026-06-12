---
title: "Noise removal, without sacrificing sound quality"
date: 2009-09-29
forum: Ubuntu Studio
---

### Post by SoylentSteak on 2009-09-29
I'm trying to remove noise from my demo recordings, but both Audacity and wave cleaner can't get the job done without making what's left sound poor. I'm using a a guitar tone with a lot of gain. Noise removal easily gets rid of all the noise, but it makes my tone sound a lot thinner. Is there any way to clean up at least some of the noise without affecting tone?

---

### Post by solarbird on 2009-09-30
What kind of noise are you trying to remove? That matters.

I mean, if you're just trying to get silent parts of the recording to be silent, you want a gate filter. That'll leave your high-signal portions alone, and sure, the noise will still be there, but it'll be lost in the guitar.

Also, you're always best off if you can remove noise in the recording processes, not after recording. Any alteration/filtering/and so on will affect your signal, so you want to avoid such things if possible.

---

### Post by kayosiii on 2009-09-30
Its easy you just need to break the laws of physics :p
Failing that - throw out the old material and record again.

Think about what you are asking here for a second. noise remove works by sampling a piece of audio with no signal in it to figure out what is signal and what is noise. In your noise sample some of the noise is going to correspond to your useful signal in terms of frequency, period etc. In this case how is the audio figure out that this particular frequency is in fact signal - It's really not possible to do with 100% accuracy. If you use a noise reduction filter you are going to loose some of your original signal.
Having as good a noise sample as possible will give you better results.

I guess you want some practical advice
This is what I do to get the best results.... make a copy of my original audio, do a noise removal on the copy - errring on the side of too much rather than two little, then load both samples into a multitrack editor drop the original file to have no volume - then steadily increase the volume until such a point as I can live with the amount of noise and the amount of signal loss. If you use something like Ardour you will be able to automate this tradoff so that it can be different at different parts of the track.

---

### Post by SoylentSteak on 2009-09-30
I want to go the route of eliminating the noise beforehand, but I'm a bit perplexed. The thing is, I only hear the noise when I run it through my Tascam DP-004, which I record to directly. When I've got my earphones plugged directly into the amp's line out, it's clear, even without the built in noise gate on. So, it seems the noise my be coming from the recorder, which is odd, because it's all digital. Before I moved into this apartment and could actually use the amp's speakers at a decent volume, the noise gate left a little hiss, but not as much as with direct recording now. The recorder is brand new, so I think it's perhaps just a limitation and not a malfunction.

That's the only thing I can think of.

---

