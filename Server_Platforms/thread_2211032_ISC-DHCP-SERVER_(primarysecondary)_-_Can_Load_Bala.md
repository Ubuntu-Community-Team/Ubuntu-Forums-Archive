---
title: "ISC-DHCP-SERVER (primary/secondary) - Can Load Balancing Be Disabled?"
date: 2014-03-13
forum: Server Platforms
---

### Post by Sniperm4n on 2014-03-13
Hi everyone,

When I was hired at my company, I quickly determined that one of my  highest priority projects would be to improve our ancient DNS/DHCP  setup. It was running on an Ubuntu-based workstation-grade server that  was more than 7 years old, and was in serious danger of keeling over.  So, I started researching options for adding fault tolerance. I ended up  building a standard Ubuntu Server 12.04.3 LTS 64-bit ISC DHCP failover  cluster with a primary and secondary server, utilizing load balancing.  The way things currently work, if my DHCP range consists of 54 IPs, the 2  servers split the IP pool evenly (27 each) while remaining in constant  communication with one another. If one of the servers goes down for more  than an hour without getting put into a partner-down state, my life  then becomes hell.


  I've since come to realize that the load balancing aspect is overly complex, and *VERY*  unnecessary for our small shop. Unfortunately, I've been unable to find  any documentation on how to create a simple primary/secondary  relationship, whereby the secondary will take over all responsibilities  in the event the primary experiences a failure (it would ideally  function as a hotspare). Does this functionality exist within  ISC-DHCP-SERVER v4.1.ESV-R4-0ubuntu5.6? If so, how in the world is it  configured? I've seen mention of things such as "split 256" (as opposed  to the "split 128" I'm currently using), but I can't find anything to  definitively confirm this. If the convoluted load balancing feature is a  requirement for fault tolerance, then so be it. Also, a quick note that  I'm more of a Windows Admin than a Linux Admin, so please be gentle :P

Thanks,
-Snipe

---

### Post by aerokid240 on 2014-03-25
"Heartbeat" sounds like the solution for you. The two servers will monitor each other using the heartbeat deamon. One of the servers will be the master, the other the slave. The master will be utilizing a virtual IP address and in the event the master goes down, the slave will take over this virtual ip address and start up its own dhcp daemon to serve clients. When the master comes back online, the slave will stop the server daemons and hand over the virtual IP back to the master.

Update:

Here is a useful tutorial that i recommend; [Link]("http://www.howtoforge.com/high_availability_heartbeat_centos").

---

### Post by SeijiSensei on 2014-03-25
How long are your leases?  With such a small number of hosts, you can give the machines very long leases like six months.  I'm pretty sure that if the server happens to go offline, the workstations will still be able to use the leases they have already received.  If the leases are long enough, you'll have plenty of time to fix the server.

---

### Post by aerokid240 on 2014-03-25
> **SeijiSensei said:**
> How long are your leases?  With such a small number of hosts, you can give the machines very long leases like six months.  I'm pretty sure that if the server happens to go offline, the workstations will still be able to use the leases they have already received.  If the leases are long enough, you'll have plenty of time to fix the server.

If the client machines are restarted every morning, then they will need an available dhcp server to hand out IPs, no matter the length of the lease time. For high availability, a second server is needed.

---

