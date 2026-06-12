---
title: "Fail to start webmin"
date: 2006-11-18
forum: Server Platforms
---

### Post by satimis on 2006-11-18
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64

Failed to start the admin page of Webmin with;

[http://localhost:10000](http://localhost:10000)
[https://localhost:10000](https://localhost:10000)
[http://127.0.0.1:10000](http://127.0.0.1:10000)
[https://127.0.0.1:10000](https://127.0.0.1:10000)

on Firefox started as root, saying "can't connect to this site".

$ sudo /etc/init.d/dhcp restart```

Stopping DHCP server: dhcp.
Starting DHCP server: dhcpd.

```

DHCP started already.

$ cat /etc/dhcpd.conf```

#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $

default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "mydomain.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.100;
range 192.168.1.150 192.168.1.200;
}

```

Please help.  TIA


B.R.
satimis

---

