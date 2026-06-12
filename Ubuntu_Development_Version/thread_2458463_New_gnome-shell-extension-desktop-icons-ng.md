---
title: "New: gnome-shell-extension-desktop-icons-ng"
date: 2021-02-25
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-02-25
New extension for desktop icons: gnome-shell-extension-desktop-icons-ng

Desktop Icons NG for GNOME Shell. It is a fork/rewrite of the official 'Desktop Icons' extension,
with these advantages:
Drag'n'Drop, both inside the desktop, between desktop and applications, and nautilus windows
Allows to use "Open with..." option with several files
When hovering or clicking on an icon with a name too large to fit, it shows the full name
Doesn't hang the compositor when there is too much activity in the desktop folder

Edit: the old gnome-shell-extension-desktop-icons is no longer present in the today ISO but has been replaced by the new one.

---

### Post by corradoventu on 2021-02-26
Works fine but... Allow launching does not work. [https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/1917044](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-desktop-icons-ng/+bug/1917044)
Copied an app eg firefox.desktop from /usr/share/applications to desktop.
new icon on desktop is a gray rectangle with a gear.
right click on the icon on desktop.
click on 'Allow launching' - nothing happen
  - icon should change to Firefox icon and Firefox should start if clicked
click on Properties -> Permissions -> Allow executing: OK

---

