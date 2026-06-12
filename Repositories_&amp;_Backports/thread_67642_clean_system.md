---
title: "clean system"
date: 2005-09-20
forum: Repositories &amp; Backports
---

### Post by uten on 2005-09-20
ok while i was at school today i installed ubuntu on my laptop. i have been using ubuntu for a couple weeks, but due to an error on my part i accidentally deleted the partition. when i installed the OS today i had no network connection available. as soon as i got home i went to update my machine, apt-get update, but surprisingly it said update finished without connecting to any repositories. same thing with the upgrade command. how can i get apt-get to work properly? plz help

---

### Post by Xian on 2005-09-20
Please post the output of the following command:

```
$ sudo apt-get update
```

---

### Post by uten on 2005-09-20
uten@ubuntu:~$ sudo apt-get update
Password:
Reading package lists... Done
uten@ubuntu:~$

---

### Post by Xian on 2005-09-20
Hmmm....okay, please post the contents of the file below
and of the command listed next.

$ sudo gedit /etc/apt/sources.list
$ ifconfig

---

### Post by uten on 2005-09-20
[QUOTE=Xian]Hmmm....okay, please post the contents of the file below
and of the command listed next.

$ sudo gedit /etc/apt/sources.list
$ ifconfig[/QUOTE]
 deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



ohh they are all commented, let me remove the comments and see if it works

---

### Post by uten on 2005-09-20
[QUOTE=uten]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://jm.archive.ubuntu.com/ubuntu](http://jm.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe



ohh they are all commented, let me remove the comments and see if it works[/QUOTE]
 yeh its working well now, thnx for the help

---

