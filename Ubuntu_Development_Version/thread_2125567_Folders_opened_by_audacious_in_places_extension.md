---
title: "Folders opened by audacious in places extension"
date: 2013-03-14
forum: Ubuntu Development Version
---

### Post by ft_ on 2013-03-14
Hi,

Since the today's (raring-proposed) update of desktop-file-utils (that affects /etc/gnome/defaults.list), when I choose e.g. "File system" in "Places menu" extension, the folder is opened by Audacious...
If I remove Audacious, Nautilus handle the selected folder, as usual.

Does this happen for somebody else ?

Thx

---

### Post by mc4man on 2013-03-14
Am assuming you mean in a gnome-shell session because this change has no apparent effect in a ubuntu session
Not sure why they made the change anyway, haven't seen a nautilus*.desktop with --new-window option in  sometime & the current nautilus has removed the option to open any dir. in something other than nautilus - dumb idea

You could try moving ~/.local/share/applications/mimeapps.list to a .bak & see if that 'fixes'. If so take a look in that file (.bak) & see what lines have audacious.desktop in 
If you don't have a mimeapps.list take a look in ~/.local/share/applications/mimeinfo.cache

---

