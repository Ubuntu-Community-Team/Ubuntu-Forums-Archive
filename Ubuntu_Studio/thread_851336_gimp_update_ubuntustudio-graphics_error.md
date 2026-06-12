---
title: "gimp update ubuntustudio-graphics error"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by Blind Tiger on 2008-07-06
I just did an auto software update for gimp.  It required a partial updgrade, to which I approved.  After upgrade/update, it recommended removing obsolete packages, which I did, thinking it was outdated config/versions of various graphics programs for Ubuntu Studio.  It removed my entire ubuntustudio-graphics package.  

When I try to reinstall the graphics package, it gives me a dependency error for package gimp-print.  If I try to install gimp-print, synaptic says it will have to mark additional changes which would then remove even more packages, including some software involved with video production.  What is the source of this error?

---

### Post by Ninja Krow on 2008-07-07
I had this issue my self. needless to say, Gimp wasn't changed enough to warrant that upgrade. The difference between Blender 2.45 and 2.46 on the other hand are pretty major advancements.

As for your issue. I did this and like you said. Epic Fail with all that dependency stuff.

I then had to completely remove Gimp. after having to tell the system to fix it self in a Terminal Window, sorry i don't remember the Command string, but it tells you in a dialog somewhere on the Desktop.

I had to do some pretty funky stuff with a terminal instance to get it to fix itself in a couple of places. Letting it uninstall a few things, I think it was some video apps like you said BTW.

I then reinstalled ubuntustudio-graphics but that pretty much failed. but i still had pretty much everything but the Gimp at that point so deb by deb i installed the newer Gimp. and then it was pretty much as far as I could tell fixed.

After all that head ache, It was pretty much the thing that convinced me that i needed to be very careful with getdeb.com and that it was not the best method to go for certain things. Still Got me a working upgrade for blender to it current Stable version.

wish I could be of more help...

---

