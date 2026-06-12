---
title: "Bug: Jack can't rewind (10.10)"
date: 2010-11-07
forum: Ubuntu Studio
---

### Post by MagisterBibendi on 2010-11-07
Hi

My Jack can't rewind. I'm running 10.10.

When I use ardour "internal" timer, there is no problem. The problem occurs when I change to "jack". When I rewind, there is no problem at the surface, but as soon as I click play again, it jumps to the last position.

Which makes my homestudio pretty useless.

And I hope, that I dont have to go back to 10.04.

When I search google, I've found others describing the problem with older installations, but I can't find any solution.

Anyone know what to do?

BTW: I'm NOT a linux expert.

---

### Post by Pablo_F on 2010-11-08
Hi, 

This is a know bug in ardour [http://tracker.ardour.org/view.php?id=2856](http://tracker.ardour.org/view.php?id=2856)

Afaik, the only thing you can do is installing jackd1. jackd2 is new in ubuntu so that explains that it worked in lucid.

Jackd1 package will uninstall jackd2 and maybe some apps, reinstall the apps and you are done. 

Cheers! Pablo

---

### Post by MagisterBibendi on 2010-11-09
That was perfect! 

Thanks a lot
:guitar:

---

