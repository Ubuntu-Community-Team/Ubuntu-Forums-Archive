---
title: "server development tools packages?"
date: 2008-04-09
forum: Server Platforms
---

### Post by E1000 on 2008-04-09
I would like to run Ubuntu server on my flash based mini-itx PC because I have fallen in love with Ubuntu on my laptop. But there is one issue that is still preventing me from doing so. I like to compile some programs from souce. I was wondering what packages I should 'apt-get' in order to have a fully functional 'make'.

---

### Post by StarMonkee on 2008-04-10
I'm not 100% certain, but I think you just need 'build-essential', which will do the following:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binutils cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1 gcc-4.1-base libc6-dev libstdc++6-4.1-dev linux-libc-dev make patch
Suggested packages:
  binutils-doc cpp-doc gcc-4.1-locales debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc gcc-multilib manpages-dev autoconf
  automake1.9 libtool flex bison gdb gcc-doc gcc-4.1-multilib glibc-doc libstdc++6-4.1-doc make-doc diff-doc
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed
  binutils build-essential cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1 gcc-4.1-base libc6-dev libstdc++6-4.1-dev linux-libc-dev
  make patch
0 upgraded, 15 newly installed, 0 to remove and 0 not upgraded.
Inst binutils (2.18-0ubuntu3 Ubuntu:7.10/gutsy)
Inst linux-libc-dev (2.6.22-14.52 Ubuntu:7.10/gutsy-updates)
Inst libc6-dev (2.6.1-1ubuntu10 Ubuntu:7.10/gutsy-updates)
Inst gcc-4.1-base (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Inst cpp-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Inst cpp (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Inst gcc-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Inst gcc (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Inst libstdc++6-4.1-dev (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy) []
Inst g++-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Inst g++ (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Inst make (3.81-3build1 Ubuntu:7.10/gutsy)
Inst patch (2.5.9-4 Ubuntu:7.10/gutsy)
Inst dpkg-dev (1.14.5ubuntu16 Ubuntu:7.10/gutsy)
Inst build-essential (11.3ubuntu1 Ubuntu:7.10/gutsy)
Conf binutils (2.18-0ubuntu3 Ubuntu:7.10/gutsy)
Conf linux-libc-dev (2.6.22-14.52 Ubuntu:7.10/gutsy-updates)
Conf libc6-dev (2.6.1-1ubuntu10 Ubuntu:7.10/gutsy-updates)
Conf gcc-4.1-base (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Conf cpp-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Conf cpp (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Conf gcc-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Conf gcc (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Conf g++-4.1 (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Conf libstdc++6-4.1-dev (4.1.2-16ubuntu2 Ubuntu:7.10/gutsy)
Conf g++ (4:4.1.2-9ubuntu2 Ubuntu:7.10/gutsy)
Conf make (3.81-3build1 Ubuntu:7.10/gutsy)
Conf patch (2.5.9-4 Ubuntu:7.10/gutsy)
Conf dpkg-dev (1.14.5ubuntu16 Ubuntu:7.10/gutsy)
Conf build-essential (11.3ubuntu1 Ubuntu:7.10/gutsy)
```

---

