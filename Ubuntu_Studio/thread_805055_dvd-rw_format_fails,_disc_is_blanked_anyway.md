---
title: "dvd-rw format fails, disc is blanked anyway"
date: 2008-05-23
forum: Ubuntu Studio
---

### Post by Jonie on 2008-05-23
When I try to erase dvd-rw disc in either brasero or k3b in Hardy, it says that format failed, but media is blanked anyway. What's wrong?

---

### Post by pietjanjaap on 2008-05-23
Did you only try 1 dvd-rw?

---

### Post by Jonie on 2008-05-24
No. I tried different brands of -rw (my standalone player likes them better than +rws ;).

Running dvd+rw-format manually, here is the output:

jonie@jonie-desktop:~$ dvd+rw-format -blank /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
* blanking 100.0\

from sequential into sequential, all ok

jonie@jonie-desktop:~$ dvd+rw-format -force /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
* 4.7GB DVD-RW media in Sequential mode detected.
* formatting _30.8%_

changing modes - format goes up to 30 % and then quits abruptly

jonie@jonie-desktop:~$ dvd+rw-format /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
/* 4.7GB DVD-RW media in Restricted Overwrite mode detected.
- media is already formatted, lead-out is currently at
  4595776 KiB which is 100.0% of total capacity.

just to check - everything is all right anyway

Probably that premature quit is caught by recording software I would tend to think it's firmware issue wasn't for that it didn't happen before Hardy. But the recorder isn't all the newest (LG GSA-H10A) and maybe has some firmware limitations that don't play well with latest software.

---

### Post by Jonie on 2008-09-17
And yes, I bump my old thread.

One more question: why since Hardy my DVD-RW discs are being background formatted each time I write something to them (not DVD+RW), even if the disc is full and is already in the mode I want to use. I even installed Schilly's cdrtools, it didn't change a thing.

Not to mention speed decreases by about 3x factor and the led flashes rapidly every few seconds (when the buffer goes empty) hence my assumption about background formatting.

---

