---
title: "Request : rhythmbox 0.8.8cvs20050614-0ubuntu1"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by DarkSilver on 2005-06-15
Hello,

  [size=1]0.8.8cvs20050614-0ubuntu1 is in Breezy now... 
There are a lot of important fixes !
[/size]
  here is the log :  ```
  * Package of the current CVS:
      - fix some issue with the automatic playlist conditions (Ubuntu: #1930).
      - fix for non-UTF-8 filenames (Ubuntu: #2716).
      - fix the import dialog title to mention only folders (Ubuntu: #4490).
      - don't break the tray icon actions on gnome-panel restart (Ubuntu: #7855).
   * debian/patches/02_patch-134_ipod-crash.patch,
     debian/patches/03_patch-135_utf-8-filenames.patch,
     debian/patches/04_patch-136_musepack-wma-support.patch,
     debian/patches/05_patch-137-song-rating.patch,
     debian/patches/20_bugzilla-attach-38781_ipod-gnomevfsvolumemonitor-hal-support.patch,
     debian/patches/21_re-autotools.patch,
     debian/patches/30_bugzilla-attach-39194_fix-null-mountpoint.patch,
     debian/patches/40_debian_geometry_hints.patch,
     debian/patches/50_debian_xmlsaveformatfile_check.patch:
     - fixed upstream.
   * debian/patches/07_translations.patch:
     - updated.
```

---

### Post by Mez on 2005-06-15
Iyt depends on libdbus-glib-1-dev which is new to breezy.

I'll let John do this one - cause it'l need a lib backporting, and I dont want to break anythign :D

---

### Post by Technoviking on 2005-06-15
[QUOTE=Mez]Iyt depends on libdbus-glib-1-dev which is new to breezy.

I'll let John do this one - cause it'l need a lib backporting, and I dont want to break anythign :D[/QUOTE]
To update libdbus-glib-1-dev you have to update many other libraries.

Mike

---

### Post by DarkSilver on 2005-06-15
[QUOTE=Mike Basinger]To update libdbus-glib-1-dev you have to update many other libraries.

Mike[/QUOTE]
So, if I understand, that means no new version of rhythmbox for Hoary ... :(

---

### Post by MaX on 2005-06-17
[QUOTE=DarkSilver]So, if I understand, that means no new version of rhythmbox for Hoary ... :([/QUOTE]
 This version sucks anyway, it will play one song then hang.

---

