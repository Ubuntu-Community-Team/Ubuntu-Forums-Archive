---
title: "Do I need a custom kernel for my NAS?"
date: 2009-08-15
forum: Server Platforms
---

### Post by fela on 2009-08-15
I installed the Ubuntu 8.10 desktop version (which has now been upgraded to 9.04 against my better judgement, by an unwitting soul :P). My question is that is having a custom kernel designed for throughput instead of low latency important? It seems to run alright, but I'd love to get some extra decent performance out of it. The big thing is, one person does access it from time to time via VNC, which I presume would be more needy of low latencies.

What do you think? All it's used for is servers (lots of them), there's no desktop apps such as music playing involved. I'd compile the custom server kernel on a different (faster) computer, and I'd have to compile it as 32bit (the faster computer is 64bit) as - even though the server has an athlon64 - the OS is all 32 bit and I wouldn't fancy reinstalling the whole OS now.

---

### Post by hessiess on 2009-08-15
It wouldn't make much difference, VNC, like any remote desktop protocol is extremely bloated as it has to transfer 1024x768x32+ of image data quickly enough to look smooth. The bottleneck here will always be the bandwidth of the underlying network transport. If you want a more responsive remote connection, ditch the GUI and just use SSH, which has MUCH less overhead.

---

### Post by fela on 2009-08-16
> **hessiess said:**
> It wouldn't make much difference, VNC, like any remote desktop protocol is extremely bloated as it has to transfer 1024x768x32+ of image data quickly enough to look smooth. The bottleneck here will always be the bandwidth of the underlying network transport. If you want a more responsive remote connection, ditch the GUI and just use SSH, which has MUCH less overhead.

I don't actually use the GUI, my dad does. I always SSH into it, with the -Y option sometimes to run GUI programs locally (if I absolutely have to - eg setting up a printer is easier in the GUI when it works :)).

I think there's something bottlenecking the bandwidth to 10 MB/s even though it's supposed to be a 10/100 ethernet network and both NICs in my comp and the server are both 10/100 (very similar GIGABYTE mobos). EDIT: could be the ultra cheap netgear router. Doubt it though as they're all 10/100 at least, sometimes even 1000, aren't they? I know that it's being bottlenecked because when I transfer something from my computer to the server via an NFS share it's always at exactly 10MB/s. Strange.

The reason I was looking into a custom kernel wasn't to speed up VNC (I knew the bottleneck was the network) - I just thought that some things would run more efficiently as they're not constantly having to deal with high priority processes such as pulseaudio to slow them down.

Maybe I'll ditch that idea though, as it seems to be running pretty well right now. :)

---

### Post by handy on 2009-08-16
Have you done any tuning of your NFS setup?

I use FreeNAS, & wasn't getting very good transfer speeds, so I played around with some NFS settings & it dramatically improved the situation.

This page may get you started, the stuff down near the end of the page is what did it for me:

[http://www.dba-oracle.com/oracle_tips_linux_nfs.htm](http://www.dba-oracle.com/oracle_tips_linux_nfs.htm)

---

### Post by fela on 2009-08-16
> **handy said:**
> Have you done any tuning of your NFS setup?

I use FreeNAS, & wasn't getting very good transfer speeds, so I played around with some NFS settings & it dramatically improved the situation.

This page may get you started, the stuff down near the end of the page is what did it for me:

[http://www.dba-oracle.com/oracle_tips_linux_nfs.htm](http://www.dba-oracle.com/oracle_tips_linux_nfs.htm)

I have tried tweaking it actually, I'm currently using the async option and using hard mounts. It's not related (99% sure) to NFS, I always get exactly 10MB/s on every protocol that I use. It has to be a network bottleneck somewhere. Oh well, it's not exactly like I'm booting off an NFS share or using it as my home partition...although that would be cool!

---

### Post by HermanAB on 2009-08-16
Lose the VNC.

This is better:
$ ssh -X -C -c blowfish user@server gnome-panel

---

### Post by fela on 2009-08-16
> **HermanAB said:**
> Lose the VNC.

This is better:
$ ssh -X -C -c blowfish user@server gnome-panel

Of course I would do exactly that (maybe not with the -C and -c - we're on a secure and reasonably fast home network here) - but my dad uses windows, ie no X11. I use X11 on my Linux box but that's besides the point as I always use the command line (or web interface) on it - I never need the GUI.

---

### Post by cariboo on 2009-08-16
Most nics are rated in Mbps, so if you have a 100Mbps nic it should transfer up to 12.5 MBps in a perfect world. Due to line loses, dodgy connections, the best I've ever seen with a 100Mbps nic is about 11MBps. Running ethtool on eth0 this is the result I get:

```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	**Speed: 100Mb/s**
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
``` 

I have bolded the speed my nic runs at. Unfortunately in a mixed network, it will run at the speed of the slowest device, so if your router, switch or any computer on the network only supports 100Mbps that is the maximum speed of your network throughput.

A good way to check your internal network throughput is to use iperf. It is in the repositories, and there is also Windows and Mac versions available. Setup one of the computers on the nextwork as a server:

```
sudo iperf -s
```

then run iperf on one of the other computers run:

```
sudo iperf -c <server name>
```

This the result I get between the computer I'm using right now and my server:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.100 port 60952 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    113 MBytes  94.6 Mbits/sec
```

For more options check man iperf.

---

### Post by HermanAB on 2009-08-16
If your Dad uses Windows, then install MinGW and PuTTY (run Mingw first!) then launch gnome-panel.  This is xigackly the same as on Linux.  You can safely lose the VNC cruft.

---

### Post by fela on 2009-08-17
@kariboo907 - that explains it then! I know that HDD manufacturers are cheeky like that aswell. They say the number of gigabytes a harddrive has but in 1,000,000,000 bytes instead of 1,073,741,824 bytes as almost every OS displays. Therefore it appears that it has an extra few gigs (or an extra 50GB in the case of my old 750 (700) GB harddrive :)).

> **HermanAB said:**
> If your Dad uses Windows, then install MinGW and PuTTY (run Mingw first!) then launch gnome-panel.  This is xigackly the same as on Linux.  You can safely lose the VNC cruft.

I already had PuTTY installed, never heard of MinGW...I could try that. Thanks :) I didn't know you could have X11 ontop of windows. Well I know you can have KDE4 on windows but that doesn't run on X11 in that case does it?

---

