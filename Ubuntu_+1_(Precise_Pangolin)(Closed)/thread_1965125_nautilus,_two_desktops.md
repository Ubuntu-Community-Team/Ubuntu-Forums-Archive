---
title: "nautilus, two desktops"
date: 2012-04-25
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jeremy on 2012-04-25
I suddenly have two desktop icons in Nautilus, not a show stopper, but if anyone knows how to remove one, or how to 'reset' nautilus, that would be appreciated greatly.

---

### Post by dino99 on 2012-04-25
maybe you get both installations of:
- indicator-applet-complete package
- old manual "add to panel" icons (mainly gtk2)

so a gnome-panel --replace &     will clean the room, or do it by hand

---

### Post by jeremy on 2012-04-25
Thanks for your answer. I looked, and do not have any gnome-applet-complete package installed (or available).
I tried gnome-panel --reset and only got:

$ gnome-panel --reset
Unknown option --reset

---

### Post by mc4man on 2012-04-25
It looks like your Downloads has been switched to Desktop, what does this file show?
```
gedit ~/.config/user-dirs.dirs
```
The default file is this
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

---

