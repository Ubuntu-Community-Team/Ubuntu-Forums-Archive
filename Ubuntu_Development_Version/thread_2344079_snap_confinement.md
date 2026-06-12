---
title: "snap confinement"
date: 2016-11-22
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-11-22
snaps are confined to the user's home folder & /snap/the snap's folder. This is a feature though I figure it's not going to go over all that well with existing Desktop users.
Feel free to chime in one way or the other...
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1643706)

---

### Post by P-I H on 2016-11-22
I have added me to the bug report.
I have all my media files on a server, which I think is most common. As the server uses the NFS protocol I manage to find the files, but as media is stored in both files and directories, it is not that convenient to use VLC Snap. It is also not possible to right click on the file or folder and use VLC Snap to play a file or a folder.

---

### Post by ventrical on 2016-11-23
I am getting an overlay bug in unity8 using the vlc snap .. but basically.. the same as you .. confinement. VLC cannot find my USB key. Same with .DEB install.

btw .. that pic is me with my EAA shirt on (experimental aviation association t-shirt :)

---

### Post by mc4man on 2016-11-24
Without some change then there will be a ton of advice floating about such as below that may be contrary to what Ubuntu is looking to achieve.,

Want to allow vlc snap to load files from anywhere? - install with --devmode option

---

### Post by ian-weisser on 2016-11-24
Seems like an interface issue more than a confinement issue.
Snap connectivity is defined by *snap interfaces*. One interface is made up of a plug and a slot.
The VLC snap apparently lacks a common (snap) interface with the File Manager.

```
~$ snap interfaces | grep vlc:home                    libreoffice,micropolisj,vlc
:network                 libreoffice,vlc
:network-bind            libreoffice,vlc
:opengl                  freecell-solitaire,libreoffice,mahjong-game,sudoku-game,ubuntu-clock-app,vlc
:optical-drive           vlc
:pulseaudio              freecell-solitaire,mahjong-game,sudoku-game,vlc
:unity7                  freecell-solitaire,libreoffice,mahjong-game,sudoku-game,ubuntu-clock-app,vlc
vlc:mpris                -
-                        vlc:camera
-                        vlc:mount-observe
```

Nautilus, and other file managers, need some kind of 'open with' slot. VLC needs an 'I open this kind of file' plug. Or perhaps some kind of deeper design-thinking.
On mobile, this is handled by ContentHub.

We really should review the snappy-dev mailing list. I would be quite surprised if this was not already foreseen.

---

### Post by mc4man on 2016-11-24
> **ian-weisser said:**
> Seems like an interface issue more than a confinement issue.
Snap connectivity is defined by *snap interfaces*. One interface is made up of a plug and a slot.
The VLC snap apparently lacks a common (snap) interface with the File Manager.

```
~$ snap interfaces | grep vlc:home                    libreoffice,micropolisj,vlc
:network                 libreoffice,vlc
:network-bind            libreoffice,vlc
:opengl                  freecell-solitaire,libreoffice,mahjong-game,sudoku-game,ubuntu-clock-app,vlc
:optical-drive           vlc
:pulseaudio              freecell-solitaire,mahjong-game,sudoku-game,vlc
:unity7                  freecell-solitaire,libreoffice,mahjong-game,sudoku-game,ubuntu-clock-app,vlc
vlc:mpris                -
-                        vlc:camera
-                        vlc:mount-observe
```

Nautilus, and other file managers, need some kind of 'open with' slot. VLC needs an 'I open this kind of file' plug. Or perhaps some kind of deeper design-thinking.
On mobile, this is handled by ContentHub.

We really should review the snappy-dev mailing list. I would be quite surprised if this was not already foreseen.
Based on a couple of dev comments in bug I'd say it's confinement & currently intended results for any snap not using devmode.

---

### Post by ian-weisser on 2016-11-24
Okay, prior comment cheerfully withdrawn.
Confinement it is.

---

