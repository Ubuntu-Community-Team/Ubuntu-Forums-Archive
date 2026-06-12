---
title: "Anyone want to test an app?"
date: 2012-12-31
forum: Ubuntu Application Development
---

### Post by Marcappuccino on 2012-12-31
I have a project up of sourcefourge that I made in openSUSE (sorry :( i left), which allows you to quickly change any visual settings, ie window / gtk / icon and cursor themes.

It is, essentially a frontend to gsettings, but with predefined schemas and a simplified range of commands.
You can change a theme in three arguments:

`$ change icon-theme Faience`

`$ change gtk-theme Raleigh`

It is written in Python3, and it the only dependency, apart from a GNOME based system.
It has already been tested on openSUSE 12.2 (GNOME) and elementary 0.2, so if anyone could try it out that would be great. Please report any bugs on SF or to my email at 'marco@scannadinari.co.uk'.

Thanks

:)

---

### Post by Marcappuccino on 2012-12-31
I have a project up of sourcefourge that I made in openSUSE (sorry  i left), which allows you to quickly change any visual settings, ie window / gtk / icon and cursor themes.

It is, essentially a frontend to gsettings, but with predefined schemas and a simplified range of commands.
You can change a theme in three arguments:

`$ change icon-theme Faience`

`$ change gtk-theme Raleigh`

It is written in Python3, and it the only dependency, apart from a GNOME based system.
It has already been tested on openSUSE 12.2 (GNOME) and elementary 0.2, so if anyone could try it out that would be great. Please report any bugs on SF or to my email at 'marco@scannadinari.co.uk'.

Thanks

: )

---

### Post by ibjsb4 on 2012-12-31
And the link is ?

---

### Post by sffvba[e0rt on 2012-12-31
*Threads **merged **(one thread per topic please).*


404

---

### Post by Marcappuccino on 2013-01-01
bump

Oh sorry the link is [https://sourceforge.net/projects/zh-change/?source=directory](https://sourceforge.net/projects/zh-change/?source=directory).
Sorry not found I realized it was in the wrong section

---

### Post by ibjsb4 on 2013-01-01
I got a lot of crap in this copy of 12o4 in my home directory, so Im not sure but I think these files have been installed by you program.

/source.py

/Multiple Commands~

/install

/change

Anyhow I think its installed, but ..

"gksudo change" or just "change" didn't seem to do anything.

Did I miss the "read me" file?

---

### Post by Marcappuccino on 2013-01-03
@ibjsb4, After extracting the .tgz, execute (as root) '$ sudo python3 [directory to 'install]', you can now run it from /usr/bin, byt typing change from the CLI.
change is a command line app, it is not graphical, so gksudo is not needed (In fact it will not work if you use it as root)
So, after installing it, you can run it by just typing in:

'$ change [icon/wm/gtk/cursor]-theme [value]

(add '-h' or '--help' for more details)

There is no readme as of yet, sorry, but the help argument will do for now.

Source.py is for those who would like to examine/learn from the code and possibly contribute to it, install is the executable install script, change is the actual app, and COPYING is the GPL license. Anything else and 'multiple commands' are not mine, they are part of your /home ;).

EDIT: It  would be better to extract it into a folder to prevent confusion.

---

### Post by ibjsb4 on 2013-01-05
> **Marcappuccino said:**
> EDIT: It  would be better to extract it into a folder to prevent confusion.

Yep, going to start doing that one of these days  :D

Going to play with it again this weekend.

---

