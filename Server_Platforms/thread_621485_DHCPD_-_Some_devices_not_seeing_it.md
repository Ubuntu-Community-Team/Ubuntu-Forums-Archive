---
title: "DHCPD - Some devices not seeing it"
date: 2007-11-23
forum: Server Platforms
---

### Post by quietas on 2007-11-23
Howdy folks, here's a bit of a kicker. I had an old Debian (ie 3.0) box that sat at one of my company's locations for who knows how long. It basically worked and did almost nothing, thus it lasted a long time.

We have a direct network connection (via telco) from our main location to the smaller office. The small office is on it's own subnet and the Telco's router is the gateway we use to point at our main network. The DHCP box just sat there and gave out IP/DNS/Gateway info.

I swapped the old Debian box which just went through major hardware failure and inserted a newer (still old hardware) Ubuntu 7.10 server in it's place. Setup for dhcpd.conf, interfaces, and resolv.conf was easy as copying the pertinent data. It works fine on all the computers.

The catch is that the NEC DtermIP VOIP phones will not see the DHCP server. Any ideas?

192.168.13.X = main network
192.168.60.X = small office network

/etc/dhcpd.conf
```

option domain-name "domain.com";
option domain-name-servers 192.168.13.5,192.168.13.10;

option subnet-mask 255.255.255.224;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.60.0 netmask 255.255.255.0 {
  range 192.168.60.100 192.168.60.245;
  option broadcast-address 192.168.60.255;
  option routers 192.168.60.1;
}

```

/etc/network/interfaces
```

iface eth0 inet static
        address 192.168.60.12
        netmask 255.255.255.0
        network 192.168.60.0
        broadcast 192.168.60.255
        gateway 192.168.60.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.13.5 192.168.13.10
        dns-search domain.com

```

/etc/resolv.conf
```

search domain.com
nameserver 192.168.13.5
nameserver 192.168.13.10

```

---

