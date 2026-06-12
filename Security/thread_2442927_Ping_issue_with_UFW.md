---
title: "Ping issue with UFW"
date: 2020-05-09
forum: Security
---

### Post by gilibz on 2020-05-09
Hey guys,
Just got my fresh installment of ubuntu 20.04, and I enabled ufw. 
When i try to ping google , I dont see IPV4 address.
[COLOR=#1A1A1B][FONT=&amp]superman@superman-forever:~$ ping [google.com]("https://google.com/")[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]PING [google.com]("https://google.com/")([kul08s10-in-x0e.1e100.net]("https://kul08s10-in-x0e.1e100.net/") (2404:6800:4001:80e::200e)) 56 data bytes[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]64 bytes from [kul08s10-in-x0e.1e100.net]("https://kul08s10-in-x0e.1e100.net/") (2404:6800:4001:80e::200e): icmp_seq=1 ttl=53 time=37.0 ms[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]64 bytes from [kul08s10-in-x0e.1e100.net]("https://kul08s10-in-x0e.1e100.net/") (2404:6800:4001:80e::200e): icmp_seq=2 ttl=53 time=37.8 ms[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]64 bytes from [kul08s10-in-x0e.1e100.net]("https://kul08s10-in-x0e.1e100.net/") (2404:6800:4001:80e::200e): icmp_seq=3 ttl=53 time=38.0 ms

So when I used ping -4 google.com I got error: Ping:sendmsg: Opreation not permitted
After that I notice if i disable ufw the ping -4 is working well. First- why by default the pinging command points to IPV6 and not ipv4? is this normal ? also - how I can allow the ping working on ufw ? 
Thanks in advance,

[/FONT][/COLOR]

---

### Post by EuclideanCoffee on 2020-05-09
This doesn't happen for me. I'm able to use IPv4 and IPv6.

Could you please show us your ufw profile?

```

$ sudo ufw status verbose

```

---

### Post by gilibz on 2020-05-09
Sure.

Status: active
Logging: on (full)
Default: deny (incoming), deny (outgoing), disabled (routed)
New profiles: skip


To Action From
-- ------ ----
80/tcp ALLOW OUT Anywhere on wlp2s0 # allow HTTP on wlp2s0
443/tcp ALLOW OUT Anywhere on wlp2s0 # allow HTTPS on wlp2s0
631 ALLOW OUT 192.168.1.0/24
1.1.1.1 53/udp ALLOW OUT Anywhere on wlp2s0 # allow DNS on wlp2s0
80/tcp (v6) ALLOW OUT Anywhere (v6) on wlp2s0 # allow HTTP on wlp2s0
443/tcp (v6) ALLOW OUT Anywhere (v6) on wlp2s0 # allow HTTPS on wlp2s0

---

### Post by TheFu on 2020-05-09
```
Default: deny (incoming), deny (outgoing), disabled (routed)
```
There's the issue.  It blocks ... all inbound and all outbound by default.  I doubt that is really what you want.  The internet has so many more protocols than what you have allowed.  Also, HTTP and HTTPS happen on thousands of other ports than 80 and 443.

Usually, home users would allow all outbound and only have a default deny for inbound.  Corporations would block all internet in/out, but also have a proxy server setup for outbound access which isn't blocked.

---

### Post by gilibz on 2020-05-09
Well, I dont have any issues with my internet with this setup, and I used it for maximum security to avoid any trojans. Any idea how to just unblock the ping for ipv4 issue ?

---

### Post by TheFu on 2020-05-09
The ufw manpage has this about the default rules and ICMP:
```
       - ACCEPT certain icmp  packets  (INPUT  and  FORWARD):  destination-unreachable,
       source-quench, time-exceeded, parameter-problem, and echo-request for IPv4. des&#8208;
       tination-unreachable,  packet-too-big,  time-exceeded,  parameter-problem,   and
       echo-request for IPv6.

       - ACCEPT icmpv6 packets for stateless autoconfiguration (INPUT)
```
I don't know what to make of that, except to check the resulting iptables rules for what actually got put into the rules on the machine.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) has a section about ICMP too.

---

### Post by EuclideanCoffee on 2020-05-11
Have you tried this solution from an older thread?

[https://ubuntuforums.org/showthread.php?t=1801151](https://ubuntuforums.org/showthread.php?t=1801151)

It requires iptables, which is what ufw modifies.

---

