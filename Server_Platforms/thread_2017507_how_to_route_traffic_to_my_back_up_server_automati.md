---
title: "how to route traffic to my back up server automatically when primary is unavailable"
date: 2012-07-05
forum: Server Platforms
---

### Post by the1joker on 2012-07-05
Hi every1,
 
I have two servers installed (ubuntu 12.04), they are running DNS, Mail, FTP, SSH, Web, etc... serverices.. this all works fine. The only thing is they domains i have are registered to external nameservers.
 
They are both located at two different locations, one functioning as a primary and the secondary more as a backup.
 
Now i would like all traffic automatically rerouted to the second server when the first is unreachable, how would i accomplish this... through use of my own nameservers , if so how would i set this up, or if there are other ways please enlighten me..
 
Thanks in advance,
Tobias

---

### Post by SeijiSensei on 2012-07-05
This is a complicated task, and not one that DNS can handle alone.  You can use "[round-robin]("http://www.zytrax.com/books/dns/ch9/rr.html")" DNS entries to distribute the traffic between the servers, but for one server to back up another completely, you need to look into the "[high-availabilty]("http://www.linux-ha.org/wiki/Main_Page")" features of Linux.

---

### Post by the1joker on 2012-07-05
Awesome thanks, ill go check that out.

---

