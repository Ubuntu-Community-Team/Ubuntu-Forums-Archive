---
title: "unable to resolve host"
date: 2009-10-28
forum: Tunisia Team
---

### Post by BLiTZ TN on 2009-10-28
Hello brothers, 

when i try to fix do something
i have this error

root@(none):~# sudo: unable to resolve host (none)

some one can help me ? 

[Ubuntu 8.04 - on dedicated server]

---

### Post by sahabcse on 2009-10-28
Have you change the hostname of your system. Check the hostname entry in /etc/hosts file?

---

### Post by BLiTZ TN on 2009-10-28
No i do not change it, this is the file


root@(none):/etc# vi hosts
> 
### etherconf DEBCONF AREA. DO NOT EDIT THIS AREA OR INSERT TEXT BEFORE IT.
127.0.0.1       localhost
::1             localhost       ip6-localhost ip6-loopback
fe00::0         ip6-localnet
ff00::0         ip6-mcastprefix
ff02::1         ip6-allnodes
ff02::2         ip6-allrouters
ff02::3         ip6-allhosts

***.**.***.**

---

### Post by sahabcse on 2009-10-28
it is one type of bug follow below url for more info

[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)
[https://launchpad.net/bugs/203593](https://launchpad.net/bugs/203593)

---

### Post by omrisaber on 2009-10-29
[B]Your config file seems to beb ok.
Try to update to the 9.10 today if you can, then see what goes around (I think this bug will be fixed with this newrelease)[/B]

---

