---
title: "[HOW TO] Ubuntu Studio 16.04.1 with GNOME 3.20"
date: 2016-07-31
forum: Ubuntu Studio
---

### Post by helios16v on 2016-07-31
Just writing this guide here to help out anyone else that has had this issue I ran into yesterday while switching over to Ubuntu Studio and didn't want to use XFCE.

Now there are ways to get Ubuntu Studio working with GNOME 3.20, however it's easier to go the other route with Ubuntu GNOME and install the Studio packages.

First download and install [Ubuntu GNOME 16.04.1](https://wiki.ubuntu.com/UbuntuGNOME/GetUbuntuGNOME/LTS)

Once Ubuntu Gnome is installed, lets update GNOME 3.18 to 3.20 using
```
sudo add-apt-repository ppa:gnome3-team/gnome3-staging
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt update
sudo apt dist-upgrade
reboot
```

At this point you're now on Ubuntu GNOME with GNOME 3.20 and we can convert that into Ubuntu Studio while keeping GNOME3 using
```
sudo apt-get update
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
reboot
```

Congratulations! Once you have all of that finished, you should be on Ubuntu GNOME using GNOME 3.20 with all Ubuntu Studio Packages and Programs installed and ready to use.

I hope this helps anyone else who wants to use Ubuntu Studio but doesn't want to use XFCE

---

