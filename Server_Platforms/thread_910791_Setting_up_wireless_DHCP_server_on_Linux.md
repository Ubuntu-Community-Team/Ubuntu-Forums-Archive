---
title: "Setting up wireless DHCP server on Linux"
date: 2008-09-04
forum: Server Platforms
---

### Post by GargoyleMusic on 2008-09-04
My goal is use my Linux laptop as a wireless router. I want to do this for two reasons:

1. I want to learn about routing/networking. As playing with the options for an HTTP server gives insight into how web servers work, I want to get a DHCP server working on my laptop so that I can better understand how those things work.

2. I want to show my dorm roommates the [Upside-Down-Ternet]("http://ex-parrot.com/~pete/upside-down-ternet.html")! 


I have been following the instructions on the above link.

I am running Ubuntu 7.10, have installed dhcpd, but I cannot get the DHCP daemon to run. I  have a LAN connection to the internet on eth0 and my wireless is on eth1.

```

$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:DF:01:1C  
          inet addr:152.7.23.x  Bcast:152.7.23.255  Mask:255.255.254.0
          inet6 addr: fe80::216:36ff:fedf:11c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:390426 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151879 errors:2 dropped:0 overruns:0 carrier:2
          collisions:52563 txqueuelen:1000 
          RX bytes:187974695 (179.2 MB)  TX bytes:27768661 (26.4 MB)

eth1      Link encap:Ethernet  HWaddr 00:19:D2:39:C5:86  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:104950 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 Memory:d6000000-d6000fff 

```

My /etc/dhcpd.conf looks like this:

```

authoritative;

shared-network local {

        subnet 1.1.0.0 netmask 255.255.255.0 {
                range 1.1.0.2 1.1.0.10;
                option routers 1.1.0.1;
                option subnet-mask 255.255.255.0;
                option domain-name "my.domain.com";
                option domain-name-servers 1.1.0.1;
                deny unknown-clients;

                host trusted1 {
                        hardware ethernet  00:19:D2:39:C5:86;
                        fixed-address 1.1.0.5;
                }
                }

        subnet 192.168.0.0 netmask 255.255.255.0 {
                range 192.168.0.2 192.168.0.10;
                option routers 192.168.0.1;
                option subnet-mask 255.255.255.0;
                option domain-name-servers 192.168.0.1;
                allow unknown-clients;

        }
}

```

Additionally, /etc/default/dhcp:

```

jpgoel@pastry:~$ cat /etc/default/dhcp
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```

Finally, when I try to start dhcpd, /var/log/syslog yields this:

```

Sep  4 22:13:45 pastry dhcpd: No subnet declaration for eth1 (0.0.0.0).
Sep  4 22:13:45 pastry dhcpd: Please write a subnet declaration in your dhcpd.conf file for the
Sep  4 22:13:45 pastry dhcpd: network segment to which interface eth1 is attached.
Sep  4 22:13:45 pastry dhcpd: exiting.

```

I will be the first to admit that I do not know exactly what all of the directives in dhcpd.conf do; but I have not found any decent tutorials or documentation that describes how to start a dhcp server on a separate interface than the one that is connected to the internet.

Does anyone have a decent (n00b-friendly) guide? Has anyone gotten the upside-down-ternet to work? Does anyone have any thoughts on where I would be mistaken in my config files?

Thank you!

---

