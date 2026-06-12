---
title: "Max TCP connections (per process ?)"
date: 2009-03-25
forum: Server Platforms
---

### Post by mr_meuble on 2009-03-25
Hi there,

I've been hanging around for a while, looking for a way to change this parameter.

On several applications (MTA's), I tried to evaluate the maximum SMTP connections my box was able to handle. Well, it appears that I just can't reach the application limit because the maximum TCP connections is reached beforehand.

This maximum remains the same : 1023. Another user, Googler, [wrote]("http://ubuntuforums.org/showthread.php?t=758083") about that a year ago, but he never get close to a solution that I'm aware of.

Finally, my question is : what is (are) the parameter(s) involved in limiting the number of TCP connections at the OS level (more precisely ubuntu) ?

Thanks !


Note: box running Intrepid.

---

### Post by Anthon on 2009-03-25
Have you looked here?:
[http://fasterdata.es.net/TCP-tuning/linux.html](http://fasterdata.es.net/TCP-tuning/linux.html)

---

### Post by mr_meuble on 2009-03-25
Yep, did it before but there's no option for number of connections. It's mainly about the connection itself.

---

### Post by marcusherou on 2009-12-15
> **mr_meuble said:**
> Yep, did it before but there's no option for number of connections. It's mainly about the connection itself.

ulimit -n

then persist it in /etc/security/limits.conf

---

