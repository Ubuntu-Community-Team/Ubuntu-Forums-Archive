---
title: "Gmail icon on desktop?"
date: 2021-12-12
forum: Ubuntu Development Version
---

### Post by corradoventu on 2021-12-12
Installer slideshow slide: 'Make the most of the web' says:
web applications ... like Facebook or Gmail ... can be pinned to your desktop ...
but this seems impossible in recent Ubuntu releases after 20.04.
am I wrong or is the slide wrong?

---

### Post by T6&amp;sfpER35% on 2021-12-12
on xubuntu 20.04 i can drag and drop a bookmark , like FB or gmail , from Brave browser (probably FF too haven't tried) onto the desktop and voila , there's your shortcut.
from what iv'e read that's not possible on gnome . apparently gnome don't like desktop shortcuts .

---

### Post by Frogs Hair on 2021-12-12
This refers to web-apps which I have never used since they were first introduced. Could be that you have set up a web-app first.

Edit: I see no such option in online accounts , do they mean dash or desktop ?

---

### Post by grahammechanical on 2021-12-12
I agree that Gnome developers do not want icons on the desktop. Ubuntu developers have produced a Gnome shell extension that allows desktop icons on the desktop. It is installed by default. I have tried this on 22.04 development version. This is what we do.

Find the .desktop file for the application and copy it to the desktop folder. That will put a generic icon on the desktop. Set the .desktop file to allow executing as a program and that will change the generic icon to the particular icon for the chosen application and it will have a small green circle with a white tick superimposed to indicate that it is a launcher.

The location for .desktop files for deb applications is /usr/share/applications/

The location for .desktop files for snap applications is /var/lib/snapd/desktop/applications/

I have tried this for Firefox and zoom-client (both snaps) and Thunderbird a deb application. And it works.

Regards

---

### Post by corradoventu on 2021-12-13
I commonly use applications on desktop from /usr/share/applications/ and have no problem. My note is about web apps like Facebook or Gmail, they are obviously not present in  /usr/share/applications/ or /var/lib/snapd/desktop/applications/ but are just a link.

---

### Post by Frogs Hair on 2021-12-13
That part of the media is describing Firefox which has shortcuts to frequently used sites and that is possibly what's implied. It is inaccurate should be reported. If were a new user expecting to have shortcuts to facebook etc as indicated , I'd be disappointed when it wasn't so.

---

