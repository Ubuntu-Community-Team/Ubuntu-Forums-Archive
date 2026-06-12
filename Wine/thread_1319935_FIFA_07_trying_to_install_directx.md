---
title: "FIFA 07 trying to install directx"
date: 2009-11-08
forum: Wine
---

### Post by Viva on 2009-11-08
I'm trying to install FIFA 07 on karmic(none of the newer versions work with wine) and it is forcing me to install directx 9.0C. I've read some where that you should not install directx because wine supports it natively by default. So, how do I install games that force you to install directx? I don't quite remember what I did with jaunty, but the game worked flawlessly.

---

### Post by hikaricore on 2009-11-08
No game should ever force you to install libraries... that's just flawed installer design.
It's possible in the past you'd installed dll overrides with winetricks to avoid this?
The installer is likely looking for a specific dll that is missing and trying to install directx as a fallback.
Doubt this helps you much but it's a start.  :)

---

