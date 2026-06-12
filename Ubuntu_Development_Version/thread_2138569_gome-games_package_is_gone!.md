---
title: "gome-games package is gone!?"
date: 2013-04-24
forum: Ubuntu Development Version
---

### Post by pqwoerituytrueiwoq on 2013-04-24
i just used that packages last week now it is gone
it was a meta packages, why remove it? it was there on the 12th when i installed raring to my laptop
```
~$ apt-cache depends gnome-games
gnome-games
  Depends: glchess
  Depends: glines
  Depends: gnect
  Depends: gnibbles
  Depends: gnobots2
  Depends: gnome-sudoku
  Depends: gnomine
  Depends: gnotravex
  Depends: gnotski
  Depends: gtali
  Depends: iagno
  Depends: lightsoff
  Depends: gnome-mahjongg
  Depends: quadrapassel
  Depends: swell-foop
  Suggests: gnome-hearts
  Recommends: aisleriot
```
it says it has been replaced with aisleriot 
```
~$ apt-cache depends aisleriot 
aisleriot
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: gconf2
    gconf2:i386
  Depends: gconf-service
    gconf-service:i386
  Depends: guile-2.0-libs
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libcanberra-gtk3-0
  Depends: libcanberra0
  Depends: libgconf-2-4
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: librsvg2-2
  Suggests: gnome-cards-data
  Breaks: gnome-games
  Breaks: <gnome-games:i386>
  Breaks: <gnome-games-data>
  Breaks: <gnome-games-data:i386>
  Replaces: gnome-games
  Replaces: <gnome-games:i386>
  Replaces: <gnome-games-data>
  Replaces: <gnome-games-data:i386>
  Conflicts: aisleriot:i386
```

---

