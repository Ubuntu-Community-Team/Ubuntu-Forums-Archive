---
title: "ssh ubuntu"
date: 2010-05-06
forum: Security
---

### Post by coolman98 on 2010-05-06
[LEFT]When I try to ssh into my other ubuntu machine I get an error that says "port 22 connection refused" . I have been hunting around for an answer but can't find any.
[/LEFT]

---

### Post by cdenley on 2010-05-06
Either you don't have an ssh server installed, or it is being firewalled.
```

sudo apt-get install openssh-server
sudo netstat -tlnp
sudo iptables -L -n

```

---

