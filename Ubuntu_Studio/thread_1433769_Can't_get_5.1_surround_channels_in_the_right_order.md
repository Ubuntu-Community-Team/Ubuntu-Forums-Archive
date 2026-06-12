---
title: "Can't get 5.1 surround channels in the right order."
date: 2010-03-19
forum: Ubuntu Studio
---

### Post by davemar on 2010-03-19
I've just installed Studio 9.10, and am trying to get my Audigy soundcard generating correct 5.1 surround outputs.

If I do:
```
speaker-test -Dsurround51:CARD=Audigy -c6 -t wav
``` 
it all seems to work perfectly with the sounds coming out of the right speakers.

However I've downloaded the "6_Channel_ID.wav" file from here: [http://www-mmsp.ece.mcgill.ca/Documents/AudioFormats/WAVE/Samples.html]("http://www-mmsp.ece.mcgill.ca/Documents/AudioFormats/WAVE/Samples.html"), and tried to play that.

If I use:
```
aplay -Dsurround51:CARD=Audigy 6_Channel_ID.wav
```
All the channels play, but in the wrong order (only the front two are OK).

If I try using audacity to play this file all the sounds come from rear left.

The channel order does appear to be correct in that .wav file, so I would hope aplay would work. 

So why does speaker-test seem to be different to aplay, and audacity appears clueless?

Ta,D.

---

### Post by davemar on 2010-03-22
I've just tried:
```
mplayer -channels 6 6_Channel_ID.wav
```
which did play the channels in the correct order, so something does work. It would be nice to get everything doing the same thing though.

---

### Post by cchhrriiss121212 on 2010-03-22
You could use jack to set up the correct channels and save the setting in patchbay. You might not want to use jack all the time though.

---

