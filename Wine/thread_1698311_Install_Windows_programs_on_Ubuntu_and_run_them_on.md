---
title: "Install Windows programs on Ubuntu and run them on Windows"
date: 2011-03-02
forum: Wine
---

### Post by Alin_X on 2011-03-02
Hello,
I have a PC with Windows XP/Vista and Ubuntu. Is there any way to install a Windows program in Ubuntu (while booted in Ubuntu), and then run it on Windows as if it was installed normally? (e.g. using wine, or modify the Windows System files in Ubuntu)
Note: I don't want to use a Virtual Machine :D but any other ideas would be highly appreciated :)
Thanks in advance,
Alin

---

### Post by cogadh on 2011-03-02
Not possible. Allowing Wine to interact with Windows will wreck you Windows installation and allowing Windows to interact with Wine will wreck your .wine directory. The main problem is the Windows and Wine registries, they are not compatible with each other.

---

