---
title: "Gvfs"
date: 2016-03-03
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2016-03-03
~ usr/share/gvfs was causing a metadata dump in the home folder. I could not trace it to opening any particular application though it could be stopped by logging out. This also causes 100 % CPU usage in one or more cores. This was a known bug on releases going back to 12.04 and a patch was released for 12.04-15.10 . This combined with odd boot messages has me back on 15.10 for a while. :o

---

### Post by howefield on 2016-03-03
Stopped doing that on my systems over the last day or two. (Famous last words...)

Usually triggered by a logout and very occasionally a shut down produced it, but as I say seems to have started behaving lately.

---

### Post by v3.xx on 2016-03-03
My work-a-round was to rename /usr/lib/gvfs/gvfsd-smb-browse to /gvfsd-smb-browse.old

[https://ubuntu-mate.community/t/gvfs-smb-eats-up-a-lot-of-cpu-after-a-update/3869/3](https://ubuntu-mate.community/t/gvfs-smb-eats-up-a-lot-of-cpu-after-a-update/3869/3)

Sounds like maybe it can be restored to normal.

---

### Post by Frogs Hair on 2016-03-03
Good Luck ! Be back in a few weeks.

---

### Post by Frogs Hair on 2016-03-13
Couldn’t wait a few weeks, and have had no usr/lib/gvfs problems on this installation. The last attempt was an upgrade with the gnome-shell installed at the time of the upgrade. Could have been related. :confused:

---

### Post by v3.xx on 2016-03-13
I haven't given it any more attention and not going to.

In another month this all gets removed and I start out with a fresh install.  And of course all my problems will then go away :)

---

