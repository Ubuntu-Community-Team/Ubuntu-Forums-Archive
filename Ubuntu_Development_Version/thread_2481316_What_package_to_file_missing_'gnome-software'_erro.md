---
title: "What package to file missing 'gnome-software' error against?"
date: 2022-11-25
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2022-11-25
If you are creating a .desktop on the desktop... or in Nautilus... and use: Open With > Open With Other Application > Find New Applications... It errors out and locks up everything. The error displayed says that it can't find 'gnome-software'.

If I install 'gnome-software', it continues on normally... I want to file a bug to report it and get that resolved, but unsure what package to file it against.

I'm guessing nautilus or gnome-shell... (Lunar 23.04)

---

### Post by Claus7 on 2022-11-26
Hello,

I create a .desktop file under desktop using text editor. I open nautilus and allow show hidden files. I right click on .desktop and I cannot find the option Find New Applications. Do I miss something?
edit: Doing it directly from Desktop it locked momentarily everything. I have to press Cancel first and then OK for the Desktop to become cleared.

Regards!

---

### Post by MAFoElffen on 2022-11-26
See attached photo, near bottom.

Another user had said that with the newest version of Gnome, that you could no longer launch a script straight from the desktop, nor straight from Nautilus... Since I had that in the instructions to users, to be able to launch the UbuntuForums 'system-info' script, I wanted to ensure it was still possible. While testing and making sure the script works for 23.04, that is when I found this problem.

I updated my code, and everything also works with launching BASH scripts from Nautilus and from a Desktop.

---

### Post by jbicha on 2022-11-28
Please file that bug against nautilus. Thank you!

---

### Post by MAFoElffen on 2022-11-28
Bug Reported against Nautilus:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1998124](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1998124)

---

