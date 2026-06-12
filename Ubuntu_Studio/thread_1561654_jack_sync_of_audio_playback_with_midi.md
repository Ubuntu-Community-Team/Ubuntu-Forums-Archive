---
title: "jack sync of audio playback with midi?"
date: 2010-08-26
forum: Ubuntu Studio
---

### Post by linuxgrrl on 2010-08-26
Apologies if this is a stupid question, but:
is it possible to use the Jack transport to sync playback of an audio file (such as an ogg file) with Rosegarden while the Rosegarden is recording midi input?

Background: I am trying to make a midi backing track for home use based on a commercial song I purchased. The easiest way for me to transcribe the bass line, for example, is to try playing it on my Midi keyboard while listening to the song, and let Rosegarden record the Midi input. The results do NOT have to be perfectly synced, I just want a convenient way to sketch out the music. But it's too much pain to click "play" in aqualung, then "record" in Rosegarden, then try to play, stop, back up a few measures to repeat them, etc.  I'm probably just not seeing an easier way to do this.

The ultimate would be if i could stop, start, and play the ogg file in half speed and have RG also go to half speed in sync, but I'd be satisfied with just using a single Play and Stop button at this point.

Thanks
Mary

---

### Post by mango42 on 2010-08-27
Hi **linuxgrrl** - I'm no expert and I don't use **Rosegarden** (far prefer **Qtractor**) but the way I see your issue, would it not be better to place your .ogg audio file into a track in your DAW, set the bpm to slow it all down, then set up another track in the same app to record your midi keyboard bangin out the bassline?

That way, everything's in sync without needing overall Jack control.

Good luck.

---

