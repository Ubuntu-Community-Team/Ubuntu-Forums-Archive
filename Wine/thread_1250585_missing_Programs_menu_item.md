---
title: "missing Programs menu item"
date: 2009-08-26
forum: Wine
---

### Post by nhasian on 2009-08-26
i know i screwed this up myself.  during my troubleshooting i completely uninstalled wine.  of course that left the menu items under applications.  So I right Clicked on Applications, and choose edit menus.  then i opened up the wine menu item and *manually removed the Programs folder*.  okay now how do i get that back?

i did a complete removal from synaptic, and i also deleted the .wine folder in my home directory.

when i install the latest version of wine from winehq now it creates the menu item Wine in the applications list, but the Programs submenu is missing.  I still have the other three items Browse C:, Configure Wine, Uninstall Wine.  When i install an application via wine, it does not get added to the menu because Programs is missing.  on a fresh wine install isnt it suppose to have notepad in there?

I should note that wine appears to be working fine for me.  if i browse the c: drive i can execute the .exe and it runs fine.  My only problem is that i'm missing the program files menu :(

---

### Post by andrea000 on 2009-08-27
When you delete items from the Applications menu, they are not actually removed, but permanently
flagged as deleted. You can undo this by opening the /home/<user name>/.config/menu/applications.menu
file with a text editor and finding the Wine section. Remove the <Deleted/> flag from everything you
want back and the programs menu should come back.

---

### Post by nhasian on 2009-08-28
andrea000,

you are a lifesaver!  I was pulling my hair out trying to figure out how to get back to square one with a fresh installation of wine.  As i mentioned earlier my wine was working fine but when i installed apps, they werent appearing in the programs folder which i had inadvertantly deleted and couldnt get back.  Per your instructions, I removed the <Deleted/> flag from /home/<user name>/.config/menus/applications.menu and all was right with the world again.

---

### Post by andrea000 on 2009-08-28
Glad i could help

---

### Post by abijah on 2009-09-08
I had the same problem.  I reinstalled wine a few times, and un-installed the windows apps that I had in those previous wine set-ups. 

However, those old apps are now in my "Wine>Program" menu.

What's the best way to get rid of those menu items.

---

### Post by hikaricore on 2009-09-08
Open the menu editor and disable them.

---

