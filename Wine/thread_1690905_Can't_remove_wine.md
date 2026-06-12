---
title: "Can't remove wine"
date: 2011-02-19
forum: Wine
---

### Post by Cha0sBG on 2011-02-19
So i've downloaded, patched, compiled wine 1.3 and installed it via tearminal.  But the problem is when i try to remove it via ```
 sudo apt-get remove --purge wine
``` it says that the package wine is not installed tryed with 1.3 etc but nothing seems to work. I wanna completely remove it and start over as it never existed on my computer + delete the installed programs, files, dlls etc that i messed with. Any help ?

---

### Post by An Sanct on 2011-02-19
This is from the official FAQ
> **5.3. How do I uninstall Wine?**

 If you  installed Wine with your distribution's package manager, use the package  manager again to uninstall Wine. (If you installed Wine from source,  then use make uninstall in the source directory to remove it.) 
This won't uninstall your Windows apps, though; see above for that.

You may also want to delete .wine directory in your home folder.

---

### Post by Cha0sBG on 2011-02-19
Ok ty i've deleted it and ( if my .wine is in $HOME ) i've deleted that too, Are all the programs , dll's etc in my .wine folder ?

---

### Post by An Sanct on 2011-02-19
Yes, ~/.wine contains your "C:" drive location

This is true with a normal install from the repo, I don't know if it is accurate with a custom compile. If you have wine in your menu, there should also be a "Browse C: driver" option, do that and you will see where it is.

---

### Post by BlackStar.pt on 2011-03-01
This worked with me:

> sudo apt-get remove wine

apt-get autoremove

Then, _right click under Applications>Edit Menus_ and _uncheck_ Wine folder.
:popcorn:

---

