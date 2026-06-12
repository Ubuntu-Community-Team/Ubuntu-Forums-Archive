---
title: "limiting the upload traffic for pppX"
date: 2006-04-02
forum: Server Platforms
---

### Post by thefaint on 2006-04-02
```
tc qdisc add dev eth0 root handle 1: htb default 10
tc class add dev eth0 parent 1:1 classid 1:10 htb rate 400kbit burst 6k prio 1
tc qdisc add dev eth0 parent 1:10 handle 10: sfq perturb 10
```

With this I have limited the upload for eth0 to 400Kbit. The problem is that I can't use it for pppX (ppp0 for example)... HELP ](*,) :confused:

---

