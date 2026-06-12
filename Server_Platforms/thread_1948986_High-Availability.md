---
title: "High-Availability"
date: 2012-03-29
forum: Server Platforms
---

### Post by pamiller3 on 2012-03-29
Hey All,

I am working on making a set of 2 webservers both installed with wordpress that access a mutual mysql server.  I am working on building another ubuntu server to be the load balancing point, all 4 servers are 10.4.4 and have webmin installed as well. Problem is I am afraid that I am over my head.  I am not sure where and how to install the cluster and heartbeat programs.

I apologize for just an open question, but I have searched and searched and all documentation is either too old or too vague.

Any help would be appreciated.

---

### Post by a2j on 2012-03-29
keep in mind, high availability and load balancing are not quite the same. I think first one is easier to get working. I'm also interested in load balancing of apache servers. More like live synchronization of two/multiple servers part.

pound is very easy to use for load balancing. I use it.

---

### Post by pamiller3 on 2012-03-29
Yes I suppose I worded that wrong.  I have no need for load balancing as I don't get hardly any traffic, I need HA and, like you said, live sync between the 2 webservers.

---

### Post by a2j on 2012-03-29
yeah, just for HA, I'd look into rsync type of scenario. I'm looking for a true load balance. So, if somebody can point me in the right direction, that would be great. Thanks.

---

### Post by pamiller3 on 2012-03-29
Alright does anyone have an advice on how to do a live sync and HA amongst them?

---

### Post by Cheesemill on 2012-03-30
Linode do some great guides:
[http://library.linode.com/linux-ha](http://library.linode.com/linux-ha)

---

