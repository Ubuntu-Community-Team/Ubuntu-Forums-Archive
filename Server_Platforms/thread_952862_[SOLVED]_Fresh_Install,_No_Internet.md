---
title: "[SOLVED] Fresh Install, No Internet"
date: 2008-10-19
forum: Server Platforms
---

### Post by TreeFinger on 2008-10-19
Last night I installed ubuntu 8.04 server edition on an extra computer. I plan on using it as a webserver.

I am able to SSH in and SSH out of the box, but from this box I can not reach the internet. 

```

# ping 66.197.194.166
connect: Network is unreachable


# ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.238 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.232 ms

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.232/0.235/0.238/0.003 ms

```

I am thinking this is a firewall problem. Does a firewall come installed default on the server edition? The nameserver is set up in resolv.conf.

The only packages I selected to install during the installation were SSH server and LAMP.


/etc/network/interfaces
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	mtu 1500

```

/etc/resolv.conf
```

# cat /etc/resolv.conf
nameserver 192.168.0.1

```

---

### Post by cariboo on 2008-10-19
Enter your gateway address in your /etc/network/interfaces file. This is what it looks like on my server:

```
auto eth0
iface eth0 inet static
address	192.168.1.200
netmask	255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Jim

---

### Post by TreeFinger on 2008-10-19
> **cariboo907 said:**
> Enter your gateway address in your /etc/network/interfaces file. This is what it looks like on my server:

```
auto eth0
iface eth0 inet static
address	192.168.1.200
netmask	255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Jim


perfect-o ! Thank, you, very much :)

---

