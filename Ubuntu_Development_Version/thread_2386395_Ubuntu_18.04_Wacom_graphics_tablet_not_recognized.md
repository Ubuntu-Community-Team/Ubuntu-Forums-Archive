---
title: "Ubuntu 18.04: Wacom graphics tablet not recognized"
date: 2018-03-05
forum: Ubuntu Development Version
---

### Post by siggi2 on 2018-03-05
Hi,

I have the same problem with Ubuntu 18.04 developing branch as described for Ubuntu 16.04 ([https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1575887]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1575887")): I can draw, e.g., with tuxpaint, I can use stylus and graphic tablet "Wacom Intuos Art Black Pen + Touch S" like a touchpad with mouse (left, muddle, right button), 

But I cannot access the pad via Settings > Devices > Wacom Tablet: "Stylus not recognized". So, no reprogramming of stylus buttons and tablet buttons :(

**Hopefully this will be resolved till the final version of 18.04 in April?**

I already described it in the link cited above, but this discussion forum here on Bionic Beaver development seems to be more appropriate.

---

### Post by siggi2 on 2018-03-05
It is a bug report now: [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1575887]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1575887")

Hopefully some other Wacom Intuos users who also test Bionic will be affected, too. This would help getting Bionic Wacom tight for the final version.

---

### Post by siggi2 on 2018-03-05
My solution, as posted on  [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1753525]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1753525")

sudo apt update
sudo apt install ubuntu-gnome-desktop
sudo apt install --reinstall gnome-control-center

Reboot, login into 'Gnome on xorg', Wacom now programmable with Settings > Devices > Wacom Tablet

Log out, login on 'Ubuntu', now Ubuntu does it too :)

---

### Post by chamira on 2018-04-30
I hope so, I have been using versions of Wacom tablets for over 10 years now and there have always been issues which eventually get fixed but others crop up.

At the moment, on a new install of Ubuntu 17.10 using CTH 490 everything works apart from the 'mode' setting that does not seem to stick: [https://ubuntuforums.org/showthread.php?t=2390056&highlight=wacom](https://ubuntuforums.org/showthread.php?t=2390056&highlight=wacom)

---

### Post by QIII on 2018-04-30
18.04 is now in released and is no longer the development version.

Closed.

---

