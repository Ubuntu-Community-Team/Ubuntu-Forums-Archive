---
title: "Automatic fallback from one server to an other?"
date: 2020-11-04
forum: Server Platforms
---

### Post by Elmi77 on 2020-11-04
Hi,

I'm currently running a webpage on a dedicated server and now want to implement some as much as possible automatic fallback mechanism. That's what I have:

[LIST]
[*]Domain- and DNS-configuration at a provider P, here the domains are registered and configured to point to the IP aaa.aaa.aaa.aaa which belongs to my main server
[*]a dedicated server A (full root access) running Ubuntu 18.04 which owns the IP aaa.aaa.aaa.aaa and serves the webpage by default
[*]a backup virtual server B (also full root access) running Ubuntu 18.04 which owns an other IP (bbb.bbb.bbb.bbb) and is intended to work as fallback system
[/LIST]

What I want to have:
[LIST]
[*]automatic synchronisation of the webpage contents from aaa.aaa.aaa.aaa to bbb.bbb.bbb.bbb (not a big deal, can be done easily via rsync/cron jobs/automated download and unpacking of .tar.bz-archives/whatever)
[*]automatic synchronisation of the server configuration (this is somewhat more complicated: in /etc/apache2/apache.conf the IP aaa.aaa.aaa.aaa is configured for the different virtual hosts - but that will not work on server bbb.bbb.bbb.bbb - so is there a possibility to configure Apache2 in a more generic way and without fixed IP's?)
[*]automatic switching to server B as soon as server A is down or not accessible for any reason (this is the major question: how can this be done when the DNS are configured at provider P, how can one switch the configuration of my domains to no longer point to aaa.aaa.aaa.aaa but to bbb.bbb.bbb.bbb in case of a failure?)
[/LIST]

So...any ideas/suggestion how such an automated fallback system could be configured? May be there are already some solutions available so that there is no need to build up something for my own?

Thanks!

---

### Post by LHammonds on 2020-11-04
Use a load balancer + virtual IP sitting in front of both web servers.

Example: [How to Load Balance Apache Web Server on Ubuntu Server 18.04 LTS](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=260)

LHammonds

---

### Post by TheFu on 2020-11-04
Is there a DBMS?

For static websites, just put a load balancer up, give that LB the main static IP and have it point to both back ends.  Pretty much every WSGI/PSGI web app server supports this.  I use nginx as a load balancer for my small sites, but ha-proxy or 20 others can work too. I terminate SSL in nginx as well.

The DBMS is harder. You need to decide lots of things.  If you have shared storage, then you can use a simple heartbeat and storage failover method.  If you don't have shared storage or want to avoid loading backend reporting on the transactional DBMS instance, then you'll want DB transaction replication from the master DBMS to the slave DBMS.  Oh - sorry, we aren't supposed to use master/slave terms anymore.  Primary/Failover?  I don't know the new terms.  Replication can be synchronous or asynchronous. Synchronous means the client writes to both the primary and the secondary DBMS - effectively slowing down all write transactions, but both writes are ACID compliant and errors are reported to the client.  Asynchronous means the client is synchronous writes to the primary and then returns, OK.  Any the primary DBMS forwards transactions to the secondary quickly, but there is a delay.  The delay can become multiple minutes if the primary becomes very busy.

Anyway ... we need to know more about the web-app, the database involved and the storage.  In general, it is easiest to setup DNS to point at 2+ IPs (dig google.com for an example; I see 6 IPs returned), have each of those servers write to the same DBMS running on a separate system, and replicate to another system.

This is how HA is done.  If all these systems are in the same 250 mile area, this doesn't handle DR needs. A properly designed HA solution can often address DR too for zero to minimal extra costs.

So, the first thing I'd do is to have my client complete an **RTO/RPO questionnaire** so they get the idea that nothing comes for free and to ensure I'm designing the HA and DR solution to meet their true needs.  Everyone want 100% uptime when it is free.  That isn't realistic - it won't be free and it can never be 100% uptime, doesn't matter who you are.
[LIST]
[*]Which web server?
[*]which web-app server?
[*]which DBMS?
[*]which storage?
[*]do you have redundant networking?
[*]how are the backups? 
[*]Can the restore happen pretty quickly to new hardware?
[/LIST]

---

### Post by Elmi77 on 2020-11-04
OK, loadbalancer sounds good but I afraid I do not understand the general concept behind it. In my scenario, where should I run it, on server A or server B? And what happens when that sever dies where the loadbalancer is doing his work?

---

### Post by ameinild on 2020-11-06
Try and research a bit more about NGINX and Traefik. Both are well proven and widely used reverse proxy and load balancer solutions.

This an image showing how Traefik works:

[ATTACH=CONFIG]287318[/ATTACH]

Also, what you're really asking sounds like you need a "VM cluster", where you have multiple machines running a hypervisor in a cluster, where instances can move between machines. This can be done in Proxmox for instance, although I don't have experience with it.

Jeff from Craft Computing recently made a video about a 3-cluster Proxmox setup:
[https://www.youtube.com/watch?v=08b9DDJ_yf4&t=568s](https://www.youtube.com/watch?v=08b9DDJ_yf4&t=568s)

---

### Post by TheFu on 2020-11-06
> **Elmi77 said:**
> OK, loadbalancer sounds good but I afraid I do not understand the general concept behind it. In my scenario, where should I run it, on server A or server B? And what happens when that sever dies where the loadbalancer is doing his work?

Basic HA architecture is too hard to answer in this forum.  You'll need to do outside research. There are infinite answers for how to setup local HA. 2 servers is better than 1, but not the ideal. The architecture of the software system would matter greatly. 

I've asked a few questions, none which have been answered, so I can't make any recommendations. 

A few terms to learn:
[LIST]
[*]heartbeat
[*]virtual-IP
[*]active-passive
[*]active-active
[*]load-balancing
[*]round-robin DNS
[*]sticky sessions
[/LIST]

Good luck.

---

### Post by LHammonds on 2020-11-06
> **Elmi77 said:**
> OK, loadbalancer sounds good but I afraid I do not understand the general concept behind it. In my scenario, where should I run it, on server A or server B? And what happens when that sever dies where the loadbalancer is doing his work?
I guess you did not look at and/or understand the diagram on the tutorial I linked you to.

If you only have 2 servers and nothing else, that diagram changes slightly.  Load Balancer 1 (LB1) would be part of Web Server 1 (Web1) (installed together) and LB2 would be part of Web2.  Both servers would share a virtual IP but only one of them would be actively owning that IP (e.g. LB1).  If the active server goes dark (e.g. the heartbeat on LB2 does not see LB1), then LB2 will become the active owner of the virtual IP and all traffic will flow to LB2.  If a server is down, the LB will realize this and only send traffic to the active Web server (which in your case will be the same server as the active LB.

LHammonds

---

### Post by slickymaster on 2020-11-06
@ameinild:
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by ameinild on 2020-11-06
> **slickymaster said:**
> @ameinild:
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

The image I posted was 40 kb, but I understand your point. ;)

---

