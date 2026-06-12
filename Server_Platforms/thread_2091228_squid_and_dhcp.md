---
title: "squid and dhcp"
date: 2012-12-04
forum: Server Platforms
---

### Post by kanjah on 2012-12-04
hi guyz, am a newbie of both ubuntu and squid3.... i have installed ubuntu server 12 with 2 NIC, for WAN & LAN and squid3, i dnt know how to configure the LAN to dish out dhcp i.p and connect transparently to my clients. The squid.conf has 
http_port 3128 transparent.
i have to configure their browser manually in-order to connect to squid,
can anyone help me?
thanks

---

### Post by papibe on 2012-12-04
Hi kanjah.

Could you explain a little but about your network topology? That is, how your devices are connected to each other?

Who is the DHCP server both in the WAN and the LAN? Is it the same Squid server?

Could you post the result of these commands?
```
cat /etc/resolv.conf

cat /etc/network/interfaces

cat /proc/sys/net/ipv4/ip_forward

route -n
```
Regards.

---

### Post by SeijiSensei on 2012-12-05
Didn't we just have this discussion in [this thread](http://ubuntuforums.org/showthread.php?t=2089221)?  Didn't you say there that adding the iptables rule I suggested fixed this problem?  So why are you asking the same thing again here?

---

### Post by kanjah on 2012-12-05
thanks for the reply
etc/resolve.conf
nameserver 91.42.48.48
nameserver 91.42.49.49


etc/network/interface
auto eth0
iface eth0 static
address 192.168.10.235
netmask 255.255.255.0
broadcastn192.168.10.225
gateway 192.168.10.1

auto eth1
iface eth1 inet static
address 198.168.1.2
netmask 255.255.255.0
broadcast 192.168.1.255

proc/sys/net/ipv4/ip_forward is empty

---

### Post by kanjah on 2012-12-05
i did what you adviced and it worked and thankd you for it, now
 am using a wireless router to connect my clients, they cnt connect to squid, but if i connect one node to the lan it works well

---

