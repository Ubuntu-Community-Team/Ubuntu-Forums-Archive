---
title: "Networking problems with two adapters"
date: 2009-10-04
forum: Server Platforms
---

### Post by uGJ on 2009-10-04
Hello. I am using Ubuntu 9.04 server edition (amd64) and now I have some problems with networking.

The computer it is running on has two ethernet ports (eth0 and eth1 as labeled by the OS). When I first set it up, the network set up was like this:

eth1 -- LAN router (NAT, multiple computers) -- ADSL Modem (bridge, no NAT) -- Internet

I set up eth1 with static IP address, netmask and gateway and it worked fine.


Now I wanted to do the final network set up, to connect eth0 directly to the modem to give the server a public IP address different than the rest of the network. For that I made eth0 be dynamic and use DHCP, and removed the gateway from eth1. So the network set up is like this:

eth0 ---------------------v
eth1 -- LAN router -- ADSL Modem == Internet

The intent is that for any connection that would involve Internet, it would use only eth0, and for any connection that involves the local NAT (192.168.2.0 space), it would use only eth1.

The output from 'route' looks fine to me:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
62.240.80.0     *               255.255.240.0   U     0      0        0 eth0
default         IP-62-240-80-1. 0.0.0.0         UG    100    0        0 eth0

```

The actual problems are these:

[LIST=1]
[*]eth0 loses all connectivity in 1 - 1.5 hours after connecting
[*]ping to Internet servers acts weird
[*]traceroute to LAN computers does not work
[/LIST]

To elaborate:

1. After eth0 gets connection to Internet (gets IP and stuff from ISP's DHCP), it takes from 1 hour to 1.5 hours until all connections to Internet suddenly halt and no new connections can be made until I sudo ifdown and ifup to eth0, after which it works for another hour or such before dropping again

2. ping command to any Internet server gives duplicate replies and Redirect Host replies
> PING [www.l.google.com](www.l.google.com) (209.85.229.106) 56(84) bytes of data.
From IP-62-240-94-20.telemail.fi (62.240.94.20): icmp_seq=1 Redirect Host(New nexthop: IP-62-240-80-1.telemail.fi (62.240.80.1))
64 bytes from ww-in-f106.google.com (209.85.229.106): icmp_seq=1 ttl=54 time=69.1 ms
64 bytes from ww-in-f106.google.com (209.85.229.106): icmp_seq=1 ttl=53 time=69.6 ms (DUP!)

Note that 62.240.94.20 is the public IP of the LAN router and 62.240.80.1 is my ISP's gateway.

It's as if it is sending the PING packets through both eth0 and eth1, while to my logic it should only send them through eth0.

3. traceroute to any LAN computer (accessible only through eth1) shows this:
> traceroute to 192.168.2.7 (192.168.2.7), 30 hops max, 60 byte packets
 1  * * *
 2  * * *

and so on. Ping to the same address works properly, without any problems unlike in problem #2.


For reference, here is my /etc/network/interfaces

```
# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
 address 192.168.2.50
 netmask 255.255.255.0
# gateway 192.168.2.1

```


Now any kind of ideas on how to make the network work in the way I want: eth0 for Internet, eth1 for LAN only (even though 192.168.2.1 is a gateway with Internet access)? Especially in a way that it wouldn't disconnect everything of eth0 every hour or so.

Thank you in advance.

---

### Post by Bachstelze on 2009-10-04
> **uGJ said:**
> Now I wanted to do the final network set up, to connect eth0 directly to the modem to give the server a public IP address different than the rest of the network.

Does your ISP give you two public IPs?

---

### Post by uGJ on 2009-10-04
> **Bachstelze said:**
> Does your ISP give you two public IPs?
Yes. Up to 5 IP addresses if I remember correctly. So that is not the problem; eht0 shows it being bound to a public IP address, and the router has a different public IP address.

---

### Post by uGJ on 2009-10-10
I hope this is not a hopeless situation...

---

### Post by koenn on 2009-10-10
> Now I wanted to do the final network set up, to connect eth0 directly to the modem to give the server a public IP address different than the rest of the network. For that I made eth0 be dynamic and use DHCP, and removed the gateway from eth1. So the network set up is like this:

eth0 ---------------------v
eth1 -- LAN router -- ADSL Modem == Internet
I can't figure out what you mean by this. It Looks wrong and seems to contradict what you say about eth0 being your internet connection.
Try to make a better drawing.

Loosing your connection after 1 hr may be a dhcp lease that doesn't get renewed when it should, but you can look in to that *after* you made sure your network is functioning - network malfunction could be the cause of the lease renew not happening.


Although I don't understand the "redirect" part of your ping, i don't see anything that would lead me to thinnk that ping goes out through both eth0 and eth1. Why do you think that ? 

traceroute uses udp datagrams so it's different from ping. You may be blocking udp somewhere or have other issues that affect udp but not icmp. Again, make sure your network works reliably.
 
Post the output of ifconfig for eth0 and eth1

Again, make an accurate drawing, preferably with ip addresses and netmasks in it, and some context : why you set it up that way, what you hope to achieve, how you expect things to work.

---

### Post by uGJ on 2009-10-10
Thank you for your replies.

I hope this image illustrates it better, then:

[img]http://content.screencast.com/users/godjonez/folders/Jing/media/4e39a947-f167-4f1f-9e35-78f05f0c07bb/2009-10-10_2312.png[/img]
(note that the IP addresses given by the ISP have changed since the opening post, in case you are wondering)

The target of this setup is that the server has a direct access to Internet (through eth0) but that the computers in the local network can still access the server directly (through eth1).

The workstations have Internet access too, through the router for which my ISP gives a different IP address than what it gives for the Ubuntu server.

The server computer should only be able to access Internet through eth0, and not through eth1, so that all traffic between the server and the wide area network is done through a single interface.


Basically the setup works, except for the fact that the server computer becomes unable to have any communication through eth0 after the connection has been established for one hour. Looking at the log files, the DHCP client successfully renews the IP address and everything seems fine (output of ifconfig seems fine, output of route seems fine, log files make it seem fine) except that anything that used the connection is disconnected and no connection can be made before the interface is brought down and up again. (also running dhclient manually makes it work again, but it seems to leave another instance of that process running, so that doesn't seem very good way, and it still breaks again anyway)


Any more information that is needed? I'll happily hand it out in order to get this fixed.

---

### Post by koenn on 2009-10-10
Post the output of ifconfig for eth0 and eth1

---

### Post by uGJ on 2009-10-10
```

eth0      Link encap:Ethernet  HWaddr 00:16:17:95:28:f1
          inet addr:217.24.107.21  Bcast:217.24.107.255  Mask:255.255.252.0
          inet6 addr: fe80::216:17ff:fe95:28f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11955 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2820513 (2.8 MB)  TX bytes:1030546 (1.0 MB)
          Interrupt:248 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:16:17:95:9c:96
          inet addr:192.168.2.50  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe95:9c96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11725862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8716100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14132039093 (14.1 GB)  TX bytes:3359257934 (3.3 GB)
          Interrupt:249 Base address:0xc000

```

Note that for a while I have kept eth0 down and configure eth1 to user the router as a gateway; just to keep the server online. I activated eth0 with "sudo ifup eth0" just now to get the output for them both, meaning eth1 still has the gateway configured at this point.

BTW, this is the output from DHCP client when I did ifup:
> bound to 217.24.107.21 -- renewal in 1647 seconds.

---

### Post by koenn on 2009-10-10
what does your routing table look like the after the connection  through eth0 gets lost ?

---

### Post by koenn on 2009-10-10
both interfaces have IPv6 addresses too. I don't know much about IPv6, just that it works rather different than IPv4. Possibly, routing and subnetting is sufficiently different to explain for the weird ping behaviour and the fact that eth1 can get internet access even though the IP v4 routing doesn't provide it. 
Do you know how to disable that (at least temporarily, until you've got your IPv4 issues figured out)?

[http://www.cyberciti.biz/tips/linux-how-to-disable-the-ipv6-protocol.html](http://www.cyberciti.biz/tips/linux-how-to-disable-the-ipv6-protocol.html)

---

### Post by uGJ on 2009-10-10
Thank you. I also thought it could have something to do with IPv6 too, but considering the router (to which eth1 is connected to) does not support IPv6 itself, I view that as an unlikely scenario. I shall still try disabling it (what good does it do being enabled anyway if the network doesn't support it?)

Also, once the connection dies, I will get the route output. Unless the situation has magically fixed itself :P

---

### Post by koenn on 2009-10-10
it's getting late on this side, so I'm out of here for now. 

Let's see what things look like without IPv6 and take it from there - tomorrow or so.

Also, if the connection dies, do ifconfig to see if the status of eth0 actually changes (and how)

---

### Post by uGJ on 2009-10-10
I cannot follow the instructions to disable IPv6 from the link you gave me. There is no /etc/modprobe.d/aliases file.

I did follow the link there and came across adding "blacklist ipv6" to blacklist file, so I did, but I doubt it works since looking with lsmod there even is no such module as ipv6. I guess it's built into the kernel?

It's getting late here too, but I'll hang on to at least enough to get these tests done tonight.

Thank you for the interest and suggestions so far!

---

### Post by uGJ on 2009-10-10
Okay, like predicted, the Internet access ceased to be, this time after about 1 hour 20 minutes.

Output of 'route':
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
217.24.104.0    *               255.255.252.0   U     0      0        0 eth0
default         217.24.104.1    0.0.0.0         UG    100    0        0 eth0

```
Note that printing the last line took a long time and it has only IP address instead of the hostname, because at this point even DNS didn't work.

The output of ifconfig now for the two adapters (excluding localhost adapter lo):
```

eth0      Link encap:Ethernet  HWaddr 00:16:17:95:28:f1
          inet addr:217.24.107.21  Bcast:217.24.107.255  Mask:255.255.252.0
          inet6 addr: fe80::216:17ff:fe95:28f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1882529 errors:0 dropped:0 overruns:0 frame:0
          TX packets:945091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1440190069 (1.4 GB)  TX bytes:74343592 (74.3 MB)
          Interrupt:248 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:16:17:95:9c:96
          inet addr:192.168.2.50  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe95:9c96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11767780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8749761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14135987922 (14.1 GB)  TX bytes:3442368549 (3.4 GB)
          Interrupt:249 Base address:0xc000

```


I have some running long-time processes active right now, so I cannot reboot the server to test if the IPv6 changes to blacklist have any effect. I guess I'll try that once those processes have finished. And I hope someone will find a more definitive way to disable IPv6 on this version, if it is even possible without a modified kernel.

---

### Post by uGJ on 2009-10-19
Could not disable IPv6. It appears to be integrated into kernel (am I right)?

So that did not help. Any other ideas? Or is this simply a bug in the system?

---

### Post by koenn on 2009-10-19
Even if it's a bug, there has to be an explanation.
But I'l all out of ideas - the IPv6 thing is the only explanation that makes sense to me.


Here's an other way to disable Ipv6 - from [http://www.g-loaded.eu/2008/05/12/how-to-disable-ipv6-in-fedora-and-centos/](http://www.g-loaded.eu/2008/05/12/how-to-disable-ipv6-in-fedora-and-centos/)
> Completely disable the ipv6 module

To completely disable IPv6 in your system, all you have to do is save the following line in a file inside /etc/modprobe.d/.

install ipv6 /bin/true

The above line means: whenever the system needs to load the ipv6 kernel module, it is forced to execute the command true instead of actually loading the module. Since /bin/true, does absolutely nothing, the module never gets loaded.

Again, it is required to reboot for the changes to take effect.

It is obvious that this is an aggressive method to disable kernel modules, but it guarantees that the module never gets loaded.

This is the recommended way to disable IPv6.



Other idea :the bridge at the modem ? 
Didn't think this through yet (I'm watching CSI, and the commercial break just ended :) ) and I don't know much about bridging (I tend to solve stuff by routing and switces mostly) but It may be wort a closer look.

---

### Post by uGJ on 2009-10-19
Guess what? It didn't help.

I added that line "install ipv6 /bin/true" inside /etc/modprobe.d/blacklist.conf and it didn't do anything after I rebooted. Which would make sense in a way, since it is apparently not loaded as a module (modprobe doesn't list it at all).

Yet, ifconfig lists IPv6 addresses and dmesg has
> [   26.332523] eth1: no IPv6 routers present
[   27.030016] eth0: no IPv6 routers present



I tried pinging again and found something interesting. If I don't have eth1 connected to the router, so the server only has eth0 connected to the modem, it still gets duplicate pong replies as long as the router is also connected to the modem. If I disconnect the router from the modem, then ping works fine, even if eth1 is connected to the router.

So it seems like the modem is distributing the PING packets to both my router and to the ISP gateway and the router tries to be smart and tells back to use another gateway and then produces duplicate reply.

So yes, the modem does also have some routing capabilities even when in bridged mode. If it sees a request coming from one computer connected to it going to another computer connected to it, it relays the packets directly without looping them through the ISP's gateway, even though both computers connected to the modem do not "see" the modem, the first gateway for both is the ISP's gateway. So the modem is kind of cheating here. Not sure if that has anything to do with the disconnection issue, though. 

I guess I can fix the ping thing by poking some settings in the modem when I connect to it in routing mode (so that it uses NAT and DHCP itself). But the disconnection issue seems weirder.

---

### Post by windependence on 2009-10-19
You are essentially creating a router out of your Ubuntu box. I don't really think you want to do that. Correct me if I'm wrong but you want to be able to reach the server from outside your LAN using the public address, BUT you also want to be able to access the server from the inside through the LAN. If that is the case, you want to use ONE interface and then create a virtual interface to reach it from the inside like this:

eth0 IP = 217.24.107.21
eth0:0 IP = 192.168.2.50

Then, plug in your Ubuntu server to your router with a single cable. You will then be able to reach it from inside using 192.168.2.50 and from outside using 217.24.107.21. I have several web servers running FreeBSD this way and they work great.

The reason you are seeing weird things happen is that the packet may go out through one nic and the ack packet may come back through the other nic. each one of them has a different MAC address and that confuses TCP/IP.

If you are in the US, there is no reason to use IPV6 at all, in fact it's a security risk here. 

-Tim

---

### Post by uGJ on 2009-10-20
Yes, I want to be able to access the server from LAN using the LAN IP address and directly from WAN using the WAN IP address. But the way you made it up, it wouldn't work since the Internet connection only works if the IP address was assigned by ISP's DHCP server. (I have tried setting an address manually to the same I got from DHCP, no data was allowed through)

Also, the router device there should be able to route requests to 217.24.107.21 (in your example) which it obviously couldn't do.

By poking around the settings in the modem, I managed to separate the connections. There was this VLAN configuration stating that both bridged ports were in the same VLAN, so also bridged together. I separated them into different VLAN's and now the ping problem is gone, as the lines are now virtually separate.

And interestingly enough, now the connection on eth0 also works. It didn't at first after doing those changes on the modem, but after deleting all contents of /var/lib/dhcp3/ it seemed to fix itself.

So in my case it's now resolved.

Thank you for everyone who showed interest in the problem and gave hints into what could be the problem. The problem appeared to be in a setting in the modem (I wonder why it didn't affect the router and connections going through it, though) and some old leases in /var/lib/dhcp3/ messing the DHCP client up.

---

### Post by koenn on 2009-10-20
Glad you got it working.

---

### Post by Iowan on 2009-10-21
> **uGJ said:**
> So in my case it's now resolved.Is it resolved enough to mark the thread [SOLVED] (Under Thread Tools)? :)

---

### Post by uGJ on 2009-10-21
> **Iowan said:**
> Is it resolved enough to mark the thread [SOLVED] (Under Thread Tools)? :)
I wouldn't have marked it as [SOLVED] otherwise ;)

It's been running fine since then in the way I wanted it to. No problems with ping or eth0 disconnecting every so often.

Well, there's a little problem that I cannot access the server with its WAN IP from my computer now, but that's the modem being retarded. And I can still access it via the LAN IP, as was the intention, so it's not a big issue, and definitely out of scope of Ubuntu anyway.

---

