---
title: "where is libcap2-bin"
date: 2010-07-24
forum: Virtualisation
---

### Post by marcocz on 2010-07-24
Hi all, i'm following this howto to install KVM
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

when i try setcap command, i get this error
root@27819-67255:/etc/apt# setcap cap_net_admin=ei /usr/bin/qemu-system-*
The program 'setcap' is currently not installed.  You can install it by typing:
apt-get install libcap2-bin
setcap: command not found
root@27819-67255:/etc/apt# apt-get install libcap2-bin
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libcap2-bin

so i try to install libcap2-bin but:
E: Couldn't find package libcap2-bin


my sources.list:

# [Ubuntu 9.10 _Karmic Koala_- Release ]
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
#Security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

Where my repository are wrong?

Marco







DONE:
[http://packages.ubuntu.com/lucid/i386/libcap2-bin/download](http://packages.ubuntu.com/lucid/i386/libcap2-bin/download)

---

