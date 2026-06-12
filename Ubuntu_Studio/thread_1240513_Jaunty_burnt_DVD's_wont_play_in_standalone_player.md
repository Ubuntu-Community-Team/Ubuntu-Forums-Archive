---
title: "Jaunty burnt DVD's wont play in standalone player"
date: 2009-08-14
forum: Ubuntu Studio
---

### Post by serfcx on 2009-08-14
I have recently upgraded to jaunty and any video DVD's that I create now wont play in my standalone player. Is this another problem with genisoimage ?
The last version I got to work was 1.1.6 from the gutsy repos but this is not available anymore:(
I would really like some help to solve this please.

---

### Post by Stochastic on 2009-08-15
can you clarify what method you're using to create your video DVDs?

---

### Post by serfcx on 2009-08-15
I have used 2 main methods
Using DeVeDe to create an iso and burn with K3b
Using tovid to create the mpg file, makexml and makedvd to create xml file and dvdauthor to burn.
I believe that both of the burning methods use genisoimage to burn as part of the cdrkit.
I previously had issues in Hardy about the same and this was solved by pinning genisoimage 1.1.6 rather than use the one that came with hardy.
I have since replaced genisoimage 1.1.9 which is part of Jaunty with genisoimage 1.1.6 as before but the problem persists.
I have used the same burning drive and DVD media under windows using Convertxtodvd and the result is OK.
I can only assume that genisoimage is at fault somehow as discs burnt with this are not recognised in my standalone dvd player - "No disc present" message.
At this point I am stumped:confused:

---

