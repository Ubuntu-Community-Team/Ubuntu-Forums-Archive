---
title: "How install Xorg and a windows manager on Ubuntu server?"
date: 2012-05-29
forum: Server Platforms
---

### Post by alelinuxbsd on 2012-05-29
Today i installed Ubuntu server 12.04 (64 bit edition) and i want install Xorg and a windows manager as icewm but when i make:
apt-cache search Xorg
apt-cache search icewm
i don't find anything.
Where i'm wrong?

As you can see there isn't anything wrong:
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) precise-updates main restricted
...
but don't work.

---

### Post by HermanAB on 2012-05-29
Install LXDE.

---

### Post by alelinuxbsd on 2012-05-29
Was sufficient update the packages.
sudo apt-get update
sudo apt-get upgrade
After that i installed:
sudo apt-get install xserver-xorg-core icewm xfe firefox xinit

With vi i add on .xinitrc
exec icewm-session

---

