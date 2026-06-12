---
title: "jwm"
date: 2015-12-21
forum: Ubuntu Development Version
---

### Post by oui on 2015-12-21
I know, I know, JWM is not the window manager of lubuntu, but as some applications does not appear in lubuntu after installation, you can need a WILLING window manager ;) different of the not willing one of lubuntu (actually, I NEED for this reason JWM + xfce4-appfinder !!!)

if you do that, you will have a deception:

- the hidden tray does not work
- jwm require divers own subdirectories, but they don't exist after installation!

pls check it!

---

### Post by oui on 2015-12-21
absent directories / files:

/etc/menu-methods/jwm-desktopmenu: Zeile 329: /usr/share/desktop-directories/jwm-accessories.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 345: /usr/share/desktop-directories/jwm-development.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 361: /usr/share/desktop-directories/jwm-education.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 376: /usr/share/desktop-directories/jwm-graphics.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 391: /usr/share/desktop-directories/jwm-network.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 406: /usr/share/desktop-directories/jwm-system.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 421: /usr/share/desktop-directories/jwm-settings.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 436: /usr/share/desktop-directories/jwm-games.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 451: /usr/share/desktop-directories/jwm-office.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 466: /usr/share/desktop-directories/jwm-other.directory: Datei oder Verzeichnis nicht gefunden
/etc/menu-methods/jwm-desktopmenu: Zeile 481: /usr/share/desktop-directories/jwm-multimedia.directory: Datei oder Verzeichnis nicht gefunden

---

### Post by zika on 2015-12-21
Did You report that as a bug so that we (others) could confirm it?

---

