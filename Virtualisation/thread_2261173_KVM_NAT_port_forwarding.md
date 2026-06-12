---
title: "KVM NAT port forwarding"
date: 2015-01-16
forum: Virtualisation
---

### Post by Roswebnet on 2015-01-16
Hello everyone,

I would like to publish guests services (http, ssh and etcetera) to the outside world through NAT. I followed many tutorials and I have following rules in iptables:
```

iptables -t nat -I PREROUTING -p tcp -d x.x.104.49 --dport 22 -j DNAT --to-destination 192.168.122.20:22
iptables -I FORWARD -m state -d x.x.104.49/27 --state NEW,RELATED,ESTABLISHED -j ACCEPT
iptables -t nat -I PREROUTING -p tcp --source -d 192.168.122.0/24 -j ACCEPT

```

I save it with this:
```

service iptables-persistent save

```

But still, I cannot access guest en services.

My network settings:
```

em1       Link encap:Ethernet  HWaddr b8:ac:6f:8b:7d:49
          inet addr:x.x.104.49  Bcast:x.x.104.63  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3631264 (3.6 MB)  TX bytes:3491706 (3.4 MB)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1616262 (1.6 MB)  TX bytes:1616262 (1.6 MB)
virbr0    Link encap:Ethernet  HWaddr fe:54:00:51:b2:fe
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5057 (5.0 KB)  TX bytes:5749 (5.7 KB)
vnet0     Link encap:Ethernet  HWaddr fe:54:00:51:b2:fe
          inet6 addr: fe80::fc54:ff:fe51:b2fe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:5701 (5.7 KB)  TX bytes:174513 (174.5 KB)


```

The IP forwarding is enabled in sysctl.conf
```

net.ipv4.ip_forward = 1

```
What I am doing wrong?

Thank you.

---

### Post by TheFu on 2015-01-17
Please explain what you are trying to accomplish, clearly, with details.  It is not obvious to me.

---

### Post by The Cog on 2015-01-17
I would use tcpdump to verify whether the packets are being translated and forwarded correctly.
But I suspect you have forgotten to enable IP forwarding: [http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/](http://www.ducea.com/2006/08/01/how-to-enable-ip-forwarding-in-linux/)

You may also have to either add a route to the 192.168.122.20 machine so it knows where to forward its reply packets (via 192.168.122.1) or enable masquerading so it thinks the caller is your local 192.168.122.1 box.

---

### Post by Roswebnet on 2015-01-17
@ [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685") the first post is updated.

@ [**[COLOR=#c61919][B]The Cog**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=437760") I have this (HOST) routes in my table:
```

 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         x.x.104.33  0.0.0.0         UG    0      0        0 em1
x.x.104.32  0.0.0.0         255.255.255.224 U     0      0        0 em1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

```

Moreover, from host I can access the guest services (browsing website on guest through ssh tunnel connected to the host) , but incoming connections from em1 not.
Thank you.

---

### Post by Doug S on 2015-01-18
Try this (I have only dealt with port 22 in this example. If it works add other ports as desired):```
iptables -t nat -A PREROUTING -p tcp -i em1 --dport 22 -j DNAT --to-destination 192.168.122.20:22

# No FORWARD rules are needed if the default policy is ACCEPT and there is no generic DROP

iptables -A FORWARD -i em1 -o virbr0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i virbr0 -o em1 -j ACCEPT
iptables -A FORWARD -i em1 -o virbr0 -p tcp --dport 22 -d 192.168.122.20 -m state --state NEW -j ACCEPT
iptables -A FORWARD -j DROP

iptables -t nat -A POSTROUTING -o em1 -j SNAT --to x.x.104.49

# Note: instead of SNAT you could do this, particulary if your external IP is not always x.x.104.49:

iptables -t nat -A POSTROUTING -o em1 -j MASQUERADE
```where I have virbr0, if you have troubles try vnet0 instead.

---

### Post by Roswebnet on 2015-01-18
I solved it! :) Cost me couple of days...

The network topology looks like this:
```

Internet---------[Virtual Host Server]
WAN------------[[em1|virbr0]-------------LAN]
x.x.104.49-------[[em1|virbr0]-------------192.168.122.0/24]

```

I like the abstraction of packet flow of the IPtables provided by *Jan Engelhardt*:

[ATTACH=CONFIG]259347[/ATTACH]

Therefore, the simple investigation of image above, manual and some internet sources could pretty easy lead to this final rule:

```

iptables -t nat -I PREROUTING -p tcp -d x.x.104.49 --dport 22 -j DNAT --to-destination 192.168.122.20:22
iptables -I FORWARD -m state -d 192.168.122.20/24 --state NEW,RELATED,ESTABLISHED -j ACCEPT

```

If something does not work to delete existing rules from every iptables table, execute the following commands:
```

iptables -X
iptables -F
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

```

To reset iptables rules to original libvirt rules set:
```
service libvirt-bin restart
```

The result will looks like this:
```

# Generated by iptables-save v1.4.21 on Sun Jan 18 23:25:54 2015
*mangle
:PREROUTING ACCEPT [272:19236]
:INPUT ACCEPT [92:12036]
:FORWARD ACCEPT [179:7160]
:OUTPUT ACCEPT [76:13256]
:POSTROUTING ACCEPT [255:20416]
-A POSTROUTING -o virbr0 -p udp -m udp --dport 68 -j CHECKSUM --checksum-fill
COMMIT
# Completed on Sun Jan 18 23:25:54 2015
# Generated by iptables-save v1.4.21 on Sun Jan 18 23:25:54 2015
*nat
:PREROUTING ACCEPT [2:80]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [4:240]
:POSTROUTING ACCEPT [6:320]
-A POSTROUTING -s 192.168.122.0/24 -d 224.0.0.0/24 -j RETURN
-A POSTROUTING -s 192.168.122.0/24 -d 255.255.255.255/32 -j RETURN
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p tcp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -p udp -j MASQUERADE --to-ports 1024-65535
-A POSTROUTING -s 192.168.122.0/24 ! -d 192.168.122.0/24 -j MASQUERADE
COMMIT
# Completed on Sun Jan 18 23:25:54 2015
# Generated by iptables-save v1.4.21 on Sun Jan 18 23:25:54 2015
*filter
:INPUT ACCEPT [92:12036]
:FORWARD ACCEPT [179:7160]
:OUTPUT ACCEPT [76:13256]
-A INPUT -i virbr0 -p udp -m udp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 53 -j ACCEPT
-A INPUT -i virbr0 -p udp -m udp --dport 67 -j ACCEPT
-A INPUT -i virbr0 -p tcp -m tcp --dport 67 -j ACCEPT
-A FORWARD -d 192.168.122.0/24 -o virbr0 -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -s 192.168.122.0/24 -i virbr0 -j ACCEPT
-A FORWARD -i virbr0 -o virbr0 -j ACCEPT
-A FORWARD -o virbr0 -j REJECT --reject-with icmp-port-unreachable
-A FORWARD -i virbr0 -j REJECT --reject-with icmp-port-unreachable
-A OUTPUT -o virbr0 -p udp -m udp --dport 68 -j ACCEPT
COMMIT
# Completed on Sun Jan 18 23:25:54 2015

```

Save rules:
```
iptables-save > /etc/iptables/rules.v4
```
or:
```
service iptables-persistent save
```

Sources:
[http://www.bctes.com/nat-linux-iptables.html](http://www.bctes.com/nat-linux-iptables.html)
[http://www.atrixnet.com/red-hat-libvirt-kvm-iptables-what-to-do-when-your-kvm-network-stops-working/](http://www.atrixnet.com/red-hat-libvirt-kvm-iptables-what-to-do-when-your-kvm-network-stops-working/)
[http://serverfault.com/questions/170079/forwarding-ports-to-guests-in-libvirt-kvm/](http://serverfault.com/questions/170079/forwarding-ports-to-guests-in-libvirt-kvm/)

---

