---
title: "[SOLVED] Problem Uninstalling Photoshop CS2 in Wine"
date: 2009-01-02
forum: Wine
---

### Post by sendblink23 on 2009-01-02
I'm running Ubunto 8.10
Using Wine 1.0.1

*YES Photoshop CS2 is working perfectly, I just don't want it anymore*

I'm having an issue trying to uninstall Photoshop CS2

Tried using "Uninstall Wine Software", selecting to uninstall Photoshop CS2 (or even all the rest included Adobe software when it installed) and to all of them After *the supposely uninstalling*  It is still there in the List of *uninstall* inside Wine

And also in the *System Folder of Wine .. inside *Programs / Adobe  .. all the files are still there, after doing the uninstall through Wine.

Its just not working the Normal Uninstall Function of Wine for me.

**Can anybody help me out**, I wanna Uninstall entirely Photoshop CS2 & also to have it Removed from the *Wine Program List Menu.

Thanx

---

### Post by cogadh on 2009-01-02
The applications menu shortcuts are left behind normally, you will need to manually delete them. As for removing the application itself, if you don't have anything else installed in Wine, you can simply delete the .wine directory in your home directory, that eliminates your entire "fake Windows" directory and you can just build a new one. Otherwise, you will probably have to perform a manual uninstall (delete the installed files, remove registry entries, etc.).

---

### Post by sendblink23 on 2009-01-02
> **cogadh said:**
> The applications menu shortcuts are left behind normally, you will need to manually delete them. As for removing the application itself, if you don't have anything else installed in Wine, you can simply delete the .wine directory in your home directory, that eliminates your entire "fake Windows" directory and you can just build a new one. Otherwise, you will probably have to perform a manual uninstall (delete the installed files, remove registry entries, etc.).

Manually Remove Menu Shortcuts.. how? Right-Click doesn't work in the Applications menu

So explain that only ...  as for removing manually the *Applications folder of Adobe & Registry etc,  I have no problem with that

So yeah..  how can i remove it from the Wine Applications Menu?

---

### Post by sendblink23 on 2009-01-02
> **sendblink23 said:**
> Manually Remove Menu Shortcuts.. how? Right-Click doesn't work in the Applications menu

So explain that only ...  as for removing manually the *Applications folder of Adobe & Registry etc,  I have no problem with that

So yeah..  how can i remove it from the Wine Applications Menu?



Sorry  My bad... found it

*I just Right-Clicked literally ...  on *Applications,  and saw the  *Edit Menu


Well thanx anyways

---

### Post by Daminvar on 2009-01-02
If you cd to ~/.local/share/applications/wine/Programs you can delete the entries there, and to delete the icons (if you want to clean up even further) cd to ~/.local/share/icons and delete the icons to the program you removed.

It's a pity that wine doesn't remove the entries itself, but fortunately it's not too hard to remove them manually.

---

