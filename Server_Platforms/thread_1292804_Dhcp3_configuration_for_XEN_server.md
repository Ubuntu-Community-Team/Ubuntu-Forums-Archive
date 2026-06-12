---
title: "Dhcp3 configuration for XEN server"
date: 2009-10-16
forum: Server Platforms
---

### Post by globemast on 2009-10-16
Hi all,

I am running an Ubuntu 9.04 Server (32-bit) and i have installed the XEN kernel in order to run a XEN Virtual Appliance (VA).

I want to setup a DHCP server in order to serve the VAs. The host machine is part of a server farm and uses a static IP address. 

So far i have created a virtual interface (eth0:1) so as not to mess with the hardware (eth0) interface and cause any problems in the cluster.

However I'm struggling in getting the DHCP server running. I'm attaching below the dhcpd.conf , dhcp3-server files and syslog.

Any help would be highly appreciated...

Thanks.

```

#
# DHCP Server Configuration file.
#   see /usr/share/doc/dhcp*/dhcpd.conf.sample  
#

# Required for dhcp 3.0+ / Red Hat 8.0+
ddns-update-style interim;                                   
ignore client-updates;

default-lease-time 259200;
max-lease-time 518400;

subnet 192.168.1.0 netmask 255.255.255.0 {
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.1.255;
	option routers	192.168.1.1;
	option domain-name "rubisva.cy";
	range 192.168.1.50 192.168.1.100;
	option domain-name-servers 194.42.16.11;
	#option domain-name-servers 192.168.1.1;
}
```


```
#
# DHCP Server Configuration file.
#   see /usr/share/doc/dhcp*/dhcpd.conf.sample  
#

# Required for dhcp 3.0+ / Red Hat 8.0+
ddns-update-style interim;                                   
ignore client-updates;

default-lease-time 259200;
max-lease-time 518400;

subnet 192.168.1.0 netmask 255.255.255.0 {
	option subnet-mask 255.255.255.0;
	option broadcast-address 192.168.1.255;
	option routers	192.168.1.1;
	option domain-name "rubisva.cy";
	range 192.168.1.50 192.168.1.100;
	option domain-name-servers 194.42.16.11;
	#option domain-name-servers 192.168.1.1;
}
```

```

Oct 16 16:50:56 vm101 dhcpd: No subnet declaration for eth0:1 (0.0.0.0).
Oct 16 16:50:56 vm101 dhcpd: ** Ignoring requests on eth0:1.  If this is not what
Oct 16 16:50:56 vm101 dhcpd:    you want, please write a subnet declaration
Oct 16 16:50:56 vm101 dhcpd:    in your dhcpd.conf file for the network segment
Oct 16 16:50:56 vm101 dhcpd:    to which interface eth0:1 is attached. **
```

---

### Post by BQAggie2006 on 2009-10-16
Could you post your eth0:1 configuration?

---

### Post by globemast on 2009-10-19
Hi Thanks for the reply.

```

auto eth0:1
iface eth0:1 inet static
        address 192.168.1.123
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 194.x.x.x
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 194.x.x.x
        dns-search mydomain.com


```

---

