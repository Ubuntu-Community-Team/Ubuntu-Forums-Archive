---
title: "Unity 2D bug or feature?"
date: 2011-12-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-11
I have been noticing that there is this 'effect' when hovering the mouse over app panel Unity 2D icons on multiple systems -

[http://www.youtube.com/watch?v=roDwWB1fkF8](http://www.youtube.com/watch?v=roDwWB1fkF8)

and am wondering if it is a bug of some sort. I do not see it as a feild feature because it will happen anywhere in the row, even if not under a panel typeset indicator.


Does not happen with Unity 3D

---

### Post by Cookieh on 2011-12-11
Hey Ventrical, I had Unity 2D on my old PC until GRUB had crashed, and I always used Unity 2D as my PC was not able to support 3D, but when I used it on my other PC which did support 3D, I did not see any difference in 3D and 2D, so I kept with 2D. This isnt a help but just mentioning this..

---

### Post by Cookieh on 2011-12-11
BTW I was using Ubuntu 11.10.. sorry for lack of info..

---

### Post by ventrical on 2011-12-11
> **Cookieh said:**
> BTW I was using Ubuntu 11.10.. sorry for lack of info..


Thanks .. I am using all Precise alpha and kernel transition here on my PCs where accessing these forums. I am not sure if this bug transmigrated from an earlier bug from natty or Oneiric .. but it is certainly prevalent with Precise.

 I do have some Oneiric installs and will double check with them accordingly.

  Unity 2D does work well enough with Precise alpha and it is important to note that it is a welcome fallback for slower PCs with less resources.

---

### Post by ventrical on 2011-12-11
I just checked and this is a bug specific to Precise (at least form the perspective of Oneiric) although I do not know of any bug reports.

---

### Post by mc4man on 2011-12-11
It's a new PP unity-2d bug, fix committed but not yet released

[https://bugs.launchpad.net/unity-2d/+bug/901491](https://bugs.launchpad.net/unity-2d/+bug/901491)

---

### Post by ventrical on 2011-12-11
> **mc4man said:**
> It's a new PP unity-2d bug, fix committed but not yet released

[https://bugs.launchpad.net/unity-2d/+bug/901491](https://bugs.launchpad.net/unity-2d/+bug/901491)

  Thanks mc4man.

---

### Post by mc4man on 2011-12-11
one bug in unity-2d that's really annoying is when you open a 2nd window unmaxed, it always covers (hides) the launcher.

One reason it's annoying is that it was fixed with a patch in metacity but when metacity was last rebuilt almost **3 months ago **the patch was either removed without comment or forgotten by Chris Coulson. 

So since then the bad behavior has returned.
Find it hard to understand (& not the only known bugs from 11.10 that continue on still.

[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/900063](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/900063)

---

