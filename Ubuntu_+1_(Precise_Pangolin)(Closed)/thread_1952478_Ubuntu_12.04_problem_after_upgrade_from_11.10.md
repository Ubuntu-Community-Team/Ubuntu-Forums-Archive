---
title: "Ubuntu 12.04 problem after upgrade from 11.10"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BSG Fan on 2012-04-04
Today I upgraded my computer from Ubuntu 11.10 [Oneiric Ocelot] to Ubuntu **12.04** LTS.

Okay, all look okay but in the process of running there were two files needed, beign one of them: Python-uno.

well, I thought that with the incming updates thoese problems may be fixed, but it doesn't.

so I have problems with the Download Manager for updates.
I can not download those updates since it says that the package system is broken.

Any opinion to solve this?

---

### Post by BSG Fan on 2012-04-04
Any idea?

---

### Post by 2F4U on 2012-04-04
Try running command line apt-get command without the update manager or software center open. Thats the reason why it can't aquire a lock.

---

### Post by codemaniac on 2012-04-04
saearch the python-uno package and try to install it with apt .

```
sudo apt-cache search python-uno
```

---

### Post by philinux on 2012-04-04
Moved to testing forum.

---

### Post by Alan F on 2012-04-04
I had just the same problem yesterday. However synaptic sorted it out.

---

### Post by buzzmandt on 2012-04-04
I had this issue as well. From command line run```
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade

```fixed it for me

---

### Post by BSG Fan on 2012-04-05
Thank you everybody.
The problem was solved.

:popcorn:

---

