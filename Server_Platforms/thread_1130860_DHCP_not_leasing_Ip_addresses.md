---
title: "DHCP not leasing Ip addresses"
date: 2009-04-20
forum: Server Platforms
---

### Post by chrislynch8 on 2009-04-20
Hi,

Ubuntu Server6.06LTS - DHCP3-Server 3.03-6ubuntu7

It was working up until last week, then one morning no users where able to receive IP addresses. 

I restarted the DHCP service, restarted the server, checked all syslog, messages, kern logs are nothing stating an error with the DHCP server. I have all local7* going into a dhcpd.log file and there are no errors in here either.

These are the last few lines in the log file.
```

Apr 20 09:50:18 server06 dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Apr 20 09:50:18 server06 dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Apr 20 09:50:18 server06 dhcpd: All rights reserved.
Apr 20 09:50:18 server06 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr 20 09:50:20 server06 dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Apr 20 09:50:20 server06 dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Apr 20 09:50:20 server06 dhcpd: All rights reserved.
Apr 20 09:50:20 server06 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr 20 09:50:20 server06 dhcpd: Internet Systems Consortium DHCP Server V3.0.3
Apr 20 09:50:20 server06 dhcpd: Copyright 2004-2005 Internet Systems Consortium.
Apr 20 09:50:20 server06 dhcpd: All rights reserved.
Apr 20 09:50:20 server06 dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr 20 09:50:20 server06 dhcpd: Wrote 0 leases to leases file.

```

Any one have any issues like this, I double, checked my config files, the default/dhcp file, it is set to the correct Interface device.

I also found no messages in the firewall blocking DHCP request on both the clients pc and the server.

Rgds
Chris

---

### Post by nandemonai on 2009-04-20
General network connectivity ok? Perhaps set a static IP for one of the clients and do some tests to ensure it's not a general networking issue.

---

### Post by chrislynch8 on 2009-04-20
> **nandemonai said:**
> General network connectivity ok? Perhaps set a static IP for one of the clients and do some tests to ensure it's not a general networking issue.

Hi should have mentioned, I had to set all user to static to allow normal day to day business to run. All user now have normal access to network shares, files on other servers over VPNs, there doesn't seem to be any network issues.

Rgds
Chris

---

### Post by Iowan on 2009-04-20
Along the network connectivity theme - machine can ping? (be pinged?)

---

### Post by dubhear on 2009-04-20
[http://http://www.isc.org/sw/dhcp/]("http://http://www.isc.org/sw/dhcp/")
says:
Page not found

The page you requested was not found.

hmm.. makes me wonder...

ps. you have tried to bring firewalls down so firewalls cannot be the problem?

pps. maybe you need to upgrade to hardy, or add hardy's repositories. maybe there is not supportet packages available for older versions any more... can you or do you want to upgrade your repositories?

---

### Post by chrislynch8 on 2009-04-21
> **Iowan said:**
> Along the network connectivity theme - machine can ping? (be pinged?)

The server running DHCP can be pinged, it can also ping all the clients now that static IP have been assigned, it is the firewall, it is acting as a squidGuard proxy server, it has DNS, NFS, autofs, NIS, all running and working correctly. I can ssh into the server from another server over a VPN. I cannot find anything wrong with the server, no errors in the logs, etc.

---

### Post by chrislynch8 on 2009-04-23
> **dubhear said:**
> [http://http://www.isc.org/sw/dhcp/]("http://http://www.isc.org/sw/dhcp/")
says:
Page not found

The page you requested was not found.

hmm.. makes me wonder...

ps. you have tried to bring firewalls down so firewalls cannot be the problem?

pps. maybe you need to upgrade to hardy, or add hardy's repositories. maybe there is not supportet packages available for older versions any more... can you or do you want to upgrade your repositories?

I don't see why upgraded to Hardy will help, I have the Dapper LTS version so its supported for another two years, and the DHCP is not causing an issue on another 15 servers with the exact same setup.

I have compared, iptables, netstat output, firewall rules, config files, binaries, I've checked everything I could think of, I scanned the network to see if there is a rogue IP on the network, etc, etc.

Rgds
Chris

---

### Post by chrislynch8 on 2009-04-27
Bump

---

### Post by chrislynch8 on 2009-04-27
Hi,

Just for anyone that was reading this thread, The issue is now resloved, I had a faulty switch that for some reason worked fine when the users had static IP addresses but when they required a Dynamic IP they seem to just not be able to get thorough the switch.

Odd

---

### Post by Iowan on 2009-04-27
Very odd... Glad you found it - sorry I couldn't have been more help.

---

