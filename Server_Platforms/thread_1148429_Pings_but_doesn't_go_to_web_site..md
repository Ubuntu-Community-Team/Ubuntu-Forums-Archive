---
title: "Pings but doesn't go to web site."
date: 2009-05-04
forum: Server Platforms
---

### Post by TCarr on 2009-05-04
I'm at a loss here. I have Ubuntu 8.04 server running in VMWare Server 2.0 running in Windows Vista Home Premium.

I have it set up for virtual hosts, and I have it set up in /etc/network/interfaces for Static IP (I'm not on a static IP service, but just want to use it inside my wireless home network with Linksys wireless router):

/etc/network/interfaces:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.100.135
netmask 255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255
gateway 192.168.100.2

```

My /etc/hosts file looks something like this:

```

127.0.0.1       localhost
#127.0.1.1      myserver.localdomain      myserver
192.168.100.135 myserver.localdomain      myserver

```

Then some IPV6 stuffs.

My /etc/resolv.conf looks like this:
```

search localdomain
nameserver 192.168.100.2

```

Ok, I can ping it in a DOS window in Windows:

```

Pinging myserver.localdomain [208.69.36.132] with 32 bytes of data:
Reply from 208.69.36.132: bytes=32 time=38ms TTL=57
Reply from 208.69.36.132: bytes=32 time=151ms TTL=57
Reply from 208.69.36.132: bytes=32 time=35ms TTL=57
Reply from 208.69.36.132: bytes=32 time=37ms TTL=57

Ping statistics for 208.69.36.132:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 35ms, Maximum = 151ms, Average = 65ms

```

I have my router set up to use OpenDNS so it looks like it's using that in Windows. However, if I ping it from the Ubuntu Server I get this:

```

PING myserver.localdomain (192.168.100.135) 56(84) bytes of data.
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=1 ttl=64 time=3.88 ms
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=2 ttl=64 time=0.076 ms
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=3 ttl=64 time=0.046 ms
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=4 ttl=64 time=0.073 ms
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=5 ttl=64 time=0.077 ms
64 bytes from myserver.localdomain (192.168.100.135): icmp_seq=6 ttl=64 time=0.041 ms

```

So it works from only within the Ubuntu Server.

If I go in Firefox in Windows to try to access the info on the web server in Ubuntu, I get a search page on OpenDNS.com instead!

I tried [http://myserver.localdomain](http://myserver.localdomain) and [http://myserver](http://myserver) but I just get the OpenDNS.com search page.

What do I do to fix it so I can get to the server on Ubuntu Guest OS from the Windows host OS?

---

