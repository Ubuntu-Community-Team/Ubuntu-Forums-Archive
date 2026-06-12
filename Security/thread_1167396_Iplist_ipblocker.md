---
title: "Iplist ipblocker"
date: 2009-05-22
forum: Security
---

### Post by Cavs23 on 2009-05-22
I installed the program in my title. The GUI worked two days ago. Now the program doesn't even work. Log files are clean. Only thing that happens is in the terminal ```
416: LOG_IPTABLES: parameter not set

```

---

### Post by uljanow on 2009-05-23
It looks like you're using an old configuration file. Try:

```
sudo cp /usr/share/doc/iplist/examples/ipblock.conf /etc
```

---

### Post by Cavs23 on 2009-05-23
That worked. Kudos for you.

---

