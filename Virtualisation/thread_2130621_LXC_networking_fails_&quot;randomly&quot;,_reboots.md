---
title: "LXC networking fails &quot;randomly&quot;, reboots of the host OS fix it"
date: 2013-03-30
forum: Virtualisation
---

### Post by davidparks21 on 2013-03-30
I'm getting very unpredictable results from an environment I have set up for LXC. 

I run windows 7 on my laptop, where I run a virtual box instance of ubuntu 12.10 server. 

Virtualbox is set up to use NAT on network 10.1.x.x/16, default gateway of 10.1.0.2 (these IPs match the IPs that these containers will use on production hardware later). This works fine, both the Host OS can access the internet and containers (sometimes) can. So configuration is good.

But sometimes a container OS won't be able to access the internet.

I've configure br0 on the host OS to bridge between the container OSs and the Hosts eth0 (static IP configured on the host, **not** using lxcbr0 for NAT). 

Yesterday I had a case where the container couldn't access the internet. I could ping the host OS, but pinging the router at 10.1.0.2 failed. When I did a tcpdump on the host OS I could see ICMP packets from the container and the response from the router, but I didn't get that on the container. A full reboot of my laptop fixed the problem (arrrrggggg!!!)

I'm working with a container today that works fine, networking is working. But when I cloned that container and set the new container to an IP of 10.1.0.45 (the original being 10.1.0.4) that one can't access the router. Pinging the host OS works, pinging other containers work, but I cannot ping the default gateway. Again, tcpdump on the host shows me the traffic to and from the router, but the container doesn't get it.

```

davidparks21@hostOS:~$ sudo tcpdump icmp
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
11:56:44.356877 IP 10.1.0.45 > 10.1.0.2: ICMP echo request, id 336, seq 46, length 64
11:56:44.357964 IP 10.1.0.2 > 10.1.0.45: ICMP echo reply, id 336, seq 46, length 64
11:56:45.356940 IP 10.1.0.45 > 10.1.0.2: ICMP echo request, id 336, seq 47, length 64
11:56:45.357718 IP 10.1.0.2 > 10.1.0.45: ICMP echo reply, id 336, seq 47, length 64


davidparks21@hostOS:~$ arp -a
? (10.1.0.4) at c6:63:bb:a7:d8:60 [ether] on br0
? (10.1.0.2) at 52:54:00:12:35:02 [ether] on br0
? (10.1.0.45) at 32:8c:fc:c1:7f:e5 [ether] on br0


davidparks21@hostOS:~$ brctl show
bridge name     bridge id               STP enabled     interfaces
br0             8000.080027ca5f7a       no              eth0
                                                        vethB864oI
                                                        vethQ2kfp9
                                                        vethYHH03A

```

I'm starting to think "bug" here... I shouldn't possibly be able to see the traffic cross to and from the host OS and not see it in the container.

I know the configuration works because this configuration works "sometimes" but not others.

---

