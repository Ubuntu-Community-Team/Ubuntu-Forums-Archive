---
title: "Ebox - dansguardian/squid problems - Cant ssh :("
date: 2008-09-01
forum: Server Platforms
---

### Post by w1z4rd on 2008-09-01
Network background:


ADSL Router (172.16.1.1)----> eth0 (172.16.1.2) EBOX eth1 (10.0.0.3)-----> LAN

I had a couple of small problems with DNS and eth0... I think I am not setting up the gateway or DNS or something correctly, but basically when I set the IP of eth0 to 172.16.1.2, I could not get DNS to resolve. So what I did was I got the Netgear router to hand out an IP to eth0, and this was statically mapped to its MAC address, so that eth0 will always get the same dns and IP handout from the router.

The services I am running on ebox at the moment for the person I set this up are:

mail (works 100%)
http proxy (causing me major problems)

Initially, it was going to be a dansguardian setup with the ebox, but I quickly ran into a whole bunch of problems with Dansguardian that I was unable to figure out. Basically, dansguardian would work for a bit.. then completely stop working, and the error logs would tell me that it had problem binding to the port.. no matter what port I set it up as.

So I set the http proxy as transparent, and set it to allow all.

Now my new problem comes up....

Our area has a lot of power failures and this weekend the server went offline again. When it and the router came back online, I was unable to access the ebox system (but was able to access the router). From the router I am able to ping the ebox server. 

However, I am completely unable to ssh into ebox, or access any other of its services. When I login to the box directly from it.. and restart the squid service.. the box seems to come back alive again.

I cant ssh into the box from the LAN or WAN networks.. I have to log directly into the box to restart the services.

This is a pain because it means I have to drive out there everytime the box goes down to manually restart squid.

Im not sure where the probelms are. Heres a couple of lines outta /var/log/syslog

```
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:27:59 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:27:59 ubuntu dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Sep  1 06:27:59 ubuntu dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Sep  1 06:27:59 ubuntu dhcpd: All rights reserved.
Sep  1 06:27:59 ubuntu dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Sep  1 06:28:00 ubuntu dhcpd: Wrote 0 leases to leases file.
Sep  1 06:28:00 ubuntu dhcpd:
Sep  1 06:28:00 ubuntu dhcpd: No subnet declaration for eth0 (172.16.1.2).
Sep  1 06:28:00 ubuntu dhcpd: ** Ignoring requests on eth0.  If this is not what
Sep  1 06:28:00 ubuntu dhcpd:    you want, please write a subnet declaration
Sep  1 06:28:00 ubuntu dhcpd:    in your dhcpd.conf file for the network segment
Sep  1 06:28:00 ubuntu dhcpd:    to which interface eth0 is attached. **
Sep  1 06:28:00 ubuntu dhcpd:
Sep  1 06:28:02 ubuntu dansguardian: Error binding server socket (is something else running on the filter port?
Sep  1 06:28:02 ubuntu dansguardian: Exiting with error
Sep  1 06:28:02 ubuntu /usr/sbin/cron[9906]: (CRON) INFO (pidfile fd = 3)
Sep  1 06:28:02 ubuntu /usr/sbin/cron[9907]: (CRON) STARTUP (fork ok)
Sep  1 06:28:02 ubuntu /usr/sbin/cron[9907]: (CRON) INFO (Running @reboot jobs)
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:02 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:28:03 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:03 ubuntu slapd[5710]: <= bdb_equality_candidates: (uid) not indexed
Sep  1 06:28:03 ubuntu slapd[5710]: <= bdb_equality_candidates: (memberUid) not indexed
Sep  1 06:28:03 ubuntu fetchmail[9952]: starting fetchmail 6.3.8 daemon

```

So the things I am looking for solutions for are:

1) How to stop squid from bailing on me, or how to access the server even when squid does not start up

2) Figure out whats causing dansguardian to misbehave

3) Work out how to setup the network settings so I dont have to use the DHCP on the router to hand out an address (something I think .. by looking at those logs files.. is complicating stuff.

Hope to hear from you!

---

