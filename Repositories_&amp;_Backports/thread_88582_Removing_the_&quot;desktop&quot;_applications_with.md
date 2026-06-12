---
title: "Removing the &quot;desktop&quot; applications without removing the desktop"
date: 2005-11-10
forum: Repositories &amp; Backports
---

### Post by arcanistherogue on 2005-11-10
Well, I use a variety of programs and I constantly switch between the three common desktop environments, XFCE KDE and GNOME.  Therefore, I have ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop installed.  However, I only use one set of apps aross all of these.  Firefox for web browsing, Konqueror for a File Browser, Gaim for IM, Open Office for office work, Kontact for email, etc.  However, I have a bunch of programs I don't use such as kopete, abiworld, and Evolution but I cannot remove because when you remove them they remove the actual kubuntu or xubuntu desktop installation.

Is it possible to remove these apps without actually removing the desktops themselves? I really don't like having all this space wasted and all my menus cluttered with at least 4 apps that all do the same thing.

---

### Post by brk3 on 2005-11-10
The desktop packages arent actually real packages they're just sort of fake packages so that you can easily install everything at once(kde for example). In other words you can safely remove these without removing the the desktop.

---

### Post by SSTwinrova on 2005-11-16
Yeah, ironically the *-desktop (or any meta-packages for that matter) take advantage of something that lots of people would love to see fixed: namely, removing a package does not remove it's dependencies.

---

