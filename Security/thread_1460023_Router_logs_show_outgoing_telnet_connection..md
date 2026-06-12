---
title: "Router logs show outgoing telnet connection."
date: 2010-04-22
forum: Security
---

### Post by a.walker on 2010-04-22
```

2010-04-21T21:11:19-05:00   fw,fwmon   src=192.168.1.65 dst=92.243.8.139 ipprot=6  sport=52491 dport=23 Telnet Dropped 
                                                    
2010-04-21T21:12:04-05:00   Previous log entry repeated 4 times                                                     

2010-04-21T21:12:52-05:00   fw,fwmon   src=192.168.1.65 dst=92.243.8.139 ipprot=6 sport=52491 dport=23 Telnet Dropped

```I have my router configured so that it drops outgoing telnet connections (and other protocols I don't use). It's a 2wire gateway. 192.168.1.65 is the internal IP of my ubuntu box.

I'm trying to figure out what normal network traffic looks like and whether I should be worried by this log entry. At the time this happened I was testing out TOR (just navigating to a few sites (dell, ubuntu forums, etc.) nothing all that interesting.)

---

### Post by cdenley on 2010-04-22
That is tor traffic. Tor routers can use any arbitrary TCP port, although port 23 is rather uncommon.

---

### Post by a.walker on 2010-04-22
> **cdenley said:**
> That is tor traffic. Tor routers can use any arbitrary TCP port, although port 23 is rather uncommon.

Thanks for clearing that up.

---

