---
title: "Load Balancer Setup"
date: 2012-10-16
forum: Server Platforms
---

### Post by monarck on 2012-10-16
I'm currently recreating my company's server setup and I'm looking to make it as stable and reliable as possible (read I hate customers complaining).

What I'd like to do is distribute different services (web, mail, database, DNS, etc.) among different physical machines.  Each of these machines will be linked to an identical machine through DRDB for data syncing and Heartbeat/Pacemaker for failover.  Something like this:

web 1    <--> web 2
mail_a 1 <--> mail_a 2
mail_b 1 <--> mail_b 2
mail_c 1 <--> mail_c 2

In front of all of these I would really like to set up an Ubuntu+LVS load balancer pair (again linked with Heartbeat/Pacemaker for failover) to further reduce any chance of downtime.  

My main question is how do people usually connect a self-made load balancer to so many machines?  Also, what are the usual recommended specs for a load balancer?

Thanks ):P

---

### Post by darkod on 2012-10-16
What do you mean, how do you connect?

Usually the pair of load balancing machines will have a third common IP on both the external and internal interfaces.

So, on your server you configure the gateway to be the internal common IP of the load balancing front-end.

If the servers themselves are organized in pairs for load balancing (or only failover), also they will have common IP on their interface (I assume you will need only one interface for them).

Something like:

x.x.x.x (public IP of your router)
Internet Router
192.168.1.1 private IP of router

192.168.1.2 common IP
load balancer 1, 192.168.1.100, 10.10.0.100
load balancer 2, 192.168.1.101, 10.10.0.101
10.10.0.1 common IP

10.10.0.10 common IP
web 1, 10.10.0.200
web 2, 10.10.0.201

That would be the flow of traffic. On the router you forward the necessary services (ports) to 192.168.1.2 which are accepted by the load balancing pair on their common IP, so it doesn't matter if one server is down.

Then the load balancers forward the traffic to 10.10.0.10, the common IP for the web, again so that it doesn't matter if one server is down.

For the exit router, the gateway for the web servers would be 10.10.0.1, the common IP, so that if any of the load balancers are offline the other one will still provide an exit route.

Etc, etc...

---

### Post by monarck on 2012-10-16
Alright, thanks for clearing a bit of that up for me.  I was under the impression that every machine that the load balancer manages has to be connected directly to it, like a router, requiring a NIC for each machine.  I originally thought this from looking at load balancer appliance images on Google.  So, all I have to do is put them on the same LAN, and then set the web/mail servers to route threw it as a gateway?

I also threw a quick diagram together to better explain what I'm doing: [http://imageshack.us/photo/my-images/338/serversetup.jpg](http://imageshack.us/photo/my-images/338/serversetup.jpg)

Also, what is the most common way of setting up a balancer?  Is it with something like Ubuntu+HAProxy or would pfSense be a better fit?  The balancer needs to be able to manage HTTP, HTTPS, FTP, POP, SMTP, and DNS requests.

Thanks again!

EDIT:
Also, as I'm going to use DRBD for data syncing, I was wanting to make sure that I can still go with balance loading for both servers.  For example, if both web servers are fine, will the server set up to be the secondary with DRBD, can it still process requests or is the hard drive asleep?  I read somewhere that with DRBD, only one server can be active at once.  When the primary server has a problem, the secondary will become active, stop the primary, and take all requests.

---

### Post by darkod on 2012-10-17
Correct, just put them on the same LAN and make the load balancers common IP as gateway for the other servers.

Unfortunately, I don't have any experience with load balancing. For my needs I did one quick fail over system, but that was only fail over with heartbeat and very easy to set up, with the correct info.

I used this link:
[http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html](http://www.fwbuilder.org/4.0/docs/users_guide/heartbeat_cluster.html)

The tutorial is for something called Firewall Builder, but on this page in the middle it has a very short and precise info about the heartbeat config files. It took 5mins to set them up, and worked wonderfully right away.

But I still haven't gotten around to load balancing with pacemaker or similar. Or DRDB.

---

### Post by monarck on 2012-10-18
Well, I've decided to go without load balancers and just go with a simple DRBD+Heartbeat/Pacemaker failover solution since we really don't have too many visitors.  I thought it would be a good idea to go ahead and set one up while I was changing things around, but I've read quite a few cases where people can't get primary/primary DRBD to work quite right.  I guess I'll wait a little while until I either learn a bit more about the subject or the technology changes.

Thanks for the help though, that link might come in handy :)

---

