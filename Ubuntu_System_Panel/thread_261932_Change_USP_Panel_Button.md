---
title: "Change USP Panel Button?"
date: 2006-09-20
forum: Ubuntu System Panel
---

### Post by Uncle Spellbinder on 2006-09-20
I'd like to chnange the USP Panel button with one of the images below (I have a .png and .SVG). Which should I use and how might I do this?

---

### Post by sktx on 2006-09-21
Well, there's a lot of ways to go about doing this, but this is the way I figured out first, and as such, has been the way I've stuck with as long as I've been using Ubuntu.  

the default GNOME Applications menu logo is here:```
/usr/share/icons/hicolor/48x48/apps/distributor-logo.png
```

these are the steps that I follow to set up a symlink that points to whatever menu icon i happen to want that day:
```
cd /usr/share/icons/hicolor/48x48/apps/
sudo mv distributor-logo.png distributor-logo.old.png
ln -s ~/.pixmaps/menu-icon.png distributor-logo.png
cd ~
mkdir .pixmaps
```

then it's just a matter of copying/moving the new graphic to ~/.pixmaps/menu-icon.png ... once it's in there, to see your new graphics on the panel, enter this into your terminal:
```
killall gnome-panel
``` which will kill and restart your panel, forcing it to load the icon graphics again. 


You can try substituting .png for .svg in the **ln -s ~/.pixmaps/...** line, I'm pretty sure that works.  

For a more flexible solution, you can insert the graphic into one of your icon themes...

try to:
```
cd ~/.icons/*InsertThemeNameHere*/scalable/apps/
```

if you get an error saying that the dir isn't there, do this:
```
mkdir ~/.icons/*InsertThemeNameHere*/scalable/apps/
```

then, to copy the file into the theme:
```
cp LinSta_Start_Button.svg ~/.icons/*InsertThemeNameHere*/scalable/apps/distributor-logo.svg

```

From here, you can either switch your icon theme to something else, and back again, or:```
killall gnome-panel
```

Anyway, hope this helps... Lemme know if you have any problems.

..*sktx*

---

### Post by Uncle Spellbinder on 2006-09-21
Tried the second option, the image was tiny. I'll keep tryin' though.  Thanks! :D

---

