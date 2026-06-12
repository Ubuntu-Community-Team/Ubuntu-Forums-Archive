---
title: "gnome-shell is broken in zesty"
date: 2017-01-19
forum: Ubuntu Development Version
---

### Post by jbicha on 2017-01-19
gnome-shell is [broken]("https://launchpad.net/bugs/1657958") in zesty.

Because unattended-upgrades are currently upgrading all zesty packages [automatically]("https://ubuntuforums.org/showthread.php?t=2346439"), I recommend you run these commands and wait for a post here saying that things are working again.

```

sudo apt-mark hold gnome-shell
sudo apt-mark hold gnome-shell-common
```

---

### Post by harry332 on 2017-01-20
So Jeremy,
you mean the gnome-shell (v. 3.22.2-1ubuntu1~ubuntu16.10.1) in Gnome3-Staging (Yakkety branch) is not the same?
That one works just fine in Zesty too.

You are only saying the Zesty official repo gnome-shell ( v. 3.22.2-2ubuntu1) is broken:
[https://launchpad.net/ubuntu/+source/gnome-shell/3.22.2-2ubuntu1](https://launchpad.net/ubuntu/+source/gnome-shell/3.22.2-2ubuntu1)

---

### Post by jbicha on 2017-01-20
Yes, yakkety and the GNOME3 Staging PPA for yakkety never had this bug. Yes, 3.22.2-2ubuntu1 is the broken version. Sorry for not mentioning that in my original post.

---

### Post by fthx on 2017-01-20
[https://launchpad.net/ubuntu/+source/gnome-shell/3.22.1-1ubuntu2/+build/11097027/+files/gnome-shell-common_3.22.1-1ubuntu2_all.deb](https://launchpad.net/ubuntu/+source/gnome-shell/3.22.1-1ubuntu2/+build/11097027/+files/gnome-shell-common_3.22.1-1ubuntu2_all.deb)
[https://launchpad.net/ubuntu/+source/gnome-shell/3.22.1-1ubuntu2/+build/11097027/+files/gnome-shell_3.22.1-1ubuntu2_amd64.deb](https://launchpad.net/ubuntu/+source/gnome-shell/3.22.1-1ubuntu2/+build/11097027/+files/gnome-shell_3.22.1-1ubuntu2_amd64.deb)

Just in case... :-)
Of course I've read your messages after updating and restarting (to see the sound pop-up not moving !).

---

### Post by jbicha on 2017-01-20
A Debian developer identified a fix. Hopefully this new version [3.22.2-3ubuntu1]("https://launchpad.net/ubuntu/+source/gnome-shell/3.22.2-3ubuntu1") will arrive in zesty soon!

---

### Post by harry332 on 2017-01-20
GS 3.22.2-3ubuntu1 is already in Zesty proposed.

---

### Post by jbicha on 2017-01-20
This is fixed now.

```
sudo apt-mark unhold gnome-shell
sudo apt-mark unhold gnome-shell-common
sudo apt update
sudo apt upgrade
```

---

### Post by #&amp;thj^% on 2017-01-20
Thanks Jeremy for the update.

---

