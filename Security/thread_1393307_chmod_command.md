---
title: "chmod command"
date: 2010-01-29
forum: Security
---

### Post by Mall Zombie on 2010-01-29
i used the chmod ugo+rwx command in the usr/share/games directory to edit some game files. I was just wondering if it is at all safe to use the chmod command like this?

---

### Post by gradinaruvasile on 2010-01-29
In principle, its not safe. Better off just edit the files with sudo.

---

### Post by Mall Zombie on 2010-01-29
i used sudo thunar to edit the files but when i went to play the game the files i edited werent usable. is there a workaround to this?

---

### Post by gradinaruvasile on 2010-01-29
Not thunar... The text editor
In a terminal:

gksudo gedit filename

Or graphically: press alt+f2 and type:

gksudo gedit filename

Or mousepad instead of gedit for xubuntu. The filename is with full path (ex: /home/user/text.txt).

---

### Post by Mall Zombie on 2010-01-29
ok ill give that a go.

---

### Post by Mall Zombie on 2010-01-29
Doh! my bad i ment that i  was moving around files with thunar and the only way i could use the cp command to move files were to chmod the usr/share/games folder.

---

### Post by cariboo on 2010-01-29
You should be able to run thunar as root. Try Alt-F2:

```
gksu thunar
```

---

