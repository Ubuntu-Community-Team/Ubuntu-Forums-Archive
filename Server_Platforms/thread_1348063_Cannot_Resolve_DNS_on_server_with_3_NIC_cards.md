---
title: "Cannot Resolve DNS on server with 3 NIC cards"
date: 2009-12-06
forum: Server Platforms
---

### Post by eschnell on 2009-12-06
I have a server with 3 NIC's installed, 2 integrated, 1 PCI.

eth0 is the PCI card, eth1 and 2 are integrated. At startup, I am unable to resolve anything. dig google.com will come up with connection timeout.

After setting the link state for eth0 and 1 to down, it magically starts to work.

/etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# SchnellNet router gets static IP
auto eth2
iface eth2 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

# eddieschnell.com gets eth0 (pci)
auto eth0
iface eth0 inet dhcp

# schnellnetworks.com gets eth1
auto eth1
iface eth1 inet dhcp

/etc/resolv.conf
search schnellnet.net
nameserver 192.168.1.5

Bind is installed and configured with forwarders.

Thanks,
Eddie Schnell

---

### Post by Iowan on 2009-12-06
What addresses is the DHCP server handing out - might be a problem if they are in the 192.168.1.X subnet.

---

### Post by eschnell on 2009-12-06
DHCP is giving me 8.23.82.138 and 8.23.28.139, both are external IP addresses.

---

### Post by eschnell on 2009-12-07
help please

---

### Post by Iowan on 2009-12-07
Well, not what I thought... but two interfaces in the same subnet still causes problems for routing - unless you've added some **iptable** rules to fix things. A static address on another interface* might* make the whole thing work...

---

### Post by eschnell on 2009-12-07
The problem with setting another static address is that eth0 and eth1 are both external internet addresses. What kind of iptables would I need to put in? It's been a while since I have even heard of them.

Thanks
Eddie Schnell

---

### Post by Iowan on 2009-12-07
Sorry - it just occurred to me that those two interfaces are (probably - depending on netmask) not in the same subnet.  
I need to un-confuse myself about the nameserver...

---

### Post by lisati on 2009-12-07
> **Iowan said:**
> Sorry - it just occurred to me that those two interfaces are (probably - depending on netmask) not in the same subnet.  
I need to un-confuse myself about the nameserver...

:) Just spotted the reversed digits, 28 & 82, myself.....

---

### Post by windependence on 2009-12-07
Can you explain what you are trying to accomplish here? There may be a better or easier way to do it. If these other interfaces are external addresses, you should assign them statically to the interface. You will not be able to reach it from the inside of your LAN unless you have a router that supports NAT reflection (not common). If you want to use the same interface and reach it from your LAN, then create a virtual interface for that NIC e.g. eth0:0 and assign it a static internal address. I could give you more tips if I know what you are trying to do.

-Tim

---

### Post by eschnell on 2009-12-07
Here's the output of ifconfig

root@SchnellNet:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:27:19:cd:2e:73
          inet addr:8.23.82.138  Bcast:8.23.83.255  Mask:255.255.254.0
          inet6 addr: fe80::227:19ff:fecd:2e73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4724321 (4.7 MB)  TX bytes:8740514 (8.7 MB)
          Interrupt:24 Base address:0x6000

eth1      Link encap:Ethernet  HWaddr 00:e0:81:56:c5:84
          inet addr:8.23.82.139  Bcast:8.23.83.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:81ff:fe56:c584/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46207 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2870323 (2.8 MB)  TX bytes:362514 (362.5 KB)

eth2      Link encap:Ethernet  HWaddr 00:e0:81:56:c5:85
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:81ff:fe56:c585/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:157397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:79489192 (79.4 MB)  TX bytes:42606191 (42.6 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2362 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2362 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:194242 (194.2 KB)  TX bytes:194242 (194.2 KB)

root@SchnellNet:~#

/etc/resolv.conf
nameserver 127.0.0.1

Thanks,
Eddie

---

### Post by windependence on 2009-12-07
What is in your /etc/resolv.conf?

-Tim

---

### Post by eschnell on 2009-12-07
> **windependence said:**
> Can you explain what you are trying to accomplish here? There may be a better or easier way to do it. If these other interfaces are external addresses, you should assign them statically to the interface. You will not be able to reach it from the inside of your LAN unless you have a router that supports NAT reflection (not common). If you want to use the same interface and reach it from your LAN, then create a virtual interface for that NIC e.g. eth0:0 and assign it a static internal address. I could give you more tips if I know what you are trying to do.

-Tim

Here's my understanding of my ISP's setup.
There is a fiber connection coming in to the apartment complex. The complex has an ip range, 8.23.82.1-8.23.82.254(?). This connection is put into a coax cable distribution system, which is like a giant network switch with ports in different rooms (simpelest way to distribute between buildings). I put a network switch onto the port in my apartment, instead of the router that was pre-installed. Each port on my switch now gets it's own external IP address, assigned by their DHCP server. Our connection is throttled, but it is by IP address. if I had static IP addresses on these external addresses I would not have to deal with dynamic DNS, but they want $15 a month for it, so it's not really an option.

The goal is to have the server running my website and email on one NIC so it will not be slowed by streaming a movie on the Xbox through the routers connection, but it's nice to have the third if I need to download a big file, I have a spare connection. I have 3 nics installed so there are 2 external IP addresses (eth0 and eth1), and one internal(static) ip (eth2) address behind a router. The server is going to provide DHCP and DNS for the network behind the router on eth2, but the dns will not resolve unless I shut off eth0 and eth1, then it works like a charm.

Thanks for the help,
Eddie

---

### Post by eschnell on 2009-12-07
> **windependence said:**
> What is in your /etc/resolv.conf?

-Tim

```
nameserver 127.0.0.1
```

the computer has dns server installed with forwarders. works when eth0 and eth1 are disabled.

---

### Post by Iowan on 2009-12-08
I have a DHCP/DNS server (**dnsmasq**) on my network - it's */etc/resolv.conf* references an external nameserver besides 127.0.0.1.

---

### Post by windependence on 2009-12-09
> **eschnell said:**
> Here's my understanding of my ISP's setup.
There is a fiber connection coming in to the apartment complex. The complex has an ip range, 8.23.82.1-8.23.82.254(?). This connection is put into a coax cable distribution system, which is like a giant network switch with ports in different rooms (simpelest way to distribute between buildings). I put a network switch onto the port in my apartment, instead of the router that was pre-installed. Each port on my switch now gets it's own external IP address, assigned by their DHCP server. Our connection is throttled, but it is by IP address. if I had static IP addresses on these external addresses I would not have to deal with dynamic DNS, but they want $15 a month for it, so it's not really an option.

The goal is to have the server running my website and email on one NIC so it will not be slowed by streaming a movie on the Xbox through the routers connection, but it's nice to have the third if I need to download a big file, I have a spare connection. I have 3 nics installed so there are 2 external IP addresses (eth0 and eth1), and one internal(static) ip (eth2) address behind a router. The server is going to provide DHCP and DNS for the network behind the router on eth2, but the dns will not resolve unless I shut off eth0 and eth1, then it works like a charm.

Thanks for the help,
Eddie
There are a few problems with what you are trying to do. First, TC/IP uses mac addresses to route packets, not IP addresses, so you can't guarantee that requests going out of one interface will return that way. They may very well come back through another interface, which can cause you problems. Of course, there are ways to solve this problem, but it involves some advanced routing. You are probably much better off NATing everything back to the server as it would be much easier to control what traffic goes where.

-Tim

---

### Post by capscrew on 2009-12-09
Thanks to Tim for asking the obvious.  :-)

> **eschnell said:**
> Here's my understanding of my ISP's setup.
There is a fiber connection coming in to the apartment complex. The complex has an ip range, -8.23.82.254(?). 

Simply put, the public network which you are part of is```

8.23.82.0/24   #subnet mask of 255.255.255.0
```
> 

This connection is put into a coax cable distribution system, which is like a giant network switch with ports in different rooms (simpelest way to distribute between buildings). I put a network switch onto the port in my apartment, instead of the router that was pre-installed. 

Each port on my switch now gets it's own external IP address, assigned by their DHCP server.
Actually; each host (device) connected to a port on your switch is assigned an address in the network range.> 

Our connection is throttled, but it is by IP address. if I had static IP addresses on these external addresses I would not have to deal with dynamic DNS, but they want $15 a month for it, so it's not really an option.

The goal is to have the server running my website and email on one NIC so it will not be slowed by streaming a movie on the Xbox through the routers connection, but it's nice to have the third if I need to download a big file, I have a spare connection. 
Ahemmmm....What router are you referring to?  You said your removed the router.(e.g. *"I put a network switch onto the port in my apartment, instead of the router that was pre-installed."*.  > 
I have 3 nics installed so there are 2 external IP addresses (eth0 and eth1), and one internal(static) ip (eth2) address behind a router. 

The server is going to provide DHCP and DNS for the network behind the router on eth2, but the dns will not resolve unless I shut off eth0 and eth1, then it works like a charm...

*[SIZE="2"][COLOR="Navy"]Just because you can, doesn't mean you should...[/COLOR][/SIZE]* 

So downstream of the multi-homed host ([the] server with 3 NIC cards) is a router.  The multi-homed host is a router (and NEEDS to be) in its own right.

If you are to isolate your private network from the public network you do need a router.  If you wish to use the Linux host for this purpose then you need to use a combination of IP forwarding and NAT. IPTables in the server does just that.

The reason you are having trouble is partly because some of what you are trying to accomplish does not use TCP/IP at all.  Anything that is (or uses) a switch is a *layer 2* protocol and is subject to spanning tree protocol (STP).  This is to prevent network loops.  You can't have multiple IP's on a switch that end up at the same place.  If you do STP blocks one (or more) to prevent looping.

Anything that is in the same subnet (using the switch (i.e. 8.23.82.0/24)) is subject to STP blocks.

Why do you need more than one "public IP address?  You can successfully host a network of 65,000+ devices behind the router that was originally fitted.

If you are streaming video off the internet, multiple NIC's will not make it any faster or safer.  The bottleneck is the 8.23.82.0/24 network anyway.

If you are streaming off your own private LAN, it's layer 2 Ethernet and has nothing to do with TCP.  IP is only the addressing scheme.

What you do is whatever you wish to do, but I suggest learning the IP stack and networking.  Then KISS.

Edit: And again, thanks Tim for the simple answer.

---

### Post by eschnell on 2009-12-09
> **capscrew said:**
> Thanks to Tim for asking the obvious.  :-)


Simply put, the public network which you are part of is```

8.23.82.0/24   #subnet mask of 255.255.255.0
```Actually; each host (device) connected to a port on your switch is assigned an address in the network range.Ahemmmm....What router are you referring to?  You said your removed the router.(e.g. *"I put a network switch onto the port in my apartment, instead of the router that was pre-installed."*.  

*[SIZE=2][COLOR=Navy]Just because you can, doesn't mean you should...[/COLOR][/SIZE]* 

So downstream of the multi-homed host ([the] server with 3 NIC cards) is a router.  The multi-homed host is a router (and NEEDS to be) in its own right.

If you are to isolate your private network from the public network you do need a router.  If you wish to use the Linux host for this purpose then you need to use a combination of IP forwarding and NAT. IPTables in the server does just that.

The reason you are having trouble is partly because some of what you are trying to accomplish does not use TCP/IP at all.  Anything that is (or uses) a switch is a *layer 2* protocol and is subject to spanning tree protocol (STP).  This is to prevent network loops.  You can't have multiple IP's on a switch that end up at the same place.  If you do STP blocks one (or more) to prevent looping.

Anything that is in the same subnet (using the switch (i.e. 8.23.82.0/24)) is subject to STP blocks.

Why do you need more than one "public IP address?  You can successfully host a network of 65,000+ devices behind the router that was originally fitted.

If you are streaming video off the internet, multiple NIC's will not make it any faster or safer.  The bottleneck is the 8.23.82.0/24 network anyway.

If you are streaming off your own private LAN, it's layer 2 Ethernet and has nothing to do with TCP.  IP is only the addressing scheme.

What you do is whatever you wish to do, but I suggest learning the IP stack and networking.  Then KISS.

Edit: And again, thanks Tim for the simple answer.

There is a regular router after the network switch. One port of this router goes to the server. Map below.

[IMG]http://img81.imageshack.us/img81/6841/mapr.jpg[/IMG]

---

### Post by NIT006.5 on 2010-01-14
While I'm not an expert on this, I have to say that this setup doesn't make sense to me. You've effectively got two gateways (the server and the wireless router) which are connected together both at the switch and directly, which I would imagine is already likely to cause confusion. For any of the clients to use the two public links on the server, the wireless router first has to send the traffic to the server, and then the server has to sort out which link to send the traffic out on depending on the protocol or destination, etc. This also isn't likely to work because the wireless router isn't made to route traffic on the local network - it's there to "join" the public network and the private network. 

Since name resolution only works when you disable the two interfaces connected to the switch it would seem that your successful resolution is then going through the wireless router. Obviously when the other two are enabled, the default route is changing on the server and it's trying to go direct on one of the other two interfaces (which one?) and failing.

I have serious doubts as to whether a configuration like this would ever work, but I don't know enough but the lower level networking protocols to be certain. However, I would strongly recommend having only one gateway (either the server or the wireless router, but not both) and then handling the routing on whichever one you use. That's just for starters. Even then I'm not sure how it will work having two connections to the same public network, as per previous post which refers to STP.

---

