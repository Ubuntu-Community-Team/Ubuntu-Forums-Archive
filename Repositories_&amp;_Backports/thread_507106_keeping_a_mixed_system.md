---
title: "keeping a mixed system"
date: 2007-07-22
forum: Repositories &amp; Backports
---

### Post by user317 on 2007-07-22
I would like to install some packages from gutsy, but mostly keep feisty the way it is.  

specifically i would like to install libghc6-happs-dev.  I am following this apt guide,

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-upgrade)

so would this work:

```
; sudo echo 'APT::Default-Release "gutsy";' >> /etc/apt/apt.conf
; sudo echo "deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe" >> /etc/apt/sources.list
; sudo echo "deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe" >> /etc/apt/sources.list
; sudo apt-get update
; sudo apt-get gutsy install libghc6-happs-dev
```

---

### Post by smartboyathome on 2007-07-22
Mixing different releases is highly advised against (especially for a development release), since this may not only break dependancies, but may also result in you getting a package which is not stable.

---

### Post by user317 on 2007-07-23
yea i know its advised against, but i would like to know if i am doing this correctly.  can anyone who is familiar with mixed systems comment if i am doing this correctly?

---

