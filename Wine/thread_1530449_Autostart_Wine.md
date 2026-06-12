---
title: "Autostart Wine"
date: 2010-07-13
forum: Wine
---

### Post by xtremesupremacy3 on 2010-07-13
Hey there,

Recently I have been using a lot of wine applications and have to do a lot through CLI. 
Now I don't mind CLI but it seems a little silly doing this so often.

My question is, is there a way of script or something which will automatically run the autorun file from a CD for lets say a game. And if it's a Windows game that it fires up with wine straight away.

If that's a little too hard to do, maybe a script so that when I right click on the icon on the desktop and select the correct script it will run the autostart in wine?

Arthur

---

### Post by 3Miro on 2010-07-13
Autorun as in automatically run a program from the CD is not a good idea. You never know what will run from one CD or another.

Right now, you should be able to open the CD with Nautilus (Places -> CD or Home and navigate to the CD) and then select an executable to either double-click or right click -> run with wine. This avoids the CLI. 

Another option is to create a desktop icon/launcher. This now depends on the environment (Gnome, KDE, XFCE, LXDE), but you will have to tell it to execute a command of the form of:
```
WINEPREFIX="/path/to/.wine/" wine /path/to/MyFavoriteGame.exe
```
WINEPREFIX thing is optional in case you are not using the default .wine, otherwise you can just ignore it. I usually install different games in different wine folders, so I have WINEPREFIX="/path/to/WineOblivion, WINEPREFIX="/path/to/WineStalker and so on.


Third option (the one that I am using) is to create a script. Create an empty file and then edit the file:
```
#!/bin/bash
WINEPREFIX="/path/to/.wine/" wine /path/to/MyFavoriteGame.exe

```
you can also add other commands like:
```
#!/bin/bash
cd /path/to/MyGameFolder
WINEPREFIX="/path/to/.wine/" wine MyFavoriteGame.exe
```
Then you need to give execute permissions to the file, from CLI it is:
```
chmod 755 filename
```
and you can do it from Nautilus. Once you have the file, you can just double-click on it or right click -> execute and it will run the program.

---

### Post by xtremesupremacy3 on 2010-07-14
I appreciate your reply and ideas.

It maybe something I will look at.
I can always go into the CD folder, right-click and use Wine, but still.

When I right-click on the desktop entry of the CD i get an autorun entry but half the time it doesn't work right.

I think it might be an idea to let a small window pop up when a cd with autorun has been inserted asking if you want to autorun or not. That way you at least have the option.

Thanks

---

