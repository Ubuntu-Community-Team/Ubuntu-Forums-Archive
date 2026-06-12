---
title: "Netplan breaks with multiple interfaces"
date: 2018-11-27
forum: Server Platforms
---

### Post by xubuntu84 on 2018-11-27
I hope someone can convince me to stick with netplan and not blow it away for ifupdown...

I have a server with 3 network interfaces: ens160, ens192, and ens224:

```

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens160: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ... brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.124/25 brd 192.168.0.127 scope global ens160
       valid_lft forever preferred_lft forever
    inet6 .../64 scope link
       valid_lft forever preferred_lft forever
3: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ... brd ff:ff:ff:ff:ff:ff
    inet 172.16.1.250/24 brd 172.16.1.255 scope global ens192
       valid_lft forever preferred_lft forever
    inet6 .../64 scope link
       valid_lft forever preferred_lft forever
4: ens224: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ... brd ff:ff:ff:ff:ff:ff

```


When I comment out the ens192 interface in 01-netcfg.yaml, and reboot the machine (because, [FONT=courier new]netplan apply[/FONT] doesn't cause a change??), I can ping the machine on the ens160 interface. However, with ens192 configured, reboot, I cannot ping the machine. On the machine, I *can* ping google, etc.

Here's my yaml:
```

network:
  version: 2
#  renderer: networkd
  ethernets:
    ens160:
      addresses:
      - 192.168.0.124/25
#      dhcp4: no
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
#    ens192:
#      addresses:
#      - 172.16.1.250/24
#      gateway4: 172.16.1.1
#    ens224:
#      addresses:
#      - 10.55.200.33/16
#      gateway4: 10.55.200.1

```

I've tried with [FONT=courier new]renderer: networkd[/FONT] commented and uncommented, doesn't make a difference. Same story with [FONT=courier new]dhcp4: no[/FONT]

When I generate the netplan:
```

user@server:~$ sudo netplan --debug generate
DEBUG:command generate: running ['/lib/netplan/generate']
** (generate:2330): DEBUG: 21:47:57.476: Processing input file /etc/netplan/01-netcfg.yaml..
** (generate:2330): DEBUG: 21:47:57.476: starting new processing pass
** (generate:2330): DEBUG: 21:47:57.476: ens192: setting default backend to 1
** (generate:2330): DEBUG: 21:47:57.476: ens160: setting default backend to 1
** (generate:2330): DEBUG: 21:47:57.476: Generating output files..
** (generate:2330): DEBUG: 21:47:57.477: NetworkManager: definition ens192 is not for us (backend 1)
** (generate:2330): DEBUG: 21:47:57.477: NetworkManager: definition ens160 is not for us (backend 1)

```

And again, after I comment out the ens192 section, netplan generate, netplan apply, my pings continue until I reboot, at which point networking from the outside in starts working. The opposite is true: if I uncomment ens192, netplan apply, I can still ping until a reboot.

I'm pretty sure my indentation is correct, but I'm unsure if the '-' for addresses should be nested 2 more spaces to the right. Speaking of that, the reason why I'm not using addresses: [<ip>/<cidr>] is because I have 13 IPs in the 172.16.0.0/16 that I need to assign to the ens192 interface.

---

### Post by wildmanne39 on 2018-11-27
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by darkod on 2018-11-27
1. Is you netplan content pasted correctly in that CODE box? Does it look on screen as it does in reality? I am asking because using spaces is VERY important in netplan yaml. And spaces, not tab key.
If it really looks like on screen here on the forum, the layout is not correct. For example the interface names do not have the same indent, and they should.

2. Why are you using more than one gateway? You should use only one, otherwise you might get inconsistent results. Maybe that's why it works with ens192 commented out.

---

### Post by xubuntu84 on 2018-11-27
> **darkod said:**
> 1. Is you netplan content pasted correctly in that CODE box? Does it look on screen as it does in reality? I am asking because using spaces is VERY important in netplan yaml. And spaces, not tab key.
If it really looks like on screen here on the forum, the layout is not correct. For example the interface names do not have the same indent, and they should.

2. Why are you using more than one gateway? You should use only one, otherwise you might get inconsistent results. Maybe that's why it works with ens192 commented out.


Thanks darkod.

Yes, the pasted code is exactly what I am using, with the exception that the 192.168.0.124/25 and the associated gateway are actually  public IPs that I've changed for sake of the forum. I use spaces (not tabs) to indent the lines. Here's the yaml with ens192 uncommented. Each adapter has 4 spaces before the first letter:

```

network:
  version: 2
#  renderer: networkd
  ethernets:
    ens160:
      addresses:
      - 192.168.0.124/25
#      dhcp4: no
      gateway4: 192.168.0.1
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]
    ens192:
      addresses:
      - 172.16.1.250/24
      gateway4: 172.16.1.1
#    ens224:
#      addresses:
#      - 10.55.200.33/16
#      gateway4: 10.55.200.1

```

I'm using 172.16.1.1 as the gateway for that subnet because that's the router for 172.16.0.0/16. The 192.168.0.1 gateway is a different router that routes to the Internet (for system updates, etc.). ens192 and ens224 are private ranges that shouldn't be accessible on the 192.168.0.0/24 network.

I'll try using a different gateway tomorrow to see what that gets me, but I was hoping for a different solution.

---

### Post by xubuntu84 on 2018-11-28
Consider me schooled... it worked with having the same gateway on all 3 adapters, and I can ping inside the private networks from the machine. But, why? Why won't the machine respond to pings with an internal router set as the gateway for the two private network adapters? And since I apparently don't understand networking anymore, does this run the risk of routing public traffic to my private networks? IE, could someone potentially hop on 10.55.200.0/16 via 192.168.0.1?

---

### Post by darkod on 2018-11-28
If those private ranges need to talk only to devices in the same range/submet, you dont even need to specify gw.
For example, any ip in /24 subnet can talk to any device in that subnet.
Gateways come into play for routing traffic cross-network.

---

### Post by xubuntu84 on 2018-11-28
Ah, that makes sense! I had assumed gateway was a required component. Thank you very much for your insight.

---

