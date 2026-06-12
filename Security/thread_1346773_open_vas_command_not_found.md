---
title: "open vas command not found"
date: 2009-12-05
forum: Security
---

### Post by yoma819 on 2009-12-05
hello all
i am trying to install Anny configure open vas client and server
i have succeed in getting both to run and connect however when i run the command:
sudo openvas-nvt-sync 
to update my plugins i get:
sudo: openvas-nvt-sync: command not found
i can connect to my server however no plugins are listed
any help would be appreciated
thanks
yoma

---

### Post by hackertarget on 2009-12-07
sounds like the openvas binaries might not be in your path.

Try - locate openvas-nvt-sync

sudo /full/path/to/openvas-nvt-sync

---

### Post by chocolateboy on 2010-01-16
[https://bugs.launchpad.net/ubuntu/+source/openvas-server/+bug/486790](https://bugs.launchpad.net/ubuntu/+source/openvas-server/+bug/486790)

---

### Post by BinaryEnCoder on 2010-02-26
it has a right sequence to install it

first download the right packages
wget [http://wald.intevation.org/frs/download.php/595/openvas-client-2.0.4.tar.gz](http://wald.intevation.org/frs/download.php/595/openvas-client-2.0.4.tar.gz)
wget [http://wald.intevation.org/frs/download.php/561/openvas-libnasl-2.0.1.tar.gz](http://wald.intevation.org/frs/download.php/561/openvas-libnasl-2.0.1.tar.gz)
wget [http://wald.intevation.org/frs/download.php/600/openvas-libraries-2.0.3.tar.gz](http://wald.intevation.org/frs/download.php/600/openvas-libraries-2.0.3.tar.gz)
wget [http://wald.intevation.org/frs/download.php/607/openvas-manager-0.6.1.tar.gz](http://wald.intevation.org/frs/download.php/607/openvas-manager-0.6.1.tar.gz)
wget [http://wald.intevation.org/frs/download.php/588/openvas-plugins-1.0.7.tar.gz](http://wald.intevation.org/frs/download.php/588/openvas-plugins-1.0.7.tar.gz)
wget [http://wald.intevation.org/frs/download.php/593/openvas-server-2.0.2.tar.gz](http://wald.intevation.org/frs/download.php/593/openvas-server-2.0.2.tar.gz)

then install them in this order
1. openvas-libraries
2. openvas-libnasl
3. openvas-server
4. openvas-plugins

just untar, configure, make, make install

then you just follow the instructions , create a certificate , create a user then you run
openvas-nvt-sync and will work just fine , it woked for me

---

