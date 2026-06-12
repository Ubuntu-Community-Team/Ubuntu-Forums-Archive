---
title: "How to public ip addresses behing ubuntu router"
date: 2009-10-21
forum: Server Platforms
---

### Post by dragos2 on 2009-10-21
This is a silly question.

I want to set up an ubuntu server as a router, then I want to assign 4 public IP
addresses behind him in a DMZ zone like this:

  internet
  /\
  ||
  \/
 router (ubuntu server)
 |     |                  |
 |     |                  |
server1 server2     www-server


On the router (ubuntu server) box I will set one interface with a public ip address, then
how do I set it in order that the 3 other servers can have public ip addresses too ?

---

### Post by Lars Noodén on 2009-10-21
So the router gets 1 public IP, and then one each for the three servers inside. 

Do you have three ethernet ports on the ubuntu router?  
Or is it connecting to a switch or hub on the inside?
Not that it makes much difference, but it will help determine how to tune IP Tables.

**A)**
```

                                         +--- server1
                                         |
Internet --- Ubuntu Router --- switch ---+--- server2
                                         |
                                         +--- www-server

```

or

**B)**
```

                        +-------------------- server1
                        |
Internet --- Ubuntu Router ------------------ server2
                        |
                        +-------------------- www-server

```

---

### Post by dragos2 on 2009-10-22
> **Lars Noodén said:**
> So the router gets 1 public IP, and then one each for the three servers inside. 

Do you have three ethernet ports on the ubuntu router?  
Or is it connecting to a switch or hub on the inside?
Not that it makes much difference, but it will help determine how to tune IP Tables.

**A)**
```

                                         +--- server1
                                         |
Internet --- Ubuntu Router --- switch ---+--- server2
                                         |
                                         +--- www-server

```or

**B)**
```

                        +-------------------- server1
                        |
Internet --- Ubuntu Router ------------------ server2
                        |
                        +-------------------- www-server

```

Hi Lars, thanks for answering, I think I will use a switch rather than 4 network cards.

But I still don't know how to set up the router. One interface will be the external one
which will get 1 public ip, but how do I make him act as  a router and allow the other
3 public ips from the servers behind him be visible in the internet?

Is is like a forward ? Since I don't think it is a NAT.

Also the servers behind the router will get only their public ip addresses configured
with the ubuntu router as gateway ?

---

### Post by Lars Noodén on 2009-10-22
> **dragos2 said:**
> Hi Lars, thanks for answering, I think I will use a switch rather than 4 network cards.

But I still don't know how to set up the router. One interface will be the external one
which will get 1 public ip, but how do I make him act as  a router and allow the other
3 public ips from the servers behind him be visible in the internet?

Is is like a forward ? Since I don't think it is a NAT.

Also the servers behind the router will get only their public ip addresses configured with the ubuntu router as gateway ?


Ok.  A,C,D,and E all have public IP addresses.  

```

                                         +--- server1    (C)
                  (A)            (B)     |
Internet --- Ubuntu Router --- switch ---+--- server2    (D)
                                         |
                                         +--- www-server (E)

```

The external [interface](http://manpages.ubuntu.com/manpages/jaunty/en/man5/interfaces.5.html) on A will have to listen for all four.  See tools [ifconfig](http://linux.die.net/man/8/ifconfig) or the newer [ip](http://linux.die.net/man/8/ip) to set up aliases.  

e.g.

[INDENT][FONT="Courier New"]
ip addr add *xx.yy.zz.aa* dev eth0  label eth0:server1
ip addr add *xx.yy.zz.bb* dev eth0  label eth0:server2
ip addr add *xx.yy.zz.cc* dev eth0  label eth0:web-server
ip addr show eth0:*
[/FONT][/INDENT]

That will get you all four addresses on the same interface.  

When you can successfully ping each one, you are set to keep them between reboots.  To do so, make a backup copy of  /etc/network/interfaces and then add your changes.
( sudo cp /etc/network/interfaces /etc/network/interfaces.orig )

---

### Post by dragos2 on 2009-10-22
> **Lars Noodén said:**
> Ok.  A,C,D,and E all have public IP addresses.  

```

                                         +--- server1    (C)
                  (A)            (B)     |
Internet --- Ubuntu Router --- switch ---+--- server2    (D)
                                         |
                                         +--- www-server (E)

```The external [interface]("http://manpages.ubuntu.com/manpages/jaunty/en/man5/interfaces.5.html") on A will have to listen for all four.  See tools [ifconfig]("http://linux.die.net/man/8/ifconfig") or the newer [ip]("http://linux.die.net/man/8/ip") to set up aliases.  

e.g.
[INDENT][FONT=Courier New]
ip addr add *xx.yy.zz.aa* dev eth0  label eth0:server1
ip addr add *xx.yy.zz.bb* dev eth0  label eth0:server2
ip addr add *xx.yy.zz.cc* dev eth0  label eth0:web-server
ip addr show eth0:*
[/FONT][/INDENT]That will get you all four addresses on the same interface.  

When you can successfully ping each one, you are set to keep them between reboots.  To do so, make a backup copy of  /etc/network/interfaces and then add your changes.
( sudo cp /etc/network/interfaces /etc/network/interfaces.orig )

Great, thanks. After this setup when I will ping the public C address the packets
will be automatically forwarded to C or they will stop on the router alias interface ?

Do I still need to do forward with iptables or nat on the router or what you described is
enaught ?

---

### Post by Lars Noodén on 2009-10-22
> **dragos2 said:**
> Great, thanks. After this setup when I will ping the public C address the packets
will be automatically forwarded to C or they will stop on the router alias interface ?

Do I still need to do forward with iptables or nat on the router or what you described is
enaught ?

The packets will stop on the router alias interface.  But you have to get to that stage before moving onto forwarding with iptables.  

To plan routing, you have to answer these to yourself : what services do you want available to the public on C,D,and E?  Do you want any rate limiting, throttling or other restrictions?
Are C,D, and E using static internal IP addresses or are they getting them dynamically?  If dynamically are the from A or B? etc

Probably, since E is a web server you'll want http (tcp 80) and https (tcp 443) and ping with a few other necessary options (ICMP 0,3,4,8,11,30).  If you expect to log in via ssh then port 22.  

When you have that charted out, move on to working with IPTables.  First just the INPUT and OUTPUT chains for A.  When that is working, save a copy and then work out forwarding for one of C,D, or E.  When that is working also, save a copy and do the last two.

---

### Post by dragos2 on 2009-10-22
> **Lars Noodén said:**
> The packets will stop on the router alias interface.  But you have to get to that stage before moving onto forwarding with iptables.  

To plan routing, you have to answer these to yourself : what services do you want available to the public on C,D,and E?  Do you want any rate limiting, throttling or other restrictions?
Are C,D, and E using static internal IP addresses or are they getting them dynamically?  If dynamically are the from A or B? etc

Probably, since E is a web server you'll want http (tcp 80) and https (tcp 443) and ping with a few other necessary options (ICMP 0,3,4,8,11,30).  If you expect to log in via ssh then port 22.  

When you have that charted out, move on to working with IPTables.  First just the INPUT and OUTPUT chains for A.  When that is working, save a copy and then work out forwarding for one of C,D, or E.  When that is working also, save a copy and do the last two.

Ok, I think I got it now. If I only want to forward all the traffic and let the firewalls on
C, D and E to handle it can't I just use the forward chain should I still use the INPUT
and OUTPUT chain ? I was thinking that this can be handled with the forward chain ?

And the last thing that I am unsure about is the switch. What ip should I give to him?
And from where? From the routers dhcp ?

---

### Post by Lars Noodén on 2009-10-22
> **dragos2 said:**
> Ok, I think I got it now. If I only want to forward all the traffic and let the firewalls on
C, D and E to handle it can't I just use the forward chain should I still use the INPUT
and OUTPUT chain ? I was thinking that this can be handled with the forward chain ?


A uses INPUT and OUTPUT

C,D,E are managed by FORWARD

> **dragos2 said:**
> 
And the last thing that I am unsure about is the switch. What ip should I give to him?
And from where? From the routers dhcp ?

Can the switch be set to operate transparently so that it looks to A like C,D, and E are connected directly to A?  Then C,D,and E.  There is no need to set up DHCP unless you are planning to include other computers inside the LAN on an ad hoc basis.  It would be faster and easier to assign static LAN IPs for CDE and use those.  Less parts to worry about.

---

### Post by thomasbau on 2009-11-19
Hi 

 I 'm fiddling with my new ubuntu server 9.10 (Dell PowerEdge2800 with 2 NIC) to get him route internal IP's (192.168.51.0/24) to the internet
 I' m using following settings:
 

 /etc/network/interfaces
 
```

auto lo eth0 eth1
iface lo inet loopback

#External network
iface eth0 inet static
    address 162.7.108.202
    netmask 255.255.255.252

#Internal network
iface eth1 inet static
     address 192.168.51.10
     network 192.168.51.0
     netmask 255.255.255.0

#static route
up route add -net 0.0.0.0 gw 162.7.108.201 dev eth0

```the output of *sysctl -p* command 

```

net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.ip_forward = 1
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.conf.all.accept_redirects = 1
net.ipv6.conf.all.accept_redirects = 1
net.ipv4.conf.all.secure_redirects = 0
net.ipv4.conf.all.send_redirects = 1
net.ipv4.conf.all.accept_source_route = 1
net.ipv6.conf.all.accept_source_route = 1

```command *route*

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
162.7.108.200   *               255.255.255.252 U     0      0        0 eth0
192.168.51.0    *               255.255.255.0   U     0      0        0 eth1
default        162-7-108-201.st 0.0.0.0         UG    0      0        0 eth0


``` This configuration did work on a knopix box kernel 2.6.19 with the difference that only 

 ```
 
 net.ipv4.conf.default.rp_filter = 1 
 net.ipv4.conf.default.forwarding = 1 


```                                 where set.   
 

 Further I can ping 162.7.108.201, which is the gateway given by my provider, from within 192.168.51.0/24 but I can not ping successfully any Internet IP


Any body a suggestion?
Thanks for any response

---

