---
title: "Wine under the Applications Menu"
date: 2009-06-09
forum: Wine
---

### Post by twjolson on 2009-06-09
I uninstalled Wine some time ago, and the submenu for Wine persisted afterwards, so I manually removed it from the Applications menu.  Now, I reinstalled more recently, but the wine menu did not return.  Is there a way to put that back?

---

### Post by lightstream on 2009-06-09
System > Preferences > Main Menu

---

### Post by twjolson on 2009-06-09
Thanks for the quick reply.

I know about editing the main menu, unfortunately I know the removing part much better than the adding part.  How do I add the Menu that was put there when wine was originally installed?  With the "Browse C:\" for instance, not just a shortcut to wine though.

---

### Post by lightstream on 2009-06-09
hmmm, dunno a good way... I presumed that it not returning when you reinstalled meant it was still in the menu, just hidden.

"Browse C:\" has the following command: **xdg-open .wine/dosdevices/c:**

"Configure Wine" is **winecfg** of course, and "Uninstall Wine Software" is **uninstaller**.

Probably not really the solution you wanted though, sorry.

---

### Post by twjolson on 2009-06-09
It doesn't have to be pretty, it just has to work; thanks for the help!

---

### Post by andrea000 on 2009-06-09
> **twjolson said:**
> I uninstalled Wine some time ago, and the submenu for Wine persisted afterwards, so I manually removed it from the Applications menu.  Now, I reinstalled more recently, but the wine menu did not return.  Is there a way to put that back?

you should just go and install wine then the only one that shouldn't show up is the programs menu.
Is that the menu you are talking about the menu were you start your software from?

edit:sorry

When you delete items from the Applications menu, they are not actually
removed, but permanently flagged as deleted. You can undo this by
opening the /home/<user name>/.config/menus/applications.menu file with
a text editor and finding the Wine section. Remove the <Deleted/> flag
from everything you want back.

---

### Post by twjolson on 2009-06-14
That worked beautifully, thank you

---

### Post by cogadh on 2009-06-14
In the future, don't actually delete anything using the menu editor. Instead, just un-check them so they are no longer shown, but can be easily brought back if you ever have need to re-install the application.

---

### Post by jdogface on 2009-06-27
Andrea you rule. Thank you thank you thank you.
Did I remember to say thank you? If not, thank you.
If I did remember to say thank you, then I'll say it one more time;
THANK YOU.

---

### Post by andrea000 on 2009-06-30
your welcome glad i could help

---

### Post by rijidij on 2009-07-17
I had exactly this problem too.
Thanks Andrea. You rock! :D

---

