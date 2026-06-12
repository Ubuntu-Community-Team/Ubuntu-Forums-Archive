---
title: "Webmin dependency issue Ubuntu Server Edition 10.04"
date: 2010-04-03
forum: Server Platforms
---

### Post by haddog on 2010-04-03
I encountered a a dependency issue when trying to install Webmin on Ubuntu Server Edition 10.04 Beta1. When you try to install webmin, libmd5-perl is not available in any of the lucid repositories:

haddog@mydeb32server1:/options$ sudo dpkg -i webmin_1.490_all.deb
Selecting previously deselected package webmin.
(Reading database ... 66348 files and directories currently installed.)
Unpacking webmin (from webmin_1.490_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
webmin depends on libmd5-perl; however:
Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
webmin

I resolved the dependency prob by adding the following repository to my /etc/apt/sources.list :

**deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) etch main**

Then I did a sudo apt-get update then sudo apt-get install and libmd5-perl installed fine along with webadmin. BTW. I got a GPG error when doing a apt=get update because I did not import the public key for the debian repos I used to get libdm5-perl, which doesn't matter to me as I commented out the repos once I got libmd5-perl installed.

---

### Post by KB1JWQ on 2010-04-03
While this works, you may not like the long term results of this.

The proper solution is to log a bug in Launchpad-- remember, you're on a beta, not a stable release. :-)

---

