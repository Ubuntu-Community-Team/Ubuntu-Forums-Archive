---
title: "DHCP server won't start"
date: 2011-05-10
forum: Server Platforms
---

### Post by smslavin on 2011-05-10
I'm trying to configure a 11.04 sever as a VM with 2 NICs to act as a gateway. The first NIC is a static IP set up as bridged to the host. The second NIC is going to run off DHCP and connect to a host-only network with several isolated VMs.

I'm having a problem getting the DHCP server to start.

```

administrator@Io:~$ sudo service isc-dhcp-server start
 * Starting ISC DHCP server dhcpd
 * check syslog for diagnostics.
   ...fail!
administrator@Io:~$ tail -f /var/log/syslog
May 10 07:33:32 Io dhcpd: Wrote 0 leases to leases file.
May 10 07:33:32 Io dhcpd: 
May 10 07:33:32 Io dhcpd: No subnet declaration for eth1 (192.168.126.128).
May 10 07:33:32 Io dhcpd: ** Ignoring requests on eth1.  If this is not what
May 10 07:33:32 Io dhcpd:    you want, please write a subnet declaration
May 10 07:33:32 Io dhcpd:    in your dhcpd.conf file for the network segment
May 10 07:33:32 Io dhcpd:    to which interface eth1 is attached. **
May 10 07:33:32 Io dhcpd: 
May 10 07:33:32 Io dhcpd: 
May 10 07:33:32 Io dhcpd: Not configured to listen on any interfaces!
May 10 07:40:17 Io dhclient: DHCPREQUEST of 192.168.126.128 on eth1 to 192.168.126.254 port 67
May 10 07:40:17 Io dhclient: DHCPACK of 192.168.126.128 from 192.168.126.254
May 10 07:40:17 Io dhclient: can't create /var/lib/dhcp3/dhclient.eth1.leases: No such file or directory
May 10 07:40:17 Io dhclient: bound to 192.168.126.128 -- renewal in 746 seconds.

``` 

A few lines above that in syslog is the following.

```

May 10 07:00:36 Io dhclient: DHCPOFFER of 192.168.126.128 from 192.168.126.254
May 10 07:00:36 Io dhclient: DHCPREQUEST of 192.168.126.128 on eth1 to 255.255.255.255 port 67
May 10 07:00:36 Io dhclient: DHCPACK of 192.168.126.128 from 192.168.126.254
May 10 07:00:37 Io dhclient: can't create /var/lib/dhcp3/dhclient.eth1.leases: No such file or directory
May 10 07:00:37 Io dhclient: bound to 192.168.126.128 -- renewal in 801 seconds.

```

dhcpd.conf looks like this:

```

default-lease-time 6000;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
 authoritative;
 range 192.168.1.2 192.168.1.10;
 option broadcast-address 192.168.1.255;
 option routers 192.168.1.1;
}

```

interfaces look like this:

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 10.0.1.35
        netmask 255.255.255.0
        gateway 10.0.1.1

# The secondary network interface
auto eth1
iface eth1 inet dhcp

```

This is somewhat new to me so I'm not sure what else I may be missing. From the digging around I've been doing, it appears that the isc-dhcp-server has replaced dhcp3, yes? Should I just install dhcp3?

Thanks.

---

### Post by Lars Noodén on 2011-05-10
Does the ip number of the interface you plan to serve DCHP on match the range of ip numbers served up by DHCPd?  It looks like yours don't match.  Are you planning on serving DHCP on Eth0?

(PS. FWIW, I recommend dnsmasq for dhcp)

---

### Post by smslavin on 2011-05-10
This is what I have for /etc/default/isc-dhcp-server

```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```

Shouldn't that tell the DHCP server that I want DHCP on eth1? I'm not sure where it is grabbing the current address.

I'll take a look at dnsmasq. Thanks.

---

### Post by Lars Noodén on 2011-05-10
> **smslavin said:**
> 
Shouldn't that tell the DHCP server that I want DHCP on eth1? I'm not sure where it is grabbing the current address.

It's not grabbing any address, and can't, thus the error messages.

If you are serving DHCP from Eth1 then it needs to have a static IP address that matches the range you are serving.  So if you are serving up 192.168.1.2 through 192.168.1.10, then a static IP of 192.168.1.1 would be appropriate.

---

### Post by smslavin on 2011-05-10
Doh! Totally missed that. Guess I was just staring at it for too long. Thanks. Service is started and handing out address.

---

