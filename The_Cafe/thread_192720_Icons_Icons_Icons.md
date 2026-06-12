---
title: "Icons Icons Icons"
date: 2006-06-09
forum: The Cafe
---

### Post by CameronCalver on 2006-06-09
Hello i have dapper but i am dissapointed with the buttons and i need a good networking icon can some1 help me

---

### Post by Alyaev A. on 2006-06-09
I have *gperfection* icon theme. I can sent for you all of networking icons from this theme, or you can search your own favor at [Gnome-look]("http://www.gnome-look.org") or somewhere else.

---

### Post by CameronCalver on 2006-06-09
can you send the icon theme plz and i could not find gperfection on gnomelook can you show me plz

---

### Post by givré on 2006-06-09
For networking icone, see my howto
[http://www.ubuntuforums.org/showthread.php?t=184128](http://www.ubuntuforums.org/showthread.php?t=184128)

---

### Post by Alyaev A. on 2006-06-09
Sorry, but i can't send whole theme (3.5Mb with my Dial-Up &#8212; it's like suicide). Only some of the icons. If you interested, write me your mail to Private Messages.

---

### Post by CameronCalver on 2006-06-09
i tryed to private msg you but it said ou were not found can you send me one and ill reply

---

### Post by s6dalane on 2006-06-09
The gperfection theme suite is available [here]("http://www.deviantart.com/deviation/28701700/")

---

### Post by Zodiac on 2006-06-09
I tried to install that great theme and ran into some problems...

How do I properly install it?

I basically moved the icons to /usr/share/icons and moved the theme to /usr/share/themes

but something is missing.... sup???

---

### Post by ComplexNumber on 2006-06-09
[quote=Zodiac]I tried to install that great theme and ran into some problems...

How do I properly install it?

I basically moved the icons to /usr/share/icons and moved the theme to /usr/share/themes

but something is missing.... sup???[/quote] what kind of problems? you do realise that you have to untar the archive first before you place in /usr/share/icons, dont you?

---

### Post by Zodiac on 2006-06-09
It just doesn't look right... like I didn't move something properly or am missing something.

Where does the "office-metacity-theme" go?

---

### Post by ComplexNumber on 2006-06-09
> It just doesn't look right.. doesn't look right in what way? please try to give more detail otherwise nobody can help.


>  Where does the "office-metacity-theme" go? both gtk and metacity go in the same directory - ie /usr/share/themes. you will notice that in some gtk themes, there is also a metacity theme prepackaged.

---

### Post by Zodiac on 2006-06-09
I don't know how to explain it, it is just missing features. It looks like it is appying the default window border rather than the gperfection one...

Should the metacity theme have its own folder within /usr/share/themes ??

---

### Post by ComplexNumber on 2006-06-09
[quote=Zodiac]I don't know how to explain it, it is just missing features. It looks like it is appying the default window border rather than the gperfection one...

Should the metacity theme have its own folder within /usr/share/themes ??[/quote]go into the gperfection directory and tell me what files and directories are in the top level. by 'top level', i mean as soon as you click on the gperfection folder.
it may be that the index.theme is missing the MetacityTheme entry. or it maybe because you just don't have a metacity theme. or it could be because the metacity theme has somehow been palced in a different directory to that of the gtk.

---

### Post by Zodiac on 2006-06-09
Okay, in the folder is:

gtk-2.0
Office
gperfection2

---

### Post by ComplexNumber on 2006-06-09
[quote=Zodiac]Okay, in the folder is:

gtk-2.0
Office
gperfection2[/quote] whats that gperfection2 folder doing in there? that belongs in /usr/share/icons. its no wonder your gperfection icon theme isn't showing up.
also, the Offic fiolder does not belong in there. put it in the level above (ie the /usr/share/theme directory. don't have it in the gperfection directory because it won't show up. if you open up Office, you will see a metacity-1 theme in there.

is there no index.theme file?



also, when you select the gtk theme, the metacity one will not be activated. and visa versa. when you go into theme manager, it will show you a picture of the theme, with the name of it and a comment by the side of it. if you don't see gperfection there, it is because there is no index.theme file.


btw the index.theme file for my gperfection themes (i have several - ubuntulooks-gperfection, clearlooks-gperfection, and gperfection) looks like this:
> [Desktop Entry]
Name=gperfection2
Type=X-GNOME-Metatheme
Comment=Clearlooks theme using the gperfection2 suite
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=gperfection2
MetacityTheme=Office
IconTheme=gperfection2 

notice that the metacity theme is pointing to "Office".




in sumary:
-leave your gtk-2.0 directory where it is
-move your gperfection icon theme to /usr/share/icons
-move the metacity Office theme to the level above (ie so that it resides at /usr/share/themes/Office)
-as an option, you can create your own index.theme file so that when you select gperfection, the metactiry, gtk, and icon themes show up all at once. copy the code that i've given above, then save it as index.theme in the gperfection gtk theme folder. therefore, when you open up your gtk theme folder, it should only show 'gtk-2.0' and 'index.theme'.



let me know how you get on.

---

### Post by CameronCalver on 2006-06-09
Hey i dont want a new theme i  just want a new icon theme and also you no when you go into nautilus and it says file system how can i put that on the desktop

---

### Post by ComplexNumber on 2006-06-10
[quote=CameronCalver]Hey i dont want a new theme i  just want a new icon theme and also you no when you go into nautilus and it says file system how can i put that on the desktop[/quote] in that case, just move the gperfection folder out into /usr/share/icons then.

to put the icons on the desktop, go into gconf-editor, and type in 'nautilus'. look through the list - one of them will give the option of putting icons on the desktop


**EDIT**: move the Office folder out of that directory into the level above. it doesn't belong in that folder.

---

### Post by nalmeth on 2006-06-10
gnome-look.org has a lot of good themes.

I personally like the Still Life icon theme

---

### Post by CameronCalver on 2006-06-11
Ok i downloaded icon theme how do i install it

---

### Post by CameronCalver on 2006-06-13
Ok when i am root user in nautilus and there is a .sh file i like that icon but when i am normal it is the new icon how do i change it to the old one

---

