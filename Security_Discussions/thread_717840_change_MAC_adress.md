---
title: "change MAC adress"
date: 2008-03-07
forum: Security Discussions
---

### Post by etusha on 2008-03-07
i cant change mac 

sudo macchanger -r eth0
ERROR: Can't change MAC: interface up or not permission: Device or resource busy

---

### Post by Biochem on 2008-03-07
Those instructions worked for me

[http://ubuntuforums.org/showthread.php?t=167177](http://ubuntuforums.org/showthread.php?t=167177)

good luck

---

### Post by HermanAB on 2008-03-07
$ man ifconfig

$ sudo ifconfig eth0 hw ether :2:3:4:5:6

Cheers,

Herman

---

