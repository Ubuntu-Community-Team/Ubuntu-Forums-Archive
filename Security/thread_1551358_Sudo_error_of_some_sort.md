---
title: "Sudo error of some sort"
date: 2010-08-12
forum: Security
---

### Post by dogdo on 2010-08-12
Whenever i try to access gufw, update manager or anything that requires sudo password i get the error '
Unable to copy the user's Xauthorization file.' WTF?

---

### Post by Bachstelze on 2010-08-12
How exactly are you running those programs? If you're running them from a termina, you're supposed to use gksudo instead of sudo for graphical apps.

---

### Post by dogdo on 2010-08-12
> **Bachstelze said:**
> How exactly are you running those programs? If you're running them from a termina, you're supposed to use gksudo instead of sudo for graphical apps.

no i not running them in the terminal-i trying to access these programs within the gnome interface. For example System - Administration- Firewall Configuration. Is this some sort of bug or have i been hacked?

---

### Post by bodhi.zazen on 2010-08-12
What are the ownership and permissions of ~/.Xauthority ?

---

