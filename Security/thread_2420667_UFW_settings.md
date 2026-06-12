---
title: "UFW settings"
date: 2019-06-08
forum: Security
---

### Post by thumper76 on 2019-06-08
I am new to Linix and Ubuntu. I just activated UFW set the following permissions. Basically only allowing HTTP, HTTPS and email as well as DNS out.
In checking the log, I see the the kernel is being blocked out by UFW. How do I correct this so the kernel can do it's thing? 

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
Anywhere                   DENY IN     Anywhere                  

53/udp                     ALLOW OUT   Anywhere                  
80,443,587,993/tcp         ALLOW OUT   Anywhere                  
Anywhere                   DENY OUT    Anywhere                  
53/udp (v6)                ALLOW OUT   Anywhere (v6)             
80,443,587,993/tcp (v6)    ALLOW OUT   Anywhere (v6)             
Anywhere (v6)              DENY OUT    Anywhere (v6)
```

---

### Post by kevdog on 2019-06-11
Sorry about the late reply.  The forums now-a-days are not as active as they were 5-7 years ago.  Can you post your kernel log messages so we can determine what ports are trying to be accessed?

---

