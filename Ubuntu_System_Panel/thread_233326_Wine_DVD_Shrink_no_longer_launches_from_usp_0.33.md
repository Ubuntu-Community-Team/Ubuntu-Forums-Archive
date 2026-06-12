---
title: "Wine DVD Shrink no longer launches from usp 0.33"
date: 2006-08-09
forum: Ubuntu System Panel
---

### Post by orb9220 on 2006-08-09
Was working until I upgraded to 33.

Launches from main menu just fine.
Deleted usp icon from favourites. And readded still no go.

Name
DvD Shrink

Generic Name
DVD Movies

exec
wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe"

icon
/usr/share/pixmaps/DVDShrink.png

Hope this helps and can be fixed,

Edit: Sorry will post in bugs thread,

---

### Post by tslining on 2007-04-20
I'm having the same problem with Wine 0.9.35...

Any solutions?

I have wine set to XP (have tried w/ NT 4 also), all other programs will open, dvdshrink will not.  Help!

---

### Post by Malac on 2007-04-21
Try replacing the spaces in the exec command with %20 and see if it then launches.
Unfortunately I don't use DVD Shrink so I can't test this out.

Hope this helps.

---

### Post by Trespasser on 2007-04-29
Wine 0.9.35 and 0.9.36 have regressed with reference to DVD Shrink. Lots of bug reports about it at Nabble dot com. Use Wine 0.9.34 until it's fixed.

Later....

---

