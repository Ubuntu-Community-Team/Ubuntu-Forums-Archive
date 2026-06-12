---
title: "iptables installation"
date: 2011-05-26
forum: Security
---

### Post by janis.briedis on 2011-05-26
Hello, Ubuntu world,

can anyone advise the best practice of installing and setting
the iptables on U 8.04 LTS? currently iptables is not installed
nor as package nor included as kernel module.

with best,
Janis Briedis

---

### Post by bodhi.zazen on 2011-05-26
iptables should be installed, what makes you think it is not ?

If for some reason you are using a mininimal install , LXC, Xen, or openvz perhaps it was not installed as a part of a minimal base, in that event,

```
sudo apt-get install iptables
```

How much or little do you know about managing iptables ?

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://packages.ubuntu.com/hardy/iptables](http://packages.ubuntu.com/hardy/iptables)

---

### Post by janis.briedis on 2011-05-30
Hello, bodhi.zazen,
Thank You for the provided tip, links are quite usful,
and I got my problem fixed.

wbr,
Janis Briedis

---

