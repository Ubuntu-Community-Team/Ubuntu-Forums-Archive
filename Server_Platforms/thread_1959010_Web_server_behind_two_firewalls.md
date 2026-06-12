---
title: "Web server behind two firewalls"
date: 2012-04-15
forum: Server Platforms
---

### Post by darkod on 2012-04-15
Hi all.

This is sort of a windows/linux question, and I wasn't sure whether to post in Servers or Networking either.

I am trying to set up a Windows Server 2008 R2 web server behind two Ubuntu Server 10.04 firewalls/routers.

The idea of having two of them, is for redundancy. Right now load balancing is not under consideration.

Lets say for example, the IP are like this:
Firewall1, internal interface 10.0.0.11
Firewall2, internal interface 10.0.0.12
Web server, LAN IP 10.0.0.22, gateway 10.0.0.11, in advanced options second gateway 10.0.0.12

To cut a long story short, it all works as planned, only it seems the server is listening on only one gateway at a time. Is this some kind of general networking limitation, or windows networking limitation?

Would it help if one subnet is 10.0.0.x and the other 10.0.1.x for example?

Both firewalls are online but for example with Remote Desktop or FTP you can only get in from one at a time.

Is there anything that can be done for both to be "active" at the same time, or this kind of setup is impossible and I should just drop one machine and have a single gateway?

Thanks a lot for any ideas. I have been googling around but haven't found anything specific to my case.

---

### Post by Jonathan L on 2012-04-15
Hi darkod

Interesting post.

There are a number of issues to iron out to get it to work how you want it.

My first thoughts were that this can be rather difficult to make work at the IP layer, and you might be better at ethernet (HSRP, for example) or HTTP (inbound proxies).

Can you tell us what the top side looks like?  That is, the outside portion of f1, f2 and the links to the internet?

Kind regards,
Jonathan.

---

### Post by Dangertux on 2012-04-15
Why not just float the public IP address between each firewall machine in an HA configuration. That would give you the redundancy you need.

Look at heartbeat or pacemaker for that.

Hope this helps.

---

### Post by SeijiSensei on 2012-04-15
It sounds like the firewalls have only one network interface card.  Firewalling and routing is always much easier with two interfaces, one pointing upstream and one pointing downstream.  Having all the machines in the same address space is also problematic.

How are you handling routing in this setup?  What machine do the clients have defined as their default gateway?  I'd imagine the other machine sits idle all the time, no?

---

### Post by darkod on 2012-04-15
Both firewalls have their own external interface with different public IP, and same gateway since they are at the same hosting provider.

The routing through them works fine, I have managed (bit by bit) to set the firewall rules, etc.

With only one machine I guess all will be fine.

My only issue (or improvement rather said) right now, is whether both of them can serve at the same time instead of one at a time.

On the inside there will only be the web server and a SQL server. I am still not sure if any traffic will need to be directed at the SQL because mostly the websites will talk to the data, so that would be only internal traffic between the web server and DB server.

I was wondering if anything can be done without adding more hardware, or complicated configuration changes.

For example, what if I remove the second gateway from the web server. If that confuses things, I could do that. I believe this might be the issue that is making the webserver listen to only one firewall at a time.

Or in that case there will be traffic going only through firewall1 making firewall2 just sitting there?

---

### Post by SeijiSensei on 2012-04-15
If you can control the routing table on the Windows machine, you could assign different "[metrics]("http://en.wikipedia.org/wiki/Metrics_%28networking%29")" to the two routers.  The one with the lowest metric will be used unless it goes offline.

I have no idea how to write routing commands in Windows, though.  In Linux it would be something like:

```

sudo ip route add default via 10.0.0.1 metric 1
sudo ip route add default via 10.0.0.2 metric 10

```

---

### Post by darkod on 2012-04-15
> **SeijiSensei said:**
> If you can control the routing table on the Windows machine, you could assign different "[metrics]("http://en.wikipedia.org/wiki/Metrics_%28networking%29")" to the two routers.  The one with the lowest metric will be used unless it goes offline.

I have no idea how to write routing commands in Windows, though.  In Linux it would be something like:

```

sudo ip route add default via 10.0.0.1 metric 1
sudo ip route add default via 10.0.0.2 metric 10

```

But that's the thing. I don't know how to explain it, and not sure if it is windows issue or networking issue, it seems to be listening only to the gateway which is used at that moment.

The metric settings are Auto right now, so I guess it uses them in order that they were configured. If something happens (overcharge, outside attack, etc) it can continue working with the other gateway, we have seen that happen.

But if firewall2 is the current gateway for example, if I do:
telnet <public ip 2> 80

the service is listening. But:
telnet <public ip 1> 80

doesn't work.
Both firewalls forward the same ports to the same private ip (in the example 10.0.0.22) which is the private IP of the server in the internal LAN.
So when firewall1 receives a request on 80 and it has port forward configured, why doesn't the web server accept it?
The same happens with the RDP port, FTP port, etc.
It's like only one machine is active, the current gateway, and the other is in stand-by, even though it is online of course, I have ping, SSH, etc.

The idea was to have a fail safe option if the firewall goes down until you get it running again, but obviously my tests were not thorough enough. Later by reading, I have seen it mentioned here and there that if you use port forwarding like this with the same port numbers from two different gateways, the server will listen to only one at a time. But nothing specific, or with more information. And whether there is a fix. :)

---

### Post by darkod on 2012-04-15
> **Dangertux said:**
> Why not just float the public IP address between each firewall machine in an HA configuration. That would give you the redundancy you need.

Look at heartbeat or pacemaker for that.

Hope this helps.

Thanks, this looks very interesting but it seems overkill for my purpose.

I will continue reading them anyway, to upgrade my knowledge.

---

### Post by darkod on 2012-04-16
For anyone in a similar situation to mine, I found this that looks impressive. Haven't had time to play with it though.
[http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html](http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html)

---

