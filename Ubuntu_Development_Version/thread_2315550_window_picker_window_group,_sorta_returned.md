---
title: "window picker window group, sorta returned"
date: 2016-02-29
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-02-29
The ability to use window picker for window group from *all workspaces* was broken in 11.04 & never returned. While it remains not settable via ccsm it has been returned to unity using Shift+Ctrl+Super+w on a focused window.

This is a bit unwieldy but can be altered by users by maybe in dconf ( see edit) or editing the unityshell gschema & re-compiling glib schemas. (not a process without danger..

For myself had been enabling this thru compiz via an integrated binding & dbus command but while that worked very well it required the set combo to be done exactly in order or bad things happened. Seeing as though I use Ctrl+Alt+z for single hand init that was always a possibility so this is a good deal from Marco Trevisan. 

Because altering locally could cause a big issue if done wrong will not post generic, if anyone wants to change to a specific binding that's not used elsewhere post & I'll take a look.
For myself will likely just alter the unity source to use my preferred one hand binding & let launchpad provide new unity packages as I also change the expo icon to work for rotate/cube/1x4 workspaces.

Edit: maybe one doesn't have to edit the schema, I see this editable value in dconf editor - screen

---

