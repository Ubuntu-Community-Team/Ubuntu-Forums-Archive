---
title: "I won a bid for a Sun Blade 2000"
date: 2006-10-02
forum: Sun Sparc Users
---

### Post by cptnapalm on 2006-10-02
Soon, I will be joining the ranks of Sparc users with my spiffy brand used Sun Blade.  I thought that I'd ask some questions to which I cannot find too much useful info before it gets here.  No rush :)

The machine has a SunPCI card (probably a II).  Any way to use this under Ubuntu?

The video card is either a Creator 3d or Elite 3d; not sure which.  Do either or both have acceleration under Ubuntu?

Any other things I should know before it arrives?

---

### Post by netztier on 2006-10-03
> **cptnapalm said:**
> Soon, I will be joining the ranks of Sparc users with my spiffy brand used Sun Blade.  I thought that I'd ask some questions to which I cannot find too much useful info before it gets here.  No rush :)

Forum search will help a lot here, make sure to also search in the (closed) forums of the Dapper Drake development phase, where we had quite a few discussion threads, too. 

> **cptnapalm said:**
> The video card is either a Creator 3d or Elite 3d; not sure which.  Do either or both have acceleration under Ubuntu?

Both use the **sunffb** driver in X.org (there's some posts about how to use that driver). 

While the Creator 3D won't have acceleration (in terms of OpenGL), I have read about the latter that it was possbile to get "acceleration" [COLOR="Gray"](although it's not being cleary said if that also pertains to 3D and OpenGL)[/COLOR] by loading some firmware file first. You'll have to google this one up, I am afraid ("afbinit" is your best keyword).

kind regards

Marc



Any other things I should know before it arrives?

---

### Post by cptnapalm on 2006-10-03
many thanks for the pointers and info.

---

