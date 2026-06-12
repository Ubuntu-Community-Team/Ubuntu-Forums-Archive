---
title: "uninstall help"
date: 2011-03-10
forum: Wine
---

### Post by Sina_RJ on 2011-03-10
I want to uninstall wine from my system but i can't run any application but terminal
can anyone help me with a code?
sudo apt-get remove ....?
i don't know what to insert after remove
i want to remove it completely

---

### Post by cogadh on 2011-03-10
"sudo apt-get remove wine" then delete the .wine directory from your home directory.

You can only run the terminal?

---

### Post by Sina_RJ on 2011-03-11
yeah,I had a terrible problem with my system,i couldn't run anything but desktop and terminal by alt+ctrl+t
i really needed package name for wine,thx a lot :)

---

### Post by Sina_RJ on 2011-03-11
yeah,I had a terrible problem with my system,i couldn't run anything but desktop and terminal by alt+ctrl+t
i really needed package name for wine,thx a lot :)

---

### Post by smurphy_it on 2011-03-11
```
dpkg --get-selections | grep wine
sudo apt-get remove wineXX
```


Replacing the XXX with the version...  example.  sudo apt-get remove wine1.2

---

### Post by cogadh on 2011-03-11
The generic package name "wine" should uninstall any version of the product you installed via the package manager, regardless of actual version number. That package name is just a "dummy package" that points to whatever current version is available or installed.

---

### Post by Replicounts on 2011-03-13
How to uninstall Wine -- here's what worked for me (with hints on improving the Wine system):

I'm using Ubuntu 10.4. Installed Wine successfully using Ubuntu Software Center (search for "wine") -- EXCEPT that then I could not launch a .txt file from its icon that I had placed in the menu bar at the top of the screen. Something happened (brief flash on left of my screen), but no result. The .txt file itself still worked fine, if I double clicked it from its folder. Removing and replacing the icon, and then restarting the system, did not help.

I use my handy .txt file all the time, so I uninstalled Wine from the Ubuntu Software Center -- successfully, EXCEPT that launching the .txt file from the menu-bar icon then got an error message saying Wine was not found (instead of doing nothing). The uninstall wasn't complete.

So in my Home Folder, under View I checked "Show Hidden Files" --- then opened ".local", then "share", then "applications". Moving all the files in that "applications" folder that included "wine" in the filename to the trash did fix the problem immediately (be sure to remove userapp-wine-AUJYRV.desktop).

My system is now fine (I needed Wine just once), but to help future users, the installation should not use Wine to overwrite a launcher that is already working in Ubuntu (or if that would be problematic, give the user an option). And at the very least, the uninstaller should restore the Ubuntu launch from any data icons in the menu bar. (Ubuntu program icons in the menu bar, such as Chrome, already work fine when Wine is installed.)

---

