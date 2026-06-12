---
title: "Nautilus Restart"
date: 2015-03-19
forum: Ubuntu Development Version
---

### Post by Frogs Hair on 2015-03-19
The following command is now depreciated and I can't find a replacement. ```
nautilus -q
``` I ask because I used the command to keep dropbox from prompting to restart nautilus after login. Running the command once usually stopped the dialog box from appearing again.

---

### Post by zika on 2015-03-20
> **Frogs Hair said:**
> The following command is now depreciated and I can't find a replacement. ```
nautilus -q
``` I ask because I used the command to keep dropbox from prompting to restart nautilus after login. Running the command once usually stopped the dialog box from appearing again.It still works at my place(s).```
killall nautilus
```should, also, do the trick.

---

### Post by Frogs Hair on 2015-03-20
```

killall nautilus
``` Works :) and removes the restart prompt at login.
 ```
nautilus -q
Initializing nautilus-dropbox 2.10.0

(nautilus:2616): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

(nautilus:2616): GLib-GObject-WARNING **: The property GtkSettings:gtk-button-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

```  After this the terminal window becomes uncontrollable and only closing works   as you can see by the screen shot.All that remains is the close button.

---

### Post by zika on 2015-03-20
> **Frogs Hair said:**
> ```
killall nautilus
``` Works :) and removes the restart prompt at login.;)
 > **Frogs Hair said:**
> ```
nautilus -q
Initializing nautilus-dropbox 2.10.0
(nautilus:2616): GLib-GObject-WARNING **: The property GtkSettings:gtk-menu-images is deprecated and shouldn't be used anymore. It will be removed in a future version.
(nautilus:2616): GLib-GObject-WARNING **: The property GtkSettings:gtk-button-images is deprecated and shouldn't be used anymore. It will be removed in a future version.

```  After this the terminal window becomes uncontrollable and only closing works   as you can see by the screen shot.All that remains is the close button.This is not Nautilus trouble it is nautilus-dropbox being in trouble... ;)

---

### Post by Frogs Hair on 2015-03-20
> **zika said:**
> ;)
 This is not Nautilus trouble it is nautilus-dropbox being in trouble... ;)

Thanks !

---

