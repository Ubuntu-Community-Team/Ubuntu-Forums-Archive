---
title: "Missing dependency on wine1.4 package"
date: 2012-03-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sworddragon on 2012-03-29
On 64 bit systems wine1.4 isn't installing libxcursor1:i386 as a dependency (but as a recommendation). If somebody uses --no-install-recommends or APT::Install-Recommends 0; he wouldn't get any recommendations (for example for a minimalistic system). Without libxcursor1:i386 applications which are using animated cursors have graphic problems.

Now I'm wondering: Should such a package be a dependency or stay a recommendation? If it should stay a recommendation what is the reason for this?

---

