---
title: "lxc bind for wine compilation"
date: 2014-10-01
forum: Virtualisation
---

### Post by MikeCyber on 2014-10-01
Hi, I want to compile wine but on /media/michael/DATA
as I've not enough space in home. How to change that link below?
Thanks

sudo lxc-create -t ubuntu -n my32bitbox -- --bindhome $LOGNAME -a i386 --release trusty

(from: [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit))

---

