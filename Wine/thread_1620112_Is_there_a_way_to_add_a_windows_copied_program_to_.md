---
title: "Is there a way to add a windows copied program to the WINE menu?"
date: 2010-11-12
forum: Wine
---

### Post by Aydos on 2010-11-12
Hello,

I know when I install a Windows game with WINE it adds it into the WINE menu to launch it.

I am wondering if there is a way to add a copied over game to the menu.

I have a perfectly good and updated install of WoW on my windows drive that I launch from my Ubuntu drive and I am wanting to just copy it over to the Ubuntu drive.

Is there any way to add it to the menu after I have drag and drop copied the whole WoW folder over?

For anyone who does not know the WoW folder is 100% portable. You can cary it on you iPod and launch it for windows, linux, or mac if needed.

---

### Post by sikander3786 on 2010-11-12
If it is portable as you mentioned, just try copying it to your home directory and try to launch *.exe using wine. If it runs, you can move that folder to wine's hidden directory that is /home/.wine/drive_c. Moving it there will not make any difference except putting it in the right place as it would have installed to using Wine.

You'll need to press Ctrl + H in your home directory to see hidden files.

Once done, go to System > Preferences > Main Menu and add a custom entry to your Applications > Wine menu regarding WoW.

Hope this helps.

---

