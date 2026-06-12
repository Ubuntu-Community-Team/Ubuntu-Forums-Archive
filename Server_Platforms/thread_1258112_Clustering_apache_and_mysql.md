---
title: "Clustering apache and mysql?"
date: 2009-09-04
forum: Server Platforms
---

### Post by grantemsley on 2009-09-04
I have a website that is getting past the limits of what one server will do, and I've been looking at linuxvirtualserver.org's guides.

I think what I want is 2 load balancing machines, 2 web servers and 2 database servers.

I'm pretty sure I've figured out setting up the load balancing machines from the guides on that site.  However, I'm a bit stuck with apache and mysql.

With apache, how do I make them all see the same files?  Do I need a SAN?  I can probably get one, but have no idea how to configure it.

With mysql, how do I get their databases to sync?

Any guides or pointers would be greatly appreciated.

---

### Post by gombadi on 2009-09-04
> 
I have a website that is getting past the limits of what one server will do


Is this single server currently doing web and database? If so then can you move the database function to a different machine so you have separate web and database machines?

I am currently consolidating some servers from different locations into one location. We are using two base web servers running OpenVZ to provide multiple environments where all the environments use a common nfs server which has the web site code.
We are also using two base MySQL servers with OpenVZ to provide multiple databases to the web servers in a master-master type setup.
If only I could convince the developers to update the code so we don't need to run MySQL4 and 5 and PHP4 and 5 then my life would be easier :-)

I believe in the KISS principle - Don't add extra servers unless you need them. First I would separate the web and database functions to different machines. Then as things grow see which is loaded the most. If web setup DNS round robin and install extra web servers all using an nfs mount for a common view of the code. If the database servers are the bottleneck then have a look at MySQL replication and splitting database reads from writes and maybe even master-master configuration.

---

### Post by grantemsley on 2009-09-04
Database and webserver are already on separate servers.

At the moment, I could probably get away with using NFS to share the web files to a second web server, mysql replication, and round robin dns.  However, $BOSS believes that the site may quickly grow into needing many more servers, and wants a solution that will let us quickly and efficiently scale up the site.  My understanding is that those solutions won't scale well into dozens or hundreds of servers.

---

