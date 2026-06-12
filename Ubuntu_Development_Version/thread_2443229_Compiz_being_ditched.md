---
title: "Compiz being ditched?"
date: 2020-05-13
forum: Ubuntu Development Version
---

### Post by zika on 2020-05-13
```
:~$ sudo apt dist-upgrade -s
[sudo] password for ....: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  compiz compiz-gnome libmetacity1
The following NEW packages will be installed:
  libmetacity3
The following packages will be upgraded:
  metacity metacity-common
2 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Remv compiz [1:0.9.14.1+20.10.20200427-0ubuntu2]
Remv compiz-gnome [1:0.9.14.1+20.10.20200427-0ubuntu2]
Inst metacity [1:3.36.1-1] (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [amd64]) []
Remv libmetacity1 [1:3.36.1-1] []
Inst metacity-common [1:3.36.1-1] (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [all]) []
Inst libmetacity3 (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [amd64])
Conf metacity (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [amd64])
Conf metacity-common (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [all])
Conf libmetacity3 (1:3.37.1-1 Ubuntu:20.10/groovy-proposed [amd64])
```
Maybe I should just wait for compiz to catch up... ;)

---

### Post by vicsar on 2020-05-13
What do you mean by this? As far as I know it is still under active development, it hasn't been deprecated.
As of today:
The latest stable release of the Compiz 0.8 series is [0.8.8]("http://releases.compiz.org/0.8.8/")
The latest stable release of the Compiz 0.9 series is [0.9.13.0]("https://launchpad.net/compiz/0.9.13/0.9.13.0")

---

### Post by zika on 2020-05-13
I'm just giving HU that at current state of 20.10 it wants to remove some parts of compiz in order to upgrade metacity. I know that Compiz and Metacity are alive and well, that is why I'm pointing to this.
```
:~$ apt policy metacity 
metacity:
  Installed: 1:3.36.1-1
  Candidate: 1:3.37.1-1
  Version table:
     1:3.37.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu devel-proposed/universe amd64 Packages
 *** 1:3.36.1-1 500
        500 http://us.archive.ubuntu.com/ubuntu devel/universe amd64 Packages
        100 /var/lib/dpkg/status
:~$ apt policy compiz
compiz:
  Installed: 1:0.9.14.1+20.10.20200427-0ubuntu2
  Candidate: 1:0.9.14.1+20.10.20200427-0ubuntu2
  Version table:
 *** 1:0.9.14.1+20.10.20200427-0ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu devel-proposed/universe amd64 Packages
        100 /var/lib/dpkg/status
     1:0.9.14.1+20.10.20200427-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu devel/universe amd64 Packages
```

---

### Post by muktupavels on 2020-05-13
Compiz needs rebuild against new metacity... It will happen. :)

@vicsar, how did you get 0.9.13.0? Newest release is 0.9.14.1... See [https://launchpad.net/compiz/+download](https://launchpad.net/compiz/+download).

---

### Post by zika on 2020-05-14
> **muktupavels said:**
> Compiz needs rebuild against new metacity... It will happen. :)

@vicsar, how did you get 0.9.13.0? Newest release is 0.9.14.1... See [https://launchpad.net/compiz/+download](https://launchpad.net/compiz/+download).It will not keep me sleepless since I use i3 and similar... ;)

Update&#8321;:```
The following packages will be REMOVED:
  libmetacity1
The following NEW packages will be installed:
  libmetacity3
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins-default libcompizconfig0 libdecoration0 metacity metacity-common
8 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
```
(Re)solved.

---

