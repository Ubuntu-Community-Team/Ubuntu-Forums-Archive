---
title: "problems installing webmin Ubuntu server 16.04"
date: 2016-08-22
forum: Server Platforms
---

### Post by dodo125025 on 2016-08-22
Hey guys, I am trying to install Webmin from here ...

[http://idroot.net/linux/install-webmin-ubuntu-16-04/](http://idroot.net/linux/install-webmin-ubuntu-16-04/)

But get the following error in the terminal when I try and get apt-get update

> N: Ignoring file 'webmin.list.' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

I look in the directory and the webmin.list there. So what can I do? It should or shouldn't be *.list extension?

---

### Post by howefield on 2016-08-23
You shouldn't have a webmin.list file in that /etc/apt/sources.list.d if you are following the linked tutorial although it'll work with one.

What is the output of 

```
cat /etc/apt/sources.list
```
and
```
ls /etc/apt/sources.list.d/
```
and
```
cat /etc/apt/sources.list.d/webmin.list
```

---

