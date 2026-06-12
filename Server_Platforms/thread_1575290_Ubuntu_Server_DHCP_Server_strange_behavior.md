---
title: "Ubuntu Server: DHCP Server strange behavior"
date: 2010-09-15
forum: Server Platforms
---

### Post by Kandi07 on 2010-09-15
Hi guys,

I hope somebody of you could help me with my very serious DHCP Server problem.

First to my settings:
I have Ubuntu 10.04 Server installed and I have added the services Samba and DHCP.
The Ubuntu Server has two network devices: One for the WAN (eth0 - IP 10.0.0.1) and one for the internal network (eth1 - IP 192.168.1.1).
I have both network interfaces configured in the
```
/etc/network/interfaces
```file

I will post the output of all files tomorrow morning when I'm back in my office.

After this I have installed the DHCP server (dhcp3-server) with apt.
Then I have edited the DHCP configuration file
```
/etc/dhcp3/dhcpd.conf
```The IP Range should start from 192.168.1.10 and will end at 192.168.1.20
The netmask is 255.255.255.0 and the default gateway should be the Ubuntu Server with IP 192.168.1.1
I have also configured that the notebook which I will connect to the DHCP Server through any 16 Port Gigabit Switch, will allocate fix ip 192.168.1.10
After all this configuration I have modified the file
```
/etc/default/dhcp3-server
```to enter the network interface which the DHCP Server will use. In my case eth1

Now the very strange things beginns:

When I connect my notebook to the switch the notebook allocate the correct 192.168.1.10 ip address from the DHCP Server. But suddenly after some minutes, I would say after the default lease time I configured for the DHCP Server, the Ubuntu Server change the ip address on network interface eth1 to ip 192.168.1.10
Now the notebook with Windows XP shows a System Error Message like "Wrong Configuration IP address is already in use" and the network share I mounted on the Ubuntu Server is disconnect.
When I now type the command on the Server:
```
sudo ifdown eth1
```and 
```
sudo ifup eth1
```the network interface eth1 get again the correct ip 192.168.1.1

I disconnect and connect the notebook again to the swith and the problem starts all over again.

I hope really somebody could help me, because it is really annoying.

Kind regards,
Kandi07

---

### Post by CharlesA on 2010-09-15
The DHCP server needs to have a static ip address.

---

### Post by Kandi07 on 2010-09-15
you mean that I should add the fix ip configuration in the 
```
/etc/dhcp3/dhcpd.conf
```
?

---

### Post by CharlesA on 2010-09-15
No. We'd have to see yer /etc/network/interfaces to see how it's set up.

---

### Post by Iowan on 2010-09-15
Fixed IP's (or static leases) need to be ***outside*** the DHCP range. If you plan to use 192.168.1.10 for the notebook, make the DHCP range 192.168.1.11 - 192.168.1.20. 

(But the server's "local" address (192.168.1.1) should still be fixed (static).

---

### Post by capscrew on 2010-09-15
> **Iowan said:**
> Fixed IP's (or static leases) need to be ***outside*** the DHCP range. 
This is partially true.  Static IPs are configured via configuration files.  The static part has nothing to do with whether the IP address stays the same.  Static refers to how the IP address is configured.  Static IP addresses should be outside the dynamically assigned (DHCP) address pool.

Reserved leases for fixed IP addresses are still dynamically applied (via the DHCP server).  These are what you call "static leases".  These IP addresses should be part of the pool.

DHCP served IP addresses = in the pool
Non-DHCP (static) IP addresses = not in the pool 
> 

If you plan to use 192.168.1.10 for the notebook, make the DHCP range 192.168.1.11 - 192.168.1.20. 

(But the server's "local" address (192.168.1.1) should still be fixed (static).

Statically configured.  Immutable (as in non-changing).  No server should rely on another server (DHCP) for its IP address.

---

### Post by jeight on 2010-09-15
To make this easier to troubleshoot could you please post a copy of your dhcp file and one of you /network/interfaces. I would have to agree that either you make eth1 a static address or make sure the dhcp server know what NC it is suppose to be listen to. Should be something like DHCPARG=ETH1.

---

### Post by Kandi07 on 2010-09-16
thanks guys for the advices.
I have now changed my settings and here the output of the necessary files:

/etc/dhcp3/dhcpd.conf
```

#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option gateway 192.168.1.1;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;
option domain-name "internal.example.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.1 192.168.1.10;

#    host dhcp_server {
#        hardware ethernet 00:0e:0c:64:c7:29;
#        fixed-address 192.168.1.1;
#    }

    host notebook {
        hardware ethernet 00:0D:60:38:69:42;
        fixed-address 192.168.1.11;
    }
} 

option netbios-name-servers 192.168.1.1;

```/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 10.0.0.1
    netmask 255.255.255.0
    network 10.0.0.64
    broadcast 10.0.0.127
    gateway 10.0.0.126
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 10.0.0.10
    dns-search domain.test

# The secondary network interface
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

```and
/etc/default/dhcp3-server
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```

here also the output of 
ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:11:2f:cc:bd:b6  
          inet addr:10.0.0.1  Bcast:10.0.0.127  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fecc:bdb6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:794776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314622 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:857166539 (857.1 MB)  TX bytes:23765815 (23.7 MB)

eth1      Link encap:Ethernet  HWaddr 00:0e:0c:64:c7:29  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe64:c729/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:569226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941706 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47879121 (47.8 MB)  TX bytes:1279069037 (1.2 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1013508 (1.0 MB)  TX bytes:1013508 (1.0 MB)

```

---

### Post by Kandi07 on 2010-09-16
server mac address: 00:0e:0c:64:c7:29
notebook mac address: 00:0d:60:38:69:42

here is the output from the 
dhcp3 -d -f 
command:

```

Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 1 leases to leases file.
Listening on LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24
Sending on   LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24

No subnet declaration for eth0 (138.232.183.104).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **

Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
uid lease 192.168.1.10 for client 00:0d:60:38:69:42 is duplicate on 192.168.1/24
DHCPDISCOVER from 00:0d:60:38:69:42 via eth1
DHCPOFFER on 192.168.1.11 to 00:0d:60:38:69:42 via eth1
uid lease 192.168.1.10 for client 00:0d:60:38:69:42 is duplicate on 192.168.1/24
DHCPREQUEST for 192.168.1.11 (192.168.1.1) from 00:0d:60:38:69:42 via eth1
DHCPACK on 192.168.1.11 to 00:0d:60:38:69:42 via eth1
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPDISCOVER from 00:0e:0c:64:c7:29 via eth1
DHCPREQUEST for 192.168.1.11 (192.168.1.1) from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPOFFER on 192.168.1.1 to 00:0e:0c:64:c7:29 (ntinstall) via eth1

```

---

### Post by dtech on 2010-09-16
You should at least alter the following statement:
```

range 192.168.1.1 192.168.1.10;

```

You now set the range of adresses from 192.168.1.1 to 192.168.1.10. This might well be a reason for the strange behaviour, as both the servers own and the laptops fixed adress are in that range.

So to recap:
1. Set your server to a fixed 192.168.1.1 (done already)
2. Pick a proper DHCP range which does not include 192.168.1.1
3. Pick a static ip for your laptop outside of that range.

What I personally always do is:
192.168.1.1 - 192.168.1.99 : fixed adresses (e.g. servers, NAS)
192.168.1.100 - 192.168.1.199 : DHCP range
192.168.1.200 - 192.168.1.254 : Static DHCP range

---

### Post by Kandi07 on 2010-09-16
thanks for the hint dtech

I have now set the range 192.168.1.10 - 192.168.1.20
fix ip address dhcp server 192.168.1.1
fix ip address notebook (on dhcpd.conf configured) 192.168.1.30

Here are is now the new output form dhcpd.conf
```

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.1;
option domain-name "internal.example.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.100 192.168.1.200;

#    host dhcp_server {
#        hardware ethernet 00:0e:0c:64:c7:29;
#        fixed-address 192.168.1.1;
#    }

    host notebook {
        hardware ethernet 00:0D:60:38:69:42;
        fixed-address 192.168.1.30;
    }
} 

option netbios-name-servers 192.168.1.1;

```

and restartet the dhcp server with command
```
/etc/init.d/dhcp3-server restart
```

now i got following output from
```
dhcp3 -d -f
```

```

Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 0 leases to leases file.
Listening on LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24
Sending on   LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24

No subnet declaration for eth0 (138.232.183.104).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **

Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.
receive_packet failed on eth1: Network is down
DHCPDISCOVER from 00:0d:60:38:69:42 via eth1
DHCPOFFER on 192.168.1.30 to 00:0d:60:38:69:42 via eth1
DHCPREQUEST for 192.168.1.30 (192.168.1.11) from 00:0d:60:38:69:42 via eth1
DHCPACK on 192.168.1.30 to 00:0d:60:38:69:42 via eth1
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPREQUEST for 192.168.1.11 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.11.
DHCPDISCOVER from 00:0e:0c:64:c7:29 via eth1
DHCPOFFER on 192.168.1.100 to 00:0e:0c:64:c7:29 (ntinstall) via eth1

```

now my server acquire still a wrong ip address. Now the ip 192.168.1.100

```

eth1      Link encap:Ethernet  HWaddr 00:0e:0c:64:c7:29  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:cff:fe64:c729/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2490449 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4105439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:208466439 (208.4 MB)  TX bytes:1327620539 (1.3 GB)

```

---

### Post by dtech on 2010-09-16
I'd suggest appending /etc/network interfaces so it contains all necessary information, as to stop the DHCP requesting
```

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

Then execute
```

sudo /etc/init.d/networking restart

```

---

### Post by Kandi07 on 2010-09-16
first it worked but suddenly the server gets from the dhcp domain the ip 192.168.1.100

```

Internet Systems Consortium DHCP Server V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/
WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
Wrote 0 deleted host decls to leases file.
Wrote 0 new dynamic host decls to leases file.
Wrote 0 leases to leases file.
Listening on LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24
Sending on   LPF/eth1/00:0e:0c:64:c7:29/192.168.1/24

No subnet declaration for eth0 (138.232.183.104).
** Ignoring requests on eth0.  If this is not what
   you want, please write a subnet declaration
   in your dhcpd.conf file for the network segment
   to which interface eth0 is attached. **

Sending on   Socket/fallback/fallback-net
Can't create PID file /var/run/dhcpd.pid: Permission denied.
DHCPREQUEST for 192.168.1.30 from 00:0d:60:38:69:42 via eth1
DHCPACK on 192.168.1.30 to 00:0d:60:38:69:42 via eth1
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPREQUEST for 192.168.1.1 from 00:0e:0c:64:c7:29 via eth1: unknown lease 192.168.1.1.
DHCPDISCOVER from 00:0e:0c:64:c7:29 via eth1
[COLOR=Red]DHCPOFFER on 192.168.1.100 to 00:0e:0c:64:c7:29 (ntinstall) via eth1[/COLOR]

```

---

### Post by dtech on 2010-09-16
It's a bit ugly, but I think it will work. Uncomment the host dhcp_server lines in dhcpd.conf. That way even if the server does a DHCP request (which it'll answer itself...) it will still get assigned the 192.168.1.1 adress.

---

### Post by terazen on 2010-09-16
On your server you may need to uninstall dhcp3-client.  On new installs I've had to do this before.  I don't know why but when setting a static ip in the /etc/network/interfaces file and running "/etc/init.d/networking restart" the script doesn't kill the dhcp client process.

---

### Post by CharlesA on 2010-09-16
Right. I forgot to mention this:

When I originally configured my server, I set it for DHCP. I then decided to use a static address, but after the lease ran out, it would grab an address from DHCP again. I had to reboot the box, but I figure that I just needed to kill dhclient.

---

### Post by dtech on 2010-09-16
[s]dhclient should not be uninstalled or killed right now, he's still using it for eth0.[/s]
Nevermind, he has a static ip for eth0

But yeah, you could set a static address for eth0 and uninstall dhclient. That does mean that you'll end up reconfiguring stuff if your providers DNS changes (unless it is configured to pass by the router).

---

### Post by CharlesA on 2010-09-16
> **dtech said:**
> But yeah, you could set a static address for eth0 and uninstall dhclient. That does mean that you'll end up reconfiguring stuff if your providers gateway or DNS changes.

Indeed. :)

---

### Post by terazen on 2010-09-16
Would killing and restarting the dhclient process make the process reread the interfaces file and stop running on each interface that has a static ip?  Now I'm curious...

---

### Post by Kandi07 on 2010-09-20
I have removed the dhcp3-client from my server and now everything works fine.

Thanks guys for your help!

Kind regards,
Kand07

---

