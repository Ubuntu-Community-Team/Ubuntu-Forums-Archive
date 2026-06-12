---
title: "Applications Menu (Main Menu) customization in Lubuntu 20.04 LTS (LXQt)"
date: 2020-06-29
forum: Tutorials
---

### Post by GhX6GZMB on 2020-06-29
*Note: probably also works for other flavors of Ubuntu, but I am not able to test it.*

The Applications Menu (bottom left corner of the screen) in Lubuntu is NOT some "menu file", so there's no reason to search for it, it doesn't exist.

Rather, it's a "frame", filled with content every time you (or others) login, making it user specific. The basic menu structure is defined in:
```
/etc/xdg/menus/lxqt-applications.menu
```
It defines the names/headlines of the menu items shown at the first/main level and assigns these names to **Categories** (more about that a bit later).
**I most strongly discourage you from changing this file!** But using it as lookup reference is a good idea.

 The real content of the menu is read from .desktop files, one or more category entries per file; [U][B][COLOR=#b22222]modifying the Applications Menu is done by editing the .desktop files.[/COLOR]
[/B][/U]
The .desktop files are located in:

Admin user:
```
/usr/share/applications
```
Normal user:
```
$HOME/.local/share/applications
```

Each .desktop file contains a line called Categories. This parameter determines the location of the menu item in the Applications Menu. The basic/mandatory categories defined for Linux systems are:
```
AudioVideo
Audio   
Video   
Development 
Education   
Game    
Graphics    
Network 
Office  
Settings
Utility
``` 
If you look in:
```
/etc/xdg/menus/lxqt-applications.menu
```
You'll find exactly these there, and also the association to the Applications Menu headlines.

Now to changing the Applications Menu for real:


[LIST=1]
[*]**Removing an item from the Applications Menu:** sudo edit the .desktop file in question and add the line: NoDisplay=true
[*]**Relocate an item in the menu:** sudo edit the .desktop file in question and locate the line "Categories". Change the category according to the list above.
[*]**Add a new menu entry:** the best approach is to copy an existing .desktop file and modify it to your program/name/category.
[/LIST]

Cheers.

---

