---
title: "apt-get behind MS ISA server"
date: 2005-06-15
forum: Repositories &amp; Backports
---

### Post by blakey on 2005-06-15
Whenever I try apt-get I get an error along the lines
 
"failed to fetch [http://archive](http://archive)...   could not connect to 10.1.1.2:3128 connection refused"

10.1.1.2 is the MS ISA server 2004 firewall. I have set a firewall rule for the Ubuntu box  that says basically 'let everything through'  but it don't work....

---

### Post by giamax on 2005-10-19
Me too. I've set up a rule to let everything through ISA 2004 from Ubuntu box, but it still requires to authorize HTTP traffic. In Firefox I just configure proxy to point to ISA server (and it asks for user+pass when loading pages). But how could we configure apt-get or Synaptic?

P.S. I've configured proxy at System -> Parameters -> Proxy at GNOME menu, but it still does not work :(:confused:

---

### Post by giamax on 2005-10-20
Yes, there IS a problem with getting packages through HTTP protocol. But there is NO problem with FTP :) . Yes, pretty simple :D  Just change http:// to ftp:// when adding repositories and things will work!

Best regards,
Giamax.

---

### Post by ngms27 on 2005-10-20
This is maybe due to having Authentication on for HTTP traffic.
You can switch this off in ISA 2004.

Alternatively it may be the Statefull packet inspection for HTTP sees that the rendered traffic isn't a conventional web page. Again this can be turned off.

JonnyT

---

