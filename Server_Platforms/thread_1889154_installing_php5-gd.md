---
title: "installing php5-gd"
date: 2011-11-30
forum: Server Platforms
---

### Post by WASasquatch on 2011-11-30
I am running Kubuntu, upgraded to the following:

```
Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick
```

I have install apache2.2 and PHP, as well as MySQL, yet when I go to install php5-gd to get GD support, I come into a problem. 

```
sudo apt-get install php5-gd
```
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 mysql-client : Depends: mysql-client-5.5 but it is not going to be installed
 php5-gd : Depends: libjpeg62 (>= 6b1) but 6b-16.1 is to be installed
           Depends: libt1-5 (>= 5.1.0) but it is not going to be installed
           Depends: php5-common (= 5.3.8-1~dotdeb.2) but 5.3.3-1ubuntu9.6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

When I search for libjpeg62, it exists on the system. 
```

root@smiths-laptop:~# sudo apt-cache search libjpeg62
libjpeg62 - The Independent JPEG Group's JPEG runtime library (version 6.2)
libjpeg62-dbg - Development files for the IJG JPEG library (old version 6.2)
libjpeg62-dev - Development files for the IJG JPEG library (old version 6.2)

root@smiths-laptop:~# sudo apt-cache search libt1-5
libt1-5 - Type 1 font rasterizer library - runtime
libt1-5-dbg - Type 1 font rasterizer library - debugging runtime

root@smiths-laptop:~# sudo apt-cache search php5-common
php5-common - Common files for packages built from the php5 source

```


Yet it won't install. I am relatively new to Ubuntu Linux, most especially running it through SSH.

---

### Post by maverickaddicted on 2011-12-06
Try to use aptitude command instead of apt-get, which deals with dependencies better than apt-get.
```
sudo aptitude install php5-gd
```

---

### Post by rubylaser on 2011-12-06
Did you try to do what apt suggested?
```
apt-get -f install
```

Then, try the install again.

---

