---
title: "Category missing from LXDE menu on Lubuntu 16.04"
date: 2017-12-12
forum: Ubuntu/Debian BASED
---

### Post by metalf8801 on 2017-12-12
I'm running OSGeo 11.0 which is based on Lubuntu 16.04

I tried to use menulibre to add gedit to lxde menu so I could open it faster. I didn't want to have to goto accessors first then click on gedit which was a big mistake because after I did that and restarted the computer the Geospatial category on the LXDE menu is now hidden and I can't unhide it using menulibre or menu://applications/

When I try in menulibre it says it's not hidden even though it is. If I try to hide Geospatial it automatically right after I save the change so I can't hide it and then unhide. 
When I right click on Geospatial in menu://applications/ I get the error "Menu path 'osgeo-main' already exists" 

If anyone knows what I should try next I would be grateful. 

Also does anyone know what directory or config file is edited when changes are made to menu://applications/ or better yet how I can find that out?

Thank you

---

### Post by ajgreeny on 2017-12-12
Not sure why it doesn't show in the LXDE menu but see if you can get it showing by copying its .desktop file to your ~/.local/share/applications folder with command ```
cp /usr/share/applications/gedit.desktop ~/.local/share/applications/
```
Logout and in again and you may find gedit, possibly under another name such as Text-editor, has appeared.

It may already be there but not named as gedit in the menu, so search first for that before copying the gedit.desktop file.
If you want it to be called **gedit** in the menu you may have to edit the desktop file line starting **Name=Text-editor** if that is what it says now to **Name=Gedit**.

---

### Post by metalf8801 on 2017-12-15
Thank you but I just solved the problem by 

logging in as guest 
copy the missing menu items from menu://applications/ to a flash drive logged out and logged back into my account then deleted the config files and the directory "applications-merged" in "/home/daniel/.config/menus" then copy the missing menu items into menu://applications/ and restarted the computer

Also Gedit wasn't missing I just just trying to put it some place where it could be opened faster and I did that by create a launch for gedit and putting it next to the main menu. 

Thank you for trying to help

---

