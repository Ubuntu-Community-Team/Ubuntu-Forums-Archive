---
title: "Lubuntu - Autostart fails to run on 12.04"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by makitso on 2012-01-12
Have a pretty stock Lubuntu 12,04 running in Virtual Box.  Installed Cairo Dock and put a startup file in  .config/autostart.  If I click on the file from the filemanager it starts correctly but will not start upon login.  Funny, if I  add @cairo-dock -e gnome to the autostart file in  /etc/xdg/lxsession/Lubuntu then two copies run.

OK fixed it.  Seems that the ~/.config/autostart/ desktop file, from 11.10 did not work.  When I copied the desktop file from /usr/share/applications then it worked as expected.

---

