---
title: "error with Multiple IP address in the same interface"
date: 2011-10-27
forum: Server Platforms
---

### Post by chrpinedo on 2011-10-27
Hello,

I need to configure multiple IP address in only one ethernet interface card (eth0). I have Ubuntu Server 11.10 64bits and I have configured "/etc/network/interfaces" as follows:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address net1-IP
        netmask 255.255.255.192
        gateway net1-GW
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        pre-up iptables-restore < /etc/iptables.rules

auto eth0:1
iface eth0:1 inet static
        address net2-IP
        netmask 255.255.0.0


But if I execute "ifconfig" i can only view the eth0 and lo interfaces:

eth0      Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          Direc. inet:net1-IP  Difus.:0.0.0.0  Másc:255.255.255.192
          Dirección inet6: fe80::d227:88ff:fe75:c290/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:2371126 errores:0 perdidos:925 overruns:0 frame:0
          Paquetes TX:987219 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:306355542 (306.3 MB)  TX bytes:285228911 (285.2 MB)
          Interrupción:40 Dirección base: 0x4000

lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:28563 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:28563 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:2559324 (2.5 MB)  TX bytes:2559324 (2.5 MB)
 
# ifconfig eth0:1
eth0:1    Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:40 Dirección base: 0x4000


But, "netstat -putan" shows me several service listening in the second IP. For example the NTP service:


udp        0      0 **net2-IP:123**         0.0.0.0:*                           1322/ntpd
udp        0      0 **net1-IP:123**      0.0.0.0:*                           1322/ntpd
udp        0      0 127.0.0.1:123           0.0.0.0:*                           1322/ntpd
udp        0      0 0.0.0.0:123             0.0.0.0:*                           1322/ntpd
udp6       0      0 ::1:123                 :::*                                1322/ntpd
udp6       0      0 fe80::d227:88ff:fe7:123 :::*                                1322/ntpd
udp6       0      0 :::123                  :::*                                1322/ntpd

What is happenging here????!

Thanks,

Christian

---

### Post by Drenriza on 2011-10-27
What!?:p

You cannot have more then one IPv4 or IPv6 address or mac address for that matter on one interface. Ethernet, Fast-Ethernet, Gigabit-Ethernet, Fiber and so on.

Also why o why would you do such a thing?

Kind regards.

Edit.
Quick search on google. 
If you wanna do this because of this example.
> This tutorial demonstrates how to bind multiple IP addresses to a single NIC. By using multiple IP's you can run a service under a specific IP while having another service under a different one (for example, have HTTP on one and SMTP on another), or create a private LAN using a local IP and have the alias hold your Internet IP (such as NAT). One of the major benefits is that you don't need a physical adapter for each IP but instead can create many virtual ones tied to a single physical card. The instructions provided apply to RedHat, Fedora, and CentOS. I'll be using LAN IP's in this example, so replace them with the ones you'll be using.

You deserve a punch in the nutts.:D
Just specify different ports for the different services with NAT. And use a single ip address.

---

### Post by bab1 on 2011-10-27
> **Drenriza said:**
> What!?:p

You cannot have more then one IPv4 or IPv6 address or mac address for that matter on one interface. Ethernet, Fast-Ethernet, Gigabit-Ethernet, Fiber and so on.

Sure you can.  IP Aliasing has been part of the Linux kernel for a long time.> 

Also why o why would you do such a thing?

Kind regards.

Edit.
Quick search on google. 
If you wanna do this because of this example.


You deserve a punch in the nutts.:D
Just specify different ports for the different services with NAT. And use a single ip address.
Pretty judgmental there don't you think.  Read up on the technique BEFORE you  start telling folks they are wrong.  You can start with [**_[COLOR="DarkSlateGray"]this article from IBM[/COLOR]_**]("http://www.ibm.com/developerworks/web/library/wa-multissl/index.html") on the subject.

---

### Post by SeijiSensei on 2011-10-27
```
auto eth0
iface eth0 inet static
address net1-IP
netmask 255.255.255.192
gateway net1-GW
```

Shouldn't the address lines in /etc/network/interfaces have IP address entries?  Even if net1-IP is in /etc/hosts, I'm not sure that the network startup scripts will do any name resolution.  Just put the actual addresses in there for the "address" and "gateway" fields, not symbolic names.

I've used interface aliasing when I wanted to have a separate HTTP and HTTPS servers on the same box.  Since HTTPS doesn't take too well to name-based virtual hosts, it's easier to assign a second IP address to the NIC and bind the HTTPS server to that address.

Of course you need an ISP that will give you an IP subnet, not just a single address to make this work.  Many ISPs will give their commercial customers a /29 or even a /28, though that's less common in these days of IP address shortages.

The netmask you're using (255.255.255.192) is for a /26, or 62 usable addresses.  Did your ISP really give you a /26?  Pretty generous if so.

---

### Post by chrpinedo on 2011-10-28
> **SeijiSensei said:**
> ```
auto eth0
iface eth0 inet static
address net1-IP
netmask 255.255.255.192
gateway net1-GW
```Shouldn't the address lines in /etc/network/interfaces have IP address entries?  Even if net1-IP is in /etc/hosts, I'm not sure that the network startup scripts will do any name resolution.  Just put the actual addresses in there for the "address" and "gateway" fields, not symbolic names.


I have put "net1-IP" and "net1-GW" instead of the IP address that I have in the /etc/network/interfaces files. It's only because I didn't want to show the IP address of the server :-D


> **SeijiSensei said:**
> 
I've used interface aliasing when I wanted to have a separate HTTP and HTTPS servers on the same box.  Since HTTPS doesn't take too well to name-based virtual hosts, it's easier to assign a second IP address to the NIC and bind the HTTPS server to that address.

Of course you need an ISP that will give you an IP subnet, not just a single address to make this work.  Many ISPs will give their commercial customers a /29 or even a /28, though that's less common in these days of IP address shortages.

The netmask you're using (255.255.255.192) is for a /26, or 62 usable addresses.  Did your ISP really give you a /26?  Pretty generous if so.

We are an ISP so we don't have that problem :-D. 

I agree with you regarding to interface aliasing is very old, but it seems to be well configured as you can see in my /etc/network/interfaces file but ifconfig don't show the interface aliases:

```

root@server:~# ifconfig
eth0      Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          Direc. inet:X.X.X.X  Difus.:0.0.0.0  Másc:255.255.255.192
          Dirección inet6: fe80::d227:88ff:fe75:c290/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:4458717 errores:0 perdidos:1674 overruns:0 frame:0
          Paquetes TX:1717477 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:586832356 (586.8 MB)  TX bytes:432502236 (432.5 MB)
          Interrupción:40 Dirección base: 0x4000

lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:53176 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:53176 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:4708318 (4.7 MB)  TX bytes:4708318 (4.7 MB)

root@server:~# ifconfig eth0:1
eth0:1    Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:40 Dirección base: 0x4000


```
It seems a bug, it isn't? or Am I doing something bad?

---

### Post by Drenriza on 2011-10-28
> Pretty judgmental there don't you think. Read up on the technique BEFORE you start telling folks they are wrong.
If you think i am unknowing about this, then inlighten me. In what situation it would be beneficial to split a single network NIC to multiple ip addresses.

---

### Post by SeijiSensei on 2011-10-28
> **chrpinedo said:**
> It seems a bug, it isn't? or Am I doing something bad?

Perhaps it's not possible to do this through the interfaces file?

What happens if you remove the entry for eth0:1 from that file then configure the interface manually with ifconfig?  When I've used aliasing, I've assigned the address to the aliased interface with an ifconfig command in /etc/rc.local.

> **Drenriza said:**
> If you think i am unknowing about this, then inlighten me. In what situation it would be beneficial to split a single network NIC to multiple ip addresses.

Read my post above for one example.

---

### Post by karlson on 2011-10-28
> **Drenriza said:**
> If you think i am unknowing about this, then inlighten me. In what situation it would be beneficial to split a single network NIC to multiple ip addresses.

If you are listening to multiple vlans on the same interface when aggregating certain feeds to come to one physical interface.  Hardware clustering such as Veritas Cluster server.

---

### Post by redmk2 on 2011-10-28
> **chrpinedo said:**
> I have put "net1-IP" and "net1-GW" instead of the IP address that I have in the /etc/network/interfaces files. It's only because I didn't want to show the IP address of the server :-D




We are an ISP so we don't have that problem :-D. 

I agree with you regarding to interface aliasing is very old, but it seems to be well configured as you can see in my /etc/network/interfaces file but ifconfig don't show the interface aliases:

```

root@server:~# ifconfig
eth0      Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          Direc. inet:X.X.X.X  Difus.:0.0.0.0  Másc:255.255.255.192
          Dirección inet6: fe80::d227:88ff:fe75:c290/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:4458717 errores:0 perdidos:1674 overruns:0 frame:0
          Paquetes TX:1717477 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000
          Bytes RX:586832356 (586.8 MB)  TX bytes:432502236 (432.5 MB)
          Interrupción:40 Dirección base: 0x4000

lo        Link encap:Bucle local
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:53176 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:53176 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0
          Bytes RX:4708318 (4.7 MB)  TX bytes:4708318 (4.7 MB)

root@server:~# ifconfig eth0:1
eth0:1    Link encap:Ethernet  direcciónHW d0:27:88:75:c2:90
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Interrupción:40 Dirección base: 0x4000


```
It seems a bug, it isn't? or Am I doing something bad?
That seems odd.  What do you get with ```
ifconfig [COLOR="Red"]-a[/COLOR]
```

---

### Post by HugoSerrano on 2011-10-28
Hello!

What you want it's perfectly normal.

But you need to do something more then that!
With the information that you're giving, i can see that both ip's are from different network, so the server must be connected to a port on the switch, with both Vlans configured.
After that, you can follow this:
[https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)

:-) If you need more help, just pass-by!

Best regards!

---

### Post by redmk2 on 2011-10-28
> **Drenriza said:**
> If you think i am unknowing about this, then inlighten me. In what situation it would be beneficial to split a single network NIC to multiple ip addresses.

You don't "split" the NIC up at all.  The NIC has a primary IP address (i.e. [COLOR="Blue"]eth0[/COLOR]) and can have aliases assigned ([COLOR="Blue"]eth0[/COLOR][COLOR="Red"]:1[/COLOR].  The host with the NIC responds to either IP address.  Once again; the secondary addresses are not separate they are just *aliases of the primary IP addresses.*.

Did you read the hyperlink in @bab1's post #3?  What about the posts of @SeijiSensei and @karlson?  Here is some more [**_[COLOR="DarkSlateGray"]info[/COLOR]_**]("http://lmgtfy.com/?q=ip+aliases").

---

### Post by elico on 2011-10-28
you should have something like this

> iface eth0:1 inet static
        address 10.0.0.250
        netmask 255.255.255.0
        broadcast 10.0.0.255
        network 10.0.0.0

try to do
/etc/init.d/networking restart

and see if there are any error messages.

---

### Post by Drenriza on 2011-10-31
To quote myself
> If you think i am unknowing about this, then inlighten me. In what situation it would be beneficial to split a single network NIC to multiple ip addresses.

>  #1 If you are listening to multiple vlans on the same interface when aggregating certain feeds to come to one physical interface.

And

> Read my post above for one example.
The post
> #2 I've used interface aliasing when I wanted to have a separate HTTP and HTTPS servers on the same box.

Quote #1.
Sounds like something that should be dealt with in the network, before it reaches the server.
But perhaps i'am misunderstanding you, and in this case i would need more details, to make a better decision.

Quote #2.
Not really much to do in such a case. But i don't see a valid reason to use the same NIC if you want to separate traffic. And also with a few clicks and 2 mins i found a 1Gbps PCI-E NIC to 15$. Then you firstly get the desired need, to separate traffic, and it makes more sense. And i don't see the xtra 15$ to be a issue.

Edit.
> You don't "split" the NIC up at all. The NIC has a primary IP address (i.e. eth0) and can have aliases assigned (eth0:1. The host with the NIC responds to either IP address. Once again; the secondary addresses are not separate they are just aliases of the primary IP addresses..
I understand that. But what i have failed to see so far. Is a valid situation where it would be a beneficial feature + make sense, to use.

---

### Post by gbiellem on 2011-10-31
I think it's a bug in 11.10

I tried it on 10.04.3 server and it works fine. :D
Tried 11.10 server and I get the same results as you...fail :confused:

---

### Post by gbiellem on 2011-10-31
The main reasons I use aliasing of IPs is for Apache IP-based Virtual Host Support ( [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/) )

---

### Post by elvar on 2011-10-31
> **gbiellem said:**
> I think it's a bug in 11.10

I tried it on 10.04.3 server and it works fine. :D
Tried 11.10 server and I get the same results as you...fail :confused:

I definitely think it is a bug. None of my aliases show up in 11.10 but the same exact same interfaces file worked fine in 11.04. This is very annoying.

---

### Post by patryk_w on 2011-10-31
from my ubuntu 11.10 with WORKING aliases:
```

root@atom:/etc/network# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth0:0
        iface eth0:0 inet static
        name Ethernet alias LAN card
        address 192.168.6.1
        netmask 255.255.248.0
        broadcast 192.168.7.255
        network 192.168.6.0

auto eth0:1
        iface eth0:1 inet static
        name Ethernet alias LAN card
        address 192.168.6.2
        netmask 255.255.248.0
        broadcast 192.168.7.255
        network 192.168.6.0
#and so on...

```
system is responding on all IPs, but they are not showing in output from ifconfig.
still that's good enough for me :D

---

### Post by LukeQuake on 2011-11-17
Hey All,

Did anyone manage to find a fix for this or further details? I upgraded three of our boxes to Ubuntu 11.10 from 11.04 earlier today and all three have lost their aliased adapters! I can't seem to manually recreate them either, just getting "SIOCSIFFLAGS: Cannot assign requested address". The alias were working fine earlier today (before the upgrade).

Any help is greatly appreciated.

Regards,

Luke

---

### Post by LukeQuake on 2011-11-17
Official Bug Report Found Here: [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829)

---

### Post by hawkmage on 2011-11-19
> **Drenriza said:**
> To quote myself
And


The post


Quote #1.
Sounds like something that should be dealt with in the network, before it reaches the server.
But perhaps i'am misunderstanding you, and in this case i would need more details, to make a better decision.

Quote #2.
Not really much to do in such a case. But i don't see a valid reason to use the same NIC if you want to separate traffic. And also with a few clicks and 2 mins i found a 1Gbps PCI-E NIC to 15$. Then you firstly get the desired need, to separate traffic, and it makes more sense. And i don't see the xtra 15$ to be a issue.

Edit.

I understand that. But what i have failed to see so far. Is a valid situation where it would be a beneficial feature + make sense, to use.
Yes you can add a single port NIC very easily and cheaply if you have an available slot to put it what about  having to have an extra network cable and port on a router/switch.

The use of virtual interfaces/multiple IP addresses has been around for a long time and it is a feature that quite commonly used on large systems.  Why should an administrator have to add hardware to a system when it is not required.  

If I wanted to set up a system to either host or proxy for 8 different instances of Apache.  And yes there are good reasons to choose to run them as separate instances and not use virtual sites.  How are you going to get each of the Apache instances to use port 80 and/or 443 without multiple IP address?  With your solution I would have to have to have either 8 NICs or  2 quad port NICs to accommodate.  WIth virtual interfaces no extra hardware is needed.

Another things that was mentioned is the use of VLANs.  This is taking the idea of virtual NICs to the next level, you are basically defining a Virtual network using the same hardware.  

Throwing hardware at a solution may be the easiest but is not always the best solution.

It is much quicker to configure a set of Virtual interfaces and VLANs to implement something that it is to reconfigure a systems hardware and the network to do what you want.  In my home network when I decided to use a VoIP service for my phones I dod not want it on the same network as the rest of my systems I did not have to changes anything in my physical network.  I just defined a virtual interface on a different VLAN for the VoIP device and set the port on my switch for that VLAN and I was done in 5 minutes.  Without virtual interfaces it it would have been hours to get the new hardware and rerun/connect some of my network.

---

### Post by unius on 2012-01-26
hey people, this is a bug, but not really big one, just compiled with *_ifconfig_* command.
I had the same problem (example):

#######################@/etc/network/interfaces##################
# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	dns-nameservers 84.32.38.10

# 1st additional interface
auto eth0:0
iface eth0:0 inet static
	address 192.168.0.129
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
#################################################################
unius@entranced:~$sudo /etc/init.d/networking restart

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                RTNETLINK answers: File exists
_Failed to bring up eth0:0._
#################################################################
unius@entranced:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:17:42:74:d2:5a  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:42ff:fe74:d25a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2123531 (2.1 MB)  TX bytes:801660 (801.6 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13263 (13.2 KB)  TX bytes:13263 (13.2 KB)


ping 192.168.0.129
PING 192.168.0.129 (192.168.0.129) 56(84) bytes of data.
64 bytes from 192.168.0.129: icmp_req=1 ttl=64 time=0.059 ms
..................................................
#################################################################
seems that eth0:0 is working, and is accessible from anetwork devices:
#################################################################
Raisecom#sho int ip
Index     Ip Address       NetMask          Vid               Status
-----------------------------------------------------------------
0         192.168.0.15     255.255.255.0    1                 active
Raisecom#ping 192.168.0.129 
Type CTRL+C to abort.
Sending 5, 8-byte ICMP Echos to 192.168.0.129 , timeout is 3 seconds:
!!!!!
---- PING Statistics----
5 packets transmitted,
5 packets received, Success rate is 100 percent(5/5) 
round-trip (ms)  min/avg/max = 0/0/0
#################################################################
so the bug is ifconfig's output :-({|=

---

### Post by unius on 2012-01-26
BTW I'm using 11.10 desktop

---

### Post by SeijiSensei on 2012-01-26
Some [progress]("https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/876829") has been made on this bug.

---

