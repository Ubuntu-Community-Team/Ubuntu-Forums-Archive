---
title: "Gnome-Shell: screenshot misses current window"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by keithpeter on 2012-04-02
Hello All

If you are using gnome-shell, try taking a screenshot of the **current window** with the screenshot application. Does it come out correctly?

I'm experimenting with gnome desktop installed on top of a command line Ubuntu netinstall, so no Unity. Screenshot is snapping current windows upside down and displaced horizontally (nvidia proprietary drivers). GIMP is screengrabbing the current window correctly.

If you have a Unity+Gnome shell install and snapshot works correctly when running gnome-shell, then I know I'm looking for a library or setting.

Apart from that it's all hunky dory. Occasional crash in line with the gs bug, but recovers quickly.

---

### Post by mc4man on 2012-04-02
Yeah - it's all messed up in Gs - creates an upside down, offset, mirror image

---

### Post by keithpeter on 2012-04-02
> **mc4man said:**
> Yeah - it's all messed up in Gs - creates an upside down, offset, mirror image

Yup, that's the way it looks. When you use GS installed alongside Xubuntu it does not do that. Installing the gnome desktop (package 'gnome') with gdm on top of a netinstall command line version of 12.04 it does.

---

### Post by jbicha on 2012-04-02
Screenshots work great here, even with GNOME Shell. What graphics driver are you using?

Do the problems still happen if you try an alternate screenshot app like Shutter?

---

### Post by pressureman on 2012-04-02
Somewhat unrelated, I noticed that the screencast/record feature in GS, which is supposed to open a separate file each time it is invoked, seems to continue recording to the same file, if activated a second time in the same sitting. The docs say that it's supposed to create a uniquely-named file, each time a recording is started.

Even moving the first file to the trash doesn't stop it - the second recording session appends to that file that is in the trash. It's as if it doesn't close the file descriptor.

---

### Post by jbicha on 2012-04-02
pressureman, could you report that bug? Forwarding it to bugzilla.gnome.org would be helpful too since it's the GNOME developers that would fix something like that. Thanks!

---

