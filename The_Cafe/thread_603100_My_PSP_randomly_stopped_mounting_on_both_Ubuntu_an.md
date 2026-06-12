---
title: "My PSP randomly stopped mounting on both Ubuntu and WinXP"
date: 2007-11-04
forum: The Cafe
---

### Post by rainwalker on 2007-11-04
It used to mount just fine on both, but one day it randomly just stopped. It stays on the "Please wait..." message forever, never connecting.
Does anyone know of a way to forcibly mount it, or even what might be wrong in the first place?

---

### Post by Polygon on 2007-11-04
try plugging it in, then opening a partitioning program like gparted, and then see if you can find the path for it (like /dev/hdc5 or something)

and then once you find that, make sure you have a directory in like /media/ or somewhere to mount it

then just do a 

sudo mount /dev/PATHHERE /media/PATHHERE

and if its recognized filesystem it should mount and be good to go.

---

