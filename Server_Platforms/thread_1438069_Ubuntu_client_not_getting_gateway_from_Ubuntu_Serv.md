---
title: "Ubuntu client not getting gateway from Ubuntu Server"
date: 2010-03-24
forum: Server Platforms
---

### Post by mavspire on 2010-03-24
Hi Everyone, 

I'm having some trouble figuring this out and would really appreciate some input. I'm convinced its something simple, but I just can't seem to figure it out.

I have an ubuntu (karmic) server setup as a webserver,email server, fileserver, router/firewall, dns and dhcp. Also have 10 windows clients and 5 ubuntu clients.

Basic topology is as follows:
(please note this is a test environment)
Internet
|
Router
|
Ubuntu Server (eth0 for local, eth1 for inet)
|
24 port Cisco Switch (no setup)
|
8 windows clients
5 ubuntu clients

The problem:
The ubuntu clients do not seem to be getting a gateway from the ubuntu server. They get IP addresses from the set range on the dhcp server but no gateways. ALL FIVE of the clients behave in this way. The 5 clients all have the SAME hardware setup. i.e they all have the same cpu/motherboard/ram/grafx/network setup. (same model was bought in bulk)

The windows computers range from windows xp, vista and windows 7; and can ALL get proper IP's and gateway information from the server.

Server gets its internet ip assigned (dhcp) via router (this is only in the test environment, once i am 100% on the server, it will connect directly to inet statically)

Therefore (correct me if im wrong) its something to do with client  side of things, possibly also my dhcp setup; perhaps subnetting?

ALSO it is important to note that if i connect the CLIENT ubuntu boxes directly into the ROUTER, they get inet right away; no probs.

Here's some code from the server, and also the client to shed more light.
[B]
SERVER dhcpd.conf[/B]
```
# Local Network on eth0
subnet 10.0.0.0 netmask 255.255.255.0 {
    authoritative;
    max-lease-time 7200;
    default-lease-time 600;
    option domain-name-servers 10.0.0.0;
    option broadcast-address 10.0.0.255;
    option subnet-mask 255.255.255.0;
    option routers 10.0.0.0;
    range 10.0.0.100 10.0.0.160;
    }

```**SERVER IFCONFIG**
```
eth0      Link encap:Ethernet  HWaddr #############
          inet addr:10.0.0.0  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:fe48:c5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13956 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12511 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:2503885 (2.5 MB)  TX bytes:10483361 (10.4 MB)
          Memory:fd9c0000-fd9e0000

eth1      Link encap:Ethernet  HWaddr ###############
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe48:a84d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21567 errors:1 dropped:0 overruns:0 frame:1
          TX packets:20828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11200431 (11.2 MB)  TX bytes:7703094 (7.7 MB)
          Interrupt:30

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:197636 (197.6 KB)  TX bytes:197636 (197.6 KB)
```**CLIENT NETSTAT -R output**
```
Kernel IP routing table
Destination     Gateway          Genmask                   Flags   MSS Window          irtt  Iface
10.0.0.0             0.0.0.0                 255.255.255.0     U             0                0                   0    eth0
```[B]

CLIENT IFCONFIG output[/B] (when connected to server)
```

eth0      Link encap:Ethernet  HWaddr ###########  
          inet  addr:10.0.0.100  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6  addr: fe80::225:11ff:fe01:ac44/64 Scope:Link
          UP BROADCAST  RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12255 errors:0 dropped:0 overruns:0 frame:0
           TX packets:13596 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000 
          RX bytes:10490434 (10.4 MB)   TX bytes:2442482 (2.4 MB)
          Interrupt:27 Base address:0x6000 

lo        Link  encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING   MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
           TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0 
          RX bytes:6924 (6.9 KB)  TX  bytes:6924 (6.9 KB)
```I have been able to establish a workaround by setting changing the "Default routers" on the dhcp server to 10.0.0.1 and the dns to 10.0.0.1 and then adding a virtual interface on the server with ip address 10.0.0.1 .

This seem to work well for about 1 minute on the clients until they seem to hit some sort of wall and come back alive after another minute....this is an endless loop.

So i then tried to set my local interface to 10.0.0.1, remove the virtual interface, and setup dhcp to run on 10.0.0.1 but i get an error trying to start dhcp as follows:

```
/etc/dhcp3/dhcpd.conf line 113: subnet 10.0.0.1 netmask 255.255.255.0: bad subnet number/mask combination.
subnet 10.0.0.1 netmask 255.255.255.0 
                                    ^
Configuration file errors encountered -- exiting
```Why can't i set dhcp to 10.0.0.1 ?? 

Would appreciate any help/suggestion/tools-in-the-face for a stupid/obvious solution.

---

### Post by mavspire on 2010-03-24
edit: my apologies for the double--post please look below

---

### Post by Iowan on 2010-03-24
10.0.0.0 would be the subnet address - No machine (server, dns server, etc) should have that address or the broadcast address (10.0.0.255). About anything else (except for what's already used by the router) should be kosher.

---

### Post by inphektion on 2010-03-24
I know in your dhcpd.conf you can't use 10.0.0.0 for:
option domain-name-servers 10.0.0.0;
    option routers 10.0.0.0;


routers should be the router IP. and same with dns. need to be actual IP's. not 10.0.0.0

---

### Post by mavspire on 2010-03-24
> **inphektion said:**
> I know in your dhcpd.conf you can't use 10.0.0.0 for:
option domain-name-servers 10.0.0.0;
    option routers 10.0.0.0;


routers should be the router IP. and same with dns. need to be actual IP's. not 10.0.0.0

This makes sense as when I set the dhcp client options to 10.0.0.1 ; my clients get the gateway of 10.0.0.1 .....

However, 10.0.0.1 does not exist?  ....

my eth0 (local facing interface on server) is set static to 10.0.0.0

I could set a virtual interface to 10.0.0.1 and then the ubuntu clients work, but only for a minute or two before they hit dead spot of some sort; then come back online for a min, then off again.

---

### Post by capscrew on 2010-03-24
> **mavspire said:**
> This makes sense as when I set the dhcp client options to 10.0.0.1 ; my clients get the gateway of 10.0.0.1 .....

However, 10.0.0.1 does not exist?  ....

my eth0 (local facing interface on server) is set static to 10.0.0.0

I could set a virtual interface to 10.0.0.1 and then the ubuntu clients work, but only for a minute or two before they hit dead spot of some sort; then come back online for a min, then off again.

What is the subnet mask for the 10.0.0.0 IP address.  Typically 10.0.0.0 indicates a network, not an individual host on the network.  The router is a host on the network and should have a valid IP address such as 10.0.0.1, 10.0.0.2 etc.

Edit: ```
inet addr:10.0.0.0  [COLOR="Red"]Bcast:192.168.1.255 [/COLOR] [COLOR="Blue"]Mask:255.255.255.0[/COLOR]
```

The item in red is not correct.

The item in blue says that the first address in the 1.0.0.0 network is 10.0.0.1 and the last address is 10.0.0.254 (not including the broadcast address of 10.0.0.255).

[SIZE="3"]No Double posting -- you only need to post your question in one sub-forum for all to see.  Double posting is confusing. [/SIZE]

---

### Post by cariboo on 2010-03-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by mavspire on 2010-03-24
> **capscrew said:**
> What is the subnet mask for the 10.0.0.0 IP address.  Typically 10.0.0.0 indicates a network, not an individual host on the network.  The router is a host on the network and should have a valid IP address such as 10.0.0.1, 10.0.0.2 etc.

Edit: ```
inet addr:10.0.0.0  [COLOR="Red"]Bcast:192.168.1.255 [/COLOR] [COLOR="Blue"]Mask:255.255.255.0[/COLOR]
```

The item in red is not correct.

The item in blue says that the first address in the 1.0.0.0 network is 10.0.0.1 and the last address is 10.0.0.254 (not including the broadcast address of 10.0.0.255).

[SIZE="3"]No Double posting -- you only need to post your question in one sub-forum for all to see.  Double posting is confusing. [/SIZE]

Sorry about the double post again; it was due to merged threads.

In regards to the BCAST; you are correct. It's wrong. But this is due to me switching to a 10.x.x.x ip range/subnetting from my previous 192.168.1.0 setup.

I am still confused. I understand that 10.0.0.0 indicates a network and that the "router" should have its own ip. But how do i set that in terms of dhcpd and also the interface its using?

When I tried to set dhcpd to 10.0.0.1; it failed to start. 

Is the solution to this to leave dhcpd as is and set my eth0 to 10.0.0.1 (and also fix the bcast)

---

### Post by capscrew on 2010-03-24
> **mavspire said:**
> Sorry about the double post again; it was due to merged threads.

In regards to the BCAST; you are correct. It's wrong. But this is due to me switching to a 10.x.x.x ip range/subnetting from my previous 192.168.1.0 setup.

Did you manually configure the interface or did you change the DHCP server IP address pool?> 

I am still confused. I understand that 10.0.0.0 indicates a network and that the "router" should have its own ip. But how do i set that in terms of dhcpd and also the interface its using?

Let's not confuse this too much.  What are YOU calling "the router"?  In my opinion both "the router" and your Ubuntu host are routers.  The IP address of these devices should never be controlled by DHCP.  If that IP address changes or fails to be configured your whole network is down.  This interface should **always be configured manually** (e.g a static IP address.> 

When I tried to set dhcpd to 10.0.0.1; it failed to start.

What did you do?  Explain this.>  

Is the solution to this to leave dhcpd as is and set my eth0 to 10.0.0.1 (and also fix the bcast)

Once again manually configuration is the proper way.

Can you describe "the router".  What is the addressing scheme for it's interfaces?  my reference is as you stated:```
Basic topology is as follows:
(please note this is a test environment)
Internet
|
Router
|
Ubuntu Server (eth0 for local, eth1 for inet)
|
```

---

### Post by mavspire on 2010-03-25
> **capscrew said:**
> Did you manually configure the interface or did you change the DHCP server IP address pool?Let's not confuse this too much.  What are YOU calling "the router"?  In my opinion both "the router" and your Ubuntu host are routers.  The IP address of these devices should never be controlled by DHCP.  If that IP address changes or fails to be configured your whole network is down.  This interface should **always be configured manually** (e.g a static IP address.What did you do?  Explain this.

Once again manually configuration is the proper way.

Can you describe "the router".  What is the addressing scheme for it's interfaces?  my reference is as you stated:```
Basic topology is as follows:
(please note this is a test environment)
Internet
|
Router
|
Ubuntu Server (eth0 for local, eth1 for inet)
|
```

To clear things up:

There are two routers in this particular case ; 
1 - a BELL dsl modem/router combo that assigns IPs in a 192.168.2.x.  
2 - the ubuntu server that handles requests from local windows/other ubuntu client

Back to the issue:

I have been able to resolve this issue by doing the following:

a - setting up the dhcpd subnet as 10.0.0.0 and salso
option domain-name-servers 10.0.0.1; 
    option routers 10.0.0.1;

b- Fixing the BCAST to 10.0.0.255 on eth0 (local facing interface) and also setting an IP of 10.0.0.1.

c- my linux firewall (iptables) was properly configured for routing/masquerading but for some reason it was not set to turn on at boot! .... I realized this while leaving one of the clients to ping google ; it managed to resolve to an ip which meant dns was working but no traffic was flowing through. Quick reset of the iptables and I was able to ping freely. the firewall has now been set to activate at boot.

All clients (windows/ubuntu) now get the gateway of 10.0.0.1 and dns of 10.0.0.1 

For some odd reason I was under the impression that 10.0.0.0 had to exist. But after reading here that 10.0.0.0 should not exist anywhere and normally just identifies a network it made sense.

Thanks everyone for your help; if you have any further suggestions on server/dhcp/firewall setup your in the mood to share; id appreciate it!

---

