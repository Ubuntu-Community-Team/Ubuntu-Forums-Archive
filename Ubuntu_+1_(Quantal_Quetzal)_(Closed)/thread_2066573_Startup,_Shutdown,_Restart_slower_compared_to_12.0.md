---
title: "Startup, Shutdown, Restart slower compared to 12.04"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cromat on 2012-10-04
I just upgraded my laptop and have noticed that it takes significantly longer to shutdown and restart, is anyone else noticing this? I have also noticed on cold boot pressing the super key takes longer to load the items from the search.

---

### Post by dino99 on 2012-10-05
yeah QQ still needs some upstart fixes

[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639)

---

### Post by serdotlinecho on 2012-10-05
On my machice using Nvidia proprietary driver, the shutdown process a little bit slow. But on(netbook) intel driver it is fast.

---

### Post by baizon on 2012-10-05
In my case, sometimes i got a fast shutdown (~1 sec), and sometimes it takes over 5 sec :(

---

### Post by cromat on 2012-10-05
I have intel as well and I am seeing shutdown and restart take about 5 seconds minimum. On 12.04 I had < 2 seconds all the time. For those on intel that are reporting a second did you upgrade or clean install 12.10. I dd an upgrade.

Just curious the bug posted exactly describes the console output I get on shutdown.  Hopefully this is fixed quickly as with the zenbook I need a 3.5 kernel and I'd rather not compile one again if 12.10 is a solid release.

---

### Post by RavisPohan on 2012-10-05
I have intel, and I have to say that my startup time has at least halved since 12.04. The first thing I noticed about Quantal was how much faster it booted. Don't know why.... Running a fresh install, by the way.

---

### Post by philinux on 2012-10-05
> **cromat said:**
> I just upgraded my laptop and have noticed that it takes significantly longer to shutdown and restart, is anyone else noticing this? I have also noticed on cold boot pressing the super key takes longer to load the items from the search.



To check what dino is saying try disabling network then try a shutdown.

---

### Post by cromat on 2012-10-05
Hey I have been testing more and everyone is correct my boot time is much faster. The shutdown time is related to the bug as if I turn the network of it shutdowns down quickly.

---

