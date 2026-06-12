---
title: "No dash on the left side, cant access installed programs"
date: 2017-07-16
forum: Ubuntu/Debian BASED
---

### Post by tli332 on 2017-07-16
So i have a problem i have Ubuntu GamePack installed and everything there is is just a drop down menu with the already preinstalled things, wine programs work.Not a english ubuntu, here are the screenshots:
[http://prntscr.com/fwdmgl](http://prntscr.com/fwdmgl)

---

### Post by deadflowr on 2017-07-16
And you wouldn't have a dash.
You're using gnome-flashback as the desktop environment, not unity.
Unity has the dash menu system.
gnome-flashback is designed to look and function like the older gnome2 desktop.

---

### Post by tli332 on 2017-07-16
Soooo, format the partition and install other distro?
EDIT: and if yes what would you suggest for gaming except for STEAM OS

---

### Post by deadflowr on 2017-07-16
> **tli332 said:**
> Soooo, format the partition and install other distro?
EDIT: and if yes what would you suggest for gaming except for STEAM OS

Do nothing and use the desktop at hand.
It's better for gaming anyway.
It's lighter.
Unity is resource heavy and that would take away gaming resources.

Everything you can install and use on Ubuntu with the unity desktop can be installed and used with the gnome-flashback desktop.
(In case that was something you were/are/could be worried about)

---

### Post by tli332 on 2017-07-16
Yeah but for example i install disord, it doesnt show up in teh dropdown menu and using ALT F2 says no such file or directory is there a fix nothing shows up even after install.

---

### Post by deadflowr on 2017-07-16
disord? Do you mean discord?
How'd you install it?

For what it's worth...
I believe that has a snap package.
Open up a terminal (try ctrl + alt + T)
paste this
```
apt-cache policy snapd
```
if it shows as Installed then try installing the snap discord package
```
sudo snap install discord
```

---

### Post by tli332 on 2017-07-16
i installed it from the main site using the deb package but now nothin, i installed Ubuntu 17.04 going to install 18 next year.

---

