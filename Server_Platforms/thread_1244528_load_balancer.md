---
title: "load balancer"
date: 2009-08-19
forum: Server Platforms
---

### Post by zeek333 on 2009-08-19
hi,

i'm lookin for good (free) and easy to set up load balancer on ubuntu. I'll run 2-3 LAMP servers. 

thanks.

---

### Post by HermanAB on 2009-08-19
Howdy,

BIND will do round robin DNS.  So just set the LAMP servers up like normal and then configure BIND as your DNS to resolve their addresses in a circle.

---

### Post by zeek333 on 2009-08-19
ok thanks i'll look about it, but does it somehow sync. data on LAMP as well or for that i'll need something else.

---

### Post by zeek333 on 2009-08-20
[B]DNS load balancing implementation (Multiple A Records)

[/B]```

[COLOR=Black]www.foodmalaysia.net.  60  IN  A 192.168.1.1
[/COLOR] [COLOR=Black]www.foodmalaysia.net.  60  IN  A [/COLOR][COLOR=Black]192.168.1[/COLOR][COLOR=Black].2
[/COLOR] [COLOR=Black]www.foodmalaysia.net.  60  IN  A [/COLOR][COLOR=Black]192.168.1[/COLOR][COLOR=Black].3
[/COLOR] [COLOR=Black]www.foodmalaysia.net.  60  IN  A [/COLOR][COLOR=Black]192.168.1[/COLOR][COLOR=Black].4[/COLOR]

```

Considering the functionality, the round robin DNS is not a load balancing mechanism but a load distribution option.


is it any other suggestion about good load balancer ?

---

### Post by HermanAB on 2009-08-20
To keep the machines in the same, use rsync over ssh.

One reason Round Robin DNS is popular, is it's simplicity.  A true load balancer is a much more complicated idea.  Have a look in the Advanced Routing Howto in tldp.org, but it generally isn't worth the trouble for web sites.

---

### Post by tubezninja on 2009-08-20
> **HermanAB said:**
> To keep the machines in the same, use rsync over ssh.

That probably won't work so well for MySQL databases in a LAMP environment, as mentioned by the OP.  Your best bet there, actually, would be to have one server act as the dedicated MySQL server and your remaining apache servers connect to it.  That way you're not messing with multiple databases, the MySQL server only handles MySQL, and the web servers worry about just Apache and PHP.  The web servers can then be rsynced periodically so that your PHP and static content will be updated across all web servers.

If you *really* start scaling traffic like crazy, then you would likely [cluster multiple MySQL servers]("http://http://www.howtoforge.com/loadbalanced_mysql_cluster_debian") to load balance the transactional portion of the delivery content, and then have a separate fleet of web servers in round-robin that all interact with that MySQL cluster.

---

### Post by zeek333 on 2009-08-20
I will not have that massive data bases, it just for security reason 

do u think is that would be enought if i'll use for ex.:

round robin DNS1 and DNS2 then 2-3 web servers and 1 sql server?


Is that round robin is included in BIND9 or i need some additional packages?

---

### Post by mbaas on 2009-08-21
There's [this]("http://www.howtoforge.com/high_availability_loadbalanced_apache_cluster") nice howto on Howtoforge as well. Might be interesting to.

---

### Post by tubezninja on 2009-08-21
> **zeek333 said:**
> I will not have that massive data bases, it just for security reason 

do u think is that would be enought if i'll use for ex.:

round robin DNS1 and DNS2 then 2-3 web servers and 1 sql server?


Sounds like that should work fine.

> 
Is that round robin is included in BIND9 or i need some additional packages?


Round robin is a function built into BIND9.  [Here's an example of how to set it up]("http://www.zytrax.com/books/dns/ch9/rr.html").

---

### Post by zeek333 on 2009-08-21
thnks **scaredpoet** I'll try with RRDNS if not will look for other solutions


btw on **mbaas** given link I've got problems I couldn't  start  heartbeat

---

### Post by zeek333 on 2009-08-26
OK,

 [**here**]("http://www.howtoforge.com/setting-up-a-high-availability-load-balancer-with-haproxy-heartbeat-on-debian-lenny") is a good manual for load balancing works for me on ubuntu 8.04 TLS

---

