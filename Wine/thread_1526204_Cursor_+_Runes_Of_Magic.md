---
title: "Cursor + Runes Of Magic"
date: 2010-07-07
forum: Wine
---

### Post by ruben0 on 2010-07-07
I'm using Wine 1.1.42 and installed runes of magic. Runes of magic runs very smooth, the only issue:

When in ROM you can look around you by holding right mouse button and moving your mouse, in windows, you can keep turning around and around. In wine however, when you do this, your cursor still moves (but you don't see it), so when you hit the boundary of the screen you stop moving in the game. This is very annoying, if you use right+left mouse button you can run around, but when you hit the boundary, you can't turn left (or right)..

Is there a way to fix this?

(I hope I have explained my problem good enough, if not, please ask me to rephrase)

Thanks in advance.

---

### Post by Zato-1 on 2010-07-07
That same problem(mouse rotation) has been confirmed in other games too and there is a fix, while it does fix mouse rotation it also makes mouse unable to move in game menus(atleast it was like that for me).

Anyway try it out.. maybe it will work for you, if not you can always undo it (:

[Software\\Wine\\DirectInput]                
"MouseWarpOverride"="force"

---

### Post by ruben0 on 2010-07-08
I tried that,  but this makes the mouse cursor fix to the center of the screen. This means I can't move it at all (not even through menus).
I know this fixes "rotation" (making your mouse cursor "spin"). But not sure this is the same problem as I'm having. My problem is I can't rotate, once I hit a boundary it just stops :)

---

