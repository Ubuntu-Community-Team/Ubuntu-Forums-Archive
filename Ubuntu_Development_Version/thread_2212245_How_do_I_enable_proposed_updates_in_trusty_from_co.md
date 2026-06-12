---
title: "How do I enable proposed updates in trusty from command line?"
date: 2014-03-20
forum: Ubuntu Development Version
---

### Post by spupazza on 2014-03-20
I need to enable the "proposed" updates by default.I installed a command line system (using ubuntu server image) and I want to test the kde 4.13 beta packages which are in proposed.I checked the /etc/apt/sources.list file but I don't see any repository about proposed hashed out.Only extras and partner are hashed out. Any tips pls?

---

### Post by zika on 2014-03-20
```
sudo nano /etc/apt/sources.list
```
Add:```
deb [arch=amd64] http://archive.ubuntu.com/ubuntu trusty-proposed multiverse restricted main universe
deb-src [arch=amd64] http://archive.ubuntu.com/ubuntu trusty-proposed multiverse restricted main universe
```and adjust accordingly to Your preference of server, extent and architecture...

---

