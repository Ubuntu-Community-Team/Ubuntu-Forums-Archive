---
title: ":: Synchronizing package databases..."
date: 2009-06-12
forum: The Cafe
---

### Post by ninja_numbnuts on 2009-06-12
error: failed to update core (unexpected error)
error: failed to update extra (unexpected error)
error: failed to update community (unexpected error)
error: failed to synchronize any databases
[root@myhost ~]#

---

### Post by Sealbhach on 2009-06-12
Maybe your mirror is down. Go to System/Administration/Software Sources and select a different mirror site in the Download From box.


.

---

### Post by Daisuke_Aramaki on 2009-06-12
> **Sealbhach said:**
> Maybe your mirror is down. Go to System/Administration/Software Sources and select a different mirror site in the Download From box.


.


i believe he is running Arch. check your pacman.d/mirrorlist first. may be a certain server is down.

---

