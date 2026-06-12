---
title: "dhcp bridge"
date: 2008-01-18
forum: Server Platforms
---

### Post by cdenley on 2008-01-18
I'm trying to setup a bridge with a dhcp server. I'm using gutsy. The client machines seems to have problems when the server has a bridge set up for my two nic's. If I remove the bridge, then it works fine. I looked at the packets sent/received on the client, and the server is sending the client a dhcp offer. However, the client just keeps sending another request, saying it's ip is still 0.0.0.0.  I compared the packets with a successful dhcp session, and don't see any difference. If I swap network cables on the two bridged devices, then it will work. However, if the machine is rebooted, I will need to swap the cables back again.

sudo iptables -L & sudo iptables -t nat -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

/etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto br0
iface br0 inet static
        bridge_ports eth0 eth1
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers xxx.xxx.xxx.xxx

```

/etc/dhcp3/dhcpd.conf
```

ddns-update-style none;
authoritative;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
   range 192.168.0.135 192.168.0.235;
   option domain-name-servers xxx.xxx.xxx.xxx,xxx.xxx.xxx.xxx;
   option routers 192.168.0.1;
   option broadcast-address 192.168.0.255;
}

```

---

