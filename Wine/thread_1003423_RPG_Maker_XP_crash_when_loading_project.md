---
title: "RPG Maker XP crash when loading project"
date: 2008-12-06
forum: Wine
---

### Post by supersteviobros on 2008-12-06
I got RPG Maker XP to install through Wine, and although the toolbar menus don't work (known problem in the appdb) it still opens and I can create a new project folder. It creates a project folder with the project files in "C:\windows\profiles\username\My Documents\RPGXP\ProjectX"

However, when RMXP tries to open the project file, it crashes with no error message or anything, the window just closes. This is the terminal output:

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  53 (X_CreatePixmap)
  Serial number of failed request:  6162
  Current serial number in output stream:  6164

```

I don't know what this means, but maybe someone has an idea?

---

### Post by koneella on 2011-12-05
SOLVED,
i had the same problem..
i dunno why, but starting projects in FULLSCREEN crashes.
Open rpg maker, after that press it to SMALL WINDOWED mode, after that u can load projects without crashing, its same issue with VX

---

