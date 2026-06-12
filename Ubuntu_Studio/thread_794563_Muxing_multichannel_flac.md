---
title: "Muxing multichannel flac?"
date: 2008-05-14
forum: Ubuntu Studio
---

### Post by sammydee on 2008-05-14
Hi everyone.

Bit of an obscure question here, but not sure really where to ask.

I've got some audio files from a 4.1 quad mix of a very famous album. I want to play these on my surround sound card, however:

The album songs are mixed with the channels in the following order:

FL, FR, LFE, RL, RR

(front left, front right, low frequency effects, rear left, rear right)

But when I try to play them with totem-gstreamer it outputs the streams like:

FL, FR, RL, RR, CF

(cf is centre front)

How can I play these back with the channels in the right places? Is there a tool I can use to mux these flacs into an ogg stream and define the channels properly?

Sam

---

### Post by warbread on 2008-05-15
Well, before I go searching all over Google for an answer, I will offer my suggestion.  If it were me, and mind you, I'm a little nuts, I would import them all into Ardour and define the channels there.  Then I would mix it down and export.  There may be an easier way, but that's what comes to me off the top of my head.

---

### Post by Stochastic on 2008-05-15
Yeah I was going to write a reply saying ardour is the way to go too, as that's where I do all my surround mixing.  But last I checked ardour's default build for Ubuntu (and studio) doesn't support flac - I haven't tested hardy's yet though.  So you'd need to convert from flac to wav first, then import to ardour.

It looks like all you need to do is put a track of silence in the centre and then move the subwoofer track to the sixth position.

---

### Post by sammydee on 2008-05-15
Well I used audacity and shuffled the channels around. It works great now!

Sam

---

### Post by sammydee on 2008-05-15
Or not.

The flacs only seem to play in totem-gstreamer. Vlc and amarok (xine) spit out horribly corrupted sound when playing them. any ideas?

Sam

---

