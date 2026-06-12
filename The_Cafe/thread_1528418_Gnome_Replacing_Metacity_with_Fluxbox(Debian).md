---
title: "Gnome: Replacing Metacity with Fluxbox(Debian)"
date: 2010-07-10
forum: The Cafe
---

### Post by Allu2 on 2010-07-10
As I searched true Google for a tutorial how to run gnome  desktop-environment with fluxbox replacing gnome's default WM metacity, I  came in conclusion that most of the guides were Old. Hard. And some  didn't seem to work at all. 

So now that i got my gnome work with fluxbox i want to share that to you too. :smile:

[COLOR="Red"]WARNING:
TESTED TO WORK ON DEBIAN SQUEEZE ON MY SYSTEM NOT YOURS, TRY WITH YOUR OWN RESPONSIBILITY.

TESTED TO FAIL IN UBUNTU 10.04(does not start fluxbox dunno why? ending with no wm running. )[/COLOR]


1. Open terminal and run.
```
gconf-editor 
```2. In gconf-editor,  select following path on side panel.
/
--->desktop
-------------->gnome
------------------------>session
----------------------------------->required_components

3.
Now change value "windowmanager" from gnome-wm to "fluxbox"

if you don't want nautilus to manage the desktop (icons and menus) but  instead you want them be like in usual fluxbox (no icons, fluxbox menus)  you can set "filemanager" value to "nautilus --no-desktop"

4.
Now all you need is to log out and log in and everything should work :smile:

5.
if you ever want use metacity again, insert the old values and you should be good to go :)

My first tutorial and i think also my first post on ubuntu forums, don't  be too harsh on comments and fix me if something doesn't work :rolleyes:

---

