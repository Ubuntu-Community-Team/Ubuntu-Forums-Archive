---
title: "Drop down info from signal strength icon &amp; screenprint"
date: 2009-02-06
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2009-02-06
FYI to the programmers.

When the Network Manager's Signal Strength Icon is left-clicked, a "drop down" of the wireless signals within "view" of the OS/hardware appears. Mine usually shows about 8 to 10 wireless signals. 

When the signals are showing, a screenprint of that is NOT available. 

I have a JobCorps center behind where I live. They have a 3 story brick & steel building and use 6 Cisco commercial grade routers which power at over 100% into my home, blocking my 30 to 40 % (max) signal. Or at least warping it. I spoke with their IT guy, and wanted to send him a screenprint of the signal strength of his routers.

Thanks for your time.

---

### Post by Jesuses Left Leg on 2009-02-06
You could install scrot and use it to delay the time before the screenshot is taken giving you time to bring up the menu.

scrot -d 10 would give you a delay of 10 seconds. Just tried it and it works fine.

---

### Post by FuturePilot on 2009-02-06
The reason why that happens is because when there's a menu open the window manager grabs the keyboard. It's not specific to just Network Manager. Just set a delay on the gnome screenshot tool.

---

