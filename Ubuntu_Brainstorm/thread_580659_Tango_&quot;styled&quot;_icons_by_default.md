---
title: "Tango &quot;styled&quot; icons by default"
date: 2007-10-19
forum: Ubuntu Brainstorm
---

### Post by wedderburn on 2007-10-19
firstly this doesn't mean using tango, it means using the style  [http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines](http://tango.freedesktop.org/Tango_Icon_Theme_Guidelines) 

This is the same style guide that tango, tangerine,ubuntu-studio, gnome and most importantly every new gnome application uses.

reasons for doing this:

[LIST]
all gnome applications are having a tango face lift applications include pidgin and the gimp 2.4.[/LIST]

[LIST]currently ubuntu looks like a mishmash of icon themes kind of like if you run a kde app in gnome.[/LIST]

[LIST]we have the Human icon theme which fills in the common icons(folders drives etc) but the ones it skips are filled with gnomes default theme.[/LIST]

example:
[IMG]http://andrew.wedderburn.googlepages.com/icon_missmatch.png[/IMG]
this is from the gnome control panel as it illustrates my point the best 

The following look out of place:
[LIST]Network[/LIST]
[LIST]Shared Folders[/LIST]
[LIST]Users and Groups[/LIST]

these are all from the human theme
now compare this to tangerine (the tango styled version of the ubuntu theme)
[IMG]http://andrew.wedderburn.googlepages.com/tangerine_styled.png[/IMG]

as you can see it all looks coherent not like a theme pasted on top of another theme.

changing icons sets styles will retain the unique ubuntu look, but also achieve a higher level of professionalism.

---

### Post by Zdravko on 2007-10-19
I don't see much difference.

---

### Post by Orra on 2007-10-19
FWIW, I use the GNOME icon theme. During the GNOME 2.19 series on Gutsy, I saw many icons in the GNOME theme (especially the main menu) change to look more modern, and probably Tangoified. I expect that'll continue.

---

### Post by Zdravko on 2007-10-19
Aha, ok.

---

### Post by frup on 2007-10-19
I think more important than worrying about minor details of an Icon theme is to ask why both Tangerine and Human icon sets show up on VRMS!!! :( With the Kernel taking up 4 spots already having another needless 2 with something as unimportant as icons is heartbreaking. Interestingly VRMS doesn't seem to pick up restricted drivers :S

---

### Post by Zdravko on 2007-10-19
Hmmm. dunno what VRMS is... :(

---

### Post by frup on 2007-10-19
sudo apt-get install vrms

Virtual Richard Stallman, tells you how many and the percentage of non-free packages in your system.

---

### Post by Zdravko on 2007-10-19
Wow. Never really used it.

---

### Post by aamukahvi on 2007-10-20
I don't understand the reasoning behind dropping the Tango inheritance from Tangerine. Now it only inherits from Gnome-icons which is suboptimal IMO. I added a copy of Tangerine which inherits from Tango:
```
sudo aptitude install tango-icon-theme-common
cp -a /usr/share/icons/Tangerine ~/.icons/Tangerine-Tango
gedit ~/.icons/Tangerine-Tango/index.theme
```
Change the beginning of the file as follows:
```
[Icon Theme]
Name=Tangerine/Tango
Name[fr]=Tangerine/Tango
Comment=Tangerine Icon Theme
Comment[fr]=Thème d'icônes Tangerine
Inherits=Tango,gnome
Example=x-directory-normal
```

---

### Post by screaminj3sus on 2007-10-20
I agree the human icon theme needs some retouching, the tangerine theme looks much more professional and complete at this point.

---

### Post by happy-and-lost on 2007-10-20
> **frup said:**
> I think more important than worrying about minor details of an Icon theme is to ask why both Tangerine and Human icon sets show up on VRMS!!! :( With the Kernel taking up 4 spots already having another needless 2 with something as unimportant as icons is heartbreaking. Interestingly VRMS doesn't seem to pick up restricted drivers :S

VRMS picks up this on mine

> linux-generic             Complete Generic Linux kernel


:lolflag:

---

### Post by Zdravko on 2007-10-20
Hmm. That's weird.

---

