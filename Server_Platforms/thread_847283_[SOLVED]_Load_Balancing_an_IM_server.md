---
title: "[SOLVED] Load Balancing an IM server"
date: 2008-07-02
forum: Server Platforms
---

### Post by abuthemagician on 2008-07-02
We are using Ubuntu 8.04 and the latest version of Openfire to provide IM to our users. What we would like to do is have a server at each branch that is a mirror of the one that is currently running, and if one goes down, everyone can still chat. Openfire has an Enterprise plugin for this, but their enterprise features are NLA.

So does anyone think its possible to load balance the servers, and have messages still go to the right people regardless of the server they are on? 

Also, we are using the AD integration as well as a MYSQL server for messaging and archiving.

---

### Post by windependence on 2008-07-02
The correct way to do this would be to have two servers where they replicate the MySQL to each other and also are clustered so that if one fails, the other one takes over. In front of those, you would have two load balancers, one primary and one backup, also clustered. The load balancers would distribute the load amongst the backend web servers. You only need to do this at one location, it's not necessary to have a server at each place and in fact would probably be much harder to implement.

-Tim

---

### Post by abuthemagician on 2008-07-02
the separate servers were for in case one of our buildings is under water or burns down. Right now we have the one server in our office, but if that office is gone... you get the idea... 

What about mirroring the server to a different one at another branch, and if we lose this one, just have everyone change their server name, or have a special DNS entry that we can change the IP of?

---

### Post by windependence on 2008-07-02
Sure, you can easily do this with rsync. You would have o run a cron job every so often that would sync up the servers.

-Tim

---

### Post by abuthemagician on 2008-07-02
Awesome. I will have to do some reading then :)

---

### Post by gurukini on 2012-05-22
> **abuthemagician said:**
> Awesome. I will have to do some reading then :)
Hi, 

Please let me know if you have achieved in setting up a load balancer in front of XMPP cluster to server many users.

 I am trying to achieve the same but I am stuck in configuring the load balancer tool.
below is my set up:
1) Two openfire (3_7_1) servers in cluster sharing one centralised MYQSL. 
2) Oracle coherence framework and openfire clustering plug-in is used to establish openfire cluster.
3) Trying to use HAProxy as load balancer ( I have configured XMPP servers in HAProxy config file)
4) Smack client API to connect server.

please let me know smack can talk to load balancer and load balancer can forward the request to XMPP servers.

Quick repose very much appreciated.

Regards,
Guru

---

### Post by gurukini on 2012-05-22
> **windependence said:**
> The correct way to do this would be to have two servers where they replicate the MySQL to each other and also are clustered so that if one fails, the other one takes over. In front of those, you would have two load balancers, one primary and one backup, also clustered. The load balancers would distribute the load amongst the backend web servers. You only need to do this at one location, it's not necessary to have a server at each place and in fact would probably be much harder to implement.

-Tim
Hi Tim,

 I am trying to achieve the same but I am stuck in configuring the load balancer tool.
below is my set up:
1) Two openfire (3_7_1) servers in cluster sharing one centralised MYQSL. 
2) Oracle coherence framework and openfire clustering plug-in is used to establish openfire cluster.
3) Trying to use HAProxy as load balancer ( I have configured XMPP servers in HAProxy config file)
4) Smack client API to connect server.

please let me know smack can talk to load balancer and load balancer can forward the request to XMPP servers.

Quick repose very much appreciated.

Regards,
Guru

---

