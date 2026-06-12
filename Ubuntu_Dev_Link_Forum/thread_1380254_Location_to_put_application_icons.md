---
title: "Location to put application icons"
date: 2010-01-13
forum: Ubuntu Dev Link Forum
---

### Post by Jordanwb on 2010-01-13
I'm packaging a PyGTK program into a deb package. I've included the .desktop file so that the program shows up in the Applications menu under Games, but its icon is a boring grey box. If I were to edit the .desktop file for brasero:

```
[Desktop Entry]
Name=Brasero
GenericName=Disc Burner
Comment=Create and copy CDs and DVDs
Categories=GNOME;AudioVideo;DiscBurning;
MimeType=application/x-cd-image;application/x-cdrdao-toc;application/x-cue;application/x-toc;audio/x-scpls;audio/x-ms-asx;audio/x-mp3-playlist;audio/x-mpegu$
Exec=brasero %U
Icon=brasero
StartupNotify=true
Terminal=false
Type=Application
X-GNOME-FullName=Brasero Disc Burner
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=brasero
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.29.4
X-Ubuntu-Gettext-Domain=brasero
```

The Icon line simply says brasero. But where is that actual image located so I can put one for the game?

*Edit* By the way the .desktop files go in /usr/share/applications/

---

### Post by Penguin Guy on 2010-01-16
You should store all your program's custom icons in: [COLOR="Green"]/usr/share/icons/hicolor/<resolution>/<type>/<name>.png[/COLOR]

---

### Post by coyotle on 2010-02-03
or /usr/share/pixmaps

---

