---
title: "SFTP server Incredibly SLOW"
date: 2009-11-02
forum: Server Platforms
---

### Post by veaviticus on 2009-11-02
I have a simple server set up. Its running the latest build of Ubuntu Server. It is set on a static IP on my router, which is mapped by DynDns to a hostname. When I connect to the server using SFTP via Nautilus on my desktop (connected wired to the same router that the server is connected to) through that internet hostname, I get transfer speeds in the realm of 5-8 Mbps. However, when I do the same technique using my laptop, connected wireless to a network at my school's campus, I get transfer speeds between 20 and 200 BYTES/sec. Painful at best. Even dialing in via the terminal using ssh, getting the login line takes 10 seconds. And once logged in, even typing lags behind, thats how slow the connection is. I can't figure out what would cause things to be so slow when connected wirelessly. 

My laptop is a fresh install of Ubuntu 9.04 Desktop, which has not had anything done to it yet (a.k.a putting the hostname in te hosts file or setting up a key-based authorization). I'm pretty new to all this, so I didn't want to mess anything up before I got some confirmation.

Any ideas?

---

### Post by Lars Noodén on 2009-11-02
And ADSL stands for "asymmetric digital subscriber line", the asymmetric part means that the transfer from the Internet to your LAN will be faster than transfers from your LAN to the Internet.  

The speed inside your LAN is going to be much faster than your Internet connection, in either direction.  Usually it is 10 Mbps, 100Mbps, or 1000Mbps depending on the quality of the router.  I'm sad to say that 10Mbps still get sold at high price.

What bandwidth does your ISP advertise that you are supposed to get?  Does it say that in your contract?

What are the rudimentary connection speeds TO you home router FROM your school wireless in general?

e.g. 

[INDENT][FONT="Courier New"]#
ping -c 5 *xx.yy.zz.aa*

# without dns lookups
traceroute -N 1 -n *xx.yy.zz.aa*
# or 
sudo traceroute -T -N 1 -n -p 22 *xx.yy.zz.aa*


# with dns lookups
traceroute -N 1 *xx.yy.zz.aa*
# or 
sudo traceroute -T -N 1 -p 22 *xx.yy.zz.aa*[/FONT][/INDENT]

---

### Post by veaviticus on 2009-11-02
Well I'm not on campus anymore, but I can tell you that at my apartment I have Charter at 10 mbps download speed. I just ran a SpeedTest and got 18.2 megabits download and 2.2 megabits upload speed.
Also, when I connect to my server from within my network, I connect to the external IP address of my router, not through my LAN. So wouldn't I be connecting the same way from my laptop?

thank You much for replying so fast

Robert Nelson

---

### Post by Lars Noodén on 2009-11-03
> **veaviticus said:**
> Well I'm not on campus anymore, but I can tell you that at my apartment I have Charter at 10 mbps download speed. I just ran a SpeedTest and got 18.2 megabits download and 2.2 megabits upload speed.
Also, when I connect to my server from within my network, I connect to the external IP address of my router, not through my LAN. So wouldn't I be connecting the same way from my laptop?


No, it would not be connecting the same way, at least not according to the network topology you originally described.  According to that, the simplest possible arrangement would be something like the below.  Though it's almost 100% sure to be more steps on the outside.

Also, I'm going to assume that the connection is in Mbps.  If you're paying for mbps in 2009 ...

```

    A                B           C          D          E           F

+--------+
| home   |        +------+     +---+     +-----+     +----+    +----------+
| server |        =   A  |     | I |     |  C  |     |  W |    | school   |
| [sshd]<=-----<--= + D<-=-<---=-S-=<----=--A -=<----=--I-=<---= [ssh]    |
+--------+        = | S  |     | P |     |  M  |     |  F |    | notebook |
                  = | L  |     +---+     |  P  |     |  I |    +----------+
+--------+        = | M  |               |  U  |     +----+
| home   |        = | O  |               |  S  |
| desk   |        = | D  |               +-----+
| [ssh]--=----->--= + E  |
+--------+        =   M  |
                  =      |
                  +------+

```

Ok.  
Between A and anything else on A, you have 10Mbps or whatever your modem is rated as for a hub or switch.

Between B and C, you get, according to the numbers you post, 18.2 mbps going in the direction from C to B download and 2.2 mbps when going from B to C.   

Between C and D, as well as from D and E, it's probably going to be the same both directions.  It is also probably going to be the fastest part of the link.  But for now it is an unknown.

Between E and F, it's going to be slow or if you are sitting where there is a bad signal, slower.  Probably around 11Mbps.  

So, with those numbers, your connection from F to A is going to be a theoretical maximum of 2.2mbps.  However, you lose a bit at each junction.
How many hops were shown in your traceroute test from F to A?  That loss is greater if you have other users on the network at the same time.  What else do you have running that could be using the bandwidth from B to C?  

However, even 2.2Mpbs  should be fast enough to type.  Again, check your connection from F to A with traceroute to see where the bottleneck might be.  

You can also try starting the client requesting compression.  -C
However, that will only help if the processor can handle the load.

---

### Post by veaviticus on 2009-11-03
Ok so I'm back on campus. Here's the results of those pings you had me run 

I've omitted my vital statistics so its not thrown out there on the interwebs.
_____________________________________________________
[FONT=Courier New]**ping -c 5 **[I]**xx.yy.zz.aa**

PING xxx.yy.com (xx.yy.zz.aa) 56(84) bytes of data.

--- xxx.yy.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


[/I][/FONT]**[FONT=Courier New]sudo traceroute -T -N 1 -p 22 *xx.yy.zz.aa*[/FONT]**
[FONT=Courier New][I]
traceroute to xxx.yyy.com (7xx.yy.zz.aa), 30 hops max, 60 byte packets
 1  131.212.196.253 (131.212.196.253)  1.318 ms  2.291 ms  0.909 ms
 2  dlh-cb-01-po-2.4012.ggnet.umn.edu (146.57.237.57)  2.555 ms  1.760 ms  1.725 ms
 3  192.168.212.194 (192.168.212.194)  15.954 ms  14.590 ms  14.782 ms
 4  172.25.0.213 (172.25.0.213)  15.065 ms  20.461 ms  18.667 ms
 5  172.25.1.113 (172.25.1.113)  17.283 ms  14.539 ms  14.566 ms
 6  172.25.1.106 (172.25.1.106)  15.291 ms  15.109 ms  14.437 ms
 7  172.25.1.162 (172.25.1.162)  14.618 ms  14.629 ms  22.777 ms
 8  172.25.0.130 (172.25.0.130)  17.568 ms  46.776 ms  14.625 ms
 9  172.25.0.158 (172.25.0.158)  14.767 ms  14.979 ms  14.659 ms
10  172.25.0.38 (172.25.0.38)  16.779 ms  15.604 ms  14.925 ms
11  telecomb-bn-02-v3220.ggnet.umn.edu (146.57.238.33)  15.683 ms  15.115 ms  17.173 ms
12  telecomb-br-02-v3229.ggnet.umn.edu (146.57.238.34)  628.327 ms  645.993 ms  570.259 ms
13  telecomb-br-01-te-4-2.ggnet.umn.edu (192.35.86.29)  575.071 ms  564.742 ms  588.210 ms
14  telecomb-gr-01-ten-2-3.northernlights.gigapop.net (146.57.252.178)  604.497 ms  560.637 ms  739.311 ms
15  infotech-gr-01-te-2-1.northernlights.gigapop.net (146.57.252.129)  615.521 ms  649.694 ms *
16  i2cpsv4-nlg.northernlights.gigapop.net (146.57.253.10)  717.586 ms * *
17  eqx.10ge.ord.wvfiber.net (206.223.119.18)  481.870 ms  547.640 ms  542.284 ms
18  mad-ten4-2-chi-ten1-5.wvfiber.net (64.127.129.150)  529.470 ms  553.353 ms  569.949 ms
19  64.127.130.30 (64.127.130.30)  587.706 ms  596.682 ms  581.026 ms
20  crr01ftbgwi-tge-0-1-0-0.ftbg.wi.charter.com (96.34.16.46)  629.874 ms  650.582 ms  553.645 ms
21  96-34-16-77.static.unas.wi.charter.com (96.34.16.77)  538.285 ms  479.656 ms  445.786 ms
22  96-34-16-228.static.unas.wi.charter.com (96.34.16.228)  515.282 ms  505.313 ms  535.343 ms
23  crr01dlthmn-gbe-2-0-0.eucl.wi.charter.com (96.34.16.73)  481.480 ms  421.181 ms  430.926 ms
24  csw01dlthmn-tge-8-1.eucl.wi.charter.com (96.34.16.13)  408.863 ms  386.810 ms  482.359 ms
25  cts02dlthmn-gbe-2-0-0.eucl.wi.charter.com (96.34.25.71)  424.924 ms  425.461 ms  469.305 ms
26  xx-yy-zz-aa.dhcp.dlth.mn.charter.com (xx.yy.zz.aa)  449.800 ms  467.722 ms  574.208 ms
27  xx-yy-zz-aa.dhcp.dlth.mn.charter.com (xx.yy.zz.aa)  52.016 ms  50.140 ms  52.930 ms


[/I]I'm not running anything else in the background, a fresh reboot. Opened terminal and ran the commands, so there shoudln't be anything taking up any bandwidth. My router and modem are brand new, with the router being a linksys N router.

I don't know if this provides you with any valuable information. Internet browsing from campus is normal for a wireless signal, the only thing that is slow is accessing my server.

But thank you for taking so much time to explain things to me. I'm learning alot :)

Robert Nelson
[/FONT]

---

### Post by Lars Noodén on 2009-11-05
Thanks.  

The last step is fast, so it's not your server nor your home network.

The first steps are fast, so it's not your notebook nor the school's Wifi LAN.  

You see at step 12, it suddenly gets slower by an order of magnitude?
From the traceroute, these networks are slow, either on purpose or by accident:

 ggnet.umn.edu
 northernlights.gigapop.net
 wvfiber.net
 wi.charter.com
 mn.charter.com

The operators of those networks would be the ones to contact.  There are a lot of reasons for bandwidth to be used up, including Windows worms. Other reasons include over-selling bandwidth, misconfiguration, etc.   

You can get the contact information by looking up the ip number in [http://manpages.ubuntu.com/manpages/karmic/en/man1/whois.1.html]whois[/url] or on your contract if you have a direct  agreement.

Each step between 12 and 26, about 14 hops, takes about half a second. Again, each step takes a little away from the speed and overall transmission suffers.  For the process see [http://condor.depaul.edu/~jkristof/technotes/tcp.html](http://condor.depaul.edu/~jkristof/technotes/tcp.html)

---

