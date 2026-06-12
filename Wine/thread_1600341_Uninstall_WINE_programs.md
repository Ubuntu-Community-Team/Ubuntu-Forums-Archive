---
title: "Uninstall WINE programs"
date: 2010-10-18
forum: Wine
---

### Post by henrywm on 2010-10-18
How do I uninstall programs installed with Wine with Ubuntu 10.10?

---

### Post by marl30 on 2010-10-19
Go to the Wine menu then scroll down to "uninstall Wine programs", or you can use a freeware uninstaller  such as Revo Uninstaller.

[http://download.cnet.com/Revo-Uninstaller/3000-2096_4-10687648.html](http://download.cnet.com/Revo-Uninstaller/3000-2096_4-10687648.html)

---

### Post by cogadh on 2010-10-19
If the program installed its own uninstaller shortcut in the menu, you can usually use that as well. It doesn't always work, but then again, neither does the Wine uninstaller.

---

### Post by sikander3786 on 2010-10-19
Some shortcuts don't go away from Wine menu after uninstallation. You can manually remove them from ~./.local/share/applications/wine/Programs.

If uninstallation doesn't work, you can delete the whole folder of related software from ~/.wine/drive_c/whatever-software. But that tool, only as a last resort.

---

