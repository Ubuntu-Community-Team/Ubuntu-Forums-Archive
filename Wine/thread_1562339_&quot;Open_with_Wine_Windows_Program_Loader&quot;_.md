---
title: "&quot;Open with Wine Windows Program Loader&quot; - Where?"
date: 2010-08-27
forum: Wine
---

### Post by ZeroLinux on 2010-08-27
I want to find "Open with Wine Windows Program Loader" in the system to change default parameters to run *.exe files
The problem is in that I want to add string 
"env LANG="ru_RU.CP1251" before wine for every program starts with right default locale.
With that parameter I can type Cyrillic symbols in programs, but without it's impossible.
Or how to pass particular locale to wine as default? (Now I am using shortcuts with right environment viriable, but I need to have it by default for all new programs)

---

### Post by YokoZar on 2010-08-27
Is your system set into a Russian locale normally?  This shouldn't be the sort of thing a user would have to set manually.


Regardless, to answer your question, the file is at /usr/share/applications/wine.desktop  and you can edit the "exec" line.

You can also try adding *export LANG="ru_RU.CP1251"* to your ~/.bashrc

---

### Post by ZeroLinux on 2010-08-28
> **YokoZar said:**
> Is your system set into a Russian locale normally?  This shouldn't be the sort of thing a user would have to set manually.

Usually I install system in English to have normal names for folders such as "Desktop", "Documents" and the localize system without giving a permission to rename folders.

> **YokoZar said:**
> You can also try adding export LANG="ru_RU.CP1251" to your ~/.bashrc


This way doesn't work. (I made logout and even full reboot). Where is the problem?
The first one with exec does. (I changed exec to Exec=env LANG="ru_RU.CP1251" wine start /unix %f)

Thanks for your answer

---

