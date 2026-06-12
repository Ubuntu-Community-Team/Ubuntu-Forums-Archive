---
title: "Sound From QSynth"
date: 2012-04-08
forum: Ubuntu Studio
---

### Post by spearlymatt on 2012-04-08
So I have exhausted about all online troubleshooting options, and still can't get sound from a soundfont through QSynth.  A year or so ago it would work beautifully, and for some reason now it won't.  I have JACK as audio, and ALSA for the midi sequencing.  I connect it through ALSA, and through the audio tab, the green light lights up when I strike keys, but no sound.  Calf works fine, and everything else, it's just QSynth.  Any help would be appreciated, thank you.

---

### Post by stevenwscott on 2012-04-08
Do you use Jack Control(Qjack)? It has connect and patchbay panels that are invaluable in getting things like Qsynth, Hexter, etc.. routed to the proper place. I have found that things don't always get auto-patched/connected to where you'd like.

---

### Post by spearlymatt on 2012-04-08
> **stevenwscott said:**
> Do you use Jack Control(Qjack)? It has connect and patchbay panels that are invaluable in getting things like Qsynth, Hexter, etc.. routed to the proper place. I have found that things don't always get auto-patched/connected to where you'd like.

Yep, everything looks proper in the connect window.  I'm not very familiar with the patchbay panel.

---

### Post by Sylos on 2012-04-09
This is a potentially foolish question but ...... have you made sure a soundfont is selected in Qsynth. I know from past experience that some soundfonts when loaded automatically have a sound mapped in and in some you have to go in and manually set it. Failing that have you tried multiple soundfonts?

Sorry if this is stuff you have already done but it often catches people (me included) out.

Cheers

---

### Post by spearlymatt on 2012-04-11
I tried multiple soundfonts that I used to use, I remember them being reliable.  I'm not sure how I would manually set it...

---

### Post by sgx on 2012-04-12
Hi, if a soundfont contains multiple samples, like a guitar
soundfont with normal, mutes, slaps, slides, and twelve-string,
click the 'Channels' button, and each available variation
will be listed to choose from. Some soundfonts with multiple
samples won't play one by default, you have to go select it.

Hope this helps.
Cheers

---

