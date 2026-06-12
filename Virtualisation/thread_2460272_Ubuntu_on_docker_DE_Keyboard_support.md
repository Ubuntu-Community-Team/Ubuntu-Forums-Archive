---
title: "Ubuntu on docker DE Keyboard support"
date: 2021-04-06
forum: Virtualisation
---

### Post by mdgreen on 2021-04-06
Hi! I am trying to run a VM with Ubuntu via docker and connecting to it through VNC.  Everything is working fine, except I cannot get support for special characters on a DE keyboard. I tried to install locales, run locale-gen de_DE.UTF-8, and set the environment variable for LANG to de_DE.UTF in the Dockerfile.  I can see that it is set correctly in /etc/defaults/locale when I connect with VNC, but for some reason when using the right-ALT modifier combinations, no character is registered at all.   I also tried to configure X11 with setxkbmap to use DE, again to no avail. Any help will be appreciated!Thanks.

---

### Post by mdgreen on 2021-04-09
After some further testing, I found out that the issue is connecting from a Windows machine, while it actually works when connecting from a Linux machine.  Further, according to xev, on Windows, right-alt gets mapped to left-ctrl + left-alt, while on Linux it is ISO Level 3 Shift.I tried to find a way to map this somehow directly in the ubuntu VM, but can not figure it out.  Any ideas on how to do this?

---

