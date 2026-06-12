---
title: "clean up the 'open with' list"
date: 2010-06-29
forum: Wine
---

### Post by mrkazoodle on 2010-06-29
Hi

After I installed office 2007 through wine, the 'Open With' list had multiple entries of the same programs.
The programs in the open with dialog can be found in:
[INDENT]~/.local/share/applications[/INDENT]
These are .desktop files, the extension is only visible if the file doesn't have execute privileges.
I gave all the wine applications (wine-extension-NAME.desktop) execute privileges, so the real program name becomes visible.

[INDENT]chmod **+**x FILE(S)[/INDENT]

Next I deleted all the duplicate entries and removed the execute privileges (chmod **-**x FILES).


All these 'wine' .desktop files didn't have icons, so I opened them in Gedit, as well as the shortcuts from the gnome menu (you can drag them from the menu into gedit) and copied the 'Icon=....' line. That does the trick.

---

### Post by K.Mandla on 2010-06-29
Moved to Wine subforum.

---

### Post by semafor on 2010-11-14
deleted

---

