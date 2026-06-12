---
title: "Replace deleted and reinstalled applications in WINE menu"
date: 2009-05-08
forum: Wine
---

### Post by violinist2009 on 2009-05-08
I've uninstalled some programs I had in WINE, and deleted their menu entries from the WINE menu in GNOME. Now, I've reinstalled some of them, but their menus no longer appear automatically in the menu. I've read a lot of threads on removing menu items no longer wanted or on manually adding menu items, but these programs had menu items added automatically when I first installed them, and they don't do the same when I try reinstalling. This makes no sense to me. Thanks for your help

---

### Post by cogadh on 2009-05-08
When you delete items from the Applications menu, they are not actually removed, but permanently flagged as deleted. You can undo this by opening the /home/<user name>/.config/menus/applications.menu file with a text editor and finding the Wine section. Remove the <Deleted/> flag from everything you want back. 

In the future, you can prevent this issue by simply unchecking things you don't want to see any more in the menu editor, instead of deleting them. That way, if you ever have a need to re-install something, getting the shortcuts back is as simple as rechecking the items.

---

### Post by andrea000 on 2009-05-30
> **cogadh said:**
> When you delete items from the Applications menu, they are not actually removed, but permanently flagged as deleted. You can undo this by opening the /home/<user name>/.config/menus/applications.menu file with a text editor and finding the Wine section. Remove the <Deleted/> flag from everything you want back. 

In the future, you can prevent this issue by simply unchecking things you don't want to see any more in the menu editor, instead of deleting them. That way, if you ever have a need to re-install something, getting the shortcuts back is as simple as rechecking the items.

Thank you so much for your post it fixed my problem

---

