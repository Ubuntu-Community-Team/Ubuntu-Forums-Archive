---
title: "High Availability Load Balancing and LAMP Servers"
date: 2010-12-29
forum: Server Platforms
---

### Post by z33k3r on 2010-12-29
Hello! I figured I would follow this up with what came of my solution search and what we have currently in production :) We are averaging 1.2m uniques/month and utilize the majority of a 6mb pipe with burst option.

While I was looking for the best of both worlds, it would seem the only easy/free solutions are either live/failover or replication servers, where I was wanting a fully redundant live master/master configuration throughout our entire server system. Reality comes in when you have to start making sacrifices for flexibility or easy of use (I know some hard code *nix monkeys are going to yell at me for that one!).

Old server specs (1 unit):
- 1 x HP DL380 G5 : Dual Xeon 4-core, 8 gig ram, 6 * Cheetah 74gb SAS1 in RAID5, CentOS 5

First hardware specs (all on a gigabit network):
- 2 x SUPERMICRO SYS-5015A-EHF-D525 : Dual Core Atom based 1U servers with 4gb DDR3 memory and a 16gb SSD SLC HDD. Low power, all flash based load balancers. Mobo's feature Intel 82574L LANs!
- 2 x SUPERMICRO AS-2022G-URF : Dual Opteron 6100's (8-core), 16gb DDR3 ECC REG memory, 8 * Seagate Cheetah 15K.7 ST3300657SS 300GB HDDs hooked to a LSI MegaRaid 9261-8i 6Gb/s SAS2 controller /w BBU in RAID10 (lots of DB read/writes), dual 80+ PSUs
- Tripp Lite SMART3000RM2U UPS
- Netgear gigabit switch all shielded CAT6 (overkill, but ya do it right the first time right!?)

Load balancers are configured but not in production or tested with SSL yet, so I will not talk about those at this time. I will update this thread as time and projects permit.

Solution settled upon was using the latest Proxmox Virtual Environment manager. Installation was simple enough. We did split our raid array (1.2tb) into two visible drives. The 0,0 was set to 100gb for OS, subsystems and logs. 0,1 was set to the remaining free space (1.1tb) for the VM storage setup in DRBD for replication.

We installed Proxmox from the 'bare-metal' ISO using a Master/Slave node configuration on drive 0,0 and then followed the Proxmox DRBD manual to configure and setup the DRBD drive share on 0,1. DRBD sync is done over a server-to-server gigabit connection bypassing the network. Needless to say, 1.1tb block sync. took for eeeeeeveeeeeerrrr...

Once this was done, we were up and going with our Proxmox Master/Slave setup. Using the DRBD subsystem we are able to utilize the single 1.1tb 'network-raided' drive for VMs. This means that if either server goes down, we just simply restart that image on the other node. As Steve Jobs would say, "It's magical!"

With this setup, I have basically unlimited options for multiple load balanced VMs including collaborative environment tool servers, Postfix servers, basic LAMP servers and the list goes on...

First thing we did was make two DB servers (one on each node) and then we have those doing Master/Slave synchronization. We then load balanced those servers by writing our PHP DB wrappers to read from the local database of that node but only write to the Master node. This was the preferred method as most of our traffic is table reads rather than writes (about 10:1). The result as you can imagine has been great and the db master server averages <1.5, the slave <1.0 where as our old server installation would freeze up CPU threads often as the single DB was local to that single LAMP installation.

While we are developing our new source API for our sites and designing them with the load balancing in mind, we have temporarily setup a mirror VM of our old server with the exception of installing Ubuntu Server x64 10.04 from scratch instead of CentOS 5 *shuder*... That single VM has been allocated 2 CPU's with 8 cores each and 8gb ram... While this is a mirror of our sites from our old server, our load on this VM alone stays an average of 0.8-1.5 with spikes up to 3.5 at at our busy peaks. This is compared to the old server that averaged 4.5-5.6 at all times. The database separation has obviously made a huge difference.

With the transition to our new serve, our Proxmox servers averaging <1.8. We are going to be doing a large email campaign here soon and we have multiple email servers setup for that. We will see how emailing newsletters etc to our millions of users affects bandwidth and server load. Our previous single server setup would basically crawl to a halt during these times. We would be able to get out around 300-400k emails a day on off peak hours. I suspect our new monsters will have no problem munching through them and I will post some numbers once those get going.

I intend to update this with my load balancing endeavors as soon as I can. For now, back to work!




**ORIGINAL POST**
------------------------------------------------------

Hello all! ):P

I am about to embark on building a small cluster with high-availability load balancers and servers that will server millions of users a month (as in we already have this much traffic and are expecting more as we grow this year) and will be supporting SSL transactions. I would like to know if any of you have done this and have any suggestions or experiences I could learn from before hitting those road blocks?

Our current plan of attack as from what we've gathered to be the best option from the various users/sites on the inter-tubes is two identical boxes running LVS + HAProxy. These would then hand off to two identical servers with LAMP stacks running with Linux-HA Heartbeat and Pacemaker.

There have been other various suggestions, but this seems like the most tightly developed grouping of packages (from what I am gathering around the web).

I haven't been able to find a complete guide to all of this; just parts and pieces. Does anybody know of a full guide that one can find to make sure they are not nuking their projects? I plan to write a full guide/journal when I have completed my journey to help others and use as a back-reference.

Any insight or experience is very helpful and appreciated. Thanks!

---

### Post by z33k3r on 2010-12-29
I should also mention that the LAMP stacks' MySQL will be in a Read/Write configuration where one database is for read only (slave) and the other for write only (master) with instant sync.

We plan to eventually add a separate HA-DB pair as well as a CDN pair for delivering our image files etc. and eventually end up with a completely redundant Load balancers, HTTP hosts, File storage and DB pairs.

---

### Post by z33k3r on 2010-12-29
So a bit more investigation into the HAProxy setup of the load balancers and it appears that I would have to add something to handle the SSL as HAProxy only forwards if using HTTP mode.

What I find most people doing is using STunnel to catch and decrypt port 443 and forward it to port 81 as unencrypted http to the Apache servers.

One such example: [http://blog.phpontrax.com/2010/02/how-to-make-an-open-source-load-balancer-stunnel-haproxy/](http://blog.phpontrax.com/2010/02/how-to-make-an-open-source-load-balancer-stunnel-haproxy/)

I would prefer to simply have the stream go like this: Client -> Web -> Firewall -> Load Balancers -> HTTP Servers -> Client... encrypted all the way to the HTTP servers and back.

I should also mention that I have EV SSL certificate that I am using, not just a standard $10 cert.

Any ideas or am I stuck using unencrypted communications between my load balancers and the HTTP servers? :confused:

---

### Post by z33k3r on 2010-12-29
Hm, thinking Pound is possibly a better solution as it does the Stunnel trick built-in...

[quote=http://www.apsis.ch/pound/]

**WHAT POUND IS:**

[LIST=1]
[*]a reverse-proxy: it passes requests from client browsers to one or more back-end servers.
[*]a load balancer: it will distribute the requests from the client browsers among several back-end servers, while keeping session information.
[*]an SSL wrapper: Pound will decrypt HTTPS requests from client browsers and pass them as plain HTTP to the back-end servers.
[*]an HTTP/HTTPS sanitizer: Pound will verify requests for correctness and accept only well-formed ones.
[*]a fail over-server: should a back-end server fail, Pound will take note of the fact and stop passing requests to it until it recovers.
[*]a request redirector: requests may be distributed among servers according to the requested URL.
[/LIST]
[/quote]

---

### Post by Lord_ on 2011-02-07
Did you ever get this working?

I need to setup a HA website, not going to be high traffic, but VERY high uptime required. I had been thinking of going the CARP and RSYNC route, but this got my attention!

---

### Post by z33k3r on 2011-02-08
We eventually decided on using a Proxmox + DRBD (network based RAID1) setup on our two servers, one as Master and one as Slave. Basically these are two VM servers utilizing a common DRBD drive for VM image storage. At any point, one of the servers could crash and you could restart the VM image from where it left off on the other server.

Now on top of this, we've built VM images for MySQL, HTTP and Postfix on seperate images with mirrors on the opposite server. These then are kept in sync with their various supported methods.

This enables us to migrate as needed. So once we out grow the current cluster, we will be able to migrate the DB images to dedicated MySQL clustered servers without much hassle. Same for Postfix.

I will have a full write up on this once it's all live and tested.

---

### Post by rubylaser on 2011-02-08
Proxmox is a dead simple method to set this up.  I love how easy it is to setup clusters, and to shared filesystems for live migrations via ISCSI or NFS shares.  I've been using it in production for almost 2 years now, and it's not let me down...knock on wood.

---

### Post by z33k3r on 2011-03-03
Updated OP with new details/summaries. :popcorn:

---

### Post by z33k3r on 2011-04-21
Well wouldn't you know it... Our master node's raid controller is having issues and it crashed... and you can't manage your KVM VMs from the slave without the Master... WTF!? 

Luckily before it did, I had happened to migrated the VM's from the Master node to the slave node!

Also, Proxmox's wiki and forums have been down as well so most of my tech reference for them is gone atm...

---

### Post by z33k3r on 2011-04-22
Well, I should correct my statement; you can start/stop/etc VMs from the CLI. You can't administrate from the web interface. This includes not being able to use the Java KVM plugin. Still looking for a way to bring up a VM from the master machine that was stored on the DRBD... it's currently not visible from the slave node.

---

