---
title: "NAT/IP Masquerading"
date: 2006-03-06
forum: Server Platforms
---

### Post by Zelut on 2006-03-06
I have been trying to setup NAT on a machine but it doesn't seem to be working.  I'm hoping someone here can give me some insight.  Below are the commands I'm using & also my network setup.  Thanks

Modem > Wireless Router
[LIST]
[*]PC 1 wlan0 (wireless desktop) > eth0 > wired hub > PC 2 + additional
[*]PC 3, PC 4 eth0 (wired servers at router)
[*]PC 5, PC 6 wlan0 (wireless notebooks)
[/LIST]
Basically I want to create a sub-net as a branch of PC 1's wlan0 connection (as wiring that part of the office isn't possible.)  In using the commands below I'm not sure that eth0 is sharing any connection from wlan0 and PC 2 also does not have a connection.

> iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

Thanks in advance

---

### Post by Andruk Tatum on 2007-07-26
You have either moved on or found an answer to your question.  But I'll give it to you anyway:

The Ubuntu Server Guide (found [here]("http://doc.ubuntu.com/ubuntu/serverguide/C/")) is fairly helpful in explaining the command line was to do things.  Mostly useful for...server admins.

Other than that, you should be able to do it through a GUI firewall tool (Firestarter) sounded good.

---

### Post by yota on 2007-07-26
> **Zelut said:**
> 
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward


You should use eth0 as the outgoing interface, like this
```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

since, from 'man iptables'
> 
-o, --out-interface [!] name
              Name of an interface via which a packet is going to be sent (for
              packets entering the FORWARD, OUTPUT  and  POSTROUTING  chains).
              When  the  "!"  argument  is used before the interface name, the
              sense is inverted.  If the interface name ends in  a  "+",  then
              any  interface  which begins with this name will match.  If this
              option is omitted, any interface name will match.


Hope this helps!

---

