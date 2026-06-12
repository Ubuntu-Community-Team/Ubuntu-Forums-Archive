---
title: "Medieval 2 Total War problem (gnome panel on top)"
date: 2009-02-10
forum: Wine
---

### Post by nosscire on 2009-02-10
Hey guys!

I have a problem with this game. It runs just fine, no errors or anything, but for some reason the gnome panel is on top of it when it's running.
The other problem is that the mouse pointer is not exacly where i'm pointing it, but actually a bit higher up.

Screen for both issues:
[http://i41.tinypic.com/2drb9cx.png](http://i41.tinypic.com/2drb9cx.png)

I'm guessing that these problems are connected. It seems that while the mouse pointer I see is based on the window thats visible, the actual graphics are a cm higher due to beeing hidden under the gnome panel. What I mean is that the mouse think that the whole window is in between the panels, but part of it is actually under the panel, if that makes sense.

Anyone know a solution for this issue, as the game right now is next to unplayable due to not clicking where I think i'm clicking.

---

### Post by cogadh on 2009-02-11
If you turn off the option to allow the window manager to control Wine's windows in winecfg, it should correct the panel problem. Not sure if it will do anything for the mouse issue, though.

---

### Post by nosscire on 2009-02-11
Thanks, that solved it, mouse issues as well!

---

### Post by betrunkenaffe on 2009-02-11
So you don't have it randomly crash when trying to enter sieges and the load screen isn't black?

---

### Post by nosscire on 2009-02-11
I have had it crash once when I tried to enter a siege. Mostly it works though. Still, it crashes sometimes even in windows, so i don't have huge expectations ;P

---

### Post by nosscire on 2009-02-13
Alright, while this solution do work, it's not perfect. When I play World of Warcraft I want the window manager to take controll of the window for example (to allow for tabbing out etc). Same thing with many other software.

Is there some way that I can make it turn that setting off when I start Medieval 2, and turn it back on afterwards?

---

### Post by betrunkenaffe on 2009-02-13
You should set it up just for that one program, you can do it from the Application window. Just select "Add" and the pick the Medieval executible, you can customize all the wine options for that one program.

---

### Post by nosscire on 2009-02-13
Doh!

The fact that you could do that never occured to me, even though that is the starting tab whenever you open up winecfg :)

Thanks, works like a charm!

---

### Post by nosscire on 2009-02-13
Also, about the crashes mentioned above.

I also installed Kingdoms expansion and the Kingdoms patch yesterday, and since then I have not had any crashes what so ever (over 6-7 hours of gameplay).

Might just be me thats been lucky, but maybe not.

---

### Post by betrunkenaffe on 2009-02-13
> **nosscire said:**
> Also, about the crashes mentioned above.

I also installed Kingdoms expansion and the Kingdoms patch yesterday, and since then I have not had any crashes what so ever (over 6-7 hours of gameplay).

Might just be me thats been lucky, but maybe not.

Sounds like additional incentive to get the expansions :)

---

