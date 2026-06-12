---
title: "Individual NICs for Specific Applications"
date: 2012-02-26
forum: Server Platforms
---

### Post by drexlock on 2012-02-26
Hello All,

I wasn't able to find this already posted on the forums so I'm not sure if it can't be done or if its really easy and I just don't realize it. 

I'm trying to consolidate my home infrastructure into a single machine. At the moment I have a Windows Home Server 2011 Box and a Server 2008 r2 machine running Hyper V. The Windows Home WHS2011 Machine is running Plex Media Server and the Server 2008 r2 machine is running OpenVPN in a Virtual Machine and has a Minecraft server running McMyAdmin on the Host OS. I originally had this one running on the one WHS2011 Machine but ran into network issues where when we had multiple people on the Minecraft Server it impact the streaming from Plex and general File Transfer. 

I know that Ubuntu can run all the applications I need but can it segregate the individual applications to different Network Cards? Such as having one NIC for File Transfer and Plex Streaming, One for OpenVPN Traffic and one for the Minecraft Server. The Machine I plan on installing thsi all one has an AMD 1090T Hex Core Processor running at 3.1 GHz and 16 Gigs of ram. I plan on keeping the Minecraft Server on a separate disk from my File Shares to help prevent I/O issues. 

Is it possible to assign individual NICs for specific applicaitons or do I have a different issue and I just don't realize it. These network cards would still be going into the same network on the same switch but I have already tested replacing network hardware and it did not effect the issue that I was seeing.

---

### Post by nsnidanko on 2012-02-27
You would have to assign 2 different IP addresses, thus each NIC (ie eth0 and eth1) will have unique IP address.

And then to make application goes through desired nic you will access it via the IP address of desired interface.

Lets say

eth0 - 192.168.244.10/24
eth1 - 192.168.244.11/24

If you want Minecraft to go through eth1 you need to access it via eth1 IP address and so on..

You can also bond network interfaces for load balancing and failover. 

Hope that helps.

---

### Post by drexlock on 2012-02-27
So it wouldn't be so much of a question of restricting an application to a specific NIC but more of accessing that application through the desired IP/NIC? 

But then how would you prevent another computer or a set top box on the network from accessing files or videos over eth1 when you want to limit them to eth0?

---

### Post by spynappels on 2012-02-28
With many applications, you can bind them to a specific IP in the conf files, so they only listen on that IP (and corresponding NIC).

You set up your most bandwidth hungry applications to use their own NICs, and whichever NIC is expected to have the least load can be used as the default route to the net as well. That would be the only NIC in /etc/network/interfaces that would have a gateway set, the rest would only have IP and netmask.

---

### Post by nsnidanko on 2012-02-28
Yes, best way would be what **spynappels** said. But if you want to have ultimate control and prevent data flow completely you can look into iptables firewall and create specific rules of each interface to match your needs (read: application needs).

ie: block Minecraft traffic on eth0 but allow it on eth1 and so on..

---

### Post by spynappels on 2012-02-29
> **nsnidanko said:**
> Yes, best way would be what **spynappels** said. But if you want to have ultimate control and prevent data flow completely you can look into iptables firewall and create specific rules of each interface to match your needs (read: application needs).

ie: block Minecraft traffic on eth0 but allow it on eth1 and so on..

You can use a combination of these two as well, so if a specific application does not allow you to bind it to a specific IP, then you can apply iptables rules to the ports used by different applications. NOTE: for this to work, each application needs to be listening on a different port, and you simply block the port using IPTables.

---

