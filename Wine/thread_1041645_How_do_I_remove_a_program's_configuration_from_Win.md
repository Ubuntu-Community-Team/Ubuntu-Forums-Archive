---
title: "How do I remove a program's configuration from Wine?"
date: 2009-01-16
forum: Wine
---

### Post by hexilum on 2009-01-16
I've tried using the wine uninstaller and just simply deleting specific folders in the .wine directory. But program traces keep oddly reappearing. 

I'm trying to uninstall a copy of Ventrilo on my system, and don't know where to look. 

Can someone with experience list some directories I would most commonly look in.

---

### Post by hexilum on 2009-01-16
So far, from my valiant attempts I've found:

```
rm -rf $HOME/.wine
```
removes the ~/.wine directory and all programs installed under Wine.

```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

```
removes all wine created menu and desktop entries

Is there anything else I should know about? I still see WINE @ '**Applications -> Wine**', and whenever I type 'wine --version' in the terminal. I get a prompt stating me the version of WINE.

---

### Post by hikaricore on 2009-01-16
You didn't uninstall WINE you just removed it's configuration files.

If you want to uninstall wine you'll need to run:

```
sudo apt-get remove wine
```

Or if you need to remove it and it's config files:

```
sudo apt-get remove --purge wine
```

This can also be done from any GUI package manager.

---

The gnome application menu is completely unrelated to WINE and still doesn't work 100% correctly.
From what I've seen it works and adds icons until people start doing stupid crap like removing WINE over and over and reinstalling the same programs over and over.
Eventually it will be better integrated into WINE, until then just disable the WINE menu or leave it alone.

---

### Post by hexilum on 2009-01-16
Thanks a lot!

---

### Post by hikaricore on 2009-01-16
In the future if you're just trying to wipe out all traces of your WINE config and start from scratch, removing the .wine directory then running winecfg (or any other program via WINE) will recreate the base directory and you'll be starting fresh.

Menu icons aside because I'va already discussed them.

---

