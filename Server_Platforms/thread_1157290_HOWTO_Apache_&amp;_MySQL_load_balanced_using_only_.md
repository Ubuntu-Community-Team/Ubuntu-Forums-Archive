---
title: "HOWTO: Apache &amp; MySQL load balanced using only software"
date: 2009-05-12
forum: Server Platforms
---

### Post by flyjedi on 2009-05-12
It had been challenging me for a while how to do it, so I thought I'd share now I've got it all working:

The Apache, HAProxy and Heartbeat bit:
[http://bluhaloit.wordpress.com/2009/04/29/how-to-quickly-setup-a-load-balanced-high-availability-apache-cluster/](http://bluhaloit.wordpress.com/2009/04/29/how-to-quickly-setup-a-load-balanced-high-availability-apache-cluster/)

The MySQL and mysql-proxy bit:
[http://bluhaloit.wordpress.com/2009/05/11/simple-mysql-replication-cluster-with-load-balancer-on-the-slaves/](http://bluhaloit.wordpress.com/2009/05/11/simple-mysql-replication-cluster-with-load-balancer-on-the-slaves/)

End result is a replicated MySQL cluster, Apache cluster, and high availability load balancers in front of each, all with software.

---

### Post by fujikofujio on 2009-06-03
Very nice post thanks, I'm sure this will be useful to me one day, I'm actually looking for mysql replication.

---

