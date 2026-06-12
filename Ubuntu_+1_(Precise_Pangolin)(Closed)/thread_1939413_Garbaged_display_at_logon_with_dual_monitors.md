---
title: "Garbaged display at logon with dual monitors"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-03-11
Running Nouveau driver on an nVidia GTS250 dual head card with 2560x1600 primary and 1920x1080 secondary displays connected. The login screen gets mirrored on both monitors at the lower of the two resolutions. The display gets completely garbaged for about ten seconds after entering my password - looking like an unsorted Rubik's cube with chopped up pieces of the login desktop scattered across the screens, before the unmirrored desktop appears correctly across both displays.

Is there any way with the Nouveau driver to not have the login screen mirrored across both displays? I don't want to use the closed source nVidia driver, even though it allows this, because then I have to run the displays as separate X screens to cope with the secondary monitor being in portrait orientation.

---

### Post by shamusl on 2012-03-11
I have a similar problem with one monitor, but with ATI drivers. Every time I login or out the system shows odd colors and distortion.

---

### Post by cariboo on 2012-03-11
The problem has been well discussed in this thread:

[http://ubuntuforums.org/showthread.php?t=1925194&highlight=lightdm](http://ubuntuforums.org/showthread.php?t=1925194&highlight=lightdm)

---

### Post by Nick Payne on 2012-03-21
Well the latest set of updates have fixed the scrambled Rubic's cube display at logon.

---

