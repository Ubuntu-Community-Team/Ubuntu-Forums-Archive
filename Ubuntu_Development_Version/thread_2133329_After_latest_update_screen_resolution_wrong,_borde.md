---
title: "After latest update screen resolution wrong, borders missing"
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by victor9098 on 2013-04-07
Hey all,

Just got the latest round of updates, restarted and my screen resolution is way off. Also no borders on any apps, unity/compiz do not seem to be working right either. I have a feeling it might be something to do with the kernel update. Anyone else?

---

### Post by victor9098 on 2013-04-07
I moved from the Nvidia drivers to the default xorg drivers on my system, that cleared up the resolution issue but still no unity or borders.

Have just tried a fresh install, but the exact same issue, resolution looks fine but no unity or borders. Major borkage.

Have reported [Bug #1165974]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1165974")

**UPDATE**

This only seems to affect one user account. I have logged into the other (standard) user accounts and Unity is working fine in them!?

**UPDATE (Solution)**

Typing this into terminally fixed it for me;

> sudo apt-get purge fglrx lightdm && sudo apt-get install lightdm ubuntu-desktop

---

