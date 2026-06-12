---
title: "Program for Polyrhythms?"
date: 2008-08-26
forum: Ubuntu Studio
---

### Post by antknee869 on 2008-08-26
Does anyone know of a good program for playing polyrhythms? I would like something I can program these rhythms in to so I can practice with them.  Can hydrogen do this?
Thanks

---

### Post by Stochastic on 2008-08-27
Hydrogen would be the tool for the job.  What complexity of polyrhythm are you looking for?

---

### Post by antknee869 on 2008-08-27
Looking for things like 5 over 4, 7 over 4 - sixteenth or eigths. But I need it to be very accurate (obviousley).

---

### Post by Stochastic on 2008-08-28
The method for doing this in Hydrogen is to find the lowest common multiple of the two given numbers (for 7 over 4 the LCM is 28).  Then translate that into the length of the pattern you want to repeat in Hydrogen.  In a 7 over 4, use a size of 7 and a resolution of 32 - a 5 over 4 would be need a size of 5 and a resolution of 32 - a 5 over 3 would need a size of 5 and a resolution of 16T.  Then to enter the pattern in, simply treat the two parts as fractions of the length (or LCM): on a 7 over 4, each 1/4 pulse would be 7/28ths apart (count seven lines then put a dot) and each 7th note would be 4/28ths apart.  The BPM tempo number will be off, but it will still adjust the playback speed.

The other method that comes to mind would be to write up a quick lilypond file with repeating 7over4s (other notation programs could probably do this too), then export it to a midi file for playback.  But Hydrogen lets you visually understand the beat placements.

Edit: To hear just the back beat 4/4 time, mute the channel that has 7 hits in hydrogen's mixer.  It also helps to play with the faders in the mixer to give different volumes to each part.  And though you've asked for preciseness, adding in some time 'humanization' from the master mixer control, is good ear training too.

---

### Post by antknee869 on 2008-08-29
Cool, thanks a lot!

---

