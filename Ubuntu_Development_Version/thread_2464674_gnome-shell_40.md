---
title: "gnome-shell 40"
date: 2021-07-08
forum: Ubuntu Development Version
---

### Post by MyMurry on 2021-07-08
Hello!

Is gnome-shell 40 already arrived in impish? On the livecd I found only gnome-shell 3.38.

Regards

---

### Post by VMC on 2021-07-08
Yes, the current ISO has Gnome 40.2.0, also Firefox version is 90.
This is the one I installed:
[http://cdimage.ubuntu.com/daily-live/pending/](http://cdimage.ubuntu.com/daily-live/pending/)

---

### Post by corradoventu on 2021-07-08
see [https://ubuntuforums.org/showthread.php?t=2464651](https://ubuntuforums.org/showthread.php?t=2464651)

---

### Post by VMC on 2021-07-08
Using the "super-key" is no different than using it on my old Gnome 38. It just brings up left-hand doc.

---

### Post by corradoventu on 2021-07-09
The current ISO dated 2021-07-08 08:37 does NOT contain gnome 40. 
here a cut-out from associated file .manifest 

```
gnome-settings-daemon	3.38.2-1ubuntu1
gnome-settings-daemon-common	3.38.2-1ubuntu1
gnome-shell	3.38.4-1ubuntu3
gnome-shell-common	3.38.4-1ubuntu3
gnome-shell-extension-appindicator	40-1
gnome-shell-extension-desktop-icons-ng	0.17.0-1ubuntu1
gnome-shell-extension-ubuntu-dock	69ubuntu1
```

gnome 40 is still only in proposed.
you may check your gnome with ```
apt policy gnome-shell
```

Here my desktop after pressing 'super' key, note the 2 thumbnails of the workspaces on top of the screen

---

