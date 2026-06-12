---
title: "Any proxy configuration (anonymous browsing) for 50kB/s internet"
date: 2009-10-23
forum: Security
---

### Post by emigrant on 2009-10-23
hi,
im looking for a good way of anonymous browsing for my 50kB/s internet without loosing little bandwidth.
excluding using proxy sites, bcz apparently they make me unable to do formattings (WYSIWYG) and some doesn't have java script.

thank you very much

---

### Post by __p1n__ on 2009-10-23
Go park outside of starbucks and use their access point.

---

### Post by emigrant on 2009-10-23
no man, im really in need to know a solution for this.

---

### Post by __p1n__ on 2009-10-23
Find an open relay and run your http traffic through that.  Do nmap syn scans against ports 80 and 8080 on your candidate hosts to find potential open relays.

Be certain to do an os check of the target open relay; you don't want to inadvertently use a tarpit or a virtual host.

edit: make sure that you have authorization from the host owner to use their webserver in this fashion.

---

### Post by emigrant on 2009-10-23
[__p1n__]("http://ubuntuforums.org/member.php?u=908110"), thank you for your reply, but i didnt understand anything u said :(.
i would like some step to step guidance if any one have time.

thank you very much.

---

### Post by doas777 on 2009-10-23
it's always just a proxy server, no matter how you route it. if proxies are inadaquate, then you are prolly hosed. 

have you tried tor? are you sure that it won't work with what you need to do?

---

### Post by emigrant on 2009-10-23
iv tried tor with my previous fedora,
and it makes my 50kB connection dead slow :mad:

---

### Post by doas777 on 2009-10-23
> **emigrant said:**
> iv tried tor with my previous fedora,
and it makes my 50kB connection dead slow :mad:

50kB/s ( < 512kbps) is a dead slow connection regardless of whether you are using a proxy. yes proxies will always seem slower than direct connection, but they are pretty much your only option for anonymity.

---

