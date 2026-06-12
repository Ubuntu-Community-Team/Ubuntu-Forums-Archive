---
title: "A folder is stuck"
date: 2009-12-09
forum: Wine
---

### Post by megaman2000 on 2009-12-09
I tried installing a program in wine, and then decided to uninstall it using wine's uninstall feature. It did uninstall the program, but there's still a folder in the programs directory in wine under applications that I can't seem to be able to remove.

How do I remove it?

---

### Post by MaindotC on 2009-12-09
It should be in .local/share/applications or .local/share/desktop-directories.  I'm sure you're familiar with the game Counterstrike - For your future referece I located it using the following command:
```

locate Steam | more

```
and it output the following:

```

/home/x/.local/share/Trash/files/Steam.desktop
/home/x/.local/share/Trash/files/Steam.lnk
/home/x/.local/share/Trash/files/SteamInstall.msi
/home/x/.local/share/Trash/info/Steam.desktop.trashinfo
/home/x/.local/share/Trash/info/Steam.lnk.trashinfo
/home/x/.local/share/Trash/info/SteamInstall.msi.trashinfo
/home/x/.local/share/applications/Steam-1.desktop
/home/x/.local/share/applications/Steam.desktop
/home/x/.local/share/applications/wine/Programs/Steam
/home/x/.local/share/applications/wine/Programs/Steam/Counter-Strike.desktop
/home/x/.local/share/applications/wine/Programs/Steam/Steam Support Center.desktop
/home/x/.local/share/applications/wine/Programs/Steam/Steam.desktop
/home/x/.local/share/desktop-directories/wine-Programs-Steam.directory

```

---

