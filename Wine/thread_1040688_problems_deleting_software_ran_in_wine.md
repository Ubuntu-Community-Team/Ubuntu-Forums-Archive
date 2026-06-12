---
title: "problems deleting software ran in wine"
date: 2009-01-15
forum: Wine
---

### Post by banana jama on 2009-01-15
i posted a problem similar to this a few months ago but it wasn't able to be answered but now this problem is getting very annoying. when i delete software that i was running in wine for some reason the shortcuts remain. i've tried going to to .config ---> application mergered and delete the files but it doesn't work. i've also tried going to main menu and deleting the shortcut but that also doesn't work when i press delete nothing happens. does anyone else have this problem or know how to solve it?

---

### Post by bob-linux-user on 2009-01-15
Have a look at the following locations which all have items put in them by WINE:-

/home/yourname/.config/menus/applications-merged
/home/yourname/.local/share/applications/wine/Programs 
/home/yourname/.local/share/desktop-directories
/home/yourname/.local/share/icons

---

### Post by banana jama on 2009-01-15
i tried them all and deleted any trace of the programs i deleted(i hope) but these shortcuts are still there. it works thats this thread is solved.

---

### Post by 2px833 on 2010-01-04
aha,i just delete the file under the path "/home/zpx/.local/share/applications/wine/Programs" and then OK 

my history:

  423  cd .config/
  424  ls
  425  cd menus/
  426  ls
  427  cd applications-merged/
  428  ls
  429  grep "wine" -l *
  430  vim applications.menu
and the icon is still in my menu:

 436  cd ../.local/share/applications/
  437  ls
  438  rm wine-Programs-*

and the icon is still:

  457  cd .local/share/
  458  ls
  459  cd applications/
  460  ls
  461  cd wine/
  462  ls
  463  cd Programs/
  464  ls
and then 
 468  rm AutoHotkey/ -rf
  469  rm CMake\ 2.6/ -r

it's ok

is my english poor enough?:)

---

