---
title: "Advanced EQ"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by geek_Man on 2008-06-15
Hey guys, does anyone know of any good programs with advanced eq capabilities? (For Linux OR Windows) 'Advanced' like I can pick a frequency down to the hertz and cut it out. I would be using it for recording guitar. A lot of times my amp will be buzzing because of stuff in the electrical current and I'm too cheap to buy a noise-gate pedal. I figure if I can cut that frequency, I'll have a much quieter signal. So if anyone has any suggestions, lemme know. Thanks! 

:guitar:

---

### Post by soulwater on 2008-06-15
Try the Sonalksis EQ's. Windows only though I believe. 4 Band EQ with high and low pass filters.

---

### Post by warbread on 2008-06-15
There are two parametric eq ladspa plugins.  Open up JackRack and add a 2 or 3 band eq under the 'frequency' menu.

---

### Post by thorgal on 2008-06-15
have you checked the frequency range of the noise ? I doubt that you can easily remove it by EQing unless you have a very special type of noise. You could try using Freqtweak (linux jack app). I think you can even directly edit the fourier transform (freq density spectrum) but I may be wrong ... I know there used to be a prog called LAUE or something like that a few years ago (a java app) that allowed such editing.

---

### Post by warbread on 2008-06-15
It might be worth your while to go get an uninterruptable power supply.  [Go here ]("http://excessups.com/apc-backups-c-135.html")to find something affordable.  Unless you actually want a good amount of battery time, you can go with some little 300w deal.  It'll clean your power up and save you from over-eqing your mix.

---

### Post by geek_Man on 2008-06-15
I dunno if getting a UPS would help. Depending on where I am (my house, friend's house, etc.), I get a variety of buzzes and hums. Sometimes there are flourescent lights in the house, other times... I dunno what it is! I also figured that if I can cut as precise a frequency as possible, it wouldn't affect my tone much. I'll try out the plugins though. If anyone else has any suggestions, please feel free to add. Thanks (as always)!

---

### Post by warbread on 2008-06-16
From the sound of it, a power scrubber is exactly what you need.  A UPS works by feeding your components power via the battery, which gives a much cleaner signal.  If you look at it on an oscilloscope, the power from the UPS will look more like a sine wave while the power from the mainline (don't actually try to look at that with a scope) will show the peaks and drops that are giving you buzz.  Exactly how dirty the power is will vary depending on what else is on the circuit, and so you'll get different sounding buzzes.  

Of course, you're free to do what you want, but if it is a matter of dirty power, then something like a UPS, even a cheap one, will help.  EQing out a buzz won't.

---

### Post by Stochastic on 2008-06-16
By definition, a buzz involves a variety of harmonically related pitches.  EQing that out becomes a nightmare of comb filtering, and really shouldn't be attempted by hand (without expecting detrimental results in the recording's frequency response).

Also, a noise-gate pedal will simply turn off the sound while it's below a certain volume (i.e. when it thinks there's only buzz/noise).  This will not do anything for the buzz in the background of your amazing solo, and could end up hurting (truncating) your quiet note tails.  But if you're okay with that result, you can find a gate plugin in the ladspa set and run that through JACK Rack (if memory serves correct).

The best solution is to seek out the source, & prevent it in the first place.

---

