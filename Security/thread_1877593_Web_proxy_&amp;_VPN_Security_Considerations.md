---
title: "Web proxy &amp; VPN Security Considerations"
date: 2011-11-08
forum: Security
---

### Post by HellesAngel on 2011-11-08
To be able to obtain IP addresses from around the world I use a [Hide My ***]("http://hidemyass.com/") subscription to establish an OpenVPN connection to their servers.  The VPN connection is established from a virtual server inside my private network (behind my IPCOP firewall inside its green zone) that then uses a Squid proxy to allow connections from around my network.  This works fine but I am worried about establishing what is effectively another external internet connection from inside my firewalled network zone.

To be able to run a HMA connection to France I now need to play with PPP and iptables and NAT, something I've not previously had much experience with  directly but seems like a good opportunity to try to secure things further.  Can anyone point me towards a good explanation of ufw, iptables, and then VPNs and security?

The server that hosts Squid and the VPN is running Ubuntu 11.04 configured as a LAMP server and is doing nothing else than running the VPN & proxy, the VPN connection is only established when needed, but my approach to security is on the paranoid side of severe.  What are the security risks of running a VPN/Proxy from inside a firewalled network?  Is it just as bad as another unsecured external network connection?

Any hints & tips welcome.

---

### Post by Dangertux on 2011-11-08
> **HellesAngel said:**
> To be able to obtain IP addresses from around the world I use a [Hide My ***]("http://hidemyass.com/") subscription to establish an OpenVPN connection to their servers.  The VPN connection is established from a virtual server inside my private network (behind my IPCOP firewall inside its green zone) that then uses a Squid proxy to allow connections from around my network.  This works fine but I am worried about establishing what is effectively another external internet connection from inside my firewalled network zone.

To be able to run a HMA connection to France I now need to play with PPP and iptables and NAT, something I've not previously had much experience with  directly but seems like a good opportunity to try to secure things further.  Can anyone point me towards a good explanation of ufw, iptables, and then VPNs and security?

The server that hosts Squid and the VPN is running Ubuntu 11.04 configured as a LAMP server and is doing nothing else than running the VPN & proxy, the VPN connection is only established when needed, but my approach to security is on the paranoid side of severe.  What are the security risks of running a VPN/Proxy from inside a firewalled network?  Is it just as bad as another unsecured external network connection?

Any hints & tips welcome.


The security implications of running 2 more services is that you're now running two more services. Whether they are exposed to the internet or not they are on your network. If a machine inside of your network becomes compromised those are two more services that are available to an attacker. That being said I would not say you are doing something overtly insecure by running a VPN or proxy server inside of your network.
 
Also note , that privacy and security are not the same thing.

---

### Post by HellesAngel on 2011-11-08
Hi DangerTux, thanks for your response - it sounds reassuring.  I was thinking that as the end of the VPN tunnel is a server somewhere on the internet that the security risks are the same as with the normal connection to the ISP.  To move this proxy server out of the green subnet to the DMZ and then set up port forwarding would be tricky for my network setup.

The VPN isn't important for my privacy, I'm not worried about my ISP seeing what I'm doing through their connection, but I need foreign IP addresses from time to time and this HMA/VPN/Squid setup works well, but the security of my network is very important to me.

---

### Post by Dangertux on 2011-11-08
The standard rules apply when adding any new service.

Keep it updated, configure it properly (in squid's case proper ACLs same with the VPN), strong credentials etc. If you're especially nervous consider confining the service with Apparmor.

Hope this is helpful.

---

