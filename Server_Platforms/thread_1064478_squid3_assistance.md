---
title: "squid3 assistance"
date: 2009-02-08
forum: Server Platforms
---

### Post by childs999 on 2009-02-08
Hi all

I'm having a bit of trouble with squid3, and would appreciate some help.

What I'm trying to do is create a transparent squid proxy, so that users don't have to modify any browser settings (and so they don't know that the proxy is even running!)

Squid afaik is configured correctly.
I've attached my squid.conf (squid.txt in the .tar file) for perusal.

Here is the layout of my network (all machines have def. gateway as .250)

LAN (.1->.249)->Juniper SSG20 (.250)->Internet
My squid box is .254 and is configured as follows:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:de:cb:d3
          inet addr:192.168.17.254  Bcast:192.168.17.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fede:cbd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1145124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815212 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000

Now the squid only works when I manually enter the settings into my browser - which makes me think it's not running transparently?

Also, do I need to forward ALL port 80 traffic from the Juniper hardware firewall (.250) to the squid box on port 80 (I have an iptables rule that forward web traffic on port 80->port 3128).

Appreciate any assistance!

cheers

---

