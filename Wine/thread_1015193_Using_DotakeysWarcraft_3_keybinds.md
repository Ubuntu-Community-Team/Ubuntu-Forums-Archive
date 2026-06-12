---
title: "Using Dotakeys/Warcraft 3 keybinds"
date: 2008-12-18
forum: Wine
---

### Post by poebae on 2008-12-18
Running WC3: The Frozen Throne under Wine, I'm trying to use Dotakeys or something similar so that I can bind item hotkeys, since I use a laptop and don't have a numpad.

In Windows I used to use a precompiled Autohotkey script that would bind Alt+Q to Numpad 7, Alt+W to Numpad 8, Alt+A to Numpad 4 and so on. I tried running the program in Wine, and it 'works' to the extent that it even places the program's icon in my system tray, but none of the in-game key binds work.

I've dug around the forums and seen a solution with some promise (quoted below), but I'm not sure how to customise it to my needs.

Any help would be greatly appreciated :)

> 
Here the solution for remap keys to mouse or keyboard on warcraft III and Dota map with cedega wine.( It's work for me )

Install:

xbindkey
xvkbd

here a .xbindkeysrc example:

# mouse button UP
"/usr/bin/xvkbd -window cedega -text "h""
b:4


# mouse Button down
"/usr/bin/xvkbd -window cedega -text "w""
b:5

# Mid mouse button
"/usr/bin/xvkbd -window cedega -text "e""
b:2

# control + button 1
"/usr/bin/xvkbd -window cedega -text "b""
control + b:1

# numpad 0
"/usr/bin/xvkbd -window cedega -text "v""
c:90 + release

---

