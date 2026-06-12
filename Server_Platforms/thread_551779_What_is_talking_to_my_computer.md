---
title: "What is talking to my computer?"
date: 2007-09-15
forum: Server Platforms
---

### Post by Sikarian on 2007-09-15
I can't figure out what on earth keeps hitting my firestarter.  This has been showing up for days.  This will show up even on a fresh boot with absolutely zero programs running save for Firestarter.  No torrent system going or anything. 
```
Time:Sep 15 15:37:13 Direction: Unknown In:eth1 Out: Port:22408 Source:76.235.196.62 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:14 Direction: Unknown In:eth1 Out: Port:22408 Source:69.117.202.196 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:15 Direction: Unknown In:eth1 Out: Port:22408 Source:88.141.174.240 Destination:192.168.1.105 Length:71 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:20 Direction: Unknown In:eth1 Out: Port:22408 Source:66.229.255.214 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:22 Direction: Unknown In:eth1 Out: Port:22408 Source:68.118.245.57 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:22 Direction: Unknown In:eth1 Out: Port:22408 Source:69.228.236.161 Destination:192.168.1.105 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:22 Direction: Unknown In:eth1 Out: Port:22408 Source:193.85.68.92 Destination:192.168.1.105 Length:70 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:23 Direction: Unknown In:eth1 Out: Port:22408 Source:83.52.129.50 Destination:192.168.1.105 Length:93 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:24 Direction: Unknown In:eth1 Out: Port:22408 Source:90.128.201.43 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:25 Direction: Unknown In:eth1 Out: Port:22408 Source:200.104.25.58 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP Service:Unknown
Time:Sep 15 15:37:25 Direction: Unknown In:eth1 Out: Port:22408 Source:213.112.109.196 Destination:192.168.1.105 Length:91 TOS:0x00 Protocol:UDP
```


I have no idea what is 22408

---

### Post by HermanAB on 2007-09-15
Hmm, this kind of crap is going on all the time.  That is why firewall tools that notify you about every little thing are quite useless.  It is a good idea to monitor things for a day or two after building a new system or changing the firewall, but then you have to turn the notifications off and let iptables get on with its job.

---

### Post by Sikarian on 2007-09-15
Yeah, I understand that this kind of thing goes on all the time, but I'm curious as to if theres something on my computer broadcasting out saying "Hey, get me on 22408!"

Sometimes I like to disable the firewall so I can bittorrent freely, and I'm curious as to wether or not I should be worried about what's going on with 22408, if theres something actually gonna answer if I turn the firewall off.

---

### Post by HermanAB on 2007-09-16
If you wish to see what your machine is doing, run tcpdump and look at the packets for a bit.  Something like this:
$ sudo tcpdump -s 256 -A -i eth0

---

### Post by HermanAB on 2007-09-16
You can test a specific port very easily with telnet:
$ telnet localhost 22408

If something answers, you'll get a banner message.

Cheers,

H.

---

### Post by Sikarian on 2007-09-17
Well, I've tried telnetting into 22408 (after disabling firestarter to open traffic), and I get connection refused.

I assume this means I am safe turning off firestarter without having to worry about it.  

It's just weird as to why I'm getting all these hits on this port... normally when I see random hits from internet scans, it's on random ports.

---

### Post by steve.horsley on 2007-09-18
Not necessarily safe. The log above reports UDP packets, but telnet uses TCP. It is still possible that UDP port 22408 is open. Unlikely though.
**netstat -lun**
 will list all open UDP ports. 
So will 
**sudo lsof -i UDP**

---

