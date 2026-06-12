---
title: "Server - Two Internet Connections - T1 line &amp; Broadband - Static IPs"
date: 2016-03-17
forum: Server Platforms
---

### Post by bsntech on 2016-03-17
Setting up a new server to replace an existing.

Server does DNS, web, e-mail services.

The current server is connected to a network with a Broadband connection with a static IP address.  It has a VM installed over the top of it that is then used to use the T1 connection with a static IP address.

Goal is to make use of both Internet connections for redundancy (connected to the same switch, just different default gateways).  If The Broadband line is down, access is still available to the server from the T1 IP address.  Vice-versa if the T1 is down.

Not sure if this is possible.  The other option would be to only use one Internet connection with a cron script that pings an outside IP.  Upon a failure, a script would be ran to change the default gateway on the server to start using the other connection.

Or, just stick with the way the current server is setup except modify it so there is the KVM host with two VMs running on top with each pointing out the different connection.  Then that means setting up NFS to share the home directories for e-mail and the web directory to share the website resources.

---

### Post by volkswagner on 2016-03-17
Why not use a router capable of DUAL WAN?

Is your server acting as DHCP for other LAN machines or just DNS?

One thing you may want to make clear, do you simply want failover (one WAN connection is primary) or do you want load balancing (both WAN connections are used to distribute the load? I believe load balancing cant take care of failover as well.  It may be good to explain, such as if one of your connections is metered and you'd rather not have it active all the time

---

