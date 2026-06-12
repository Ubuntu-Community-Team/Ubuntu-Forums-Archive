---
title: "Ubuntu Server 10.10 No internet"
date: 2011-06-02
forum: Server Platforms
---

### Post by geoffy on 2011-06-02
alright so im trying to set up Ubuntu server 10.10 on an old dell, the problem is i need to download java but i cant because the add apt repository command does not exist, i cant download any updates because they fail to be fetched which leads me to believe that i cant connect to the internet via ethernet. any help would be appreciated.

---

### Post by ruffEdgz on 2011-06-02
Do some of the commands here and post back the results:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
ps aux | grep "NetworkManager" | grep -v "egrep"
```

Thanks!

---

### Post by geoffy on 2011-06-02
i would be happy to if i could get a way to copy it off of the other computer but my flash drives wont mount. i could summarize the longer ones and i dont mind typing the shorter if that would work. im asking a bit much i know.

---

