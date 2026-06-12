---
title: "Unable to forward packets between interfaces"
date: 2012-10-15
forum: Server Platforms
---

### Post by TyIzaeL on 2012-10-15
I've been working on setting up an OpenVPN server to do some testing. What I'm trying to do is set up a routed VPN between my LAN (172.28.0.0/16)The problem I'm having is the server isn't routing traffic between the interfaces. For example, if I ping the server's eth0 interface from tun0 (ping -I tun0 172.28.4.16), I don't get any responses. Here is a network diagram:
[img]http://i.imgur.com/l8Uj3.png[/img]

I'm using UFW as my firewall. I've edited /etc/ufw/sysctl.conf as such to allow IP forwarding.
```
net/ipv4/ip_forward=1

net/ipv4/conf/all/accept_redirects=0
net/ipv4/conf/default/accept_redirects=0
net/ipv6/conf/all/accept_redirects=0
net/ipv6/conf/default/accept_redirects=0

net/ipv4/icmp_echo_ignore_broadcasts=1
net/ipv4/icmp_ignore_bogus_error_responses=1
net/ipv4/icmp_echo_ignore_all=0

net/ipv4/conf/all/log_martians=0
net/ipv4/conf/default/log_martians=0
```

I've also edited /etc/default/ufw to allow IP forwarding.
```
IPV6=no

DEFAULT_INPUT_POLICY="DROP"

DEFAULT_OUTPUT_POLICY="ACCEPT"

DEFAULT_FORWARD_POLICY="ACCEPT"

DEFAULT_APPLICATION_POLICY="SKIP"

MANAGE_BUILTINS=no

IPT_SYSCTL=/etc/ufw/sysctl.conf

IPT_MODULES="nf_conntrack_ftp nf_nat_ftp nf_conntrack_netbios_ns"
```

eth0 is configured to be promiscuous.
```
root@VPN:~# ip a sh
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,PROMISC,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:15:5d:02:18:14 brd ff:ff:ff:ff:ff:ff
    inet 172.28.4.16/16 brd 172.28.255.255 scope global eth0
    inet6 fe80::215:5dff:fe02:1814/64 scope link
       valid_lft forever preferred_lft forever
3: tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/none
    inet 172.29.0.1 peer 172.29.0.2/32 scope global tun0
```

Here are my current UFW rules.
```
root@VPN:~# ufw status
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       172.28.0.0/16
OpenVPN                    ALLOW       Anywhere
OpenSSH                    ALLOW       172.29.0.0/22
```

In /etc/ufw/before.rules I have configured NAT.
```
#Custom NAT rules start here.
*nat
:POSTROUTING ACCEPT [0:0]

-A POSTROUTING -s 172.29.0.0/22 -o eth0 -j MASQUERADE

COMMIT
#Custom NAT rules end here. 
#Beyond this point is nothing but default UFW config.

*filter
:ufw-before-input - [0:0]
:ufw-before-output - [0:0]
:ufw-before-forward - [0:0]
:ufw-not-local - [0:0]


-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-output -o lo -j ACCEPT

-A ufw-before-input -m state --state RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -m state --state RELATED,ESTABLISHED -j ACCEPT

-A ufw-before-input -m state --state INVALID -j ufw-logging-deny
-A ufw-before-input -m state --state INVALID -j DROP

-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

-A ufw-before-input -p udp --sport 67 --dport 68 -j ACCEPT

-A ufw-before-input -j ufw-not-local

-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN

-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN

-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN

-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP

-A ufw-before-input -p udp -d 224.0.0.251 --dport 5353 -j ACCEPT

-A ufw-before-input -p udp -d 239.255.255.250 --dport 1900 -j ACCEPT

COMMIT
```

Is there some step I am missing? What am I doing wrong here?

---

### Post by The Cog on 2012-10-15
Firstly, I am not sure that the ping will be natted by the MASQUERADE, so the server may be trying to respond to 172.29.0.1 via the internet.

I don't see anything really obviously wrong in the config, so a bit of debugging:

Use the command "sudo iptables-save -c" to output the iptables config along with counters to see how many hits each entry has had. Make sure the counters count the expected numbers of hits as you perform testing.

Use the command "sudo tcpdump -i eth0" to see packets going through eth0 as you are testing. Check addresses etc. on the packets as you are testing.

---

### Post by TyIzaeL on 2012-10-15
> **The Cog said:**
> Firstly, I am not sure that the ping will be natted by the MASQUERADE, so the server may be trying to respond to 172.29.0.1 via the internet.
I did some testing, and I discovered that a connected VPN client *can* ping the eth0 interface, it's just that the server can't ping its eth0 interface from tun0. I can see the echos going through tun0 with tcpdump when the client pings eth0, but I see nothing when I try to ping from tun0 directly. I've done some more testing, and it appears my VPN has been working just fine. I think my testing method was flawed.

> **The Cog said:**
> Use the command "sudo tcpdump -i eth0" to see packets going through eth0 as you are testing. Check addresses etc. on the packets as you are testing.
This helped me. For some reason I hadn't thought to use tcpdump to inspect what was going on. Once I did it was apparent traffic was going through the VPN, just that my ping test from one interface to the other was not working.

Thank you for the help. Marking post solved.

---

