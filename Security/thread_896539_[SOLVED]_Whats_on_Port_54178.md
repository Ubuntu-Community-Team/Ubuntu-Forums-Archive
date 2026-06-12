---
title: "[SOLVED] Whats on Port 54178??"
date: 2008-08-21
forum: Security
---

### Post by terry123b99 on 2008-08-21
Firestarter has just detected an attempt to connect to my Port 54178.

Anyone know if this is an attempted attack? I as far as am aware have nothing running on that port?

---

### Post by moonpup on 2008-08-21
Most likely a random port scan. To make sure nothing is running on that port you can simply:

```
netstat -an|grep 54178
```

Hopefully this will return nothing, but if it does you can type the following to see what is actually running on that port.

```
sudo lsof -i :54178
```

My guess is you are fine and it's a random scan...

---

### Post by terry123b99 on 2008-08-21
Thanks, tried that nothing shown which is good news. :)

---

