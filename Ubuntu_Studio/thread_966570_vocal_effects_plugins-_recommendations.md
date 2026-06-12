---
title: "vocal effects plugins- recommendations?"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by goodmanbrown on 2008-11-01
I don't yet have a handle on audio-production terminology, so please bear with a very basic question that I'd google if only I knew the words to use...

I've recorded a song in Ardour, and I'd like to make a portion of the vocals sound like they're coming through an old radio, far away.  It's a common enough effect that I've heard in a bunch of pop songs, but I have no idea what it's called, or how to do it.  Can anyone recommend plugins (or presets) that will have this effect?

Also, which are the good forums to use for Ubuntu audio recording?  Is this the best place?  Is there an Ubuntu Studio form somewhere I can't find?  Should I just go straight to the Ardour forum, since that's what I think I'll use for 80% of stuff?

Thanks!

---

### Post by factotum218 on 2008-11-02
Sorry I don't have a solution for you, but if you drop the low end and the level and bring the gain up juuuuust a hair and compress the snot out of it, might that get a similar result?

---

### Post by duffrecords on 2008-11-02
To emulate an old radio, think about the physical limitations that give it that particular sound.

1. The speaker would be small (poor bass response) and made of cheap material (weak highs).  You can mimic that using a bandpass filter with a center frequency of about 1 kHz (filtering out both the lows and highs).  Use a very narrow Q to get that really thin, tinny sound.

2. The small size and cheap construction of the cone give it a limited dynamic range (the difference between the absolute loudest and absolute quietest sounds it can produce).  Use heavy compression with a ratio of 10:1 or more.  In fact, prior to transmission, radio stations use limiters to increase their signal strength, so use one of those instead if you have it.  Also, a fast attack and fast release would be appropriate here.

3. Cheap, old circuitry is noisy!  Mix in a little bit of white noise for authenticity.  Actually, do this before you use the bandpass filter because you want the hiss to be relatively dull as well.  You might even apply some distortion, as those cheap op amp transistors tend to add a fair amount of odd-order harmonics.

4. Think of those little AM/FM clock radios.  They usually only have one speaker, so why not sum your recording from stereo to mono?

By now you'll probably have an ugly, lo-fi sound--perfect!  That's a cool effect for the beginning of a song because when the real mix comes in it just blows the radio sound out of the water.

---

### Post by duffrecords on 2008-11-03
Or better yet, if you want to be really authentic, play it back through some cheap speakers (or headphones cranked way up) and re-record that with a cheap mic!

---

### Post by luctor on 2008-11-03
I'd use a filter, boost it around 1000 - 2000 hz, cut off below and above this range ..
Audacity has nice filters for this (EQ ..)

---

