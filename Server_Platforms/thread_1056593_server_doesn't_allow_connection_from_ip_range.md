---
title: "server doesn't allow connection from ip range"
date: 2009-01-31
forum: Server Platforms
---

### Post by and12345 on 2009-01-31
somehow my ubuntu server doesn't allow connection from 10.0.2.x, 10.0.3.x, and more

but allow connection from 10.0.0.x 

i installed squid, apache, bind, dhcp, mysql, ssh, and samba.

i suspect squid is the problem but i already make ACL for another subnet and allowing it on the proxy restriction.

---

### Post by HermanAB on 2009-01-31
So what is your server IP address and subnet mask?  It will only connect with IP addresses in its subnet.

Cheers,

Herman

---

### Post by and12345 on 2009-02-05
my server ip 10.0.0.2 and subnet 255.0.0.0, before i reinstall my server my server can connect and client from another ip range like 10.0.2.1; 10.0.3.1, and more can connect and ping each other...

---

### Post by netztier on 2009-02-05
> **and12345 said:**
> my server ip 10.0.0.2 and subnet 255.0.0.0, before i reinstall my server my server can connect and client from another ip range like 10.0.2.1; 10.0.3.1, and more can connect and ping each other...

What are the other systems' subnet masks? 
Are there any routers or (default) gateways involved?

regards

Marc

---

### Post by and12345 on 2009-02-06
the server act as gateway and the  other clients that can't connect to my server ip is 10.0.2.1,10.0.3.1,10.0.4.1. the subnet mask is same with server which is 255.0.0.0

---

### Post by R.Bucky on 2009-02-07
the server on my network does the same thing. I use several different CMS's and only some of them show up using the internal ip's. for instance, my Concrete5 CMS will not show itself within the network unless I go through my proxy server. Wordpress only shows text, no css or images. otherwise, phpmyadmin, webmin, Jibberbook, and Glype all show up fine. 

it sounds like we both have a similar problem...

---

### Post by cariboo on 2009-02-07
I don't suppose you have your configuration files from before you reinstalled backed up somewhere?

After a server is setup, I always backup the configuration files, as you never know when you are going to need them.

Jim

---

### Post by netztier on 2009-02-09
> **and12345 said:**
> the server act as gateway and the  other clients that can't connect to my server ip is 10.0.2.1,10.0.3.1,10.0.4.1. the subnet mask is same with server which is 255.0.0.0

Sounds like a valid setup to me.
[SIZE="1"]Although personally, I would never setup a single broadcast domain (a "subnet") with a 255.0.0.0 mask. But that of course depends on your network scenario.
[/SIZE]

Check if the server can ping all machines, and have a look at it's routing table (netstat -nr) if everything is properly set up.

Then also check squid's config to see if incoming requests are allowed from the entire 10.0.0.0/8 network.

Don't forget the occasional look at /etc/hosts.deny or /etc/hosts.allow if something is listed in there.


regards

Marc

---

