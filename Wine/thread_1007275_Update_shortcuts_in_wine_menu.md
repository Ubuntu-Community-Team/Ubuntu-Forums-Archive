---
title: "Update shortcuts in wine menu"
date: 2008-12-10
forum: Wine
---

### Post by Voland on 2008-12-10
I can't update shortcuts in wine menu after M$ Office installation. There are no links to Word, Excel and others I have installed. I've tried to install uTorrent - no shortcut was created. How can I create shorcuts automatically?

---

### Post by Muffinabus on 2008-12-10
I created my own uTorrent shortcut as mine did the same thing when it installed.  I did this by right clicking Applications, clicking Edit Menus, navigating to the Programs folder, created a new one named uTorrent, then created a new launcher with 
```
env WINEPREFIX="/home/muffin/.wine" wine "C:\Program Files\utorrent\utorrent.exe"
```

in the command field.  Obviously you would replace 'muffin' with your username, heh.

---

### Post by Voland on 2008-12-11
So did I. But I want to do it automatically. :) Is there any solution?

---

### Post by Muffinabus on 2008-12-11
Uhm, I believe most of the time it is done automatically, couldn't tell you why it doesn't sometimes though.  /shrug

---

### Post by Voland on 2008-12-11
Things are strange with wine. After another one reinstallation shortcuts have appeared in Other menu.

---

