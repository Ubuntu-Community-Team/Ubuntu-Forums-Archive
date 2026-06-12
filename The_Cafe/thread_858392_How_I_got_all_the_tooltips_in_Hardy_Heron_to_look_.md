---
title: "How I got all the tooltips in Hardy Heron to look the same color in themes. (fix)"
date: 2008-07-13
forum: The Cafe
---

### Post by nowshining on 2008-07-13
Hardy Changed the way tooltips or should I say gnome changed the way tooltips are shown so some themes get half the tooltips ie: rhythmbox, etc..  get the color chosen in the theme, and not the clock as i've noticed. Due to this, I have found a way to get all tooltips the same color, etc.. All I did was add the below in code tags to the bottom in the gtkrc file and it worked, Altho if need be one may need to remove the ol' tooltips rule - if not you can try removing the "S" off any tooltips which also helped on some themes. :). 

I typed out this post incase someone else if wondering how to get all the tooltips the same color. Note: tho that things may be a bit diff. depending on the theme, hopefully this works for you. Remember tho to save, go into appearance and themes - select another theme and re-select ur theme to reset the colors or logout and back in. ;) Also note this may help get older themes to display the tooltips correctly.

```
#Tooltip color
class "GtkSpin*" style "spin"

style "tooltip"{
 bg[NORMAL]   		= "#FDFF9F" #tooltip color
 bg_pixmap[NORMAL]      = "<none>"
}

widget "gtk-tooltip" style "tooltip"

style "tooltip"{
 bg[NORMAL]   		= "#FDFF9F" #tooltip color - make same as above
 bg_pixmap[NORMAL]      = "<none>"
}

widget "gtk-tooltips" style "tooltip"
```

.......
To help with colors - so u don't have to open up gimp everytime you want a color, 

```
sudo apt-get install gcolor2
``` & by default it will show up in the Graphics Sub-Menu.

---

