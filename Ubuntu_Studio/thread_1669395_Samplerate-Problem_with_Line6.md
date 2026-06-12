---
title: "Samplerate-Problem with Line6"
date: 2011-01-17
forum: Ubuntu Studio
---

### Post by the.deathgate on 2011-01-17
Hi!

After one weekend of complete madness, my PODxt runs with the tanz-band-driver (or however you would call it) 0.8.1.

I can use it to play sounds pretty well.

But JACK and Ardour tell me the audio engine runs only with 39062Hz.
Recording works actually, but sounds like crap.
The POD supports 44.1 and 48khz as far as I know. So what the heck is going on?

I tried also the 0.9x-Drivers from the repository.
Didn't work at all and even crashed the system (yes the whole thing, tumbling in cache-dumps).

I really hope someone fixed those problems.
Thank you very much.

---

### Post by the.deathgate on 2011-01-18
OK Problem is fixed in a way.
The PODxt does not really use 41.1 or 48kHz!
It works with those strange 39kHz internally.

So JACK is right!

Seems like I need to change my interface urgently.

---

