---
title: "Starting Denyhosts up for the first time"
date: 2009-07-06
forum: Security
---

### Post by keithclark on 2009-07-06
How do I startup denyhosts?  I've installed it via synaptic and modified its config file.  Now, how do I get it to run?

Keith

---

### Post by keithclark on 2009-07-06
Ok, I tried

```
sudo denyhosts start
```

But I get

DenyHosts could not obtain lock (pid: 23471)
[Errno 17] File exists: '/var/run/denyhosts.pid'

---

### Post by Dave_Connor on 2009-07-07
Try "sudo /etc/init.d/denyhosts stop" and then enter "sudo /etc/init.d/denyhosts start" in your terminal.

---

