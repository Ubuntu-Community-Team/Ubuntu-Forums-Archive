---
title: "&quot;Cannot open 640x480 display&quot; error?"
date: 2008-12-28
forum: Wine
---

### Post by GNU Gnerd on 2008-12-28
Greetings, all.

I'm trying to get a rather obscure program called Chip's Workshop to run correctly in Wine; it's a level editor for the old Chip's Challenge puzzle game that came with Windows 3.1 and later (if any of you remember it) and for the most part it's running smoothly.  It installs fine, it fills the screen fine, everything is just dandy with the editor part itself.  However, when you want to test the levels you've made, a smaller window is supposed to pop up, with 640x480 resolution, so you can play it.  The error I get at that point is thus:

```
cannot open 640x480 display: DirectDrawSurface::Release: Unknown
DirectDraw error: 0x1
[sdlout.c:229]
```

Now, I've searched for a solution to this error and can't find any reference to not being able to open a display.  I've tried a few common solutions (edit xorg.conf, restart X, and so on) but they haven't seemed to fix the problem.  I haven't worked with sdlout in my C programming adventures, so I'm not sure whether that's an error with the game or with Wine, though a few quick Google searches lead me to believe the latter.  As I mentioned, Chip's Workshop isn't exactly a well-known program, so obviously I haven't been able to find any threads specifically about its errors in Wine.  I'm using a Lenovo t61p laptop with NVidia (all the proprietary drivers and Compiz are installed) and running Wine in XP compatibility mode; when I tried it on my Windows partition it worked fine, so I assume it's not a hardware or driver issue.

If you need any more info, I'd be happy to provide it; sorry about the longwindedness, and thanks in advance for any assistance you'd be able to render me.

---

### Post by GNU Gnerd on 2009-01-01
No one has any ideas?

---

