---
title: "Changing login password in ubuntu 10.10"
date: 2011-01-04
forum: Security
---

### Post by mukla.c on 2011-01-04
I have installed ubuntu 10.10 . I gave a login password at the time of installation . But now, I want to change my password. How I can do this?.... plz help me as soon as possible

---

### Post by PapaNerd on 2011-01-04
Open a command window, then enter:```
passwd
``` or, if you want to change another password:```
sudo passwd <username>
```

---

### Post by cariboo on 2011-01-04
The gui way to change your password is to open System-Preferences->About Me. Doing it this way makes sure that the gnome-keyring password is changed at the same time.

---

