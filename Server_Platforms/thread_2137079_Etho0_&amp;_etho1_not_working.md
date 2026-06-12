---
title: "Etho0 &amp; etho1 not working"
date: 2013-04-19
forum: Server Platforms
---

### Post by baldurmen on 2013-04-19
Hi,

I'm administrating temporarily my student union's server while we are rebuilding our network. I'm not ultra experience in doing so, but I gey around OK.

Our server used to route the Internet connection from the router to our switches but I can't get the Ethernet ports to work anymore. I bypassed the server by connecting the router directly to one of the switches so we have Internet, but our Xerox 7500 series does not work this way since it needs a printing server.

Here are /ect/network/interfaces & /ect/NetworkManager/nm-system-settings.conf files. Tell me if you need something else. I can only get physical access to the server during the week, so I might take time to answer.

/ect/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255

```

/ect/NetworkManager/nm-system-settings.conf
```

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

NB: I tried to turn ```
 [ifupdown]managed=false 
``` to true. Network Manager then see ifupdown0 & ifupdown1, but still does not connect to Internet.

---

### Post by darkod on 2013-04-19
The interfaces file looks good to me. I don't know about networkmanager since usually you don't use it on a server. I guess maybe that's why managed=false, in effect prohibiting to networkmanager to control the interfaces and leave that to the interfaces file.

Have you tried restarting both the router and the server?

If you run on the server:
ifconfig

does it show eth0 receiving an IP by dhcp? The problem might be that the server is not receiving an IP on the eth0 interface.

It is rare to see a server with dhcp anyway, usually you would use static IPs on all server interfaces.

---

### Post by baldurmen on 2013-04-19
Thanks for the quick answer.

Things are fixed. I rebooted the switch and things went back on... Still, I learned that NetworkManager is not used on servers!

Thanks again,

--
Baldurmen

---

