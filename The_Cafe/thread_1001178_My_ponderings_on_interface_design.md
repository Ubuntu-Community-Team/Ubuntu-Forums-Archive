---
title: "My ponderings on interface design"
date: 2008-12-03
forum: The Cafe
---

### Post by MaxIBoy on 2008-12-03
I've used a few operating systems in my day. In chronological order:
[LIST]
[*]Mac System 6 (I'm pretty sure. My mom had this ancient Macintosh up until I was about 10, and the screenshots I've looked up seem to suggest that it was System 6. Also, by looking at photos, I'm pretty sure it was a Mac II.)
[*]Windows 98 (Age 6 to age 11 or so.)
[*]Mac OS 8 (Mom got one of the original iMacs when her old Macintosh finally died. She didn't like it very much and got rid of it.)
[*]Windows XP (Age 11 to present.)
[*]Windows 95 (for a month or so when I was about 12, we got this dinosaur laptop from my uncle. We wound up donating it to a school.)
[*]Mac OS X
[*]Windows Vista (On other people's computers, and on my laptop for more than a month.)
[*]Linux (For three years or so.)
[*]Plus I've fooled around with Haiku in VirtualBox.
[/LIST]

I've used a number of replacement desktop environments and window managers. Not in chronological order:
[LIST]
[*]LiteStep and BBLean on Windows XP
[*]GNOME, KDE, LXDE, FluxBox, OpenBox, BlackBox, Xfce, and Wmii on Linux. I can't seem to get e17 to work.
[/LIST]



There are differences between the interfaces, and even between the themes I've used. But there seems to be one overarching paradigm: A desktop metaphor, windows (floating or tiled,) each window has a titlebar, and the titlebar has embedded buttons for controlling the window. 

Based on some law of interface design, the name of which I forgot, the ideal button is large, hard to miss, and already nearby to the mouse. That doesn't mesh well with the buttons idea. Also, it's nice if it doesn't waste space. 

Since mice now have three buttons usually, I propose a window manager where there are no buttons in the titlebar, and optionally no title either, only a ribbon. This has been done, but my proposed window manager would be controlled like this:
[LIST]
[*]Left click a titlebar to maximize-restore.
[*]Double left click a titlebar to minimize.
[*]Middle click a titlebar to close.
[*]Click and drag to move.
[*]Right click and drag to move, but the window moves way faster than the mouse and goes into neighboring workspaces.
[*]Right click a titlebar, then right click any number of other windows. After that, these windows will not be allowed to overlap with each other (or reverses it if it's already true,) but the operation doesn't move them around or anything. Left click to escape.
[*]Double right-click a titlebar, then right click any number of other windows. This moves and expands the windows such that they tile. The operation doesn't constrain the windows, though. Left click to escape.
[*]Right-click a titlebar three times to maxumize.
[/LIST]

---

