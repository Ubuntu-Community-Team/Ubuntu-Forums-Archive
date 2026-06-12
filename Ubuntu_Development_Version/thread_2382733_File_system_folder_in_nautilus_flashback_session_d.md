---
title: "File system folder in nautilus flashback session does nothing"
date: 2018-01-16
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2018-01-16
Ran across another oddity in Bionic flashback session (also exists in Artful). Go to Places > Computer, left-click to open "Files", then select File System either by double-click or right-click + open and nothing happens. Everything but the File System button/folder seems to function properly.

---

### Post by kansasnoob on 2018-01-16
If you go Places > Home > Other locations and select Computer the file system opens as expected.

---

### Post by kansasnoob on 2018-01-17
I did file a bug report:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1743686](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1743686)

I found two other bugs in the flashback session that should be confirmed if anyone is so inclined:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1737836](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/1737836)

[https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1743621](https://bugs.launchpad.net/ubuntu/+source/gui-ufw/+bug/1743621)

---

