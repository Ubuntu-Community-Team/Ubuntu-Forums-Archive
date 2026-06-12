---
title: "NFS Configuration for 10 Gbit Ethernet?"
date: 2016-12-31
forum: Server Platforms
---

### Post by mattlach on 2016-12-31
Hey all,

So I recently ran a dedicated 10GBit Ethernet line on a separate subnet between my workstation and my server.

Locally on the server, my ZFS on Linux pool performs very fast (~800MB/s)

iperf confirms that the 10 Gbit connection is working as expected:

```
$ iperf -c 10.0.2.10
------------------------------------------------------------
Client connecting to 10.0.2.10, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 10.0.2.116 port 54832 connected with 10.0.2.10 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  10.9 GBytes  9.37 Gbits/sec
```

However, when transferring files from the ZFS pool on my server to my desktop over NFS, I only get typical speeds of  ~160MB/s (~1280Mbit/s)

So, I know the pool can support high speeds, and I know the network can as well, but when I combine the two with NFS, it doesn't quite work as expected.

I found a guide that suggested adding "rsize=1048576,wsize=1048576" to the NFS options on the client side, but this does not seem to have helped.

I'd appreciate any suggestions!

Thanks
Matt

---

### Post by mattlach on 2016-12-31
I just noticed this:

Despite iperf confirming the bandwidth, mii-tool seems to think the link is stuck at 1000mbit half duplex.   Could this be having any undesired effect?

```

$ sudo mii-tool enp2s0
[sudo] password for matt: 
SIOCGMIIREG on enp2s0 failed: Invalid argument
SIOCGMIIREG on enp2s0 failed: Invalid argument
SIOCGMIIREG on enp2s0 failed: Invalid argument
SIOCGMIIREG on enp2s0 failed: Invalid argument
SIOCGMIIREG on enp2s0 failed: Invalid argument
enp2s0: 1000 Mbit, half duplex, link ok
```

---

### Post by SeijiSensei on 2017-01-01
Half-duplex will definitely degrade performance. TCP requires the receiving host to acknowledge each packet when it arrives.  On a regular full-duplex Ethernet connection it uses one of the pairs for the download and the other for the upload.  A half-duplex circuit needs to "turn the line around" every time TCP wants to send an acknowledgement.  

This sounds like a hardware issue to me.  I'd start by [replacing the cable]("https://www.google.com/search?q=ethernet+cable+for+10+gigabit&ie=utf-8&oe=utf-8").

---

### Post by mattlach on 2017-01-01
> **SeijiSensei said:**
> Half-duplex will definitely degrade performance. TCP requires the receiving host to acknowledge each packet when it arrives.  On a regular full-duplex Ethernet connection it uses one of the pairs for the download and the other for the upload.  A half-duplex circuit needs to "turn the line around" every time TCP wants to send an acknowledgement.  

This sounds like a hardware issue to me.  I'd start by [replacing the cable]("https://www.google.com/search?q=ethernet+cable+for+10+gigabit&ie=utf-8&oe=utf-8").

Yeah, but I'm thinking mii-tool must be wrong.   (Maybe it doesn't work with 10GBaseT?)    If I actually only had a 1000Mbit single duplex link, there is no way my iperf would record a 9.37Gbit bandwidth during the test.

The cable is a brand new 40ft Category 7 cable, but it's also the only copper cable I own that is officially compatible with 10gig.  Everything else is Cat6 or lower.

---

### Post by mattlach on 2017-01-01
For the record, this is what my system monitor looks like (Client side) during an iperf run:

[IMG]https://c1.staticflickr.com/1/316/31980895496_749e69fbbc_o.png[/IMG]

So it certainly looks like I am getting full 10gig bandwidth over the Ethernet interface.

I can also confirm local disk speed.

It seems to me it must be NFS that is the problem.

---

### Post by SeijiSensei on 2017-01-01
Try much larger sizes for rsize and wsize.  You may just need more buffer space to keep up with the network.  Try increasing the figures you have now by powers of ten and see if performance improves.

If you just want to transfer files, rather than providing an on-demand NFS share, I'd use rsync instead.

---

