---
title: "Removing Titles?"
date: 2007-03-28
forum: Ubuntu System Panel
---

### Post by phin on 2007-03-28
how would i remove the applications, places and system management titles from the usp2 menu?

other then that, great job, ive been a fan of the app for about 6-7 months now :)

---

### Post by Rui Pais on 2007-03-28
> **phin said:**
> how would i remove the applications, places and system management titles from the usp2 menu?

other then that, great job, ive been a fan of the app for about 6-7 months now :)

do you mean remove the menus from gnome panel?

just right clic on them and choose to 'Remove from panel'

You can add them again by righ clic on panel and enter 'Add to panel' and you can replace them by a simple "ubuntu icon" that will, when pressed" give you the those menus arranged as vertical submenus.

---

### Post by Malac on 2007-03-28
It's funny you mentioning that I was thinking about this only yesterday.
I was wondering if we could make it an option that if a plugin was in "restricted" mode we could remove the title button as it doesn't do anything when "Restrict Sending to Sidepane" is ticked. I'll put it on my list.

If you mean you just want to remove the particular plugins completely, right-click on usp button choose "Preferences" and then highlight the plugin you wish to remove and click [Remove] then [Save] at bottom right.

---

### Post by Malac on 2007-03-28
@phin
Okay I have upload a new version to the SVN (Revision 228 ) which lets you choose "Hide Stickied Headings" from "Preferences". It's a global setting as the button/headings are handled by usp itself.

This means that if you choose "Restrict Sending to Side Pane" for a plugin and then set "Hide Stickied Headings" you should end up with something like this.
With Headings : [ATTACH]28430[/ATTACH] Without Headings : [ATTACH]28431[/ATTACH]

This should save a bit of screen/menu real estate. :)
Hope it helps.

---

### Post by phin on 2007-03-28
kick *** malac, thats exactly what i was talking about :)

i'll give it a try and let you know.

my usp is very simple, just the applications plugin on the left, the places on the upper right and the system_management under.  so being able to clean it up even more is definitly something im looking todo.

---

### Post by phin on 2007-03-28
works perfect, thanks :)

---

### Post by Malac on 2007-03-28
> **phin said:**
> works perfect, thanks :)
You're Welcome. :)

---

### Post by zekopeko on 2007-03-28
Malac how did you make that Root Nautilus launcher?

i created one in alacarte with command: gksudo nautilus" but it also opens the terminal (like i started it from terminal but the Run in terminal is not ticked).

---

### Post by ADRez on 2007-03-28
Instead of gksudo nautilus use gksu nautilus

---

### Post by Malac on 2007-03-28
> **zekopeko said:**
> Malac how did you make that Root Nautilus launcher?

i created one in alacarte with command: gksudo nautilus" but it also opens the terminal (like i started it from terminal but the Run in terminal is not ticked).
I created it myself, I rarely use Alacarte as I don't like the way it names files and adds extraneous data.
The command line in mine *is* "gksudo nautilus" it works fine no terminal.
Try opening the .desktop file from within gedit and check that something in there isn't wrong.
It should look like this :
```
[SIZE=3][COLOR=DarkRed][Desktop Entry][/COLOR][/SIZE][SIZE=3][COLOR=SeaGreen]
Encoding[/COLOR][/SIZE][SIZE=3]=[/SIZE][SIZE=3][COLOR=DarkOrchid]UTF-8
[/COLOR][/SIZE][SIZE=3][COLOR=SeaGreen]Name[/COLOR][/SIZE][SIZE=3]=Root Nautilus
[/SIZE][SIZE=3][COLOR=SeaGreen]Comment[/COLOR][/SIZE][SIZE=3]=Administration Nautilus
[/SIZE][SIZE=3][COLOR=SeaGreen]Exec[/COLOR][/SIZE][SIZE=3]=gksudo nautilus
[/SIZE][SIZE=3][COLOR=SeaGreen]Icon[/COLOR][/SIZE][SIZE=3]=/usr/share/pixmaps/nautilus.xpm
[/SIZE][SIZE=3][COLOR=SeaGreen]GenericName[/COLOR][/SIZE][SIZE=3]=Administration Nautilus
[/SIZE][SIZE=3][COLOR=SeaGreen]Termina[/COLOR][/SIZE][SIZE=3][COLOR=SeaGreen]l[/COLOR]=[/SIZE][SIZE=3][COLOR=DarkOrchid]false[/COLOR][/SIZE]
```Or just cut and paste that into a new file and save it as rootnaut.desktop in ~/.local/share/applications.

---

