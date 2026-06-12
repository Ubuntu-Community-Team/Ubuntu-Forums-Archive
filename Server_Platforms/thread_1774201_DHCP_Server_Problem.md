---
title: "DHCP Server Problem"
date: 2011-06-03
forum: Server Platforms
---

### Post by Monery on 2011-06-03
I been trying to set up a DHCP3-server on my brand new learning Ubuntu 11.04 server. I can connect when i put the IP infomation in manually, so I know everything else is working, just got to fix the DHCP problem before I put the machine into production on my home LAN. Can someone tell me if these config files located at /etc/dhcp3/dhcpd.conf and another at /etc/default/dhcp3-server are correct? eth1 is the NIC that will be the LAN side of the network, I double checked that...

```
/# A slightly different configuration for an internal subnet.
subnet 192.168.10.0 netmask 255.255.255.0 {
range 192.168.10.10 192.168.10.200;
option domain-name-servers 8.8.8.8, 8.8.4.4;
option domain-name "linuxrouter.local";
option routers 192.168.10.1;
option broadcast-address 192.168.10.255;
default-lease-time 86400;
max-lease-time 86400;

authoritative;
ddns-updates on;
}

``````
interfaces="eth1"
```

---

### Post by Lars Noodén on 2011-06-03
Can you try dnsmasq instead?  It's far easier to configure.

---

### Post by SeijiSensei on 2011-06-03
The configuration file looks file except for that extraneous slash at the beginning of the first line.  Really the only way to test this out is to actually try using it, though.  

Are you also running BIND so that DNS updates will be passed to the name server?

---

### Post by lfacchinelli on 2011-06-03
> **SeijiSensei said:**
> The configuration file looks file except for that extraneous slash at the beginning of the first line.  Really the only way to test this out is to actually try using it, though.  

Are you also running BIND so that DNS updates will be passed to the name server?
Agree with you
That slash at the first line of config file isn't common.
Remove it and test
And also check log files

---

### Post by Monery on 2011-06-03
I am using these config files and they do not work :(

> **Lars Noodén said:**
> Can you try dnsmasq instead?  It's far easier to configure.

The only reason I am using DHCP3-server is that my google queries for a DHCP server returned this as very popular. I am not set on using DHCP3-server so I will look up dnsmasq and check it out. 

as far as the mystery '/' that is in my config file, that might have been an error on my part in the posting but I will check the actual file to see if it exists. Other than that it seems I knew what I was doing when I made the file, so thank all of you for letting me know that I didn't have some crazy typo. If anyone has some URL's for a dnsmasq tutorial, I'd be very thankful for the time savings

---

### Post by Monery on 2011-06-03
I just discovered a nifty tool /usr/sbin/dhcpd -f

results from this tool are
```
Internet Systems Consortium DHCP Server 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
Wrote 0 leases to leases file.

No subnet declaration for eth1 (192.168.1.56).
** Ignoring requests on eth1.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth1 is attached. **


No subnet declaration for eth0 (192.168.10.1).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **


Not configured to listen on any interfaces!

```

Maybe that will assist someone in discovering what I am doing wrong.. as far as I can tell I am declaring the subnet

---

### Post by Lars Noodén on 2011-06-04
> **Monery said:**
> I just discovered a nifty tool /usr/sbin/dhcpd -f

results from this tool are
```
...
No subnet declaration for eth1 (192.168.1.56).
** Ignoring requests on eth1.  If this is not what...

No subnet declaration for eth0 (192.168.10.1).
** Ignoring requests on eth0.  If this is not what...
Not configured to listen on any interfaces!

```

Maybe that will assist someone in discovering what I am doing wrong.. as far as I can tell I am declaring the subnet

The **-f** runs dhcpd in the foreground so the output can be viewed directly and not via a system log file.  It's very useful for this kind of diagnosis.

What the two errors are about is that the subnets defined in dchpd.conf must match the ip addresses.  If you have ip address 192.168.10.1 then you should have a subnet something like 192.168.10.0/24.

---

### Post by Monery on 2011-06-09
[SOLVED]
 
Although I was told in several threads from various sites to put my configurations into /etc/dhcp**3**/dhcpd.conf, that path was not correct. Correct path is /etc/dhcp/dhcpd.conf (note the lack of 3 in the 2nd directory path. Just goes to show you that even a single letter can mess things up. thx for all the assistance I have received regarding this issue.

---

