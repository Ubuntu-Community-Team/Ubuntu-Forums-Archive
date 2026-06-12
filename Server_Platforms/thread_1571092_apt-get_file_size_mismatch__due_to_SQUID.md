---
title: "apt-get file size mismatch || due to SQUID"
date: 2010-09-09
forum: Server Platforms
---

### Post by SlugSlug on 2010-09-09
Hi All,

I am trying to get apt-get to work on a server thats behind a squid proxy server..

I have added exections in squid.conf to allow all on .ubuntu.com.

apt-get can find updates but when it try's to download/install I get 
```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi_0.6.0ubuntu2_all.deb  Size mismatch
```if I 
```
wget http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi_0.6.0ubuntu2_all.deb
```it works..

Can anyone help?

---

### Post by SlugSlug on 2010-09-10
--bump--

---

### Post by TrinitronX on 2012-01-19
I have been seeing similar issues with both apt-get on Ubuntu and yum on CentOS behind a squid proxy.

One workaround is to clear the local package manager caches, however this is far from a good solution IMHO.

Here's how to do it:

**Ubuntu**
```
sudo find /var/lib/apt/lists/ -type f -exec rm -f {} \;
```

**CentOS**
```
sudo rm -f /var/lib/rpm/__*
sudo rpm --rebuilddb
sudo yum clean all
```

Note: There is also a potential squid.conf solution here:
[http://veejoe.net/blog/2009/05/trouble-with-apt-get-and-squid/](http://veejoe.net/blog/2009/05/trouble-with-apt-get-and-squid/)

However, after enabling this option, I was still able to reproduce apt-get problems.

There has been some discussion here about it as well:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565555](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=565555)

---

