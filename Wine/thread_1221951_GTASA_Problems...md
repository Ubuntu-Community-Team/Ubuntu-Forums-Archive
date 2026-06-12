---
title: "GTA:SA Problems.."
date: 2009-07-24
forum: Wine
---

### Post by iFuzo on 2009-07-24
Hi Ubuntu,

When I open GTA:SA I get a message saying "**Cannot find 800x600x32 video mode**"

How do I fix this?

---

### Post by hikaricore on 2009-07-24
Start gta in a virtual desktop window as such:

> wine explorer /desktop=GTASA,1500x1050 gta_sa.exe

Where 1500x1050 is the size of the window, I use this as it is over the 1440x900 res I run the game at, so the window starts larger and has to scale down. (limits visual corruption at startup)
Aside from this I've not figured out a way to resolve the issue otherwise.. the game runs without this on my roomie's comp with similar hardware.  *scratches head*

Also if this doesn't work you may have video driver issues unrelated to WINE.

---

