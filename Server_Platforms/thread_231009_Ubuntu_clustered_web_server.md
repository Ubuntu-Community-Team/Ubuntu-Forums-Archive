---
title: "Ubuntu clustered web server"
date: 2006-08-06
forum: Server Platforms
---

### Post by erat123 on 2006-08-06
Hi,
I'm in the process of building a web server using ubuntu server.  I've built a LAMP server with no problems, but I would like more than that.  My question is: does anyone know how to build a clustered LAMP server with ubuntu?  I would like to use something like linux-vs ([www.linux-vs.org)](www.linux-vs.org)).  I would like to use direct routing in the cluster.  I'm also confused about setting up these computers to use MySQL.  I know there are ways to cluster a MySQL database.

Basically, what I'm going for:
1.  The ability to down a server or two and have the site stay up.
2.  Allow many people to access information on the server without it slowing down too much (this includes MySQL data)

Thanks for any help,
Eric

---

### Post by Glut on 2006-08-08
A 'simple' solution would be to provide a round-robin dns, where multiple machines host the website and you have a single server for the MySQL backend. You could also host a MySQL cluster, where each webserver is a member of the cluster.
That would provide you with failover and a crude method of load balancing. 

A more advanced solution would be to use 'real' load balancers: [http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster](http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster)

There is also mod_backhand for apache 1.3

---

