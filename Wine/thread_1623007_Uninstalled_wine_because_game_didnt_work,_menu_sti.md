---
title: "Uninstalled wine because game didnt work, menu still showing programs."
date: 2010-11-16
forum: Wine
---

### Post by jotto! on 2010-11-16
I installed wine as I wanted to play BF1942 which I have done before using wine. Whilst I was at it I installed Desert Combat Final, a mod for BF1942 and a game on Steam, Counterstrike source.

Anyway, I started BF1942 and it just hung at the black screen, locking up PC.

Unintalled wine and removed .wine folder from home directory but I still have wine showing on my menu with Programs complete with DC Final and Steam still showing.

Tried reinstalling BF1942 but it still locked up so tried uninstalling again...same results.

I want to remove the menu and completely wipe the system of Wine and start again.

Any ideas?
TIA!

---

### Post by Sugi on 2010-11-16
To remove the menu items:
System > Preferences > Main Menu

But this won't affect your results trying to get the game to run correct.

Sugi

---

### Post by jotto! on 2010-11-16
So is the .wine folder the only thing thats installed with wine or are there other files somewhere?
I tried the sudo apt get purge command ( or something similar, googled! ) and it told me nothing would happen as wine wasnt installed. 

Just want to make sure I get rid of all remnants of it before trying again.

---

### Post by Soulcage on 2010-11-17
Uninstalling wine is only necessary if you don't want it anymore, instead you run this command into a terminal ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```

---

### Post by jotto! on 2010-11-17
> **Soulcage said:**
> Uninstalling wine is only necessary if you don't want it anymore, instead you run this command into a terminal ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
```


Copied and pasted that code in to terminal but it didnt appear to do anything. :confused:

---

### Post by jotto! on 2010-11-17
Also, now have no Programs item in the menu, ie Programs > Accessories etc etc

---

