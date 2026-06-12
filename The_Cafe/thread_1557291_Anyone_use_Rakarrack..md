---
title: "Anyone use Rakarrack."
date: 2010-08-20
forum: The Cafe
---

### Post by philinux on 2010-08-20
Just got jack ardour and rakarrack joined up. 

I get a bit of noise from using rakarrack, like hissing/clicking noises. This is using the gary moore and satriani effects.

---

### Post by transmogrifox on 2010-08-20
What version of Rakarrack are you using?

Rakarrack does not generate noise, but distortion effects amplify noise that is already there.

This problem may be a result of DC offset in the signal.  This is a small constant amount coming from your sound card.  Most likely sound cards to cause this problem are on-board microphone inputs, but it is conceivable that it is coming through a line input, or even something external to your computer (between your guitar and computer interface).

In recent development (0.5.8 and newer) there is an options in the settings to remove DC offset at the input.  If you have an older version, you will need to send your guitar through a high-pass filter (cutoff <70Hz for guitar is ok).

Other problems may be jack configuration, or other hardware issues.  I am most suspect of DC offset because these presets don't use the "pre-filter" option on the distortion & overdrive effects.

If selecting "prefilter" on the first distortion or overdrive in the chain fixes the problem, then very likely it is DC from your sound card.

If you don't have a recent version of rakarrack, I highly recommend getting it from one of the PPA's...AutoStatic keeps an up to date version in his PPA.

best of luck

---

