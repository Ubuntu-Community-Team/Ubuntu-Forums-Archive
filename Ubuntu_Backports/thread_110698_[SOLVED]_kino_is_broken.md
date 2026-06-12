---
title: "[SOLVED] kino is broken"
date: 2005-12-31
forum: Ubuntu Backports
---

### Post by arnieboy on 2005-12-31
kino-timfx and kino-dvtitler are broken in the repos (will not get installed) because of the newly backported kino 0.8 package. please look into this ASAP. Automatix users are especially getting affected because of this.

---

### Post by jdong on 2005-12-31
Thanks for bringing this to my attention -- backports of both packages are being looked into.

---

### Post by jdong on 2006-01-02
It is not broken. kino now includes both of the mentioned extensions, and as a result their packages are now obsolete.

---

### Post by fsman on 2006-01-03
also, the backport hasn't been compiled with libquicktime and other libs (unlike breezy and drapper). As a result the backport won't capture in formats other than raw DV.

see [http://www.ubuntuforums.org/showthread.php?t=107486&highlight=kino](http://www.ubuntuforums.org/showthread.php?t=107486&highlight=kino)

---

