---
title: "installation"
date: 2011-05-22
forum: Wine
---

### Post by mr.farenheit on 2011-05-22
i just started using wine again after a few years for games because most of the games i play have native installs. i tried to install taito legends and receive an error saying that .exe's are not permitted and if i did download them they may have been downloaded improperly or they are corrupt. just as a test i've also tried installing quake 3 arena and tron 2.0 and receive the same errors. i'm pretty sure there have been many advances in the wine software since i last used it which was ubuntu 5.10. i'm also sure i may have missed a step somewhere. any help would be a prreciated.

---

### Post by cayphed on 2011-05-22
Perhaps it's a configuration error, I usually use Playonlinux to configure Wine and manage the availible versions...
Try this to get it:
  wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
  sudo wget [http://deb.playonlinux.com/playonlinux_maverick.list](http://deb.playonlinux.com/playonlinux_maverick.list) -O /etc/apt/sources.list.d/playonlinux.list
  sudo apt-get update
  sudo apt-get install playonlinux

---

