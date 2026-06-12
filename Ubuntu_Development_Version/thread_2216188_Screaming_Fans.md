---
title: "Screaming Fans"
date: 2014-04-10
forum: Ubuntu Development Version
---

### Post by mayagrafix on 2014-04-10
Trusty Tahr 14.04 LTS  works great so far except for the cooling fans on MoBo. When Logon screen appears they both go into overdrive (max RPM). If I put PC into suspend mode, after I awake from suspend mode fans are working normally. Any idea when this will be fixed?

Thanks for all input :>)

[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/ScreamingFansRPM_zpsb4391318.png[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/ScreamingFansRPM_zpsb4391318.png.html)

---

### Post by ventrical on 2014-04-10
They would fly apart if they were actually going that fast. I have had that bug with O'Clocking too.

---

### Post by alan-pater on 2014-04-10
[https://bugs.launchpad.net/i8kutils/+bug/200449](https://bugs.launchpad.net/i8kutils/+bug/200449)

As for when it will get fixed, it does not look likely, as the i8kctl is not really being maintained anymore. You might try removing it and putting thermald in it's place and letting that handle things.

---

### Post by grahammechanical on 2014-04-10
This may or may not be appropriate to this discussion

[http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)

Regards.

---

### Post by ventrical on 2014-04-15
> **grahammechanical said:**
> This may or may not be appropriate to this discussion

[http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html](http://www.webupd8.org/2014/04/prevent-your-laptop-from-overheating.html)

Regards.

Yes it is because the i8kctl is needed for older Dell latitudes and thermald is only good for SandyBridge and upwards and now that i8kctl is no longer supported ?? then that leaves some in a real bind with overheating probs.


I would rather have screaming fans than no fans at all.

Regards..

---

### Post by ventrical on 2014-04-16
I found the original thread I started in Dell Support Forums and it really helped me with the saucy cycle (now about to try it with trusty).

Regards..

[http://ubuntuforums.org/showthread.php?t=2192729](http://ubuntuforums.org/showthread.php?t=2192729)

---

### Post by mayagrafix on 2014-04-16
**BINGO!!** Give the Gentleman a Cigar... After removing the i8kutils the fans act normal on startup. Thank You Very Much :>)

---

