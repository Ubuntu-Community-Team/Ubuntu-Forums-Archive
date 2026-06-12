---
title: "Cant run any .exe file...."
date: 2009-05-03
forum: Wine
---

### Post by Just64 on 2009-05-03
If i try to run a .exe file, this apears 

[[IMG]http://img220.imageshack.us/img220/5922/pantallazop.th.png[/IMG]](http://img220.imageshack.us/my.php?image=pantallazop.png)

How i can remove Wine to reistall later? I try "sudo apt-get remove wine" and wine stills on aplications menu, even with add/remove i cant remove it...

---

### Post by cogadh on 2009-05-04
The shortcuts are always left behind after an uninstall, but the application itself is actually gone. As for the error you are getting, it is because Wine, for some reason, was not appropriately associated with .exe files. You can usually get around the issue by right-clicking on the executable and selecting "Open with Wine".

---

