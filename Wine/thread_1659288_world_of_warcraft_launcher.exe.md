---
title: "world of warcraft launcher.exe"
date: 2011-01-03
forum: Wine
---

### Post by fredds on 2011-01-03
Hi, have a problem when trying to run WoW launcher.exe , I get an error message ,
The file '/media/74D81BBFD81B7E94/Program Files/World of Warcraft/Launcher.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
This is a fresh install of ubuntu10.10 and wine 1.2 on an AMD x2 3800 with Gigabyte gtx250 video card. I have tried making the file executable through .. properties; permissions; allow executing files as program;  no joy, it immediately reverts back. Tried running nautilus as sudo, same thing. Tried sudo chmod +x -v /media/74D81BBFD81B7E94/Program Files/World of Warcraft/Launcher.exe ..  says it has set permissions to 711  rwx-x-x,  still no joy. Dragged launcher.exe onto desktop and changed permissions but wow won't start if launcher is not in the same folder. It will start in a terminal, but it is easier to start it from wow folder. I have googled and searched these forums for an answer but no luck. It runs fine in 10.04. thanks  fredd

---

### Post by Tweak42 on 2011-01-04
It sounds like the drive you are trying to launch from is mounted as read only, or something with the user ownership of the files/directories.  Is the drive formatted in ext or ntfs?

---

### Post by fredds on 2011-01-04
Thanks for reply tweak42, but I don't think it is a drive permissions thing. It ran perfectly for a long while , launching in 9.10 and 10.04 and I can run the program as a normal user in a terminal.
My permissions on the file are read/write, but latest ubuntu 10.10 stops me running executables. There are a number of people complaining about this on the net; no solutions though.
Drive is NTFS
thanks
fred

---

### Post by xXDestroyerGRXx on 2011-01-04
i have 1.3.9 and it runs perfectly.

Maybe you need to install winetricks? dunno...

```
wget http://www.kegel.com/wine/winetricks
``````
sh winetricks corefonts vcrun6
```

---

### Post by Compfix101 on 2011-04-13
> **fredds said:**
> Hi, have a problem when trying to run WoW launcher.exe , I get an error message ,
The file '/media/74D81BBFD81B7E94/Program Files/World of Warcraft/Launcher.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
This is a fresh install of ubuntu10.10 and wine 1.2 on an AMD x2 3800 with Gigabyte gtx250 video card. I have tried making the file executable through .. properties; permissions; allow executing files as program;  no joy, it immediately reverts back. Tried running nautilus as sudo, same thing. Tried sudo chmod +x -v /media/74D81BBFD81B7E94/Program Files/World of Warcraft/Launcher.exe ..  says it has set permissions to 711  rwx-x-x,  still no joy. Dragged launcher.exe onto desktop and changed permissions but wow won't start if launcher is not in the same folder. It will start in a terminal, but it is easier to start it from wow folder. I have googled and searched these forums for an answer but no luck. It runs fine in 10.04. thanks  fredd
Have you tried right-clicking on the .exe file, select properties, permissions and checking the box that enables the reading of the files as executable? It is a common error that I sometimes do when I am in a hurry.

---

### Post by cwwilson721 on 2011-04-13
Any of the below can help:
[LIST]
[*]Upgrade wine to 1.3 (Seems silly, but IT WORKS BETTER OVERALL ANYWAY). Look/Google for how to add wine1.3 to Ubuntu
[*]Look at what your WoW icon actually uses as a command. Mine is: ```
env WINEPREFIX="/home/<USERNAME>/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```
[*] Run WoW in Windows XP mode
[/LIST]

---

### Post by fredds on 2011-04-14
Thanks CWWILSON 721, updating to wine 1.3 solved the problem.
I can only assume it was a permissions problem with the older version of wine.

cheers
Fred

---

