---
title: "how to achinve this look in feisty fawn"
date: 2007-05-20
forum: Ubuntu Customization Guide
---

### Post by kystorms on 2007-05-20
Hi everyone

I have run across this screen shot and this is exactly what I had hoped to do with Feisty Fawn

does anyone know if these transparent windows and such are available in beryl with feisty? I already have FF running perfectly however I do not see where this option for transparent windows would be and where i go to get this program they are running in this screenshot
[URL="http://www.kde.org/screenshots/images/3.2/snapshot10b.png"]

http://www.kde.org/screenshots/images/3.2/snapshot10b.png
[/URL]
thanks everyone, you guys are always so helpful

:KS

---

### Post by James Bennett on 2007-05-20
The transparency for the terminal window is a basic option, if I recall right, but I'm not sure how they got the menus transparent as well. 

I don't have KDE installed right now, but maybe they have those transparent menu windows because they have set up the terminal transparency?

---

### Post by kystorms on 2007-05-20
we in looking at the beryl info on thier website

it says that in beryl one can right click on a title bar to change this opacity

and I try with all my different programs , but it wont work, no options when i right click'

now, i use beryl from the red icon not as a start up option in sessions, can that be the problem? 
if so, how would i make beryl an option for start up session?

thanks:KS

---

### Post by deadlydeathcone on 2007-05-20
I haven't actually done such a thing myself, but a plugin exists that will turn a specified color transparent whenever it appears in a program, and that's probably how this was achieved.

---

### Post by Brackish_zygote on 2007-05-22
I don't actually know the answer to your first question. However, I do know how to make Beryl a startup session. Go to System > Preferences > Sessions. On the Startup tab click new, and type in for name and command "Beryl-manager". I can't say whether this will help or not, but if you want, now you can try.

---

### Post by tmogeem on 2007-05-25
to make the terminal transparent, open the terminal, then click anywhere inside it with ur right mouse button .. then edit current profile, in the effects tab, choose transparent background .. 

then u choose the options u wanna make .. i.e. background color

---

### Post by iceportal on 2007-05-26
That basic transparency has been an option in KDE for ages... Long before Beryl or Compiz.

What I see there isn't a special desktop effect, it's just KDE transparency.

BUT I could be wrong.

---

### Post by mkoehler on 2007-05-29
Like everyone else was saying, the transparency has been an option in KDE for quite a while now.  In addition, you can also change the opacity and theme of the windows by getting emerald, packages "emerald" and "emerald-themes" (you can also download more themes online).  Finally, although it may not be completely what you want, you can set windows to become opaque when you hover other windows by loading the beryl manager then going to Accessibility>Opacify, enabling it, and playing around with those settings.  I hope this helps.

---

### Post by wouterla on 2007-05-29
Though the transparency has been available in kde/konsole for a while, there is also a patched version of konsole available (though you may have to compile it yourself) that has **real** transparency.

The default transparency is 'snapshot' based, and won't show underlying windows, just the desktop background. 'Real' transparency works as a composite effect, and will show, for instance, a movie playing underneath the konsole.

---

### Post by phearnot on 2007-05-30
Beryl suports transparency for different types of windows. In the Beryl Settings Manager, navigate to the Window Management tab and select Set Window attributes by various criteria.

Here you can set opacity for, say, a window who's owning process is gnome-terminal.
Or, make menus appear transparent by adding 
```
w:DropdownMenu:90
w:PopupMenu:90
w:Menu:90
```

For more info, [http://www.beryl-project.org/faq.php#ub4](http://www.beryl-project.org/faq.php#ub4)

---

### Post by Xbehave on 2007-05-30
KDE deafult install
settings one of the window themes not sure which
menu transparecy is also in options
background also in options

that's a basic Kubuntu install, im in my edge right now but if you want the actual settings just ask and ill post them

---

### Post by Alex&amp;Linux on 2007-06-08
Im sure this is a well known idea, but if transparency of various windows is desired, the beryl window manager allows for this to be adjusted on the fly by holding "alt" and simultaneously using a mouse wheel (up increases opacity, while down decreases it).

I dont see too much reason to worry about menus being less than 100% opaque, but app windows can be usefully decreased in that regard.

---

### Post by vikrant82 on 2007-07-09
This feature is defaulty enabled these days with compiz fusion.

---

