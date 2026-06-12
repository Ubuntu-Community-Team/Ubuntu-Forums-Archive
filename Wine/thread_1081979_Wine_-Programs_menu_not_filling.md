---
title: "Wine -Programs menu not filling"
date: 2009-02-27
forum: Wine
---

### Post by davidsrsb on 2009-02-27
I just reinstalled wine 1.1.15 after wiping a few files by accident.
So I deleted .wine/ and now when I install any windows program the Applications-Wine-Programs menu is not populated.
If I manually set it up, it works except for finding the correct icon

---

### Post by smani on 2009-02-27
Likely you menu files are messed up too - I'd suggest to have a look in the following places and delete artefacts from the previous installation:
	~/.config/menus/applications-merged
	~/.local/share/desktop-directories
	~/.local/share/applications
Worst case, delete
	~/.config/menus/applications.menu
	~/.config/menus/setting.menu
to reset the entire menu.

You might also want to reinstall Wine after cleaning up so that it can create fresh menu entries.

---

### Post by Meow27 on 2009-02-27
ummm.. ..thats going to fix the wine directory or wipe all the menus out?

---

### Post by smani on 2009-02-27
It's up to you which items you want to remove, just go through those directories and remove the launchers you don't want anymore, and search for the respective entries in the *.menu files and delete them too.

---

### Post by davidsrsb on 2009-02-28
Thanks, that worked

---

