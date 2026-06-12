---
title: "Constant DNS requests for interface name"
date: 2016-04-24
forum: Server Platforms
---

### Post by Doug S on 2016-04-24
My main test server is an Ubuntu 16.04 Server, with virtualization and a bridge.
Every 5 seconds the computer issues DNS lookup requests for the interface_name.my_domain.com.
I have never been able to determine why it does this, towards the goal of understanding the root issue and then getting rid of it.
Notes: 
 . the same issue occurred back when the server was 14.04 based, albeit with different interface names (p4p1 then eth0), and not for its entire life as a 14.04 server.
 .  The issue started on 2015.05.25 15:57:15, which according to my log book was when I had issues when trying to use non-stock kernels and ended up messing with [predicable network interface names]("http://askubuntu.com/questions/628217/use-of-predictable-network-interface-names-with-alternate-kernels").
 .  I also rebuilt the system from scratch a few days prior, after [a hard disk failure]("http://ubuntuforums.org/showthread.php?t=2275528&page=3&p=13291791#post13291791").
 . The system was rebuilt from scratch for 16.04 devleopment, and no messing with interface names was done.

Does anybody have any idea why it is doing this? Or have suggestions how to investigate further?

More detail:

A tcpdump trace running on my main Ubuntu 16.04 server, router, DNS server at 192.168.111.1 (192.168.111.112 is the problem server):
```
2016-04-24 07:23:12.344324 IP 192.168.111.112.44395 > 192.168.111.1.53: 37754+ A? enp3s0.smythies.com. (37)    [COLOR="#FF0000"]<<< First it tries with a a FQDN[/COLOR]
2016-04-24 07:23:12.344609 IP 192.168.111.1.53 > 192.168.111.112.44395: 37754 NXDomain* 0/1/0 (78)
2016-04-24 07:23:12.344835 IP 192.168.111.112.50240 > 192.168.111.1.53: 30171+ A? enp3s0. (24)   [COLOR="#FF0000"]<<< Then it tries with just the interface name[/COLOR]
2016-04-24 07:23:12.345009 IP 192.168.111.1.53 > 192.168.111.112.50240: 30171 NXDomain 0/1/0 (99)
2016-04-24 07:23:17.345782 IP 192.168.111.112.43203 > 192.168.111.1.53: 60311+ A? enp3s0.smythies.com. (37)   [COLOR="#FF0000"]<<< And again 5 second later, forever[/COLOR]
2016-04-24 07:23:17.345992 IP 192.168.111.1.53 > 192.168.111.112.43203: 60311 NXDomain* 0/1/0 (78)
2016-04-24 07:23:17.346126 IP 192.168.111.112.55171 > 192.168.111.1.53: 15804+ A? enp3s0. (24)
2016-04-24 07:23:17.346314 IP 192.168.111.1.53 > 192.168.111.112.55171: 15804 NXDomain 0/1/0 (99)

```
Interfaces file on 192.168.111.112 (s15.smythies.com):
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface and bridge
auto br0
iface br0 inet dhcp
#iface br0 inet static
#  address 192.168.111.112
#  network 192.168.111.0
#  netmask 255.255.255.0
#  gateway 192.168.111.1
#  broadcast 192.168.111.255
#  dns-search smythies.com
#  dns-nameservers 192.168.111.1
  bridge_ports [COLOR="#FF0000"]enp3s0[/COLOR]
  bridge_fd 9
  bridge_hello 2
  bridge_maxage 12
  bridge_stp off

```And ifconfig:
```
br0       Link encap:Ethernet  HWaddr f4:6d:04:65:2d:8e
          inet addr:192.168.111.112  Bcast:192.168.111.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13876 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1467386 (1.4 MB)  TX bytes:947814 (947.8 KB)

[COLOR="#FF0000"]enp3s0[/COLOR]    Link encap:Ethernet  HWaddr f4:6d:04:65:2d:8e
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1661796 (1.6 MB)  TX bytes:973668 (973.6 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:15968 (15.9 KB)  TX bytes:15968 (15.9 KB)

lxcbr0    Link encap:Ethernet  HWaddr 82:53:ad:95:a5:8b
          inet addr:10.0.3.1  Bcast:0.0.0.0  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

virbr0    Link encap:Ethernet  HWaddr 52:54:00:21:9e:43
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
An example from when the server was 14.04:
```
2015-10-26 07:03:12.612101 IP 192.168.111.112.51280 > 192.168.111.1.53: 20941+ A? eth0.smythies.com. (35)
2015-10-26 07:03:12.612300 IP 192.168.111.1.53 > 192.168.111.112.51280: 20941 NXDomain* 0/1/0 (76)
2015-10-26 07:03:12.612444 IP 192.168.111.112.47742 > 192.168.111.1.53: 64909+ A? eth0. (22)
2015-10-26 07:03:12.612561 IP 192.168.111.1.53 > 192.168.111.112.47742: 64909 NXDomain 0/1/0 (97)
2015-10-26 07:03:17.613099 IP 192.168.111.112.51597 > 192.168.111.1.53: 8379+ A? eth0.smythies.com. (35)
2015-10-26 07:03:17.613310 IP 192.168.111.1.53 > 192.168.111.112.51597: 8379 NXDomain* 0/1/0 (76)
2015-10-26 07:03:17.613453 IP 192.168.111.112.40443 > 192.168.111.1.53: 31449+ A? eth0. (22)
2015-10-26 07:03:17.613571 IP 192.168.111.1.53 > 192.168.111.112.40443: 31449 NXDomain 0/1/0 (97)
2015-10-26 07:03:22.614110 IP 192.168.111.112.54335 > 192.168.111.1.53: 8635+ A? eth0.smythies.com. (35)
```

---

### Post by Graham_Willis on 2016-04-26
Have you tried turning off all the services, including crontab, running on your machine? You mentioned that it's a test server, so I think it's feasible. If that doesn't help, try to manually kill processes which are still running. If these requests doesn't appear then, you win - it'll be just a matter of identifying the exact service which causes this behaviour.

Also, investigation of syslog can reveal some interesting details.

Aha, and I assume that these requests don't show up when the server is running in single user mode?

---

### Post by Doug S on 2016-04-27
Thanks for the reply and the suggestions.

> **Graham_Willis said:**
> Have you tried turning off all the services, including crontab, running on your machine? You mentioned that it's a test server, so I think it's feasible. If that doesn't help, try to manually kill processes which are still running. If these requests doesn't appear then, you win - it'll be just a matter of identifying the exact service which causes this behaviour.I had not tried that. I did. The guilty service is nmbd.service (part of samba). I'll continue investigating with this new knowledge.

> **Graham_Willis said:**
> Aha, and I assume that these requests don't show up when the server is running in single user mode?I never tried that. I actually do not know how to run in "single user mode".

---

### Post by Doug S on 2016-04-27
There were entries in /var/log/samba/log.nmbd```
[2016/04/26 21:44:21.497985,  3, pid=1592, effective(0, 0), real(0, 0)] ../lib/util/util_net.c:256(interpret_string_addr_internal)
  interpret_string_addr_internal: getaddrinfo failed for name enp3s0 (flags 32) [Name or service not known]
[2016/04/26 21:44:21.498054,  2, pid=1592, effective(0, 0), real(0, 0)] ../source3/lib/interface.c:390(interpret_interface)
  interpret_interface: Can't find address for enp3s0
[2016/04/26 21:44:21.498085,  0, pid=1592, effective(0, 0), real(0, 0)] ../source3/lib/interface.c:543(load_interfaces)
  WARNING: no network interfaces found

```I use a bridge. In /etc/samba/smb.conf I changed the interfaces line from this:
```
   interfaces = enp3s0
```To this:```
    interfaces = br0
```And the problem is gone.

---

