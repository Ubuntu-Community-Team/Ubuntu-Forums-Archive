---
title: "Ubuntu packages for various server versions"
date: 2011-02-09
forum: Server Platforms
---

### Post by PiotrSta on 2011-02-09
Hi, 

I have Ubuntu Server 10.04 Lucid (LTS) installed on my server (EC2 instance). I'd like to install Memcached on it.

When I type "sudo apt-get install memcached" I get version 1.4.2-1ubuntu3 installed. 

I know there's a newer version 1.4.5 and looking at 
([http://packages.ubuntu.com/search?arch=amd64&keywords=memcached](http://packages.ubuntu.com/search?arch=amd64&keywords=memcached)) I found it's available in the newer version of Ubuntu (Maverick).

Question: is it possible to get the newer version 1.4.5 using apt-get on my current server? 

Thank You,
Piotr

---

### Post by Kooothor on 2011-02-09
Hello,
Ubuntu isn't (yet?) a rolling release distribution.
So you don't get the newest versions in the repos.
You can't use apt-get to install it as they don't have [PPA]("https://launchpad.net/ubuntu/+ppas"), but you can [compile]("https://help.ubuntu.com/community/CompilingEasyHowTo") it from the source \o/
It's easy :
```
wget http://memcached.org/latest
tar -zxvf memcached-1.x.x.tar.gz
cd memcached-1.x.x
./configure
make && make test
sudo make install
```
([source]("https://code.google.com/p/memcached/wiki/NewInstallFromSource"))

but before you do that, make sure you actually need the new things in the latest version.
otherwise, stick to the version in the repos :)

---

