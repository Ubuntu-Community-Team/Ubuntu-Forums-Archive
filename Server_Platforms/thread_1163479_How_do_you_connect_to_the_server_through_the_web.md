---
title: "How do you connect to the server through the web??"
date: 2009-05-18
forum: Server Platforms
---

### Post by haroman145 on 2009-05-18
I'm currently running freebsd server..planning on switching to ubuserv 2nite...just wondering..i have a server @ my house...i want my friend down the street to be able to connect @ a reasonable speed 

thanks,  Josh

---

### Post by windependence on 2009-05-18
Why are you switching away from a perfectly stable server?

Can you explain a bit more so we can figure out how to help you? 

Also, you can find some help for FreeBSD at daemonforums.com.

-Tim

---

### Post by ugm6hr on 2009-05-19
> **haroman145 said:**
> i want my friend down the street to be able to connect @ a reasonable speed 

Unless he/she is on the same LAN, you can connect via internet (i.e. at slow speed).  The speed will depend on your ISP upload limit.

Does your ISP give a fixed or dynamic IP?  If latter, try DynDNS (or similar).

Then just forward the relevant ports on your router (for whichever services you want to give access to over internet) to the server LAN IP.

He/she should then be able to connect using the IP or DynDNS url.

---

