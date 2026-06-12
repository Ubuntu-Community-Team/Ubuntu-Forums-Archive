---
title: "Whats the practial diference between Ubuntu 32 and 64bit?"
date: 2006-01-12
forum: The Cafe
---

### Post by Mr_J_ on 2006-01-12
I have an AMD which is currently not using the 64bit version of Ubuntu because I initially heard of problems with it.

Now that I'm getting somewhat bored I'm thinking of using my experience and slapping a clean install on my box.

I was wondering if there were any benefits from using Ubuntu 64bit instead of this 32bit version.

Please post "Pros" and "Cons", even if not both at once if you can't remember them.

Is there a place I could read about this I have failed to look?
:D 
Sorry for the lazyness on looking, but I think this hasn't been done before.

---

### Post by ssam on 2006-01-12
more bits lets you use larger intergers and higher precision floating point numbers, without having to resort to slower calculating methods.

in the move from from 16 bit to 32 bit this was fairly important because there where lots of case where you might want numbers bigger than 16 bit can handle (65 thousand). however few people need numbers bigger than 32 bit (about 4 billion). maybe scientists, people running simulations, etc.

the main practical advantage is being able to address more memory. a 32bit memory address limits you to 4Gb. a lot of people these days handle files/databases larger than 4Gb, and if they can keep it all in RAM their application will run faster.

---

### Post by poofyhairguy on 2006-01-12
Pros:

1. Its faster (after reading on this forum for a long time that it did not make a big difference, I will say that I think it does. the 64 bit version boots into Gnome faster -by a few seconds- has a quicker Firefox and Gimp and overall feels "snappier"). But I am REALLY sensitive to this sort of thing, so a small difference (I imagine like 10%) is a big deal to me. Plus I timed somethings with my watch (such as Gnome loading) just to make sure. If I go back it will be for this reason.

2. Supports more RAM.

3. Modern OS on modern computer (feels good).

4. Its all 64 bit (unlike Windows 64 that has many 32 bit parts).

Cons:

1. Third party support- flash, media codecs, WINE, etc.

2. Some of the programs in the Universe do not work (Skippy for one).

3. Some things are hard to do in 64 bit and require chroot (emulators- why I gave up on it).

4. Speed difference is not HUGE so a casual user might not notice.

---

