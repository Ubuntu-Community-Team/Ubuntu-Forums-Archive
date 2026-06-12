---
title: "apache2 restart fails on ubuntu 12.04 with python mismatch error on vhost ssl"
date: 2012-12-09
forum: Virtualisation
---

### Post by rcain on 2012-12-09
**apache2 restart fails on ubuntu 12.04 with python mismatch error on vhost ssl directive**

 - done: also posted bug tracker comment:: [https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/1073147](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/1073147)

 - 
i  am experiencing a problem on apache restart - whilst/after adding ssl directives to my zpanel vhosts entries.

 -  apache fails to restart, point of failure shown in error log as:

`[Sun Dec 09 02:15:03 2012] [error] python_init: Python version mismatch, expected '2.7.2+', found '2.7.3'.`

 - wherea's quick version check shows:

`root@server88-208-201-24:~# apt-get install libapache2-mod-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-python is already the newest version.`

 - this is preventing me using SSL at present, and is becoming increasingly well documented problem:

there even seems to be a bug for it, BUT it is down as status confirmed, importance low, unassigned (as of today 091212):

 - vis: [https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/1073147](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python/+bug/1073147)

also:

 - vis: [http://forums.zpanelcp.com/showthread.php?7442-Is-ZPX-changing-the-VHOSTS-after-eacht-daemon-run&p=59642&viewfull=1#post59642](http://forums.zpanelcp.com/showthread.php?7442-Is-ZPX-changing-the-VHOSTS-after-eacht-daemon-run&p=59642&viewfull=1#post59642)
 - vis: [http://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin](http://library.linode.com/web-servers/apache/installation/ubuntu-12.04-precise-pangolin)
 - vis: [https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-python)
 - vis: [http://ubuntuforums.org/showthread.php?t=2088282](http://ubuntuforums.org/showthread.php?t=2088282)

i have asked there whether they could move it up the priority stack

but in the meantime, anyone come across this, particularly anyone with experience of getting ubuntu12.04+(zpanel)+vhosts+ssl to work.

thanks for any suggestions to fix?

(preferably without a long-hand binary rebuild of apache).

---

### Post by roberthernandez on 2013-03-08
# You have to recompile mod-python and/or mod-wsgi. 


# Remove mods
apt-get remove libapache2-mod-python libapache2-mod-wsgi


# Get dependencies
apt-get build-dep libapache2-mod-python libapache2-mod-wsgi


# Build mod-python
mkdir /tmp/python
cd /tmp/python
apt-get source libapache2-mod-python
cd libapache2-mod-python-[x.x.x]
dpkg-buildpackage -rfakeroot -b


#Build mod-wsgi
mkdir /tmp/wsgi
cd /tmp/wsgi
apt-get source libapache2-mod-wsgi
cd mod-wsgi-[x.x.x]
dpkg-buildpackage -rfakeroot -b 


# Install newly compiled packages
dpkg -i /tmp/python/libapache2-mod-python-[x.x].deb /tmp/wsgi/libapache2-mod-wsgi-[x.x].deb

---

