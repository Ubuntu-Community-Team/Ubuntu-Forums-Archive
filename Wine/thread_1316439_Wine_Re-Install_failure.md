---
title: "Wine Re-Install failure"
date: 2009-11-06
forum: Wine
---

### Post by kakashi_12 on 2009-11-06
I wanted to remove Wine, because there were incompatible programs that would not remove from the start menu, even though i told them to remove deep within the "c" drive. I thought uninstalling it would do the trick. I uninstalled and Wine still showed. So I removed Wine from the applications menu, and removed the hidden folder from my home folder (.wine) to get rid of all the files. I also marked it for complete un-installation in synaptics and the other package that came with it. Then I went ahead and installed it a 2nd time. When I did, it would not show in the Applications list. I tried logging off and back in and rebooting.

What should I do? Is there a linux equivelant for CCleaner? Maybe that will do it?

---

### Post by edin9 on 2009-11-06
You need to make a new menu entry for WINE. It has likely moved any WINE things that remained to the Other section.

---

### Post by kakashi_12 on 2009-11-06
wow. I didn't think that was going to work. But it did! :)
Now I just need to get my Wine icon back on that menu item somehow. I wonder if I can also get that "configure wine" application back in the folder too. thanx. big help.

---

### Post by edin9 on 2009-11-06
It's easy, just use the edit menu option and make an entry in the WINE section with the command ```
wine config
``` I would tell you the rest but I'm too lazy to write out a long explanation ATM :P

---

### Post by kakashi_12 on 2009-11-06
thanks. that made me find my wine icon too. now i just need to find my app icon or learn to create one.

---

### Post by jasonditz on 2009-11-06
> **kakashi_12 said:**
> wow. I didn't think that was going to work. But it did! :)
Now I just need to get my Wine icon back on that menu item somehow. I wonder if I can also get that "configure wine" application back in the folder too. thanx. big help.

~/.config/menus/applications.menu 

delete the <Delete/> key after the Wine entry and all your old Wine stuff reappears.

---

### Post by kakashi_12 on 2009-11-06
thnx. do you know what extension i can save in gimp to make an icon? tried icon extension but linux didnt see that. i also tried changing the ext manually to the extension that other icons are. i think that's svg or something. gimp does not have that ext, or else it would be an official change.

---

