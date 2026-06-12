---
title: "Change/Add Keyboard Layout Utility."
date: 2009-05-15
forum: The Cafe
---

### Post by kagashe on 2009-05-15
It is easy to change/add Keyboard Layout on Gnome/KDE etc but one has to  edit xorg.conf or use dpkg-reconfigure or setxkbmap for doing this on other WMs. Moreover xorg.conf is unnecessary today.

I have written a simple bash script which interacts with user through dialog and changes/adds Keyboard Layout (using setxkbmap command). I have also converted it into .deb for easy installation. It is built on Ubuntu jaunty and may not work on Hardy, however, I may build it for Hardy if required by anyone.

The changes to your present Keyboard Layouts would be temporary and lost on logout/reboot/shutdown.

When you say 'no' to change the default layout the script changes it to 'us' on its own, therefore, select 'yes' if you are using other than 'us' as default.

I request some people to download and try. You can try it even on Gnome or KDE.

It can be installed by double clicking through gdebi or through:
> $ sudo dpkg -i mykeyboard_1.1-1_all.deb
and removed through:
> sudo dpkg -r mykeyboard

The utility can be started through:
> $ mykeyboard


The .deb file is attached.

kagashe

---

### Post by kagashe on 2009-05-25
Bump

kagashe

---

### Post by LookTJ on 2009-05-25
There's already a keyboard layout utility in Gnome. Just by right clicking on the Gnome panels, add to item. and search "keyboard".

In case you don't know :D

---

### Post by kagashe on 2009-05-25
> **Taylor said:**
> There's already a keyboard layout utility in Gnome. Just by right clicking on the Gnome panels, add to item. and search "keyboard".

In case you don't know :DThis post is not a joke. Please read the first line of my post.

What about Fluxbox/IceWM/Openbox/LXDE on Ubuntu?

kagashe

---

### Post by LookTJ on 2009-05-25
> **kagashe said:**
> This post is not a joke. Please read the first line of my post.

What about Fluxbox/IceWM/Openbox/LXDE on Ubuntu?

kagashe
All that you mentioned, except maybe LXDE, is a window manager.  You could combine GNOME, XFCE, or KDE with Openbox and other WMs.

But you do make a good point.

---

### Post by kagashe on 2009-05-25
> **Taylor said:**
> All that you mentioned, except maybe LXDE, is a window manager.  You could combine GNOME, XFCE, or KDE with Openbox and other WMs.

But you do make a good point.It is possible to use all such WMs as standalone and there are plenty of posts regarding them on this forum. On low memory machines they have a value.

Lately, this forum has lost their appreciation but it is hearting to note that memory requirement of Jaunty is less than Intrepid/Hardy/Gutsy and comparable to Feisty and Gnome has become usable on 256 MB RAM. You can see the comparison on [Memory used after Boot Chart]("http://tuxradar.com/files/ubuntu_road16.png") on [TUXRadar]("http://tuxradar.com/content/road-jaunty-look-back-ubuntus-history").


kagashe

---

