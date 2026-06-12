---
title: "WoW folder not showing up after instilation in Wine"
date: 2010-03-15
forum: Wine
---

### Post by lotsamuffins on 2010-03-15
so i was able to get Wrath of the Lich King installed, but there is no game file where i specified the install to go in Wine.  c:\programfiles\WorldofWarcraft. the only way i can play the game is to pop in the cd and right click the install button, then it asked me to play the game. it is installed because it wants to download all the patches.

do i need to log into the game the first time for it to make a folder in wine with the program in it, or is it hidden in wine?

help would be really nice :)

thanks

i used this guide [http://ubuntuforums.org/showthread.php?t=1282443](http://ubuntuforums.org/showthread.php?t=1282443)
all i did was right click the install.exe and off it went in wine.

---

### Post by DoktorSeven on 2010-03-15
It should be installed in a hidden subdirectory of your home directory by default:

.wine/drive_c/Program\ Files\World\ of\ Warcraft
(notice the dot before "wine")

Should have also made shortcuts in your programs menu to run it as well.

I always make it easy on myself by linking to my Wine drive_c so I don't have to go into the hidden directories to find it:

```
ln -s ~/.wine/drive_c/ ~/Wine
```
(Of course, you can call the linked directory (the second part of that statement) anything you want.)

---

### Post by lotsamuffins on 2010-03-16
> **DoktorSeven said:**
> It should be installed in a hidden subdirectory of your home directory by default:

.wine/drive_c/Program\ Files\World\ of\ Warcraft
(notice the dot before "wine")

Should have also made shortcuts in your programs menu to run it as well.

I always make it easy on myself by linking to my Wine drive_c so I don't have to go into the hidden directories to find it:

```
ln -s ~/.wine/drive_c/ ~/Wine
```(Of curse, you can call the linked directory (the second part of that statement) anything you want.)

so what should i do pre installation so it doesn't happen? im a new user so bare with me. ;)

---

### Post by lotsamuffins on 2010-03-16
yeh i cant find it anywhere in the wine files. there is no launcher either on my desktop. i installed it one time with a freinds help and it installed perfect. i had a destop launcher and the files where not hidden in wine. any help?

---

