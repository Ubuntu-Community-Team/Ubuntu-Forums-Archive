---
title: "WINE and native DLLs"
date: 2009-04-18
forum: Wine
---

### Post by jbrown96 on 2009-04-18
I was reading on the WINE site that adding the native Windows DLLs to WINE can help a lot with program compatibility. Since I have a legal (and unused) version of XP, I figure that I can add all the DLLs to WINE.

Does anyone have experience with this? Does it help very much? Is there a way to have WINE automatically important all of them; manually adding all of them would be a nightmare. 

I'm trying to get AutoCAD and a video slideshow program (can't remember the name) working for my brother, and there aren't any successful reports at the Wine site. I figured that I might have a shot at it if I use Windows' DLLs. Good idea or waste of time?

Thanks for the help.

---

### Post by NightMKoder on 2009-04-19
Not to rain on your parade, but using native dlls isn't that simple. Since wine tries to emulate windows, some of wine's builtin dlls are significantly different. Take, say, gdi32 (the graphics interface). Windows' dll talks to drivers through an almost black-box system, while wine has to talk to the X server. The windows version just wouldn't work.

That is not to say that all windows dlls are useless. A lot of things really do work better, since they don't use any "weird" windows functions. In fact most dlls fall in this category. But you can't just set every dll to native, as it will just crash wine.

As for your apps - trying to find a native dll if something doesn't work is the first solution everyone tries. I'm assuming you're trying autocad 2010 - It won't work since .NET framework 3.0 won't install, and autocad uses that. Try 2008.

---

