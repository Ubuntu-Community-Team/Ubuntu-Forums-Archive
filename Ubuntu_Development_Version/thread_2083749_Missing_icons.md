---
title: "Missing icons"
date: 2012-11-13
forum: Ubuntu Development Version
---

### Post by Sworddragon on 2012-11-13
After the todays update all my icons are gone. I remember that one package complained about the icon cache and showed me a command with a redirector (I think it was gtk-update-icon-cache). libgtk2.0-bin wasn't installed at this time and after installing it the command gtk-update-icon-cache hasn't helped me. Has somebody an idea how to fix this? I'm using LXDE and reinstalling lxde-icon-theme hasn't helped too.

---

### Post by dino99 on 2012-11-13
try:  lxpanel --replace

---

### Post by Sworddragon on 2012-11-14
This command wasn't available on my system and even after installing it it hasn't helped. But I have upgraded now my virtual machine to look to the exact error message. After the trigger for an icon theme this appears:

```
(gtk-update-icon-cache-3.0:7343): GdkPixbuf-WARNING **: Cannot open pixbuf loader module file '/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache': Datei oder Verzeichnis nicht gefunden

This likely means that your installation is broken.
Try running the command
  gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache
to make things work again for the time being.
```

After installing libgdk-pixbuf2.0 and running the command (the last 2 directories were missing) nothing changed. All icons are still invisible or have an error symbol. Curiously my virtual machine got this error message too but is unaffected by this bug.

Edit: Your edited command doesn't know the argument --replace.

---

### Post by raja.genupula on 2012-11-14
> **Sworddragon said:**
> After the todays update all my icons are gone. I remember that one package complained about the icon cache and showed me a command with a redirector (I think it was gtk-update-icon-cache). libgtk2.0-bin wasn't installed at this time and after installing it the command gtk-update-icon-cache hasn't helped me. Has somebody an idea how to fix this? I'm using LXDE and reinstalling lxde-icon-theme hasn't helped too.


How about re-isntalling LXDE with 
```
sudo apt-get install --reinstall lxde 
```

---

### Post by Sworddragon on 2012-11-14
lxde was never installed but lxde-core. I have reinstalled it but it hasn't helped. I have even removed all icon-themes and installed them again but without any difference. I have now updated the icon cache for all folders in /usr/share/icons but this hasn't solved the problem too.

---

### Post by raja.genupula on 2012-11-14
Ok do this in your terminal 
```
sudo cp /usr/share/lxpanel/profile/LXDE/panels ~/.config/lxpanel/LXDE/panels
```

If changes are not applied instantly then re-login/restart your system.

---

### Post by Sworddragon on 2012-11-14
I have now downgraded my system to Quantal and all is working fine. Now I will figure out first which package is triggering this bug.

---

### Post by raja.genupula on 2012-11-14
> **Sworddragon said:**
> I have now downgraded my system to Quantal and all is working fine. Now I will figure out first which package is triggering this bug.


and dont forget reporting it to launchpad .

Thank you .

Have you tried what i have given ?

---

### Post by Sworddragon on 2012-11-14
> **raja.genupula said:**
> and dont forget reporting it to launchpad .

Sure, as the ~100 reports I have already made there :)


> **raja.genupula said:**
> Have you tried what i have given ?

I will try it after I have upgraded to Raring again.


Edit: The upgrade is now complete and I couldn't find a package which is making troubles because all is working fine now.

---

