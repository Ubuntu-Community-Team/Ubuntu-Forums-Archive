---
title: "PC performance while playing a Windows-native game under Ubuntu"
date: 2008-12-18
forum: Wine
---

### Post by Tilex on 2008-12-18
Hi!
I recently installed Civ4 under my kubuntu 8.10, and I think that it's pretty cool to still play this game even though Windows has been wiped out.

When I play Civ4, however, I have to lower the details and graphical effects because it's very slow and almost unplayable.  

The thing is that I have an ATI Radeon 3450, a Core 2 64-bit 3Ghz and 4gig RAM.  Am I not supposed to play this 3-year old game at its fullest?  Is it because I'm running it on Linux that it's so slow?

I kepted the System Monitor window open the other day while playing, and while the CPU never reached above 60%, the load never exceeded 1.0, I noticed that my 10gig SWAP partition never was used.  Is this normal?

Thanks guys, Ubuntu owns! ;o)

---

### Post by Songwind on 2008-12-18
Ubuntu won't hit your swap partition if the memory isn't totally consumed, so that's normal.

As for performance under Wine, I find it to be a mixed bag.  Some things run just about as well under Wine as they do natively, and others have a bigger performance hit.  I think it probably has to do with exactly what Windows functions it's using.  Also, OpenGL tends to work better than the Direct3d-to-OpenGL translation that Wine is doing.  So if Civ 4 has an opengl option, that might help.

It is also usually better if you turn off the desktop effects when playing a game through wine - ESPECIALLY with an ATI card.

---

