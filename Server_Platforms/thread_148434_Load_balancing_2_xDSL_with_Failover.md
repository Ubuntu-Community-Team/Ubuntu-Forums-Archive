---
title: "Load balancing 2 xDSL with Failover"
date: 2006-03-22
forum: Server Platforms
---

### Post by benjo on 2006-03-22
hello.
been fiddling load balance with failover on my 2 internet providers, but seems im having problems :( i'm currently reading this article [http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html) and this [http://www.ssi.bg/~ja/nano.txt](http://www.ssi.bg/~ja/nano.txt), but when i issued :
ip route add default via GWE1 dev IFE1 src IPE1 proto static table 201
im receiving this error RTNETLINK : Network Unreachable

im using breezy, a recompiled and patch 2.6.14 kernel, iptables are also setup. im also planning this box to serve as the gateway.

anyone here who have successfully done this? inputs are greatly appreciated. 
thanks!

hapy tuxing guys! :D

---

### Post by carlexpc on 2006-03-23
i was able to implement this solution using a different distro. what i would like to do next is try this out on ubuntu breezy badger version. please try to get some ideas on [http://www.skypipes.com](http://www.skypipes.com). that site helped me a lot on my first attempt. cheers!

---

### Post by benjo on 2006-03-23
hi.
yeah, skypipes was also one of my sources.. though its "howto" is focused mainly on rh/fedora.
let me know what happens on ubuntu :)

---

### Post by benjo on 2006-03-26
bump

---

