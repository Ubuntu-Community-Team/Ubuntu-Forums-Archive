---
title: "Apache weird.  Outside connections ok: localhost ok; domain access from local not ok"
date: 2009-03-23
forum: Server Platforms
---

### Post by suffice on 2009-03-23
hello

i have kubuntu 8.10, kde 4.2 yada yada

i have set up apache many times before and got it all working nicely.

i have no router to deal with, and i use no-ip redirecting to port 8080.

i edited ports.conf to include 8080 under virtual host and then edited /sites-enables/000-default for the same.

other times this was enough to have it working from anywhere.

at the moment:

localhost works.....i can access the site from any other computer out there no prob and it all works.  but for somereason when i type in my domain on the computer that its running on it timesout.   

its this an apache problem? a no-ip problem[havnt changed anything with this]? 

hosts, hosts-allow seem to look ok.....or is it jsut the way kde set it all up..[just switched to kde from long time gnome use]

either way...anyone heard of this before?

---

### Post by netztier on 2009-03-23
> **suffice said:**
> 
either way...anyone heard of this before?

Same old question: How does name resolution work on the client systems in this case?

regards

Marc

---

### Post by windependence on 2009-03-23
> **suffice said:**
> hello

i have kubuntu 8.10, kde 4.2 yada yada

i have set up apache many times before and got it all working nicely.

i have no router to deal with, and i use no-ip redirecting to port 8080.

i edited ports.conf to include 8080 under virtual host and then edited /sites-enables/000-default for the same.

other times this was enough to have it working from anywhere.

at the moment:

localhost works.....i can access the site from any other computer out there no prob and it all works.  but for somereason when i type in my domain on the computer that its running on it timesout.   

its this an apache problem? a no-ip problem[havnt changed anything with this]? 

hosts, hosts-allow seem to look ok.....or is it jsut the way kde set it all up..[just switched to kde from long time gnome use]

either way...anyone heard of this before?

You need to put an entry in your /etc/hosts file on the server to define it's DNS name. When you are on that machine, the DNS name resolves to an outside IP, and unless you had NAT reflection on your router ( most small routers don't), it cannot reach the outside IP address from the inside.

-Tim

---

