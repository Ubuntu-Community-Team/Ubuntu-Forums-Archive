---
title: "Audacity - loop crackles - fine in Audacity???"
date: 2011-05-28
forum: Ubuntu Studio
---

### Post by wbm on 2011-05-28
Hello,
I am placing BetaMonkey loops into Ardour. The loops are wav files and play perfectly fine in Audacity or other playback apps. No crackling noise.
When I place that loop into Ardour, it makes crackling noise on some beats and shows a red dot in some spots in the wave form on the track.

Q1: Why is that?

Q2: how do I get rid of that noise?

Q3: what do the red dots inside the loop wave form mean in Ardour?

Thanks in advance!!!

---

### Post by sgx on 2011-05-29
I would load it in audacity, place the cursor in the wav, and key combo ctrl a 

or 'select all', from a menu. Use the amplify option,
but reduce the volume by/to -5 db or so. Export it with a new name.
I append a 22 to the original name for such edits, easy to find it later in file managers, and frail human gray cells :)

Make sure audacity preferences are set up to load a copy of the original file, so you can freely experiment on it.
A good time to try out lowpass/highpass filters, and more.
Cheers

---

### Post by wbm on 2011-05-30
> **sgx said:**
> I would load it in audacity, place the cursor in the wav, and key combo ctrl a 

or 'select all', from a menu. Use the amplify option,
but reduce the volume by/to -5 db or so. Export it with a new name.
I append a 22 to the original name for such edits, easy to find it later in file managers, and frail human gray cells :)

Make sure audacity preferences are set up to load a copy of the original file, so you can freely experiment on it.
A good time to try out lowpass/highpass filters, and more.
Cheers

Thanks for the reply. My wav file came from an aiff file that I had batch converted on a Mac. I ended up just placing the aiff file into Ardour instead and it works just fine. My guess is that the original conversion corrupted the wav file.

---

