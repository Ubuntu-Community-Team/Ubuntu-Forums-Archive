---
title: "UEC guests have no connectivity to outside of cloud"
date: 2010-12-14
forum: Ubuntu Cloud and Juju
---

### Post by justindossey on 2010-12-14
I feel bad for asking this, but I have searched around and haven't found anything about this question on the net yet.

I have a new UEC setup.   It's the "at least 2 machines" setup, where one machine serves as everything except the NC and I have 3 NCs.  Everything is freshly-installed via the 10.04 LTS ISO.

My CC is at 192.168.0.98, and it is set up in MANAGED-NOVLAN mode.  The DHCP server on the CC hands out 192.168.0.110-192.168.0.130.

There is an existing network of physical machines sitting at 192.168.0.0/23 that the cloud instances must be able to talk to.  I do not run any other DHCP server on the enterprise network.

VNET_SUBNET is 172.19.0.0.  

When I create an instance, the instance is assigned an IP in VNET_SUBNET and the CC allocates a public IP in the VNET_PUBLICIPS range.  I can ssh into the public IP from anywhere on the enterprise network, and I can ping between instances using their public or private IPs.

My problem is that I cannot connect to hosts outside the cloud from instances.  The CC has no trouble doing so, but instances are isolated from both the enterprise network and the Internet.

What do I need to do to tell the CC that it should route traffic from the cloud?

---

### Post by justindossey on 2010-12-14
Here's an interesting development:

If, on the instance, I configure an IP that is on the enterprise network, I can access everything on th Internet just fine.  

Therefore, there's something funky with how traffic gets routed over the 172.19 network.

---

### Post by indrasuryatama on 2010-12-15
try to open your port on TCP and ICMP
$ euca-authorize default -P tcp -p 22 -s 0.0.0.0/0
$ euca-authorize default -P tcp -p 8773 -s 0.0.0.0/0
$ euca-authorize default -P icmp -p 22 -s 0.0.0.0/0
$ euca-authorize default -P icmp -p 8773 -s 0.0.0.0/0
etc.. hope it will help

---

### Post by kim0 on 2010-12-15
Thanks Indra for the reply

---

### Post by raymdt on 2010-12-15
Hi justindossey,
i think the route for your instances (it should be 172.19.1.1   try route -n into one instance) doesn't enable  IP Forwarding.
(on CLC)  cat /proc/sys/net/ipv4/ip_forward should give "1"
Please post the result of this command line  iptables -L | grep 172.19

---

### Post by justindossey on 2010-12-15
After a lot more reading, I've determined that the issue is that the CLC doesn't route traffic to the LAN.

I tried setting the default gateway on the NC to the CLC, and I'm unable to access the Internet from the NC in that case.  Of course, the instances have the same problem.

Some networking info on the CLC.  I've masked my Internet IP with #.#.#.#.  The primary concern here is routing traffic to the 192.168.0.0 network from the instances (on the 172.19.1.0 network).  The NCs are on the 192.168.0.0 network.

# cat /proc/sys/net/ipv4/ip_forward
1

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
#.#.#.#  0.0.0.0         255.255.255.248 U     0      0        0 eth1
172.19.1.0      0.0.0.0         255.255.255.224 U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         #.#.#.#  0.0.0.0         UG    100    0        0 eth1

# iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination
DNAT       tcp  --  0.0.0.0/0            169.254.169.254     tcp dpt:80 to:169.254.169.254:8773
DNAT       all  --  0.0.0.0/0            192.168.0.110       to:172.19.1.2
DNAT       all  --  0.0.0.0/0            192.168.0.111       to:172.19.1.3

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination
SNAT       all  --  172.19.1.3          !0.0.0.0/0           to:192.168.0.111
SNAT       all  --  172.19.1.2          !0.0.0.0/0           to:192.168.0.110
MASQUERADE  all  -- !127.0.0.0/8         !0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
DNAT       all  --  0.0.0.0/0            192.168.0.110       to:172.19.1.2
DNAT       all  --  0.0.0.0/0            192.168.0.111       to:172.19.1.3

# iptables -L -n
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           ctstate ESTABLISHED
ACCEPT     all  --  0.0.0.0/0           !0.0.0.0/0
ACCEPT     all  --  172.19.1.0/27        172.19.1.0/27
admin-default  all  --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

Chain admin-default (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            172.19.1.0/27       tcp dpt:22

---

### Post by raymdt on 2010-12-15
Hi Justin,
first sorry for my poor english..... :D i'm working on it ;).

I suppose that your uec installation is new and there are no very important things running  on your cloud now.
Can you please try this as root.

(/proc/sys/net/ipv4/ip_forward should containt 1) 

#save your Firewall rules 
iptables-save -c > myfirewall.bak

#delete all the rules
iptables -F

iptables -P FORWARD ACCEPT

iptables --table -nat -A POSTROUTING -o eth1 -j MASQUERADE

(try with eth0 if eth1 doesn't work)

Did it help?

---

### Post by justindossey on 2010-12-15
It appears that the issue is that the NC and the enterprise gateway are on the same network.  I'm trying to get the instance to talk to physical hosts on the enterprise network, and the packets appear on the CLC from the instance.  

The CLC is translating the instance IP (172.19.1.2) to the enterprise network IP (192.168.0.110).  It then looks at the packet destination (192.168.0.5, for example).  In the case of ICMP, it sends an ICMP redirect to the client-- "you're on the same network as the host you're trying to contact-- don't ask me!"--but the instance cannot contact the destination directly because it is actually on 172.19.1.2.

---

### Post by justindossey on 2010-12-15
Progress!

I moved the NCs to their own network-- 192.168.10.x-- and now the NCs and instances are able to access the 192.168.0.x "enterprise" network.  

To gain access to the public Internet (the CLC has an interface connected to the DMZ), I added some masquerading rules:

 sudo /sbin/iptables -t nat -I POSTROUTING -o eth1 -s 192.168.10.0/24 -j MASQUERADE

 sudo /sbin/iptables -I FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

sudo /sbin/iptables -I FORWARD -i eth0 -o eth1 -s 192.168.10.0/24 -j ACCEPT

---

### Post by raymdt on 2010-12-15
Nice ;)
Does everything work now?

---

### Post by justindossey on 2010-12-15
Everything works now!  Lesson to everyone: Put the segment between your CC/CLC on its own network.

---

