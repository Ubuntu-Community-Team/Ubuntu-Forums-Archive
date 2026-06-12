---
title: "Screen messed up on LotRO/DDO exit"
date: 2010-12-14
forum: Wine
---

### Post by jpalko on 2010-12-14
Anybody else having a problem with this combination that when DDO or LotRO exits, the whole screen turns blueish and messed up. Only way to fix seems to be to log out so that X restarts.

I've tried this on two machines that I have of which the other one has GTX285 and the other one has 9800GTX+ and on the screen turns blue on exit. Additionally the other host has two monitors and only the screen that displayed LotRO/DDO does this and the other one remains clear and visible.

Other games ran with wine do not cause this.

First I thought it could have been because I had the x swat ppa (ppa:ubuntu-x-swat/x-updates) enabled but after I downgraded to distribution basic version of nvidia drivedrs, still the same issue.

The other ppa's that I use are:
```
ppa:ubuntu-wine/ppa
ppa:ajackson-bcs/ppa
```
Could this be caused by some wine registry setting that I'm missing currently?

---

### Post by gradinaruvasile on 2010-12-14
Does that happen with desktop effects disabled?

---

### Post by jpalko on 2010-12-15
Yes, on the one with GTX 285 it happens then too, but I added a couple of registry entries and after that it doesn't happen on that one anymore.

I added:
```
DirectDrawRenderer = opengl
StrictDrawOrdering = enabled
VideoMemorySize = 1024
```

On the other machine I have effects enabled and this did not help, there of course just 512M of memory. Some compiz switch that helps the host or just forget about running on that host with compiz?

EDIT: Oh yeah, noticed also that restarting the LotRO or DDO client also reset the output to work correctly again. :)

---

### Post by jpalko on 2010-12-16
Looks like those registry entries fix the problem with LotRO but not with DDO. :(

---

