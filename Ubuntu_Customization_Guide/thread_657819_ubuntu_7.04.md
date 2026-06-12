---
title: "ubuntu 7.04"
date: 2008-01-04
forum: Ubuntu Customization Guide
---

### Post by ebcianfrani on 2008-01-04
i have a new computer. i built it. i installed ubuntu on it got threw the cd and installed the cd. it booted and i can not get out of dos. i give my username+password . then it goes to ebcianfrani@ubuntu:$ now what to do please help.i loaded everything fromcd live and then used the cd to load on hard drive. thank you

---

### Post by bcschmerker on 2009-05-02
> **ebcianfrani said:**
> i have a new computer. i built it. i installed ubuntu on it got threw the cd and installed the cd. it booted and i can not get out of dos. i give my username+password . then it goes to ebcianfrani@ubuntu:$ now what to do please help.i loaded everything fromcd live and then used the cd to load on hard drive. thank youLooks as though your video display adapter may not have been supported with an xserver-xorg package, as your 7.04 Feisty installation (deprecated) puts you into Console.  As of May 2009, Canonical Ltd. has only backports for 7.04 Feisty and 7.10 Gutsy; the earliest version still fully supported is 8.04-LTS Hardy, which I use.

What happens in attempting to run the following command?
```
sudo apt-get install xdebconfigurator xserver-xorg
```

---

### Post by orangepenguin97 on 2009-06-09
try typing
 
startx
 
that works in freebsd

---

