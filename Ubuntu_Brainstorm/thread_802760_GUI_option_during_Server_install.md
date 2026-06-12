---
title: "GUI option during Server install"
date: 2008-05-21
forum: Ubuntu Brainstorm
---

### Post by denzilla on 2008-05-21
I realize that GUIs aren't popular among Server distros, but it would be nice if the Server installation process would allow for the inclusion of Gnome. Some of us newb jackasses would like to configure a Server with graphical tools :)

---

### Post by irrdev on 2008-05-23
I totally agree. With Opensuse and Fedora, you can install the "Server Package"  along with the desktop environment of your choice(KDE3,KDE4,GNOME). There is definitely room to fit Gnome on the Server distro CD, and it would cost nothing to add it as an optional install.

---

### Post by CrazyGuy123 on 2008-05-23
You can do this two ways round (both giving the same results):

Install Ubuntu from a desktop liveCD, and then installing the server components you need.

Install ubuntu from the server CD, and type "sudo apt-get install ubuntu-desktop", which will enable the GUI.  If you just want a basic lightweight GUI, use "sudo apt-get install gnome-desktop-environment" or "sudo apt-get install xfce", which will install the base of gnome only, or xfce only respectively.

I believe this is possible from the alternate installer already if you type "ubuntu-desktop" on one of the screens - not sure about that though - I think it might require an internet connection so it can download the extra files.

---

### Post by denzilla on 2008-05-24
I know it can be installed afterward, but the point is to have it as an option during the installation so you boot into a GUI from the moment Ubuntu boots. Some Graphical server configuration tools to come along with it would be nice as well.

---

### Post by Gina on 2008-05-26
I think you can also do it from the minimal install CD (mini.iso).

---

