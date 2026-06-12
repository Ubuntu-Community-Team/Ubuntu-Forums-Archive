---
title: "Recording Multiple tracks without gaps"
date: 2013-08-08
forum: Ubuntu Studio
---

### Post by Sylos on 2013-08-08
Hello all.

Just wondering if people could give me an idea of what they think the best way to achieve my aim is. I have three distinct songs with a (sort of) common theme that I will be recording in Ardour. I want to link them all together with some atmospheric sounds or something similar so that when burned to a CD they run into each other. I get the idea of how to set up the CD burn for this but I'm wondering what is the easiest way to do the recording. The way I see it I have 2 options:

1. Record all 3 songs with the atmospherics as one single Ardour session. Then just mix it.
2. Record each track independently. Mix them individually. Export them to WAV files when ready. Import all three into a new Ardour session, add the atmospherics and then export the complete piece.


I dont know what the best way would be. If it makes any difference, I use Hydrogen for drums and then record guitar and bass with whatever synth stuff I use done from Zynaddsubfx or similar.

Cheers

---

### Post by jejeman on 2013-08-09
I did the 2. option on my last project.
Recorded and mixed all ten songs in MusE, exported to wav.
Arranged them in Ardour, link them with samples, did the mastering, set the CD markers, exported single wav with TOC file.
Burned the CD with cdrdao.
The CD playback is gapless.

I think 2. option gives more control.

---

### Post by cub on 2013-08-09
> **jejeman said:**
> I did the 2. option on my last project.
Recorded and mixed all ten songs in MusE, exported to wav.
Arranged them in Ardour, link them with samples, did the mastering, set the CD markers, exported single wav with TOC file.
Burned the CD with cdrdao.
The CD playback is gapless.

I think 2. option gives more control.
I agree, this is how I would do it too.

---

### Post by Sylos on 2013-08-10
Thanks for the advice. The only problem I can see with this method is if I wanted to continue an instrument that ends one track into the next. So say I had a violin part that ends track one, plays through the interlude section, and continues through the start of track 2. But I suppose to do that I would just record the violin part completely in the 'combined' ardour session as a new track.

Either way it sounds like option 2 is the way forward.

Thanks.

---

### Post by cub on 2013-08-10
You could let the violin play the interlude as the end of track 1. Then start playing the interlude when you record track 2 and mix them together in the mix.

---

