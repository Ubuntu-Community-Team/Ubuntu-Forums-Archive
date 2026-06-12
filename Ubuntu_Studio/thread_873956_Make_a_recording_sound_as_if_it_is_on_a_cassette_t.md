---
title: "Make a recording sound as if it is on a cassette tape."
date: 2008-07-29
forum: Ubuntu Studio
---

### Post by insane_alien on 2008-07-29
Hey,

i'm looking for a way to edit a recording so it sounds as if it is off a cassette tape. obviously the best way to do this would be to record onto a tape and then record it onto the computer.

but, i don't have a tape recorder or even player and i don't want to buy one for something i'm just going to do once or twice. Is there an efect for audacity or something?

---

### Post by Stochastic on 2008-07-29
umm, other than a slight bit of compression (very slight) and possibly some added noise (hiss) what characteristics would you be looking for?  do you want speed fluctuations (as if the playback motor is slipping)?

These effects are all possible with the ladspa plugin set in any wave editor.

Cassette tapes theoretically have better sound quality than digital audio, so replicating it is more about adding the commonly heard defects than adjusting the overall recording.

---

### Post by insane_alien on 2008-07-29
possibly, but i think i can replicate that.

i'm just trying to replicate a tape sound as close as possible first and then i'll decide how to modify it.

all i've been given is 'make this sound as if it is being played on a slightly worn tape' its for a small game my friends making and i've done some audio editing before. but that was just pasting bits together and making it an even volume.

---

### Post by Stochastic on 2008-07-29
> **insane_alien said:**
> possibly, but i think i can replicate that.

i'm just trying to replicate a tape sound as close as possible first and then i'll decide how to modify it.

I'm not sure what you mean by this.  By trying to replicate a tape sound you will be modifying the source sound.

> **insane_alien said:**
> all i've been given is 'make this sound as if it is being played on a slightly worn tape'

Okay, so it needs to be a slightly worn tape, now we're getting somewhere.  
-Add a bit of noise by creating a track of white noise, filtering it to only a narrower bandwidth (bandpass filter or your own EQ settings), reduce it's volume, then paste it into the original file.
-Add some crackles to the audio by selecting a very small bit, amplifying it beyond full volume, then reducing it back to near it's original volume.  Do this a couple of times intermittently through the recording.

Also, many people think of a cassette sound as being the same as an old stereo sound (i.e. a teenager's boombox) if that's what you're looking for, then you need to put the entire recording through a very wide bandbass filter to take out the lows and some of the highs, then probably EQ it a bit to accentuate a few frequencies (probably the 1k, 3k and 6k zones).

---

### Post by insane_alien on 2008-07-30
> **Stochastic said:**
> I'm not sure what you mean by this.  By trying to replicate a tape sound you will be modifying the source sound.

i was just meaning i'll get it sounding like a tape first and then i'll add in some effects to make it sound a bit damaged thats all.


> 
Okay, so it needs to be a slightly worn tape, now we're getting somewhere.  
-Add a bit of noise by creating a track of white noise, filtering it to only a narrower bandwidth (bandpass filter or your own EQ settings), reduce it's volume, then paste it into the original file.
-Add some crackles to the audio by selecting a very small bit, amplifying it beyond full volume, then reducing it back to near it's original volume.  Do this a couple of times intermittently through the recording.

Also, many people think of a cassette sound as being the same as an old stereo sound (i.e. a teenager's boombox) if that's what you're looking for, then you need to put the entire recording through a very wide bandbass filter to take out the lows and some of the highs, then probably EQ it a bit to accentuate a few frequencies (probably the 1k, 3k and 6k zones).

cool thanks. i'll get started experimenting around with those, i just had no idea where to start on this.

---

### Post by insane_alien on 2008-07-31
okay, i've got the sound i was looking for thanks to your help. cheers.

---

