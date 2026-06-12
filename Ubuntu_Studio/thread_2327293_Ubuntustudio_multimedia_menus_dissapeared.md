---
title: "Ubuntustudio multimedia menus dissapeared"
date: 2016-06-09
forum: Ubuntu Studio
---

### Post by cjdg on 2016-06-09
i today after upgrade i lost all the multimedia menus

---

### Post by QDR06VV9 on 2016-06-09
Any changes that the menu editors make are saved to the ~/.config/menus and ~/.local/share/desktop-directories directory. _**If you want to try a fresh start, rename those directories:**_

```
mv ~/.config/menus ~/.config/menus.backup
mv ~/.local/share/desktop-directories ~/.local/share/desktop-directories.backup
```

...and you should get back your distro default menu structure.
(And since you've renamed them, all you have to do is rename them back and you will return to the configurations you currently have).

---

### Post by yoshii on 2016-06-15
I had the same problem, but I fixed it by deleting a certain file that gets rebuilt automatically:  [http://ubuntuforums.org/showthread.php?t=2327706](http://ubuntuforums.org/showthread.php?t=2327706)

---

