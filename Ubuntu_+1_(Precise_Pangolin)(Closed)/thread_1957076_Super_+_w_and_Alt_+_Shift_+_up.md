---
title: "Super + w and Alt + Shift + up ?"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Antron89 on 2012-04-12
Hey,

in compizconfig Super + w is bound to "initiate window picker for all windows", but it just scales the windows of the current workspace. This is also triggered by Alt + Shift + up.

In the shortcuts-overlay it states that this behavior is expected, but why didn't they just bind Super + w to "Initiate window picker" instead of "Window picker for all windows" and leave the functionality to spread *all* windows?

---

### Post by EgoGratis on 2012-04-12
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/689733)

---

### Post by mc4man on 2012-04-12
That bug removed the left click on icon pulling from all WS's. on window group
(the  ability to bind window group has been compromised for a long time in compiz 0.9.X thru scale bindings

A bit later scale was altered to also just pull from the current WS.
This change is not that difficult to revert, one can patch & rebuild compiz, then Super+W (or whatever you wish) will pull all windows  from all WS's

Additionally the patched scale plugin will allow a binding for window group for all workspaces to be set but not in scale bindings, it has to be done thru ccsm > commands with dbus enabled

Maybe at some point someone will ppa the scale revert if there is enough interest though wouldn't surprise me if there isn't.

---

