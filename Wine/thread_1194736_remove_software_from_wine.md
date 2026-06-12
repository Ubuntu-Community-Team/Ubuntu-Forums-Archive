---
title: "remove software from wine"
date: 2009-06-23
forum: Wine
---

### Post by Mia1990 on 2009-06-23
using the uninstall wine software there is a red x by all the software i have installed in wine does anyone know what this is and how i can uninstall software in wine i have tried to remove some for over a hour now i went to the terminal and did a sudo nautilus and deleted it that way but it did not remove it from program's menu thank you

---

### Post by bichopro on 2009-06-23
delete the hidden folder of wine on home maybe work, its .wine

---

### Post by Mia1990 on 2009-06-23
The hidden folder isn't that all there is?

---

### Post by themusicalduck on 2009-06-23
Uninstalling software from wine doesn't necessarily remove the menu items as well. You have to remove them manually by right clicking on Applications and selecting Edit menus. You can delete items from there. To delete an item from your panel just right click on the item and click Remove from panel.

Don't delete your .wine folder, it'll delete all your programs and configurations so far.

---

### Post by Bucky Ball on 2009-06-23
I have an ugly feeling you need to uninstall them USING WINE. I could be wrong, but that is how they got there; Ubuntu possibly has no idea what they are or how to get rid of them.

A hassle, but maybe install wine, uninstall the programs, unstall wine. Wine is messy (no joke intended); it leaves crap everywhere and it's seemingly impossible to completely uninstall all its files (just like a Windows gadget!). There are plenty of threads regarding this issue. You can get rid of Wine, but it leaves superfluous files that do nothing but sit there forever after, doing nothing, as you will discover if you uninstall wine, open a terminal and type/paste:

```
locate wine
```:)

---

### Post by Mia1990 on 2009-06-23
> **themusicalduck said:**
> Uninstalling software from wine doesn't necessarily remove the menu items as well. You have to remove them manually by right clicking on Applications and selecting Edit menus. You can delete items from there. To delete an item from your panel just right click on the item and click Remove from panel.

Don't delete your .wine folder, it'll delete all your programs and configurations so far.
omg thank you so much worked like a charm 

xoxo
Mia

---

### Post by Bucky Ball on 2009-06-23
Good. Now open a terminal and type:

locate wine

---

### Post by Mia1990 on 2009-06-23
ok but the software is still listed in the uninstall wine software and there is red x next to them the red x has always been there i don't know why any clue?

---

### Post by Bucky Ball on 2009-06-23
The method you have used has simply hidden items in your menu, it hasn't un-installed or deleted anything. 

Maybe re-read post #5, Mia. 

:)

---

### Post by Mia1990 on 2009-06-23
> **Bucky Ball said:**
> The method you have used has simply hidden items in your menu, it hasn't un-installed or deleted anything. 

Maybe re-read post #5, Mia. 

:)

ok i get wine some what.I need to uninstall the software using wine because that's how it got there ok what about any software i have not deleted i know wine flags software that has been removed but if i don't remove it will i need to reinstall it?

---

### Post by Mia1990 on 2009-06-23
never mind the last question i had a blond moment Lol:)

---

### Post by Bucky Ball on 2009-06-23
Ha! Yea, I was about to post back saying I was a little confused. I have those moments myself sometimes!

So, you have uninstalled Wine, there are programs still there that were installed with Wine?

Wine will not un-install Linux programs. Is this kinda what you are getting at?

---

### Post by Mia1990 on 2009-06-23
all up and going thank you so much your my hero.
Mia

---

### Post by Bucky Ball on 2009-06-23
Aw, Shucks! Better get my lycra suit out (which one though??). Seriously, it's a pleasure.

Glad to hear it's all up and happening. When wine is uninstalled (and the programs installed using it also), wine itself does leave a lot of it own artifacts/files about, but as I say, they do nothing and I can find no other way of killing them off than doing a complete re-install. If you discover some way let me know.

I installed wine, never used it and uninstalled straight away and have had the remnants on my machinefor over a year to no ill effect (like many other users). Just takes up space, nothing more, and occasionally p****s me off!

Happy Ubuntu-ing! :)

---

