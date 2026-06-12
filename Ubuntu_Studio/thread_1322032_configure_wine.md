---
title: "configure wine"
date: 2009-11-10
forum: Ubuntu Studio
---

### Post by judge jankum on 2009-11-10
I've installed AP Guitar tuner through wine in Ubuntu 9.04, it opens right up like it's suppose to, but is not recieving any audio signal...How do i configure the audio in wine to make it work?...The audio test in wine is working when i click test..Somehow my programs are not connecting to the audio

---

### Post by JugglinPhil on 2009-11-10
From a terminal run 'winecfg' and go to the Audio tab. The first time you do this it usually tells you that there were no drivers selected and that it has selected some for you. If it still doesn't work just play around with the settings.

---

### Post by judge jankum on 2009-11-10
Thanks, did that, sound works in wine now, but when i open a program like AP Guitar tuner it dosn't work in the program..

---

### Post by judge jankum on 2009-11-10
The only options are preferred recording device, or default...

---

### Post by AutoStatic on 2009-11-11
Why not use a Linux equivalent? Guitarix has a tuner, Rackarrak too and I think there are even seperate tuners in the repo's. Or does this AP tuner have this very special feature that the Linux equivalents don't offer?

---

### Post by JugglinPhil on 2009-11-11
> **AutoStatic said:**
> Why not use a Linux equivalent? Guitarix has a tuner, Rackarrak too and I think there are even seperate tuners in the repo's. Or does this AP tuner have this very special feature that the Linux equivalents don't offer?
Might actually be the best idea.

---

### Post by judge jankum on 2009-11-11
I grabbed  GTK. It works but i think my whole probem is a Very low input audio level.....
 I have a 300 watt Peavey head connected to line in from tape out/pre-amp out and shaking the windows in here i'm getting a low level in Audacity and now the tuner...

---

### Post by judge jankum on 2009-11-11
Fixed.....Swapped over to a Fender head head and ran line-in from a moniter channel with a volume control, turned it up a little and it's just right...

---

