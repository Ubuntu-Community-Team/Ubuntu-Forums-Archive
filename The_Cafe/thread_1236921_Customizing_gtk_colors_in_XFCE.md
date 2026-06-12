---
title: "Customizing gtk colors in XFCE"
date: 2009-08-10
forum: The Cafe
---

### Post by element_G on 2009-08-10
Of all the ubuntu variants I've tried, I am most happy with XFCE (so far). I've always cared about how my system looks and how easily I can customize and achieve a look I am happy with. 

Finding the right gtk theme hasn't been too much of an issue but while looking I have found one in particular called " Any Color You Like" which supposedly uses the bg color setting to define the look of windows and widgets. 

I know you can find these settings in the Gnome Appearance settings but I have no clue how to do this in XFCE, please help!

---

### Post by RiceMonster on 2009-08-10
Xfce doesn't have a dialog like that. You have to edit the theme's gtkrc

---

### Post by element_G on 2009-08-10
thanks for the tip

I had a look at the gtkrc file and it is riddled with references to 
bg_color
fg_color
selected_bg_color
selected_fg_color
text_color
base_color

how do I set these values in the gtkrc file? or do I have to change each value to something absolute? also what color syntax do I use in a gtkrc file ( #252525 or 252525 with/without quotes?)

sorry for all the questions, I am very new to this

---

### Post by kerry_s on 2009-08-10
> uses the bg color setting to define the look of windows

menu-> settings-> desktop

can you put a link to that theme please, i would like to try it. 
thanks :)

---

### Post by element_G on 2009-08-10
> **kerry_s said:**
> menu-> settings-> desktop

can you put a link to that theme please, i would like to try it. 
thanks :)

As far as I know that option just changes the color of the desktop. Here is the link for the theme I'm using [http://www.gnome-look.org/content/show.php/Any+Color+You+Like?content=101017](http://www.gnome-look.org/content/show.php/Any+Color+You+Like?content=101017)

Using the program gnome-color-chooser as mentioned on the theme's page has allowed me to change some of the colors but it is all screwy and inconsistent :( what's the right way to do this??

---

### Post by element_G on 2009-08-11
bumping for justice

---

### Post by kerry_s on 2009-08-11
did you make sure you got all the needed engines?

> **It uses the clearlooks, murrine, industrial and hc engine**. All of them comes pre installed in at least Ubuntu, probably in many other distributions to.

since your using xubuntu not ubuntu might want to check that.

---

### Post by element_G on 2009-08-12
clearlooks? check
murrine? check (SVN version)
industrial? check
hc? (high contrast) check

I know for sure that the "Any color you like" theme functions properly because when it is selected in xfce appearance settings the widgets do change properly (no ugly win95 look). 

Thanks for asking though, I have run into engine dependency issues a few times with murrine not being svn and aurora and candido etc.

---

