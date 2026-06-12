---
title: "Wine unable to run most windows executables"
date: 2011-02-23
forum: Wine
---

### Post by Gamemockers on 2011-02-23
So I have had Wine installed since i did a clean install of Ubuntu 10.10 64 on my latest comp build and it seemed to be working fine until i decided to run iTunes in a VM of Windows FLP instead of Wine-ing it. When i tried to uninstall it the iTunes from Wine the uninstall wizard ran and then would just end up doing nothing but reinstalling the files. So i deleted all the files in the Wine virtual C: drive folder and did a purge of wine with ```
 sudo apt-get purge wine 
```
When i reinstalled Wine, all the menu entries were gone including the default ones like the wine configuration program although when wine is searched for on the file system the file which adds the wine entries to the menu is existing and in the right directory. and wine also no longer runs programs that are proven to work. I can for example no longer run hl2.exe from steam or non steam which i believe has platinum compatibility on the Wine website. Regardless of the program I run now i get a standard windows error telling me the program has encountered a serious error. (Pic related) I really dont want to have to clean install Ubuntu but thats about all i know how to do from here. Any suggestions? Help? Advice? Links? Anything really would help. Thanks :D

---

### Post by cogadh on 2011-02-24
Windows error messages are pretty much useless for troubleshooting Wine problems. We need error output from Wine to figure out what is going on. Run something with Wine from the terminal and post the output here, it might explain what is happening.

---

### Post by Gamemockers on 2011-02-24
> **cogadh said:**
> Windows error messages are pretty much useless for troubleshooting Wine problems. We need error output from Wine to figure out what is going on. Run something with Wine from the terminal and post the output here, it might explain what is happening.

Ok I attached a screenshot of me trying to run StarCraft II from the terminal. From what I can tell, the hard drive is a non executable environment? Or something. But anyways to test my theory I copied the program files to the desktop and it ran fine. How can I fix this? Also the game and most other windows stuff is installed on a seperate internal hard drive if that helps.

---

### Post by cogadh on 2011-02-24
By default in Ubuntu, all executable are not allowed to execute (its a security "feature"). Just right-click on the SC2 executable, select properties and check the "mark as executable" option.

---

