---
title: "Xubuntu Lightdm Magneta?"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Yellow Pasque on 2012-02-29
I'm sorry to threadjack, but while on the subject on Xubuntu, is anyone else getting a solid magenta lightdm/login screen? It used to be similar to the default xubuntu desktop, but it went magenta a couple days ago.

---

### Post by cariboo on 2012-02-29
Moved to a thread of it's own, as people may not see it tacked on to a thread about font problems

---

### Post by jefsview on 2012-03-01
no problems on my 64bit version. just the regular login box.

-- jeff

---

### Post by Elfy on 2012-03-01
Fine here too.

---

### Post by Yellow Pasque on 2012-03-01
For some reason, the /etc/lightdm/<something>.conf file referred to non-existent "warty" background image.

---

### Post by cariboo on 2012-03-01
It's probably a bug in Xubuntu, did you report it?

/etc/lightdm/unity-greeter.conf points to:

> background=/usr/share/backgrounds/warty-final-ubuntu.png

---

### Post by Yellow Pasque on 2012-03-01
Do you (or anyone running regular ubuntu) have that file?
```
dpkg-query -S /usr/share/backgrounds/warty-final-ubuntu.png
```

---

### Post by cariboo on 2012-03-01
I've got it in /usr/share/backgrounds, it's called warty-final-ubuntu.png, and it seems to be broken, if you change the extension to .jpg it works fine in eog

---

### Post by Elfy on 2012-03-02
/etc/lightdm/lightdm-gtk-greeter.conf 

should be - of course it can be anything you like :)

> #
# background = Background file to use, either an image path or a color (e.g. #772953)
# theme-name = GTK+ theme to use
# font-name = Font to use
# xft-antialias = Whether to antialias Xft fonts (true or false)
# xft-dpi = Resolution for Xft in dots per inch (e.g. 96)
# xft-hintstyle = What degree of hinting to use (hintnone, hintslight, hintmedium, or hintfull)
# xft-rgba = Type of subpixel antialiasing (none, rgb, bgr, vrgb or vbgr)
#
[greeter]
background=/usr/share/xfce4/backdrops/xubuntu-precise-right.png
theme-name=Greybird
font-name=Droid Sans 10
xft-antialias=true
xft-dpi=96
xft-hintstyle=slight
xft-rgba=rgb
show-language-selector=true

---

### Post by Yellow Pasque on 2012-03-02
Thanks. I had Unity-2d installed at one point. Maybe something got mixed up there. I wouldn't report it as a bug unless I was sure it happened on clean install.

---

### Post by Toz on 2012-03-02
lightdm configuration has moved to gsettings. Install dconf-tools, run dconf-editor and find configuration settings at com->canonical->unity-greeter.

---

### Post by Yellow Pasque on 2012-03-02
> **Toz said:**
> lightdm configuration has moved to gsettings. Install dconf-tools, run dconf-editor and find configuration settings at com->canonical->unity-greeter.
Thanks, but I don't have unity-greeter installed...

---

