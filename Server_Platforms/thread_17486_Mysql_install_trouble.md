---
title: "Mysql install trouble"
date: 2005-02-28
forum: Server Platforms
---

### Post by jsaints on 2005-02-28
New to ubuntu... Just completed install

I attempt to apt-get install the mysql-server package and I get the following Error:

Could not mark all packages for installation or upgrade
mysql-server:
 Depends: mysql-client but it is not going to be installed
 Depends: libdbi-perl but it is not going to be installed

Any ideas?
Thanks
Jon

---

### Post by p!=f on 2005-02-28
What your /etc/apt/sources.list looks like? Did you run apt-get update?

---

### Post by jsaints on 2005-02-28
That was the problem...

I just uncommented the first two sources in the /etc/apt/sources file, and now all is well.  It seems if you just uncomment the security sources, then there are mysql dependancy problems.

Thanks for your help. I have been using Ubuntu one day, and the first problem I encountered was fixed in ten minutes by a post in the forum. I love it already!!

---

### Post by p!=f on 2005-02-28
[QUOTE=jsaints]That was the problem...

I just uncommented the first two sources in the /etc/apt/sources file, and now all is well.  It seems if you just uncomment the security sources, then there are mysql dependancy problems.

Thanks for your help. I have been using Ubuntu one day, and the first problem I encountered was fixed in ten minutes by a post in the forum. I love it already!![/QUOTE]
Glad to hear you've got your MySQL up and running. Feel free to ask for help in case of troubles. ;)

---

### Post by yeye on 2005-06-21
Hi p!=f,

I got the smiliar problem here while I am installing mysql-client-4.1, 

       mysql-client-4.1:
         Depends: libdbi-perl  but it is not installable
         Depends: libdbd-mysql-perl (>=1.2202) but it is not installable

Sorry to post it here but I think my problem is kinda the same. I am not sure if my source list file is messed up or not. Please advise, thanks!

Here is my /etc/apt/sources.list file:
-----------------------------------------------------------
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary universe

----------------------------------------------------

---

