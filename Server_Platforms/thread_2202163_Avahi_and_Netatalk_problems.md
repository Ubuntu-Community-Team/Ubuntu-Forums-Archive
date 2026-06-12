---
title: "Avahi and Netatalk problems"
date: 2014-01-27
forum: Server Platforms
---

### Post by radoslaw-ejsmont on 2014-01-27
Hi,

I am running a small home server under Ubuntu 12.04. After a reboot several days ago the mDNS on my home server stopped working. To be precise - it works for some time (1-5 minutes) and stops. I have seen replies to similar questions on several forums, however all that people did suggest was disabling the firewall. I am using shorewall, and traffic between my local network and the server is wide open. Moreover, the problem persist even after disabling shorewall and restarting netatalk and avahi.

More or less it looks like this from my laptop:

```

$ date; ping placebo.local
Mon 27 Jan 2014 23:36:20 CET
ping: cannot resolve placebo.local: Unknown host

$ date; ssh -A rejsmont@192.168.0.5 -C sudo service avahi-daemon restart
Mon 27 Jan 2014 23:37:15 CET
avahi-daemon stop/waiting
avahi-daemon start/running, process 20518

$ date; ping placebo.local
Mon 27 Jan 2014 23:37:31 CET
PING placebo.local (192.168.0.5): 56 data bytes
64 bytes from 192.168.0.5: icmp_seq=0 ttl=64 time=0.320 ms
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=0.316 ms
64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=0.327 ms
^C
--- placebo.local ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 0.316/0.321/0.327/0.005 ms

$ date; ping placebo.local
Mon 27 Jan 2014 23:40:08 CET
ping: cannot resolve placebo.local: Unknown host

```

I can connect to afpd when using server's IP address. mDNS connection does not work. Same applies to CUPS.

The current versions I have installed are:

```

$ uname -a
Linux placebo 3.2.0-58-generic-pae #88-Ubuntu SMP Tue Dec 3 18:00:02 UTC 2013 i686 i686 i386 GNU/Linux
$ avahi-daemon --version
avahi-daemon 0.6.30
$ afpd -v
afpd 2.2.1 - Apple Filing Protocol (AFP) daemon of Netatalk
$ shorewall version
4.4.26.1

```

From what I have read around the issue can have two origins:

1) something wrong with avahi - misconfiguration? - bug?
2) something wrong with network (with focus on multicast) - I have been thinking if I should enable any sysctl options that are not enabled by default? Why did it stop working after reboot? Kernel changes? I did not monitor if kernel version has changed after reboot.

To be honest I ran out of ideas after a week of trying and failing.

I am happy to provide avahi config, wireshark dumps, shore wall dumps or whatever can help in solving my issue.


Thanks in advance for help!

---

### Post by radoslaw-ejsmont on 2014-01-27
Just a bit of research:

after enabling broadcast ping replies

```

echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

```

I am able to receive ping reply from the server (192.168.0.5) when pinging 224.0.0.1 from my laptop (192.168.0.193):

```

$ping -224.0.0.1
PING 224.0.0.1 (224.0.0.1): 56 data bytes
64 bytes from 192.168.0.193: icmp_seq=0 ttl=64 time=0.124 ms
64 bytes from 192.168.0.5: icmp_seq=0 ttl=64 time=0.359 ms
64 bytes from 192.168.0.35: icmp_seq=0 ttl=64 time=7.294 ms
64 bytes from 192.168.0.195: icmp_seq=0 ttl=64 time=94.024 ms
64 bytes from 192.168.0.198: icmp_seq=0 ttl=64 time=96.296 ms
64 bytes from 192.168.0.192: icmp_seq=0 ttl=64 time=105.790 ms
64 bytes from 192.168.0.196: icmp_seq=0 ttl=64 time=105.800 ms


```

The weird thing is that both server and laptop are supposed to belong to the same multicast group:

Laptop:
```

IPv4 Multicast Group Memberships
Group               	Link-layer Address	Netif
224.0.0.251         	1:0:5e:0:0:fb   	en0
224.0.0.1           	1:0:5e:0:0:1    	en0

```

Server:
```

IPv6/IPv4 Group Memberships
Interface       RefCnt Group
--------------- ------ ---------------------
eth0            1      224.0.0.251
eth0            1      all-systems.mcast.net

```

The ping from server to 224.0.0.251 group:
```

$ ping 224.0.0.251
PING 224.0.0.251 (224.0.0.251) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_req=1 ttl=64 time=0.155 ms
64 bytes from 192.168.0.35: icmp_req=1 ttl=64 time=11.7 ms (DUP!)
64 bytes from 192.168.0.196: icmp_req=1 ttl=64 time=111 ms (DUP!)
64 bytes from 192.168.0.192: icmp_req=1 ttl=64 time=112 ms (DUP!)
64 bytes from 192.168.0.198: icmp_req=1 ttl=64 time=164 ms (DUP!)

```

The ping from laptop to 224.0.0.251 group:
```

$ ping 224.0.0.251
PING 224.0.0.251 (224.0.0.251): 56 data bytes
64 bytes from 192.168.0.193: icmp_seq=0 ttl=64 time=0.095 ms
64 bytes from 192.168.0.35: icmp_seq=0 ttl=64 time=4.366 ms
64 bytes from 192.168.0.195: icmp_seq=0 ttl=64 time=90.575 ms
64 bytes from 192.168.0.192: icmp_seq=0 ttl=64 time=108.418 ms
64 bytes from 192.168.0.196: icmp_seq=0 ttl=64 time=108.700 ms
64 bytes from 192.168.0.198: icmp_seq=0 ttl=64 time=117.418 ms

```

It seems that laptop and server do not recognise each other within 224.0.0.251 group.

Anyone can make sense out of this?

---

### Post by radoslaw-ejsmont on 2014-01-27
Some more tests:

When using jgroups for testing ([http://www.linuxproblems.org/wiki/How_to_check_Multicasting](http://www.linuxproblems.org/wiki/How_to_check_Multicasting)) I see the following

[TABLE="width: 500"]
[TR]
[TD]Sender[/TD]
[TD]Receiver[/TD]
[TD]Result[/TD]
[/TR]
[TR]
[TD]laptop[/TD]
[TD]server[/TD]
[TD]only first message received - following messages ignored[/TD]
[/TR]
[TR]
[TD]server[/TD]
[TD]laptop[/TD]
[TD]all messages received correctly[/TD]
[/TR]
[/TABLE]

WTF?

---

### Post by mörgæs on 2014-01-28
Moving to the server forum, hoping someone there can help you.

---

