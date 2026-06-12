---
title: "uninstall"
date: 2009-03-04
forum: Wine
---

### Post by djbenny on 2009-03-04
Hello

i uninstalled wine but the software i installed through wine remains there in the applications menu how can i get rid of it?

---

### Post by cogadh on 2009-03-04
Wine shortcuts are always left behind, you need to manually delete them using the menu editor (found under System > Preferences > Main Menu).

---

### Post by albandy on 2009-03-04
go to you home folder and remove the .wine folder

cd
rm -rf .wine

---

### Post by cogadh on 2009-03-04
That won't get rid of the menu shortcuts, they are not stored there.

---

### Post by albandy on 2009-03-04
> **cogadh said:**
> That won't get rid of the menu shortcuts, they are not stored there.

But I think he should remove the installed applications in .wine, remeber that it stores in .wine/drive_c all the windows installations

---

### Post by cogadh on 2009-03-04
Of course, but that's not what he was asking for. He wanted to know how to get rid of the shortcuts in the Applications menu. Deleting the .wine directory will do nothing for that. If you wanted to offer some additional advice on top of how to get rid of the shortcuts, you really should have said that, but the way you posted made it sound like you were saying that deleting the .wine directory would accomplish the removal of those shortcuts.

---

### Post by djbenny on 2009-03-04
cheers for the advice you guys!

---

### Post by Meow27 on 2009-03-04
never mind i misread the post.........

---

