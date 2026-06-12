---
title: "How To Set Up A Static Ip On Ubuntu Server"
date: 2007-06-05
forum: Server Platforms
---

### Post by sam1981 on 2007-06-05
How I Can Setup A Static Ip On Ubuntu Server And Its Only Text Base

---

### Post by yabbadabbadont on 2007-06-05
[http://ubuntuforums.org/showpost.php?p=338438&postcount=7](http://ubuntuforums.org/showpost.php?p=338438&postcount=7)

Basically, you need to edit /etc/network/interfaces.

---

### Post by Wim Sturkenboom on 2007-06-05
No Ubuntu at hand, but in genral linux uses *ifconfig* to configure the interfaces.
Something like this:
```
 sudo ifconfig eth0 172.31.212.191 netmask 255.255.254.0 broadcast 172.31.213.255
```

See man ifconfig

---

