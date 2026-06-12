---
title: "if you've had trouble with gnome_wave_cleaner. . ."
date: 2011-06-04
forum: Ubuntu Studio
---

### Post by a z on 2011-06-04
. . .like i have:
i guess there's some kind of bug in GWC, and i couldn't get it to work recently. it opened, but when trying to play a .wav file, it would say, "can't access /dev/dsp" (or something to that effect). 
i learned from one of the bug posts that if you open it as "padsp gnome_wave_cleaner" (w/o quotes) it may work--pulse audio weirdness, i guess.

so-- i changed its exec line in /usr/share/applications to: padsp gnome_wave_cleaner, and it worked. Yay! for noise reduction, i've found nothing finer than gwc.

cheers,
a z

---

