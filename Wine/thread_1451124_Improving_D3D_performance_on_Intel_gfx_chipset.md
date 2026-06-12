---
title: "Improving D3D performance on Intel gfx chipset?"
date: 2010-04-10
forum: Wine
---

### Post by quadomatic on 2010-04-10
Unfortunately, my laptop has been cursed with a Intel graphics chipset. It's a X3100, GM965. However, youtube has lead me to believe that it's far more capable than I thought (I thought it was good for absolutely nothing...).

I've found that I'm actually able to play plenty of OpenGL games natively and in WINE, among them being Unreal Tournament, Deus Ex, Half-Life (all in WINE) and Duke Nukem 3D with the HRP, Urban Terror (which I feel like could run better...) and Quake Live (natively).

However, it struggles horribly with D3D games in WINE. Older D3D games, like Fallout and Sanitarium, are fine. However, games like System Shock 2 and The Longest Journey are hopeless.

I suppose this is to be expected somewhat, but it's really quite terrible. Is this a limitation of the Intel linux drivers, WINE, or both? Is there anything I can do to improve performance?

---

### Post by asdfoo on 2010-04-10
> **quadomatic said:**
> 
I suppose this is to be expected somewhat, but it's really quite terrible. Is this a limitation of the Intel linux drivers, Wine, or both? Is there anything I can do to improve performance?

The Intel drivers don't support the OpenGL features that Wine uses enough to run the majority of games properly.  OpenGL games use a very simple subset of OpenGL that isn't enough to do what Wine needs to do to reliably support Direct3D, which is why they may appear to work ok but then not.

Not much you can do except express your dissatisfaction to Intel in writing.  I had to do the same with ATI years ago, I wrote to the product manager and CEO about quality and stability issues under Linux.  The alternative is to go back to Windows where Intel's drivers are slightly higher quality.

---

### Post by quadomatic on 2010-04-12
Hmm...I don't think I'll be going back to Windows, since this laptop isn't really my primary mode of gaming (got a fast desktop). Intel's drivers have been improving, so I guess I'll stick with linux and see how things change.

---

