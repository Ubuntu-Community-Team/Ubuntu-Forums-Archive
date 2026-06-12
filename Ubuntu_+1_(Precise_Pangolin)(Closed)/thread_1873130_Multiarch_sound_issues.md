---
title: "Multiarch sound issues?"
date: 2011-10-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 3vi1 on 2011-10-31
Anyone else noticed this sound issue since jumping on the Precise repos?

I notice that sound in things like Wine (1.3.31) apps works fine, unless I start a native 64-bit sound app (like Banshee or TeamSpeak3).  When I start one of those apps, they work fine but Wine starts returning:

err:winmm:WINMM_OpenDevice Activate failed: 80004005

I suspect it has something to do with the asound plugins library updates, but I was waiting for the precise uploads to settle before looking into it as a bug.  Still it would do me some good to know I'm not the only one seeing this at the moment.  :)

---

### Post by dino99 on 2011-11-12
get the same issue with Natty i386 & alsa 1.0.24+dfsg-0ubuntu1 (natty)
but dont get it with alsa 1.0.24+dfsg-0ubuntu3 (precise) on i386 system.

---

