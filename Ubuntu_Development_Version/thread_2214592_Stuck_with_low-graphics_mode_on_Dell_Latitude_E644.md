---
title: "Stuck with low-graphics mode on Dell Latitude E6440 with AMD"
date: 2014-04-02
forum: Ubuntu Development Version
---

### Post by gigix85 on 2014-04-02
Hi everyone,


As a loyal Ubuntu community  member, I took some of my spare time to take Ubuntu Trusty for a spin  and check that all was running fine on the different hardware I am  running at home and work. I did a fresh install from a live USB.


Ubuntu Trusty works absolutely fine on my Dell Latitude E6400 and E6430 laptops and I am very happy with its performance.

However,  I can't even get to the lightdm login on my Dell E6440 (running AMD  hybrid graphics). Instead, I am greeted with a low-graphics mode pop-up  and can only drop back to a shell session. Trying to restart lightdm  just keeps showing the same pop-up.


In the last 3 day, I have kept the system up to date via a  chroot on my parallel Debian install and tried again to boot Ubuntu  Trusty, but still nothing. Still running my Debian unstable system with  GNOME 3 for now.


Any suggestions ? Thanks.



Ghis

---

### Post by zika on 2014-04-02
Did You try with```
radeon.dpm=0
```kernel-boot-line switch?

---

### Post by gigix85 on 2014-04-03
did not work, but thanks for this suggestion

---

### Post by gigix85 on 2014-04-03
Any suggestion ? Otherwise, what specific details should I provide if I were to open a bug report regarding this issue ?

---

### Post by philinux on 2014-04-03
> **gigix85 said:**
> Any suggestion ? Otherwise, what specific details should I provide if I were to open a bug report regarding this issue ?

You may have hit the pixbuf bug. See my recent thread. When it says low graphics try a get  tty and use the code. I had to print it out to sort my laptop out and manually type it in.

---

### Post by gigix85 on 2014-04-04
It did not work either unfortunately.

---

### Post by wgarcia on 2014-04-04
Take a look at these bug reports:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1290745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1290745)

[https://bugs.launchpad.net/bugs/1301839](https://bugs.launchpad.net/bugs/1301839)

They seem to be the same hardware and same issue that you are having

---

### Post by gigix85 on 2014-04-04
> **wgarcia said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1290745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1290745)


For me both 12.04.4 and 14.04 beta 2 do load in live session. It's any subsequent boot after install that is however not working.

> **wgarcia said:**
> 
[https://bugs.launchpad.net/bugs/1301839](https://bugs.launchpad.net/bugs/1301839)


This could be it. Marked as affected and will help in confirming/triagging this one.

Thanks for pointing me at those bug reports. Very much appreciated.

---

