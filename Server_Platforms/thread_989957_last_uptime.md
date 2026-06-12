---
title: "last uptime"
date: 2008-11-22
forum: Server Platforms
---

### Post by razy8 on 2008-11-22
Hello, can anyone tell me how to get/calculate the last uptime ?

---

### Post by brujoand on 2008-11-22
Last as in before the resent reboot or as in right now? 
The latter is just uptime, (typed in a console).
For the first I guess you could check /var/log/syslog to calculate the previous uptime..

Anders

---

### Post by razy8 on 2008-11-22
I forgot about the syslog, thanks

---

### Post by Dr Small on 2008-11-22
I use uptimed for that. Just install uptimed, then run:
```
uprecords
```

---

