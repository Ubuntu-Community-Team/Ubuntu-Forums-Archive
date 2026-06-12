---
title: "I Screwed Up My Wine!!!"
date: 2009-03-05
forum: Wine
---

### Post by iheartubuntu on 2009-03-05
I cant believe I did this... was having some probs with wine apps after using winetricks to get some software to work. Anyways, I ened up completely uninstalling Wine, and for good measure I went and deleted my Wine Menu entries so it wouldnt appear anymore in Applications.

I then rebooted, reinstalled Wine (which I think works), but I have no Wine menu now. I feel naked without that Wine menu. is there any way to get it back? How do I access the Wine config panel to make changes to my Wine without my the config in my Wine menu?

Any help would be greatly appreciated! Thanks!

---

### Post by cogadh on 2009-03-05
Well, you can just use the terminal and type "winecfg" to configure Wine, but if you want to get the shortcuts back, open the /home/<username/.config/menus/applications.menu file with a text editor, look for the Wine section and remove the "</deleted>" from the end of it.

EDIT - BTW, in the future if you happen to screw up Wine again, don't bother with the uninstalling and deleting of shortcuts, just delete the .wine directory. Doing that restores Wine to its original clean configuration.

---

### Post by iheartubuntu on 2009-03-05
Thanks for the info. I forgot to add that I did indeed remove the .wine directory. But after removing my menus and reinstalling, I was unable to find anything :) I'll have to try your trick now to get the menus back. Many thanks!

---

