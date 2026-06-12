---
title: "strange MAC"
date: 2009-11-16
forum: Server Platforms
---

### Post by wwoollff on 2009-11-16
Hi. I've been searching for a while for a solution, but google is not that helpful. My problem sounds like this: in my iptables firewall I have a rule that dumps to the kernel messages the information that a certain user in my network uses strage flags.
```

....
iptables -N Badflags
iptables -F Badflags
iptables -A Badflags -m limit --limit 10/minute -j LOG --log-prefix "Badflags: "
iptables -A Badflags -p tcp --tcp-flags ACK,FIN FIN -j DROP
....
other bad flags
.....
 etc

```

Now...a host has probably a virus, and the /var/log/kern.log keeps logging stuff like this:
```

Nov 16 18:38:26 ubuntu kernel: [  662.127070] Badflags: IN=eth0 OUT= MAC=00:02:2a:e2:a4:f9:00:15:c6:20:b3:80:08:00 SRC=194.105.19.219 DST=82.76.142.74 LEN=1500 TOS=0x00 PREC=0x00 TTL=60 ID=38014 DF PROTO=TCP SPT=80 DPT=48973 WINDOW=524 RES=0x00 ACK URGP=0 

```
How can I locate that guy, if the MAC has a 14byte address? Wasn't that supposed to be 6bytes?

thx.
p.s. using Ubuntu Server 9.10

---

### Post by Bag-O-Stuff on 2009-11-16
According to this person, they print the source, destination and a code at the end making 14 bytes.

[http://lkml.indiana.edu/hypermail/linux/kernel/0102.2/0377.html](http://lkml.indiana.edu/hypermail/linux/kernel/0102.2/0377.html)

6 bytes mac-source, 6 bytes mac-destination and 2 bytes (08:00) indicating 
it is IP.

---

### Post by wwoollff on 2009-11-16
That helped. But now I have another problem. The first mac, is the eth0 mac of the server (00:02:2a:e2:a4:f9), and when I block the mac 00:15:c6:20:b3:80, the hosts remain connected, but with no internet connection(I've tried on different hosts).When I comment the line, everything is working perfectly.

```

iptables -A FORWARD -m mac --mac-source 00:15:c6:20:b3:80 -j DROP

```
here's the output of ifconfig: 
```

eth0      Link encap:Ethernet  HWaddr 00:02:2a:e2:a4:f9  
          inet addr:*.*.*.*  Bcast:82.76.142.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2aff:fee2:a4f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1326380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1013971 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1287516452 (1.2 GB)  TX bytes:134962983 (134.9 MB)
          Interrupt:19 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:0a:cd:13:c6:e0  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe13:c6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:846420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1231677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:126336401 (126.3 MB)  TX bytes:1381970914 (1.3 GB)
          Interrupt:16 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110240 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11542324 (11.5 MB)  TX bytes:11542324 (11.5 MB)



```
thx again for your help

---

### Post by Bag-O-Stuff on 2009-11-16
I have a feeling that the source MAC you are using is actually from your gateway and not the bad guy.  Try dropping packets by the IP address instead and I'll bet it works.

Do an "arp -vn" after pinging your gateway and see if that MAC address is in there for the gateway IP.

---

### Post by wwoollff on 2009-11-16
Well, blocking the SRC ip is not a solution, because is constantly changing...
```

Nov 16 22:12:47 ubuntu kernel: [13522.422323] Badflags: IN=eth0 OUT= MAC=00:02:2a:e2:a4:f9:00:15:c6:20:b3:80:08:00 SRC=193.189.143.34 DST=*.*.*.74 LEN=52 TOS=0x00 PREC=0x00 TTL=56 ID=60795 DF PROTO=TCP SPT=80 DPT=58318 WINDOW=16 RES=0x00 ACK FIN URGP=0 
Nov 16 22:12:52 ubuntu kernel: [13527.238617] Badflags: IN=eth0 OUT= MAC=00:02:2a:e2:a4:f9:00:15:c6:20:b3:80:08:00 SRC=81.196.26.145 DST=*.*.*.74 LEN=1500 TOS=0x00 PREC=0x00 TTL=61 ID=46409 DF PROTO=TCP SPT=80 DPT=51400 WINDOW=4876 RES=0x00 ACK URGP=0 
Nov 16 22:12:58 ubuntu kernel: [13533.487045] Badflags: IN=eth0 OUT= MAC=00:02:2a:e2:a4:f9:00:15:c6:20:b3:80:08:00 SRC=88.26.58.38 DST=*.*.*.74 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=10550 DF PROTO=TCP SPT=60654 DPT=5100 WINDOW=8192 RES=0x00 SYN URGP=0 

```
arp -vn
```

192.168.1.48             ether   00:16:44:1d:78:88   C                     eth1
192.168.1.46             ether   00:19:7e:55:47:88   C                     eth1
192.168.1.30             ether   00:1c:26:26:fe:5d   C                     eth1
192.168.1.62             ether   00:21:00:8a:ee:74   C                     eth1
192.168.1.18             ether   00:16:44:18:d1:f5   C                     eth1
192.168.1.14             ether   00:16:44:d1:0f:80   C                     eth1
192.168.1.45             ether   00:19:d2:1a:bf:b3   C                     eth1
192.168.1.91             ether   00:13:02:4c:e3:16   C                     eth1
192.168.1.56             ether   00:1c:bf:2a:ef:3a   C                     eth1
192.168.1.63             ether   00:21:00:3c:17:d5   C                     eth1
192.168.1.28             ether   00:1c:26:a1:67:1d   C                     eth1
192.168.1.37             ether   00:26:5e:24:b1:c8   C                     eth1
192.168.1.68             ether   00:1e:4c:a2:51:49   C                     eth1
*.*.*.1                  ether   00:15:c6:20:b3:80   C                     eth0
192.168.1.15             ether   00:23:4e:30:eb:fb   C                     eth1
192.168.1.24             ether   00:1a:73:0d:b5:01   C                     eth1
192.168.1.40             ether   00:16:44:84:ac:ef   C                     eth1
192.168.1.87             ether   00:13:e8:b7:7e:b7   C                     eth1
192.168.1.21             ether   00:1c:26:2d:9e:7a   C                     eth1
192.168.1.79             ether   00:16:cf:68:de:1f   C                     eth1
192.168.1.11             ether   00:21:00:fc:a3:34   C                     eth1
192.168.1.60             ether   00:22:fa:60:44:fa   C                     eth1
192.168.1.59             ether   00:1f:e1:c4:05:ea   C                     eth1
Entries: 23	Skipped: 0	Found: 23


```
now that is strange...that unknown mac seems to me my server's gateway. The IP of my server ends in .74, and the ISPs in .1 I'm confused ...

---

### Post by Bag-O-Stuff on 2009-11-16
The problem is that your router is stripping off the original MAC address and replacing it with it's own LAN MAC address.  Chances are, the MAC address has been changed half a dozen times before it arrived to you.

Dropping by MAC address is probably only going to help you with LAN issues.

---

### Post by Bag-O-Stuff on 2009-11-16
I tried to find a good document that explains why you can't really filter by the MAC address in your situation and couldn't find one.  This one has a decent explanation about halfway down that describes what happens with the MAC addresses of a packet and how they change.

[http://www.linkedin.com/answers/technology/information-technology/computer-networking/TCH_ITS_CNW/558719-54822017](http://www.linkedin.com/answers/technology/information-technology/computer-networking/TCH_ITS_CNW/558719-54822017)

Hope this helps!

---

### Post by doas777 on 2009-11-16
just as a general rule, expect a mac to only be valid if it originates from the network you are observing. I'm sure you already know, macs only allow you to traverse the local network you aare on at any given second. to get from network to network, you change macs, but keep the same IP.

---

### Post by wwoollff on 2009-11-16
Well,I guess this is it...I'm just gonna try to drop them one by one... what if this happend in a 200 hosts network?

---

### Post by Bag-O-Stuff on 2009-11-16
Can you just drop all packets that have the strange flags?  I wouldn't expect any coming from the inside.

---

### Post by wwoollff on 2009-11-17
Well, all those packages are dropped, but the guy that is sending those packages is simply flooding my network...I desperately need to find him....dropping by mac didn't work, because after dropping a few, my phone started ringing every 10 seconds...so...any ideas?

---

### Post by Bag-O-Stuff on 2009-11-17
Can you describe in detail what's going on?  When you say phone is ringing, you mean a VOIP phone?  Like SIP?

---

### Post by wwoollff on 2009-11-18
People started calling me on my phone because they had no internet connectivity(I was dropping their mac to see if they are sending those bad packages)...There must be a way to check whose sending those requests, without dropping MACs....

---

### Post by Bag-O-Stuff on 2009-11-18
Are you looking to drop every single packet from the "bad people" or just the ones with the bad flags?

---

