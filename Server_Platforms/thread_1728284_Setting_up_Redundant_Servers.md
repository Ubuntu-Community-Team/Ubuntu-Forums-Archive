---
title: "Setting up Redundant Servers"
date: 2011-04-13
forum: Server Platforms
---

### Post by kerryhall on 2011-04-13
I have two physical machines running Ubuntu and apache. I want one to mirror the other (with a manual sync command). I want either 

*Load balancing
or
*One to take over if the other fails (hardware failure) or is rebooting

depending on whichever is easier to implement. 

My biggest question is that I have port 80 forwarded to my current single server, but once I add a second server how do I set up port forwarding? 

Any good tutorials on this anywhere? It seems like a simple enough task but I can't seem to find information on this.

I have searched on here a bit but could only find info about virtual servers, and I am not interested in that. 

Thanks!!

---

### Post by spynappels on 2011-04-13
Googling "Apache Clustering Ubuntu" gives this link amongst others:

[http://www.reviewlinux.com/?m=show&id=10528](http://www.reviewlinux.com/?m=show&id=10528)

Does that help?

---

### Post by BkkBonanza on 2011-04-13
It's fairly easy to setup mirror'd servers for static data. The harder part comes when you need to handle database edits/updates. 

Typically you would use replication to keep a slave updated continuously from a master. To do this properly you need to ensure that your application is well behaved in controlling database updates so they get sent to the master and not the slave. One approach that works is to route GET requests to either machine, round robbin, but POST requests only to the master (where they update data).

If you only have one public IP available you would need to run a reverse proxy or load balancer to split the load accordingly to the two servers. Nginx is often used as a reverse proxy and can make decisions based on request type or other factors (and btw also works better than apache as a very capable fast webserver too).

If you have two public IPs then you can use DNS round robin to do simple load balancing. This is very easy to setup. You just add two A records and most DNS servers will hand them out round robin. But you still need to use rewrites or a proxy to make sure that data updates get forwarded to the master.

Application logic is also important to consider because if one user is not always routed to the same server, or if a server goes down, then you need to make sure that sessions are handled in a shared way. For example, there is support for mysql sessions in PHP that I've used to handle this.

There needs to be some monitoring and failover logic as well. This can be simple scripts or more fancy heart beat packages. It needs to determine reliably when a server is down and alter settings such that the other one can take over either for reads or updates if the master fails. Some DNS services offer monitoring and failover at the DNS end.

Anyway, thats just a rough overview.

(For your question about port forwarding - it used to be that iptables supported multiple DNAT rules and could round robin on them, but I'm not sure that is still there. Failing that you would forward to one server that has a front end (like nginx or a load balancer) that decides which of any available servers will get the request and forwards it there.)

---

### Post by kerryhall on 2011-04-19
> **BkkBonanza said:**
> It's fairly easy to setup mirror'd servers for static data. The harder part comes when you need to handle database edits/updates. 

Typically you would use replication to keep a slave updated continuously from a master. To do this properly you need to ensure that your application is well behaved in controlling database updates so they get sent to the master and not the slave. One approach that works is to route GET requests to either machine, round robbin, but POST requests only to the master (where they update data).

If you only have one public IP available you would need to run a reverse proxy or load balancer to split the load accordingly to the two servers. Nginx is often used as a reverse proxy and can make decisions based on request type or other factors (and btw also works better than apache as a very capable fast webserver too).

If you have two public IPs then you can use DNS round robin to do simple load balancing. This is very easy to setup. You just add two A records and most DNS servers will hand them out round robin. But you still need to use rewrites or a proxy to make sure that data updates get forwarded to the master.

Application logic is also important to consider because if one user is not always routed to the same server, or if a server goes down, then you need to make sure that sessions are handled in a shared way. For example, there is support for mysql sessions in PHP that I've used to handle this.

There needs to be some monitoring and failover logic as well. This can be simple scripts or more fancy heart beat packages. It needs to determine reliably when a server is down and alter settings such that the other one can take over either for reads or updates if the master fails. Some DNS services offer monitoring and failover at the DNS end.

Anyway, thats just a rough overview.

(For your question about port forwarding - it used to be that iptables supported multiple DNAT rules and could round robin on them, but I'm not sure that is still there. Failing that you would forward to one server that has a front end (like nginx or a load balancer) that decides which of any available servers will get the request and forwards it there.)

Thanks for the awesome help! So I have two machines, master and slave, slave machine mirroring the master. Master machine is a quite fast server, the slave machine is a junk box machine put together basically to maintain uptime while the master is rebooting or down for maintenance. 

I can probably figure out how to keep the slave mirroring the master, but I just need help with routing issues. Right now I have port 80 forwarding to my web server (master). My first thought was to have something that pings the master, and if it is down, change the port forwarding ip address to the slave. However, the router that I have is a crappy comca$t modem/router thing, but I do have another router with DDWRT installed on it (Or I could put openwrt on it) and run scripts that way. 

Am I correct in assuming that both machines will have to be behind a router that supports some sort of user scripting? 

Thanks again!

---

### Post by kerryhall on 2011-04-19
> **spynappels said:**
> Googling "Apache Clustering Ubuntu" gives this link amongst others:

[http://www.reviewlinux.com/?m=show&id=10528](http://www.reviewlinux.com/?m=show&id=10528)

Does that help?

Yeah that looks great too, thanks, I'm gonna read that!

---

### Post by falko on 2011-04-19
You could sync your files with rsync:
[http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

... and for MySQL you can set up replication:
[http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-ubuntu-9.10](http://www.howtoforge.com/how-to-set-up-mysql-database-replication-with-ssl-encryption-on-ubuntu-9.10)

In front of your web servers you can set up a load balancer:

[http://www.howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny](http://www.howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny)

---

