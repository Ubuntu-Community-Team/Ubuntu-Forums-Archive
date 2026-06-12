---
title: "Server Has No Outbound Connections"
date: 2012-05-18
forum: Server Platforms
---

### Post by ginge6000 on 2012-05-18
Hi,

I hope someone can help as this is really vexing me!

I have an Ubuntu server (12.04) which runs 24/7 providing a MythTV backend, local DNS, email and a LAMP stack.  The other day I could no longer access the server from outside of my LAN which I figured this was probably a router problem.

When I was back home I discovered that although I could ping the server, connect to it via SSH and still stream MythTV recordings from it, I could only access its services by IP, not hostname.  Furthermore, the server can't connect to the internet at all nor can it ping a single machine on the network including the server.  I was testing the ping whilst connected via SSH so it was definitely on the network!

I've tried all sorts, including disabling the DNS server but still nothing.  I'm beginning to wonder if it is a hardware problem as it happened suddenly with no software/OS changes?

Please let me know if there is any additional detail I can provide that may allow you to help!

Cheers,

Ben

---

### Post by roelforg on 2012-05-18
First of all, the title is wrong: Those are inbound connections, outbound connections are when you connect to someone else's server outside your network (e.g. When you browse this site, you make an outbound connection).

Check what dns/nameserver your pc's are using.
Do you use dhcp? Cause if you do, check if your server's ip has changed.

---

### Post by ginge6000 on 2012-05-18
Sorry, I meant outbound as in the server can't connect to any other PCs but the other PCs can connect to the server.

The server is on a static IP (192.168.2.100).  All the PCs on the LAN use the router's IP as the DNS server.  The router has the server set as it's first nameserver and the ISP's nameserver as it's second.

Even when I returned the router to using both of my ISP's nameservers the server could still not ping the router.

---

### Post by ginge6000 on 2012-05-18
In case the following show anything that might be causing the issue:

**cat /etc/network/interfaces**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.100
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        dns-search nosdivad.net
        dns-nameservers 192.168.2.100
        # dns-* options are implemented by the resolvconf package, if installed
```

**ifconfig -a**
```

eth0      Link encap:Ethernet  HWaddr 00:16:e6:5e:f3:17
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fe5e:f317/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1571063 (1.5 MB)  TX bytes:642017 (642.0 KB)
          Interrupt:44 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:17970949 (17.9 MB)  TX bytes:17970949 (17.9 MB)

administrator@server:~$

```

**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

Please let me know if you can spot something that I've messed up!

---

### Post by koenn on 2012-05-18
> the server can't connect to the internet at all nor can it ping a single machine on the network including the server
do you ping addresses or names ?

---

### Post by ginge6000 on 2012-05-18
> **koenn said:**
> do you ping addresses or names ?
Hi,

I've tried both! 

If I ping the router by doing ```
ping 192.168.2.1
``` I get 100% packet loss.

I've also tried ```
ping router
``` which BIND correctly resolves to 192.168.2.1 and I still get 100% packet loss.

---

### Post by koenn on 2012-05-18
and it's the same with servers on the internet or ant machine on the network including the server ?

---

### Post by darkod on 2012-05-18
And you have no firewall activated on this server?

---

### Post by ginge6000 on 2012-05-18
> **koenn said:**
> and it's the same with servers on the internet or ant machine on the network including the server ?
I'm not sure I quite understand but this is the only machine on the network that can't access the router or the Internet. When I try to connect from outside the LAN the requests don't seem to be being forwarded to the server.

---

### Post by ginge6000 on 2012-05-18
> **darkod said:**
> And you have no firewall activated on this server?

No, I don't believe I do, I just rely on the routers firewall (please correct me if that's bad!).

---

### Post by darkod on 2012-05-18
Do you have another machine on the same network so you can try a ping? If you try to ping the server, does it respond?

Can it be that the network cable is bad, or the connection to a switch/router?

Try to establish if only the server can't ping out, or other machines can't ping the server too.

---

### Post by koenn on 2012-05-18
> **ginge6000 said:**
> I'm not sure I quite understand 
funny. It's something *you* said, and now you don't understand it ?
 
>   When I try to connect from outside the LAN the requests don't seem to be being forwarded to the server.
That's something your router should be taking care of

> this is the only machine on the network that can't access [the router or] the Internet.
Again, what do you mean with  can't access the Internet ? you cant"t ping internet op addresses ? you can't ping sites by name ? you can't get mail ? co can't access webpages on webservers ?

And you do realize that "When I try to connect from outside the LAN the requests don't seem to be being forwarded to the server" is not the same as "this server can't access  the Internet", right ?

---

### Post by ginge6000 on 2012-05-18
> **darkod said:**
> 
Try to establish if only the server can't ping out, or other machines can't ping the server too.
It's definately just the server. All other machines (1 windows, 1 Ubuntu desktop & an iPhone) can all ping and ssh onto the server as well as accessing the Internet just fine. The Ubuntu desktop is able to stream MythTV recordings from the server and all can browse I it's apache page using the IP (but not the host name) just fine. 

I'm beginning the think it's hardware related because nothing was changed on the server hitch caused it to happen. I've got a LAN tester somewhere so I'll check out all the cables first. I also just bought a new switch that I was planning on putting between the router and the rest of the network so I'll install that and see what happens. 

Thanks for your help so far!

---

### Post by ginge6000 on 2012-05-18
> **koenn said:**
> Again, what do you mean with  can't access the Internet ? you cant"t ping internet op addresses ? you can't ping sites by name ? you can't get mail ? co can't access webpages on webservers ?
The server cannot ping anything other than its own IP.  I can't ping any other machine IP on the network and it can ping any IP outside the network (8.8.8.8 for example). It also can't connect to any Internet addresss so (for example) apt-get update doesn't work. 

> And you do realize that "When I try to connect from outside the LAN the requests don't seem to be being forwarded to the server" is not the same as "this server can't access  the Internet", right ?
No, absolutely I understand that, it's just that both stopped working at the same time!

---

### Post by darkod on 2012-05-18
First, if machines on the network can access it by IP and not by hostname, something is wrong with your DNS. And this server is acting like a DNS for your network, right?

But that doesn't explain why ping 8.8.8.8 doesn't work from the server. Even with the DNS totally messed up, pinging an IP should work fine.

So it looks like you have combination of problems. Focus on the connection with the network, because if that is failing, it would explain the ping not working, and it would also explain why it can be reached by IP but not by hostname because this server is the DNS and if it's not communicating with the network it doesn't translate the hostname to an IP.

Try another cable, try another switch, try connecting it directly to the router with longer cable, etc...

So, you are sure you were not enabling any firewalls recently? Or that you are not using one, even if you didn't touch it recently the rules might have gotten messed up.

What does iptables say:
sudo iptables -L -n -v

Does it show INPUT and OUTPUT as ACCEPT?

---

### Post by koenn on 2012-05-18
in that case checking the cables is definitely a good idea.

maybe also reboot the router to make sure nothing is hanging.

then see what ethtool says

---

### Post by ginge6000 on 2012-05-18
> **darkod said:**
> What does iptables say:
sudo iptables -L -n -v

```
Chain INPUT (policy ACCEPT 2552K packets, 311M bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

Chain OUTPUT (policy ACCEPT 3137K packets, 2015M bytes)
 pkts bytes target     prot opt in     out     source               destination

```

---

### Post by darkod on 2012-05-18
OK, iptables is fine.

But we are still missing something.

Try setting it up with different IP and of course make sure it's out of the router dhcp range.

It doesn't make sense that other computers on the network have internet (so the router seems to be routing fine to the outside), they can reach the server, but the server can't ping anything on the LAM or go to the internet. It's weird...

---

