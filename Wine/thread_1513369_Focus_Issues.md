---
title: "Focus Issues"
date: 2010-06-19
forum: Wine
---

### Post by Capt_Scribble on 2010-06-19
Hello all, 

I installed Warcraft III with Play on Linux and the game runs just fine. But when I  alt-tab away from full-screen it hangs and I cannot recover it.  I'm left with a frozen black image with a few green pixels smeared across the bottom after it reverts back to my desktop resolution. Then I have to force it to quit.

Another issue that might be related is when I go to configure the  wine settings for WC3 through Play on Linux, the "Wine Configuration"  window never has focus and never responds. I'm forced to close it with  the Close All button. 

I'm using Lucid 10.04, PoL 3.7.3, wine 1.1.42. On my old Jaunty setup I did not  have PoL and I could alt-tab in and out of WC3 just fine. Maybe it's just a wine setting that PoL did not set up correctly?

Any ideas? Thanks!

---

### Post by Capt_Scribble on 2010-06-20
I uninstalled PoL, Wine, and WC3 and then reinstalled them. Now I can't get PoL to bring up the Configure Wine or the Registry Editor windows for WC3 (like before) but now it won't run the game at all. Running in the terminal gives this:

```
$ /usr/share/playonlinux/playonlinux --run "Warcraft III : The Frozen Throne"
PlayOnLinux v3.7.3

Checking python :                 [ Ok ]
wine: failed to initialize: /home/mulx/wb/version/1.2-rc3/wineversion/1.2-rc3/usr/lib/wine/ntdll.dll.so: cannot open shared object file: No such file or directory
```Tried googling both these problems but found nothing. :confused:

---

