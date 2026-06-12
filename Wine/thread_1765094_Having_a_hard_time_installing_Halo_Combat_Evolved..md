---
title: "Having a hard time installing Halo Combat Evolved...."
date: 2011-05-22
forum: Wine
---

### Post by mclizardman on 2011-05-22
Hello, I am trying to install Halo Combat Evolved using Wine, but I can't conduct the first step which is to set the setup file to be able to executed as a program. But, when i check the box I get an error message saying that it couldn't set it because it is a read only file. How do I fix this? Thanks for the help! :)

---

### Post by mclizardman on 2011-05-22
Actually found a way around the permission, but now while trying to install after entering the product key and get an error that says "Cannot load PidGen.dll". What does this mean?

---

### Post by cayphed on 2011-05-22
Try Playonlinux....
wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_maverick.list](http://deb.playonlinux.com/playonlinux_maverick.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

---

