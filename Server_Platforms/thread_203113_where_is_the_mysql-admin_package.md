---
title: "where is the mysql-admin package?"
date: 2006-06-24
forum: Server Platforms
---

### Post by sean talbert on 2006-06-24
-- Sorry... somehow this thread was posted twice. --

I'm unable to find the mysql-admin package to install. After "apt-get update", I tried "apt-get install mysql-admin", but got "Couldn't find package mysql-admin". I also looked through dselect and Synaptic.

My /etc/apt/sources.list:

deb cdrom:[Ubuntu 6.06 _ Dapper Drake_ - Release i386 (20060531)]/ daper main restricted
deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

I even downloaded the .rpm from mysql.com, converted it to a .deb package using alien, installed using gdebi package installer, installed to /usr/share, but when I try to run it, I get a lot of "..GLib-GObject-CRITICAL **: g_type_register_static: assertion..." messages. I was able to uninstall this using Synaptic.

I read that if you installed it using apt-get, MySQL Admin was put in the Administration menu... I'd really appreciate some help getting that setup.

Thanks.

---

### Post by sean talbert on 2006-06-24
Thanks to tonyr, found the package after changing:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

to:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

---

