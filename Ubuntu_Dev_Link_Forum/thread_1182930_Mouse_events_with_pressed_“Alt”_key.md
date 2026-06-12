---
title: "Mouse events with pressed “Alt” key"
date: 2009-06-09
forum: Ubuntu Dev Link Forum
---

### Post by SERGYI on 2009-06-09
[FONT=Calibri][SIZE=3]Hello there! I’m porting 3d-coat editor to Linux using “gtk” ([/SIZE][/FONT][[FONT=Calibri][SIZE=3]http://3d-coat.com/[/SIZE][/FONT]]("http://3d-coat.com/")[SIZE=3][FONT=Calibri]). We have navigation input layout from “Maya”: “Alt + Left Mouse Button” – tumble, “Alt + Middle Mouse Button” – track, “Alt + Right Mouse Button” – dolly. But in “Ubuntu” when you press “Alt + Right Mouse Button” you get popup context menu for window, with “Alt + Left Mouse Button” you start window move, and with “Alt + Middle Mouse Button” you go to window resize mode. Of course, with pressed “Alt” key mouse events are no longer dispatched to callbacks (such as “button_press_event” or “scroll_event”). Please advice, how to block these system shortcuts for application window and receive mouse events with pressed “Alt” key?[/FONT][/SIZE]

---

### Post by SERGYI on 2009-06-16
[FONT=Calibri]After some investigation it seems, like a lot of Maya and Photoshop users are aware of that issue. To use camera navigation and other shortcuts with “Alt” key + “Mouse Buttons” some of them change the movement key from “Alt” to “Super” within “System -> Preferences -> Windows” (for Ubuntu). Thus the most optimal solution is duplication “Alt + Mouse Buttons” with “Super + Mouse Buttons” shortcuts. In that case you can use “Super” key instead of “Alt” for default movement key in your system preferences, and “Alt” key if you’ve changed it to “Super”.[/FONT]

---

### Post by ReKast on 2009-07-03
Thank you SERGYI, this is very helpful for me as I am using blender. This way one can keep the best of both worlds, Ubuntu's useful short-cuts and the desired programs. Cheers.

---

### Post by unimatrix on 2010-01-20
Here's a better solution (IMO, because I want to keep using my Alt+Click function in other programs).

[LIST=1]
[*]Instal CompizConfig-Settings-Manager (CCSM).
[*]Maximize Maya (you're going to have it maximized all the time anyway).
[*]In CCSM enable "Window Rules" and click it.
[*]Put "class=Maya" into the "Non movable windows" field.
[*]Go back to CCSM's main menu and click on "Move Windows".
[*]Uncheck "Snapoff maximized windows".
[/LIST]

There, now Alt+click works in Maya, and you can still move other windows with it.

---

