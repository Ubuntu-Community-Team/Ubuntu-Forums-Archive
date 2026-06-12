---
title: "A question about uninstalling wine"
date: 2010-12-14
forum: Wine
---

### Post by jwaclawsky on 2010-12-14
If I "uninstall wine" using the pull down from applications > wine > uninstall wine software. Does it clean up the wine C: drive (which seems to be .wine directory) and free up all the disk space? Or do I have to manually go in and delete left over files?

My system seems to have been corrupted when I installed the flash package from winetricks and now the Firefox browser hangs if flash is involved when I navigate to a web page using it. I reinstalled Firefox but that didn't help so I am thinking of reinstalling wine to get rid of the flash problem.

---

### Post by akand074 on 2010-12-14
From my experience, you have to delete the .wine folder manually.

---

### Post by bob-linux-user on 2010-12-14
You will find that "Uninstall Wine Software" is for uninstalling Windows programs you installed in wine, not uninstalling wine itself. It is a bit like Add/Remove programs in the Windows control panel. I have found a number of places that hold information from Wine. Suggest look at these:

/home/yourname/.config/menus/applications-merged
/home/yourname/.local/share/applications/wine/Programs 
/home/yourname/.local/share/desktop-directories
/home/yourname/.local/share/icons 
/home/yourname/.wine/drive_c/users/yourname/Start Menu/Programs
/home/yourname/.wine/drive_c/Program Files

Uninstall Wine itself using synaptic or the software centre.

---

### Post by Soulcage on 2010-12-15
If you want/need to reset wine you can run this command ```
rm -rf $HOME/.wine && rm -f $HOME/.config/menus/applications-merged/wine* && rm -rf $HOME/.local/share/applications/wine && rm -f $HOME/.local/share/desktop-directories/wine* && rm -f $HOME/.local/share/icons/????_*.{xpm,png} && rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png} && rm -f $HOME/.local/share/applications/wine-extension*
``` Then just reinstall whatever you want. (Remove any saves first if there are any.)

---

### Post by jwaclawsky on 2010-12-16
Thanks soulcage. I'll give it a try

---

