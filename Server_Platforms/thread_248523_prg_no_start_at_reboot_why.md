---
title: "prg no start at reboot: why???"
date: 2006-09-01
forum: Server Platforms
---

### Post by dirkdekker on 2006-09-01
Hi, this week i installed pound on server:5.10 breeze. That worked ok with help of this forum (Azz).
After reboot the logs reports this: Pound won't start unconfigured. Configurate & set startup=1 in /etc/default/pound

I don't now what to do now.
Please inform me what steps where I have to make.
Dirk

---

### Post by Uluen on 2006-09-01
Doesn't this message tell you exactly what to do?
Is there a value "startup=1" in the file "/etc/default/pound"?

---

### Post by dirkdekker on 2006-09-04
Hello Uluen, 
no!
I installed the standard pound version 1.9-1 and in the pound.cfg file is no default line: startup=1 

btw: if I change the pound.cfg while pound =started, how to handle to tell pound the use the new pound.cfg file
thanks for answering.
dirk

---

### Post by Uluen on 2006-09-04
You might need to read some more about it, maybe when you configure it (however that is done), the config file will be updated.

Usually you can restart a service with ```
$ sudo /etc/init.d/servicename restart
```

---

