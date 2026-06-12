---
title: "Bind9 Problems"
date: 2008-03-19
forum: Server Platforms
---

### Post by dantheman3212 on 2008-03-19
Hey, i need some help with bind 9. I have a DNS server running on Gutsy server, and everything works, except I cannot figure out how to get it to resolve the domain without the "www." prefix, so people can just type example.com instead of [www.example.com](www.example.com)

Do I just add another host? Or is this something else I need to do.

Thanks

-dan

---

### Post by Koybe on 2008-03-19
I think you should bind the domain to an IP, I would do this :
```
example.com.    IN     A     192.168.1.1
``` in your forward zone, assuming 192.168.1.1 is the IP of your web server

---

