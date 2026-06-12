---
title: "Is it me or are the ATI drivers getting worse?!"
date: 2008-01-27
forum: The Cafe
---

### Post by Scarath on 2008-01-27
Installed ATI drivers on a laptop a while back and it ran everything fine, compiz, games, etc etc. (laptop was running feisty then upgraded to gutsy) 

Install new version after fresh installing ubuntu 7.10 (have done this 3 times now with different versions of the drivers) and nothing works ... (now running gutsy)

Is it an ATI vs Gutsy problem?

Are ATIs drivers just getting more buggy?

Am i imagining things?

Anyone else having similar problems? (e.g. ATI cards working less well now than when ATI first released the linux drivers?)

Maybe its just all in my head ...

---

### Post by CCNA_student on 2008-01-27
Maybe the latest update had some new bug. It will probably be a while before the ATI drivers are as good as the Nvidea drivers anyway. I have always had a problem getting Xaos and pouetchess to work with my ATI video card.

---

### Post by Darkhack on 2008-01-27
You should specify what ATI card you are using.  I have the ATI xpress 200 on Gutsy and it works fine for me.  If you are having issues you can either use the DRI radeon driver or stick with Feisty Fawn until 8.04.  Thankfully AMD/ATI is starting to release their specifications so driver quality should improve over time.

---

### Post by jpittack on 2008-01-27
ATI's drivers are in more of an alpha stage.  They aren't getting worse, they are developmental.  This is true from 43.x on.  42.x was for high end cards.  40.4 was last real stable release, but it doesn't install nicely.  What's in the repos works for all but aiglx stuff, so just add xgl.  Latest ones are developmental to add aiglx.

Hardy will probably have a new driver.  8.01 is somewhat stable now, or so I hear.

---

### Post by bufsabre666 on 2008-01-27
i can definitly say, on my laptop, 8.1 is **way** an improvement over the old ones. it might just have a problem with your chipset, they have been known for that in the past, like my old x1600 with the 8.43((i think it was)) drivers sucked

---

### Post by Polygon on 2008-01-28
no, they are getting better. With the latest ati drivers (forget the number), everything works for me. 3d acceleration, compiz, suspend and hibernate, video WHILE using compiz, the works. The only thing that doesnt seem to work is blender when im using compiz, and that might be a blender or a compiz problem.

but otherwise, they are getting much better. Sure the latest drivers have some bugs (gnome screensaver flickers when you start it, some corruption in 3d apps like blender) but im still just so happy that finally everything works.

---

