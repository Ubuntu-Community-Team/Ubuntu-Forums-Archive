---
title: "How To Delete A Folder?"
date: 2009-07-11
forum: Wine
---

### Post by Lollating on 2009-07-11
Hello Ubuntu users !

I just installed some stuff like Wine (Not what i thought it was)
And I whant to delete wine, I uninstalled it etc..
but the Folder is still there!

How can I delete A folder ?


Thank you.


Lollating

---

### Post by Alias1407 on 2009-07-11
I will assume that you want to delete your .wine folder, the one in your home directory...

```
rm -r ~/.wine
```

That will delete the .wine folder in your home directory.

If you want to delete a specific folder then use...

```
rm -r /*insert folder path*/
```

---

### Post by jpeddicord on 2009-07-11
If you mean the category in the menu:
[LIST=1]
[*]Right-click on the menu bar (the main set with "Applications, Places, System") and selecy Edit Menus
[*]Find Wine on the left pane
[*]Find the categories you wish to remove on the right pane, and select Delete.
[/LIST]

---

