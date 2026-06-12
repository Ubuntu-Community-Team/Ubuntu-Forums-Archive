---
title: "Mouse problems in wine"
date: 2009-06-10
forum: Wine
---

### Post by Immortaly007 on 2009-06-10
So I am trying to play this FPS in wine ([http://conspirat.com/avertfate/](http://conspirat.com/avertfate/))
It seems to run allright, except some graphical issues like flickering textures everywhere, but that doesn't make it unplayable imo. The problem is that when my mouse gets to the edge of the screen i can't move it any further (effectively meaning i can't turn any further, which is pretty annoying). Is there any way to prevent the mouse from hitting the edge of the screen (or something)?

PS: I'm sorry if there already is a topic about it, but I couldn't find one.

edit: ow btw do you guys have any tips for a fun shooter for linux(single player)?

---

### Post by NightMKoder on 2009-06-10
Turn off compiz (desktop effects).

---

### Post by Immortaly007 on 2009-06-11
That doesn't seem to do the trick... (I turned it off using the compiz fusion icon)

---

### Post by aoanla on 2009-06-12
So, the underlying problem is that Wine can't grab the mouse pointer in the "correct" way to stop it moving + get direct updates from the mouse itself. This is partly a problem with X itself, which doesn't currently allow applications to receive events from a pointer trying to move "offscreen" (since the pointer itself isn't moving).
This will be fixed properly in the next release of X (and so, hopefully, the next release of Ubuntu, if the timing is right), which includes an overhaul of the entire input device system to allow this kind of thing (and other cool stuff like multiple pointers at once).
I suggest you follow the relevant bug entry for Wine:
[http://bugs.winehq.org/show_bug.cgi?id=6971](http://bugs.winehq.org/show_bug.cgi?id=6971)
where a couple of hacks are also available which might fix your problem, but require recompiling wine.

Another work around (ish) would be to turn up your mouse sensitivity ingame so you can rotate "more" within the same total mouse movement.

---

