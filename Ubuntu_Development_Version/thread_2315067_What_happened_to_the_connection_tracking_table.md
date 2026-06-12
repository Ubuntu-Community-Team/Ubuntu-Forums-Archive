---
title: "What happened to the connection tracking table?"
date: 2016-02-25
forum: Ubuntu Development Version
---

### Post by Doug S on 2016-02-25
Does anybody know where the connection tracking table has gone?
I have always accessed it via /proc/net/ip_conntrack, but that location doesn't seem to exist anymore.
I can access it via, and for example, and once I installed the conntrack package:```
sudo conntrack --dump
```Maybe that is the only way now.

---

### Post by Doug S on 2016-04-25
I've searched internet, looked briefly that the conntrack source code, and just haven't been able to figure this one out. As there are other things to fret about, I'll just use the "sudo conntrack --dump" command.

---

### Post by cariboo on 2016-04-26
Try /usr/sbin/conntrack.

---

### Post by dino99 on 2016-04-26
Also have a warning logged
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1556419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1556419)

---

### Post by Doug S on 2016-04-26
> **cariboo said:**
> Try /usr/sbin/conntrack.cariboo: Thanks for the reply. Yes, that is what I am using now. However, and the point of my question was that, it used to be that I did not have to use any program at all to observe the connection tracking table because it was just there at /proc/net/ip_conntrack. Now it doesn't seem to be there, so where did it go? It is my preference to never have to load and use extra packages/programs on my servers if I do not absolutely have to, but rather to use basic primitives.

From digging into the source code for conntrack, it seems (I might be wrong) to be registering and using callbacks to extract the information. However, also the code hasn't changed since the file used to be at /proc/net/ip_conntrack, so I am not fully understanding.

Anyway, it is not the end of the world to have to install and use "conntrack". I just thought someone might know what happened to  /proc/net/ip_conntrack and why.

> **dino99 said:**
> Also have a warning logged
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1556419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1556419)dino99: Thanks for the reply. I am looking into your link and trying to understand if it is related to my issue or not.

---

