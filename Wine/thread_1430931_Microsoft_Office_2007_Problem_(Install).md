---
title: "Microsoft Office 2007 Problem (Install)"
date: 2010-03-16
forum: Wine
---

### Post by kossae on 2010-03-16
Just to reference in this post, this is the website I used to install:
[http://wine-review.blogspot.com/2009/11/office-2007-in-ubuntu-910-with-wine.html](http://wine-review.blogspot.com/2009/11/office-2007-in-ubuntu-910-with-wine.html)

**Ubuntu 9.10**
Okay, so I installed the winetricks elements as required.  The installer started up just fine, however in the terminal I got an output like this:

fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme: x render:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:xrender:X11DRV_AlphaBlend not a dibsection
fixme:hook:IsWinEventHookInstalled (32773)-stub!
**[SIZE=1]Note: Some code spacing changed due to 'smiley face image' restrictions.[/SIZE]**
...so on and so forth in a sort of infinite loop fashion.

The installer progress bar never moved, and these "errors" just kept running through the terminal.  Now I installed Office on my other machine no problem with the same routine, and have even done it on this laptop before (I recently reformatted and installed a clean version of Ubuntu deleting my dual-boot Windows 7 installation).  If someone knows of this error it would be real helpful to me.  Also, if there is a way to start from scratch in a sense as far as installing these winetricks elements, etc.; that would also be of much help.  Thank you in advance to anyone with any information.

---

### Post by kossae on 2010-03-16
Well, I know it's still early, but also if anyone can let me know how to basically uninstall everything winetricks installed and then remove wine so i may try everything over, that would be great too.  I don't have any other programs installed with Wine atm so it wont be a problem to do a full deletion.

---

### Post by Dougie187 on 2010-03-16
> **kossae said:**
> Well, I know it's still early, but also if anyone can let me know how to basically uninstall everything winetricks installed and then remove wine so i may try everything over, that would be great too.  I don't have any other programs installed with Wine atm so it wont be a problem to do a full deletion.

I'm not sure if this clears out winetricks stuff or not, but you could try this out to clean up wine and possibly winetricks.

```
sudo apt-get autoremove --purge wine
rm -rf ~/.wine
```

This should uninstall wine, and remove your wine directory. So if you have anything in your wine installation you want backed up (I assume not from your post), then you will want to do that before you do this.

---

### Post by Dougie187 on 2010-03-16
Also, try following the instructions here.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992)

---

