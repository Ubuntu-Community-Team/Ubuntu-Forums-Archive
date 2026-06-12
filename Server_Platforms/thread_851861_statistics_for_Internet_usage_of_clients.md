---
title: "statistics for Internet usage of clients"
date: 2008-07-07
forum: Server Platforms
---

### Post by codetiger on 2008-07-07
Hi guys, 
I have been using Ubuntu server for the past 1 year and not new to unix platform. 

In our office we have one server and many xp clients connected to it for various purpose. We are sharing internet using the server. The server box has latest ubuntu server software running. Now, I have blocked few sites using iptable entries. Now, I want to check which client computer is accessing which website. 

I am expecting something similar to that of firestarter which shows the list of sites visited from different ips. I have installed ntop but it doesnt server the exact use. Can someone recommend any software that can help.

Thanks,
code

---

### Post by windependence on 2008-07-07
Have you ever thought of using the firewall logs? There's probably an IPtables log analyzer out there for this purpose.

-Tim

---

### Post by codetiger on 2008-07-07
If someone can tell me how firestarter reads and links which ip is requesting which site, We can manage to write a utility for showing live requests. All we need is live list of requests from which ip and the domain name requested.

---

### Post by windependence on 2008-07-07
[http://www.iptablesrocks.org/guide/analyze.php](http://www.iptablesrocks.org/guide/analyze.php)

-Tim

---

