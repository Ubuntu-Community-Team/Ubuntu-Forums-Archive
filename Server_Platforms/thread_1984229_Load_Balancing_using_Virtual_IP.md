---
title: "Load Balancing using Virtual IP?"
date: 2012-05-21
forum: Server Platforms
---

### Post by ridha121 on 2012-05-21
Hi guys

I have a quick question.

I have 2 Ubuntu servers running SQUID for me. I wish to load balance these two servers they are virtual machines. 

Can the use of virtual IP achieve this?

so I have my users pointing to 192.168.1.1 as the virtual IP for the two proxy servers running on physical IP of 192.168.1.2 and 192.168.1.3..

Your Help would be much appreciated

---

### Post by darkod on 2012-05-21
Yes, you should be able to use private IP for that. But I can't help you with the exact configuration for load balancing.

I know about fail-over when the backup kicks in if the primary fails, but not load balancing where they share the connections at the same time. Still haven't played with that. :)

---

### Post by ridha121 on 2012-05-21
Hi there 

Thank you for your Reply


Sorry I think I did mean failover, how would that be implemented through a VIP? 


Much appreciated

---

### Post by darkod on 2012-05-21
I used this guide which is part of a different project, but it worked perfectly:
[http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html](http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html)

Basically, install heartbeat, and create on both machines the three config files from that tutorial. You can ignore everything else.

In that tutorial the config files have configuration for two interfaces (eth0 and eth1), not sure if you want to do the same.

This guide is the shortest and fastest way to create failover that I have found. Simply install one package, create three files and it works!!! :)

When I have more time I'll have to search for something similar about true load balancing.

---

### Post by koenn on 2012-05-21
> **darkod said:**
> But I can't help you with the exact configuration for load balancing.

It's usually done with a load balancer appliance, a special sort of router that has the address that hosts will be talking to, and routes the requests to one of 2 or more identical machines behind it.

Assuming that such a device will be running an OS and routing software and some load balancing logic, I guess you can do something similar with a linux box and I don't doubt people have written the software for it already, but I've never looked into it.  
Its usually combined with a fail-over mechaniss, as you don't want the load balancer to send requests to a down server

For quick and dirty load balancing, you'd just do round robin DNS, where your DNS would return the addresses to two or more identical machines for one specific hostname.

---

### Post by darkod on 2012-05-21
Yeah, of course you can use standalone device.

I was thinking about configuring your servers for load balancing.

I wouldn't count too much on DNS load balancing. Tried it few months ago, not impressed. In fact, for most websites it didn't work.

If the first option was down, strangely enough it had problems looking for the second option. It should work fast and easy, but in this case it didn't. Still not sure why.

---

