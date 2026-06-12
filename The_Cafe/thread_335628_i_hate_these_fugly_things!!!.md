---
title: "i hate these fugly things!!!"
date: 2007-01-10
forum: The Cafe
---

### Post by fuscia on 2007-01-10
see those ugly little file icons (circled, in the attached pic)? that's a shot of thunar and i'm using it in openbox. before i dumped gnome and xfce, i had pretty little icons in thunar and i would like to have pretty little icons in thunar, once again. how can i do it without installing a whole bunch o'junk?

---

### Post by d3v1ant_0n3 on 2007-01-10
Can't you just change the icon theme?

---

### Post by fuscia on 2007-01-10
> **d3v1ant_0n3 said:**
> Can't you just change the icon theme?

i don't have gnome and xfce anymore.

---

### Post by tbroderick on 2007-01-10
Just install an icon theme like Tango and put this line in your ~/.gtkrc-2.0
```
gtk-icon-theme-name = "Tango" 
```

Change the theme name to whatever one you install.

---

### Post by picpak on 2007-01-10
Alternatively you could put

```
gnome-settings-daemon &
```

into your .xsession file (provided it's still installed).

Here's my .gtkrc-2.0 file for future reference:

```
gtk-menu-popup-delay = 100
gtk-menu-bar-popdown-delay = 100
include "/usr/share/themes/Carbonit/gtk-2.0/gtkrc"
gtk-icon-theme-name = "nuoveXT-1.6"
gtk-font-name = "Sans 9"
gtk-toolbar-style = GTK_TOOLBAR_ICONS

```

---

### Post by IYY on 2007-01-10
I usually just use gnome-settings-daemon, but there is a program called gtk-theme-switch which can be used as well.

---

### Post by G Morgan on 2007-01-10
Easiest way to get rid

#(snipped, just for safety's sake)

Not very helpful I know.




//Anyone who doesn't know that command do not try it under any circumstance.//

---

### Post by Lord Illidan on 2007-01-10
> **G Morgan said:**
> Easiest way to get rid

#(snipped, just to be safe)

Not very helpful I know.




//Anyone who doesn't know that command do not try it under any circumstance.//

as it basically erases your entire root directory...

---

### Post by fuscia on 2007-01-10
> **tbroderick said:**
> Just install an icon theme like Tango and put this line in your ~/.gtkrc-2.0
```
gtk-icon-theme-name = "Tango" 
```

Change the theme name to whatever one you install.

awesome! this is the kind of solution i dreamt about. you are a true openbox hero.

no more rheindeer games for G Morgan, btw.

---

### Post by K.Mandla on 2007-01-10
> **fuscia said:**
> see those ugly little file icons (circled, in the attached pic)? that's a shot of thunar and i'm using it in openbox. before i dumped gnome and xfce, i had pretty little icons in thunar and i would like to have pretty little icons in thunar, once again. how can i do it without installing a whole bunch o'junk?
I usually added tango-icon-theme-common and tango-icon-theme-extras to get rid of those awful things. Edit: Which is, I think, what you just did. :rolleyes:

---

### Post by fuscia on 2007-01-10
> **K.Mandla said:**
> I usually added tango-icon-theme-common and tango-icon-theme-extras to get rid of those awful things. Edit: Which is, I think, what you just did. :rolleyes:

i went with 'human'. i've got that whole 'human ultra' set somewhere, so i'll have to dig up 'green' and 'pink' when i'm more able to crawl out of the bag i just drank myself into.

---

