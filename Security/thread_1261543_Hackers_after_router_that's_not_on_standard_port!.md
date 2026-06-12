---
title: "Hackers after router that's not on standard port!"
date: 2009-09-08
forum: Security
---

### Post by Lori700698 on 2009-09-08
How can a hacker try to log into something that's not even there?  I keep getting an alarm that they are trying to log into my linksys router on port 8080, I don't have my router opened to a port anywhere.  Funambol is on 8080 and they don't appear to be opening the actual admin page to attempt a log in there.  
```

Src IP: 140.128.8.123
First time this IDS alert is generated.
[**] [1:1861:12] WEB-MISC Linksys router default username and password login attempt [**][Classification: Attempt to login by a default username and password] [Priority: 2] 
```

And how do I stop this jerk until I get time to set up my IPTable (planning on doing that this weekend!)

```
Src IP: 174.36.237.104
Proxy Authentication Required: User is not authorized to use proxy.
1252440710.638 0 174.36.237.104 TCP_DENIED/407 1857 GET http://www.yahoo.com/ - NONE/- text/html

```

This one is getting on my nerves, they are trying a few time an hour.  Could I put a deny:All: 174.36.237.104 in the host file, would it stop them until I get my IPtable running?

Thanks Lori!

---

### Post by __p1n__ on 2009-09-08
Port 8080 is the default port for remote administration on a number of linksys consumer network appliances.  You might consider logging on to the router and ensuring that remote administration is disabled.

edit: getting itables working for this application is pretty straight forward, no need to wait:

% sudo iptables -I INPUT -s 174.36.237.104 -j DROP
% sudo iptables -L

edit-edit: even better, block the traffic in pf in your NetBSD dom0 instance and don't bother with iptables in your domu ubuntu instance:

block in quick from 174.36.237.104

---

### Post by Lori700698 on 2009-09-09
I put it in IPtable to drop it, NeTBSD is slightly over my head tonight, but I will look at that this weekend.  I promise you my router is not open, heck I don't even have a linksys.

 I'm just slightly confused how you could try to log into something that isn't even there....new eye opener everyday! Man I was getting way more sleep when I was blind to the persistence of the hackers!

Thanks!!
Lori

---

