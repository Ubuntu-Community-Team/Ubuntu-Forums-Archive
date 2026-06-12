---
title: "global menu broken in 13.04"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by georgelappies on 2013-04-15
Hi all 

13.04 is looking good. Is it a known issue that the global menu's items does not lit up on a mouse over. Especially in LibreOffice.

---

### Post by Frogs Hair on 2013-04-15
No problems here so far . The lo-menubar for Libre Office is in the repository, but the global menu should be working AFAIK.

---

### Post by serdotlinecho on 2013-04-15
Working fine for me too on Writer, Calc and Impress when maximize and hover to the top panel. Maybe try delete this folder or reinstall?

```
rm -rf ~/.config/libreoffice/
sudo apt-get install --reinstall libreoffice-base-core libreoffice-core
```

---

### Post by pfeiffep on 2013-04-15
My installation 32 bit 13.04 just updated, upgraded, dist-upgraded doesn't have this problem:)

---

### Post by pnarciso on 2013-04-15
> **georgelappies said:**
> Hi all 

13.04 is looking good. Is it a known issue that the global menu's items does not lit up on a mouse over. Especially in LibreOffice.  

Known issue, and no fix yet. Here's the bug report [https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1153350](https://bugs.launchpad.net/ubuntu/+source/indicator-appmenu/+bug/1153350)

---

