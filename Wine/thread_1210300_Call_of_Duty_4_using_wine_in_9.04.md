---
title: "Call of Duty 4 using wine in 9.04"
date: 2009-07-11
forum: Wine
---

### Post by pauelmaco on 2009-07-11
Hello

I installed Call of duty 4 using wine and the installations was very good, all work, but when I start the program, it says that:

  "Error during inizialization:
   Video card or driver doesn't support enough textures for the DirectX 9
   code path"

My video card is an Nvidia GeForce GT 120 (1024mb). I installed too DirectX 9 uxing wine.

What can I do?  Please, help me !!!!!

---

### Post by ackanao on 2009-07-11
Never install DirectX in Wine - that's your first mistake. Delete .wine folder, start terminal and type **winecfg** to recreate default wineprefix - then try again with CoD 4.

This page may help you:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5934")

---

### Post by Th3_uN1Qu3 on 2009-07-11
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804](http://appdb.winehq.org/objectManager.php?sClass=version&iId=12804)

First, patch the game to the latest version and get a NoCD. Second, if it does run, don't expect to get more than 10fps on lowest settings. :)

---

