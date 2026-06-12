---
title: "server/router problems"
date: 2011-02-05
forum: Server Platforms
---

### Post by santiago79830 on 2011-02-05
I'm experiencing some difficulty in building a router, using Ubuntu 10.04, and Webmin. I've attached three drawings, showing the current configuration, the test configuration, and the final configuration.

The wireless router and computers to the right are approximately 250 feet away from the computers and satellite modem at the left of these drawings. It is impractical to colocate them. 

The current configuration works fine, except that I cannot share files across the computers, and the satellite modem does not have a very good firewall. I don't want to make my personal files accessible across the whole internet, hence the desire to install a firewall before enabling file sharing.

The test configuration is an interim way to test the firewall, file sharing, and so on, before disturbing users on the remainder of the network. In the test configuration, the router (Lancelot) has no evident problem accessing web pages, email, etc. It can ping the satellite modem at 192.168.0.1 with no difficulty.

However, the computer attempting to use the router, the other computer, Galahad, has problems with access. It can ping either Lancelot (192.168.2.1) or the satellite modem (192.168.0.1). But it cannot access web pages.

My first thought was that perhaps the name server in the router (Lancelot) was not working. However, I do not appear to be able to access web pages from Galahad, even if I enter the numeric address manually.

Any thoughts on this?

---

### Post by ephmanjmm on 2011-02-05
What subnet mask(s) is/are in use and where?  What are you using for the default gateway for the different segments of the network?

---

### Post by kevinthecomputerguy on 2011-02-05
Make sure your not using AP isolation in your wifi settings.
 
then
 
Try [http://woodel.com](http://woodel.com)  in particular page 5

---

### Post by santiago79830 on 2011-02-06
ETH0 uses gateway 192.168.2.1.
Both netmasks are set to 255.255.255.0 and the subnet mask is set to 255.255.255.0

New piece of data: I cannot ping Galahad from Lancelot, although I can ping Lancelot from Galahad. I checked the list of active leases, and Galahad has the address of 192.168.2.101. However, when I ping that from Lancelot, it's a no-show.

---

### Post by ephmanjmm on 2011-02-07
I am assuming that Lancelot has more than one ip address.  Can you give more information of the addressing and routing? List the routes from each computer and the ip addresses, mask and gateway for all interfaces please.
Or add a static route on Lancelot to the 192.168.2.0/24 subnet with 192.168.2.1 as the interface to use.

[http://linux.wxs.ro/2009/01/30/howto-add-permanent-static-routes-in-ubuntu/](http://linux.wxs.ro/2009/01/30/howto-add-permanent-static-routes-in-ubuntu/)

---

### Post by registered2-5-2011 on 2011-02-07
> New piece of data: I cannot ping Galahad from Lancelot, although I can ping Lancelot from Galahadmaybe the xp firewall is enabled and blocking those icmp by default


Is the ubuntu server running dhcpd? can the satellite modem be put in bridge mode? I have seen a setup like this before and you may have more control over firewall rules and connectivity from the wan side with it in bridged mode, having eth1 configured as the wan ip doing all of the firewalling. Then you can have the dhcpd listening on eth0.

---

### Post by hema87 on 2011-02-08
For this problem, you contact the Internet service provider,
After that check your ping test, through this site [http://www.whoisxy.com/ping.aspx](http://www.whoisxy.com/ping.aspx)
It has the best information of IP address, IP address to domain, domain  name to IP,domain name, hosting, and ping test to know the particular  connection is online or not!!!!!

---

