---
title: "Unity and Close Nvidia Drivers"
date: 2013-04-13
forum: Ubuntu Development Version
---

### Post by Rukiri on 2013-04-13
My issue is with the closed drivers, everything works with nouveau but when I need to do anything heavy I actually prefer the closed drivers (mainly just because there better overall and I prefer manufactures drivers for my hardware) 
But when I choose 313.30 from the software sources for drivers and reboot, I just get my wallpaper and whatever folders I had on my desktop.

Has anyone had this issue?  Is it the same with AMD (thinking of getting a 7990 GHZ edition) and what to know if it's the same issue?

Allot of my apps seem to slow down whenever I'm doing anything heavy with graphics, take gimp for example.  The larger the brush the slower the paint (meaning when I move the mouse quickly it doesn't stop when I stop) but works perfectly with nvidia's drivers (works fine under arch and gentoo so... it's nouveau here)

But main reason is, I have no desktop/unity when using closed drivers.
Can anyone help or is a solution available? 

Unity works fine with closed drivers on Gentoo/Arch Linux, so it's not really a unity problem per say.

---

### Post by pqwoerituytrueiwoq on 2013-04-13
can you open a terminal and try to launch compiz via keyboard shortcut
compiz --replace

on xubuntu i had to remove the .Xauthorty file and the display manager config so i could login after changing video hardware, doubt that is relevant for your issue

---

### Post by joiseystud on 2013-04-13
I have the exact issue.

> **Rukiri said:**
> My issue is with the closed drivers, everything works with nouveau but when I need to do anything heavy I actually prefer the closed drivers (mainly just because there better overall and I prefer manufactures drivers for my hardware) 
But when I choose 313.30 from the software sources for drivers and reboot, I just get my wallpaper and whatever folders I had on my desktop.

Has anyone had this issue?  Is it the same with AMD (thinking of getting a 7990 GHZ edition) and what to know if it's the same issue?

Allot of my apps seem to slow down whenever I'm doing anything heavy with graphics, take gimp for example.  The larger the brush the slower the paint (meaning when I move the mouse quickly it doesn't stop when I stop) but works perfectly with nvidia's drivers (works fine under arch and gentoo so... it's nouveau here)

But main reason is, I have no desktop/unity when using closed drivers.
Can anyone help or is a solution available? 

Unity works fine with closed drivers on Gentoo/Arch Linux, so it's not really a unity problem per say.

---

### Post by serdotlinecho on 2013-04-14
```
compiz --replace
``` 

The command does not work anymore on 12.10 and 13.04. You can try this instead, Ctrl+Alt+T and type this:

```
setsid unity
```

or

```
setsid compiz --replace
```

or delete this folders:

```
rm -rf ~/.cache/compizconfig-1 ~/.compiz ~/.config .Xauthority
sudo service lightdm restart
```

---

### Post by grahammechanical on 2013-04-14
Yesterday I did 2 Raring installs on a new hard disk as part of my arrangements for testing 13.10. I did not tick to install third party software and I had no problems because Nouveau was the default driver. For most of the Raring development cycle Nvidia drivers were broken as far as I was concerned. About a month ago I switched to Nvidia and things were fine then the other day a kernel update broke Unity in the same way that you have. I switched to Nouveau and things were fine.

A couple of days ago I tried 3 different Nvidia drivers and each broke the desktop top. If you right click the desktop and select Change Wallpapers you will open System Settings. In Software and Updates you can change video drivers. You can then run ```
dconf reset -f /org/compiz/
``` That may fix it. You may also need to reinstall compiz and reboot.

Regards.

---

