---
title: "[How-To] Nemo 3.6 in Ubuntu 16.04 / upgrading from Nemo 3.4"
date: 2017-12-08
forum: Tutorials
---

### Post by thehannibal on 2017-12-08
This is meant for installing Nemo in Ubuntu with Unity patches alongside Nautilus, **do not remove/purge Nautilus **after installing Nemo that may break your system :

Grab and add ppa from : [https://launchpad.net/~nilarimogard/+archive/ubuntu/test3](https://launchpad.net/~nilarimogard/+archive/ubuntu/test3) for some essential X libraries, do :

```
sudo add-apt-repository ppa:nilarimogard/test3
sudo apt-get update
sudo apt-get install libxapp1 xapps-common
```

Now install Nemo3 with :

```
sudo add-apt-repository ppa:webupd8team/nemo3
sudo apt update
sudo apt install nemo
```

To set Nemo as default File Manager handler and desktop drawer, do :

```
gsettings set org.gnome.desktop.background show-desktop-icons false
xdg-mime default nemo.desktop inode/directory application/x-gnome-saved-search
```

---

### Post by teklife on 2018-08-11
thank you soooooo much for this. for the first time in my 10 years using Ubuntu, i had to downgrade/upgrade going back to 16.04 from 18.04, easily the worst ubuntu experience for me ever, and one of the worst distro experiences in general ever. so many things broken, and my computer has never been slower, it was slow beyond belief, and the file managers really S*UCK!! 

i wish there was a community flavor for unity/nemo, i would have to do so few changes post install and could get right to work.

---

