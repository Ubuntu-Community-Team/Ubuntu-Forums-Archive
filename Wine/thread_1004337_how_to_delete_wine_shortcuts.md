---
title: "how to delete wine shortcuts"
date: 2008-12-07
forum: Wine
---

### Post by banana jama on 2008-12-07
i install a ipod program called ephod but i do not need it anymore. i tried to uninstall it under the uninstall wine software but it's still there. i made sure i deleted it by going into the c:/ drive and deleting the folders that contain the software but the shortcuts are still there. can ayrone help? how do i delete wine shortcuts?

---

### Post by quibbler on 2008-12-07
> **banana jama said:**
> i install a ipod program called ephod but i do not need it anymore. i tried to uninstall it under the uninstall wine software but it's still there. i made sure i deleted it by going into the c:/ drive and deleting the folders that contain the software but the shortcuts are still there. can ayrone help? how do i delete wine shortcuts?
Open Nautilus and go to your home (make sure you see hidden files and folders) -
look in /home/(yourhome)/.config/menus/applications-merged/wine-Programs-ephod.menu
and delete the file.

Regards quibbler

---

### Post by banana jama on 2008-12-07
thanks alot it worked

---

### Post by banana jama on 2008-12-07
i thought it worked but it didn't. once i restarted my computer they  were ther again. i tried to go back to applications merged but they're not there. even though all the files have been deleted the shortcuts are still there. i tried to go to 
system---> preferences--->main menu and delete the shortcuts (for some reason there are not under the wine tab but under the other tad) but when i press delete nothing happens. 
     i've been able to hide them by deselecting them but i would really like to delete them. does anyone know how i can? any suggestions would be appreciated. 
    banana jama

---

### Post by quibbler on 2008-12-07
> **banana jama said:**
> i thought it worked but it didn't. once i restarted my computer they  were ther again. i tried to go back to applications merged but they're not there. even though all the files have been deleted the shortcuts are still there. i tried to go to 
system---> preferences--->main menu and delete the shortcuts (for some reason there are not under the wine tab but under the other tad) but when i press delete nothing happens. 
     i've been able to hide them by deselecting them but i would really like to delete them. does anyone know how i can? any suggestions would be appreciated. 
    banana jama
Go to system---> preferences--->main menu and right click on the shortcut
and choose delete.

Regards quibbler

---

### Post by banana jama on 2008-12-07
i did that it doesn't work

---

### Post by quibbler on 2008-12-07
Where are the shortcuts exactly ( you said under an 'other tab')?

---

### Post by banana jama on 2008-12-07
yeah thats where they show up when i go to prefernce--->menu. originally they where in wine but, not now there under other.

---

### Post by quibbler on 2008-12-07
If the tab is called other, I have no idea what that is. I have not got a tab named other anywhere in the menus.

Regards quibbler

---

### Post by banana jama on 2008-12-07
when you go to system----> preferences----> main menu you don't see a tab name other it represented with a picture with a box with a ruler and stuff in it.
heres a picture of my main menu page all the stuff not checked off is the things im trying to delete

---

### Post by quibbler on 2008-12-07
Look in /home/yourhome/.local/share/applications, and delete everything with
ephpod. Maybe that will help, otherwise, I don't know.

quibbler

---

### Post by banana jama on 2008-12-07
no oh well i looks like it's just one of thoughs thing i'm just going to have to live with :)  thanks for your suggestions though.

---

### Post by renkinjutsu on 2009-05-03
i have the same problem.. only not in alacarte
i'm using the deskbar applet and under actions, i still get entries for wine programs that i have uninstalled... same programs appear in Gnome-do

how do i get rid of these programs? .. i'm trying to look for the launchers, but i can't find any

---

