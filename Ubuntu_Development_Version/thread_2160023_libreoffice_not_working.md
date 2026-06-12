---
title: "libreoffice not working"
date: 2013-07-05
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-07-05
is this just me. however abiword is working great.

---

### Post by ajgreeny on 2013-07-05
In what way is LO not working?

We can't help very much with your problem when you just say "LO not working".  Use command **libreoffice %U** in terminal and report any errors that show.  Do the same for commands **libreoffice --writer %U** and **libreoffice --calc %U**

---

### Post by rburkartjo on 2013-07-05
aj libreoffice splash screen comes up and then freezes indefinitely.  all the three commands gave no output when ran from the terminal.

---

### Post by ajgreeny on 2013-07-05
Which version of LO?

---

### Post by Elfy on 2013-07-05
Odd - those commands are the same as in the menu.

Works fine here from the menu.

Works fine from launchers.

From a terminal I get

a popup that hides behind the terminal with /home/hob/%U does not exist

 the terminal shows 
hob@hob-smaug:~$
> Warning: failed to read path from javaldx

Click the OK button in the popup and terminal ecoes hob@hob-smaug:~$

---

### Post by ajgreeny on 2013-07-05
> **Elfy said:**
> Odd - those commands are the same as in the menu.

Works fine here from the menu.

Works fine from launchers.

From a terminal I get

a popup that hides behind the terminal with /home/hob/%U does not exist

 the terminal shows 
hob@hob-smaug:~$


Click the OK button in the popup and terminal ecoes hob@hob-smaug:~$

Yes, very strange; in terminal you need to remove the %U from the commands, eg just libreoffice --writer.

I think perhaps the %U is just for gnome (and other GTK?) launchers, ie **application.desktop** files, see [http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html](http://www.linuxtopia.org/online_books/linux_desktop_guides/gnome_2.14_user_guide/launchers.html) scroll to bottom for the various %* suffixes.

---

