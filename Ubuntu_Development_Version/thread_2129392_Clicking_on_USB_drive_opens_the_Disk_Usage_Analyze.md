---
title: "Clicking on USB drive opens the Disk Usage Analyzer"
date: 2013-03-26
forum: Ubuntu Development Version
---

### Post by Yahoé on 2013-03-26
I've installed the SolusOs patched Nautilus 3.4.2 (gotta have the F3 split) and now when I click on a USB drive in the Unity launcher the Disk Usage Analyzer kicks in. How can I reset the behaviour so that Nautilus opens on that drive? I'm testing another machine with the same version of Nautilus and it's working as expected.

---

### Post by dino99 on 2013-03-26
click on the Files icon

---

### Post by Yahoé on 2013-03-27
Thanks for your input dino99, but it really doesn't answer my question. Any idea anyone?

---

### Post by mc4man on 2013-03-27
There was similar issue back in 11.10/12.04 but I got that fixed some time ago so maybe unrelated to your issue with the SolusOs nautilus.

Post the contents of ~/.local/share/applications/mimeapps.list & these for some add. info, may be of interest, may not.
```
ls /usr/share/applications |grep nautilus
```
```
cat /etc/gnome/defaults.list |grep inode
```

edit: if you have a .desktop for nautilus in ~/.local/share/applications then also note that.

---

### Post by Yahoé on 2013-04-03
Finally I used Ubuntu-tweak to check all file type and and now everything is back to the way it should be.

---

