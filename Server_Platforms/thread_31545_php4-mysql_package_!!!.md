---
title: "php4-mysql package !?!?!"
date: 2005-05-03
forum: Server Platforms
---

### Post by Ashtray on 2005-05-03
Hi people of this community, 

I'm a Freelance PHP/MySQL application writer, and write my stuff in linux desktop.. 
I just broke my disciplines and crossed over to Ubuntu linux, after a couple of years Red Hat and Afterwards Fedora 1 to 3...

So much for my little introduction on this forum.

I'm having troubles with the mysql extention in PHP. Apache 2, MySQL and PHP4 are up and runnning...
Now PHP got the problem it cannot connect to a MySQL database, cuz the package php-mysql is not installed, or doesn't excist in the " package list"  or something... I already searched google to solve it out, and came to a page where it told me to edit the php.ini, and uncomment the mysql extention rule.. (So i guess there isn't a php4-mysql package at all ????) 

This didn't work out for me...

Anybody else ran into this problem ? Did you solve it out, and How ?

Regards...

---

### Post by Ride Jib on 2005-05-03
```

sudo apt-get install php4-mysql

```

then probably restart mysql

---

### Post by Ashtray on 2005-05-03
If it was that easy, i wouldn't bother registering here mate !

 ;-)

edit: apt-get says it cannot find the package, and apt-cache search php OR php4 doesnt show it either)

---

### Post by Ride Jib on 2005-05-03
[QUOTE=Ashtray]If it was that easy, i wouldn't bother registering here mate !

 ;-)

edit: apt-get says it cannot find the package, and apt-cache search php OR php4 doesnt show it either)[/QUOTE]
 You may need to add new repositories to your apt-get.

Try [this](http://www.ubuntuguide.org/#extrarepositories) first, then the command above.

---

### Post by Ashtray on 2005-05-03
**This is my current sources.list**

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Ashtray on 2005-05-03
Allright that worked...

Added the "universe" to the list, and after that apt-get update..
Afterwards is was able to install php4-mysql package !

Thx allot

---

### Post by Ride Jib on 2005-05-03
Glad to be able to help.

---

