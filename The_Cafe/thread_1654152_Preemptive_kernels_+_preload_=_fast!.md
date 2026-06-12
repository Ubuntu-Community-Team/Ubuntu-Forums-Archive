---
title: "Preemptive kernels + preload = fast!"
date: 2010-12-27
forum: The Cafe
---

### Post by sandyd on 2010-12-27
I recently decided to switch to a preemptive kernel + preload, cause everything on my laptop (esp firefox) was loading at the speed of mollases (yes i know, the bottleneck is the Hard Drive). Upon switching, everything became lightning fast.

However, on another computer, there seemed to be no effect.

Yet, I was curious, so I switched it on another computer, and that sped up a little.

Can someone explain to me this weird scenario?

Currently-
Mozilla Firefox (4) - 2-3s
OpenOffice (4s)

---

### Post by NightwishFan on 2010-12-28
To be honest, I doubt the preemptive kernel has anything to do with speeding up loading times. As for preload, not sure how it works, it certainly helps with huge software I use often. I recommend it not be installed unless you feel a real need for it. I doubt it will hurt anything though.

---

### Post by undecim on 2010-12-28
Preload is supposed to help reduce the hard drive bottleneck. If I understand it correctly, it learns which programs use which files and pre-caches them when a program is launched, so that when the drive would otherwise be sitting still, it can instead be fetching files that will soon be needed.

---

