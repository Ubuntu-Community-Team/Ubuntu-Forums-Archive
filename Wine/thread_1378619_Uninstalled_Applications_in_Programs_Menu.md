---
title: "Uninstalled Applications in Programs Menu"
date: 2010-01-11
forum: Wine
---

### Post by dlfuller on 2010-01-11
I just started experimenting with WINE on 9.10 Karmic and it is working great. But in the process I installed and later uninstalled some applications. Now some of the names from those uninstalled applications remain in my Applications > Wine > Programs menu.

Clicking on one of those names leads to an Error dialog "No such file or directory". These applications all seemed to be successfully removed by their uninstallers except for these names.

I could not find any hint of the names in my .wine/drive_c/Program Files. Is what you see displayed in the Programs menu stored in a file somewhere else? Or more fundamentally, how do I get rid of the names in the menu?

---

### Post by mocoloco on 2010-01-12
Unfortunately wine doesn't yet do a thorough job of cleaning those things up.  The path you want is in the hidden folder ~/.local/share/applications.  Remove those shortcuts and or folders and they'll go away.  There's also stuff in ~/.local/share/desktop-directories.


*If you're not aware "~" refers to your home directory. You can see hidden files and folders in the file browser by hitting Ctrl+H.

---

### Post by Soulcage on 2010-01-12
Here are some commands to remove them [http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391]("http://wiki.winehq.org/FAQ#head-9893ae50079ca7a959258f0bc9a17aaf2e69b391")

---

### Post by anaconda on 2010-01-12
why not just right-click on the menu, and select "edit menus"? 
from thereyou can remove unnecessary programs from showing in the menu..

---

### Post by dlfuller on 2010-01-12
@mocoloco: Outstanding. Exactly what I needed to edit out those excess shortcuts.

The Wiki commands would remove all menu-entries which I was trying to avoid. And the Menu Editor only goes as deep as "Programs" in the hierarchy. These excess shortcuts were deeper, contained inside the "Programs" directory and not editable.

Thanks to you all for the suggestions.

---

### Post by Soulcage on 2010-01-13
I don't like using edit menu thing because all it does is edit the ~/.config/menus/applications.menu file changing the entries to become hidden.

---

