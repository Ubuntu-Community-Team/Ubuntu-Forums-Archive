---
title: "[SOLVED] Seamless Mode Unavailable"
date: 2008-03-14
forum: Virtualisation
---

### Post by nickzeff on 2008-03-14
Just so no-one else spends too long on this problem.

I have XPSP2 installed as a guest OS in Virtualbox. I also have the Guest Additions installed, but Seamless Mode is greyed out and unavailable on the menu.

I finally solved this problem by reinstalling the guest additions. Perhaps this problem was due to the fact that Virtualbox was updated a few times, and the guest additions went "out of sync"? No idea.

Cheers

N

---

### Post by Hero of Time on 2008-03-14
It depends from where you updated. If you had the guest additions of 1.4.x installed but never updated them when you updated to 1.5.x, then that is the cause, as the 1.4.x additions don't support seamless mode.

---

