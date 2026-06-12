---
title: "Wine Uninstaller"
date: 2009-11-25
forum: Wine
---

### Post by petrocles on 2009-11-25
ubuntu 9.10 
kernel linux 2.6.31-14-generic
gnome 2.28.1
wine 1.2

i am unable to find the uninstaller program for wine


faz@faz-laptop:~$ uninstaller
The program 'uninstaller' is currently not installed.  You can install it by typing:
sudo apt-get install wine
uninstaller: command not found
faz@faz-laptop:~$ sudo apt-get install wine
[sudo] password for faz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  ttf-mscorefonts-installer
The following packages will be REMOVED
  wine1.2
The following NEW packages will be installed
  wine
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/9,122kB of archives.
After this operation, 979kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
(Reading database ... 155103 files and directories currently installed.)
Removing wine1.2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package wine.
(Reading database ... 154029 files and directories currently installed.)
Unpacking wine (from .../wine_1.1.33~winehq0~ubuntu~9.04-0ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Setting up wine (1.1.33~winehq0~ubuntu~9.04-0ubuntu1) ...
procps stop/waiting

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
faz@faz-laptop:~$ uninstaller
The program 'uninstaller' is currently not installed.  You can install it by typing:
sudo apt-get install wine
uninstaller: command not found
faz@faz-laptop:~$

---

### Post by beastrace91 on 2009-11-25
Install the latest Wine from the [ Official Wine Repositories](www.winehq.org/download/deb) - should do the trick.

Cheers,
~Jeff

---

### Post by seeker5528 on 2009-11-25
> **petrocles said:**
> 
i am unable to find the uninstaller program for wine


faz@faz-laptop:~$ uninstaller
The program 'uninstaller' is currently not installed.

The command used on the menu item is:

```
wine uninstaller
```

Which makes sense, since it is part of Wine.

Later, Seeker

---

### Post by petrocles on 2009-11-25
lol ty


kind of embarrasing!

---

### Post by HeadHunter00 on 2009-11-25
Don't worry, you're not the only one. Or maybe you're. Whatever, you found your solution, so it's all good.

---

