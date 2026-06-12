---
title: "How to interpret new [ufw block] in logs"
date: 2016-01-21
forum: Security
---

### Post by wgw on 2016-01-21
Since the latest update of 14.04 LTS, my ufw log has been growing in size daily. I found tons of [UFW BLOCK]s about every 20 seconds, sometimes a bit longer. Here are the main cases, case 1 and 2 ({nm}=my network card mac; {om} another mac address I don't recognize -- not the router's!): 

```
Jan 21 12:37:08 bill-laptop kernel: [ 4838.310714] [UFW BLOCK] IN=wlan0 OUT= MAC={nm}:xx:xx:xx:15:49:5e:08:00 
SRC=192.168.1.89 DST=192.168.1.68 LEN=543 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=59904 DPT=52554 LEN=523 

Jan 21 12:37:43 bill-laptop kernel: [ 4873.430032] [UFW BLOCK] IN=wlan0 OUT= MAC={om}:01:xx:xx:xx:xx:xx:e8:08:00 
SRC=192.168.1.254 DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 

```

My machine is at 192.168.1.68, and I suppose the router is 192.168.1.254. Chromecast is at 192.168.1.89. 

Case 1: Why is Chromecast trying to contact my machine? This happens (I believe) whether chrome is running or not... Should I make a new rule that will allow it? Or should I just deny it silently? 

Case 2: If neither the source nor the destination is my machine's address, why does it trigger my firewall? 

I do have samba running. Maybe that explains the second case?

---

### Post by Doug S on 2016-01-22
> **wgw said:**
> Case 1: Why is Chromecast trying to contact my machine? This happens (I believe) whether chrome is running or not... Should I make a new rule that will allow it? Or should I just deny it silently?That one, I do not know. I would not allow it.

> **wgw said:**
> Case 2: If neither the source nor the destination is my machine's address, why does it trigger my firewall? That is a [broadcast type packet]("https://en.wikipedia.org/wiki/Multicast_address"), and so it is destined for your computer. I specifically DROP those, so that they don't clog up my logs files with crap.

---

### Post by wgw on 2016-01-22
Thanks! I will do as you suggested for Case 2: drop silently. (I googled a bit for "firewall multicast" and it looked like I would have to do some serious studying to understand multicast. Later!)

For Chromecast, I think I will have to drop silently according to the mac address, because the ip will change with reboots. Of course, I will have to figure out whether chromecast needs that access in fact; for the moment, it seems to work with blocking, but I did notice that cc is flaky on my ubuntu machine. Could be the firewall...

---

### Post by bashiergui on 2016-01-22
Are you streaming chromecast to ubuntu? I would expect it to use udp for that.

---

### Post by wgw on 2016-01-22
I have installed the app in Chrome, and streamed from there, but only a few times, and not constantly! But the blocking happens constantly...

---

### Post by bashiergui on 2016-01-22
Okay Chromecast streams in ubuntu through the chrome plugin? That would account for the udp packets between chromecast and ubuntu. I would expect them to poll each other periodically and routinely. You need to allow those for optimal streaming.

---

### Post by wgw on 2016-01-22
Ok -- thanks! I will open it to Chromecast (perhaps to its mac address, since the ip may change). I should try to monitor the polling to understand what's going on... (I'll see if I can figure out how to watch that polling...)

---

### Post by bashiergui on 2016-01-23
Use tcpdump or some other packet capturing like wireshark if you want to see what chromecast is chatting about.

---

### Post by wgw on 2016-01-23
I will give wireshark a try; used etherape in the past (nice display), but did not understand the output well enough.

---

### Post by bashiergui on 2016-01-24
Search for "wireshark tutorial" and you'll find tons of free video tutorials you can watch.

---

### Post by wgw on 2016-01-24
Thanks! it looks like the standard, so I should have enough doc.

---

### Post by wgw on 2016-01-24
Here are my first wireshark captures. I will need to learn more to understand the implications and to tweak my firewall, but it looks like wireshark will teach me a lot. (Understanding network communication is one of the many areas where I am a total noob; but it is fascinating to see all that chatting going on silently under the hood.)

When Chrome starts, Chromecast tries to connect:
2544	1442.502009000	192.168.1.89	192.168.1.68	UDP	557	Source port: 55362  Destination port: 36325
2886	1443.427086000	192.168.1.89	192.168.1.68	UDP	557	Source port: 48370  Destination port: 36325

Now they seem to be talking...
7410	1546.462514000	192.168.1.89	192.168.1.68	TCP	177	[TCP segment of a reassembled PDU]
7411	1546.462588000	192.168.1.68	192.168.1.89	TCP	66	52673 > 8009 [ACK] Seq=3725 Ack=7428 Win=46080 Len=0 TSval=22328220 TSecr=538845

This is my cellphone. 
844	424.404158000	192.168.1.90	239.255.255.250	SSDP	164	M-SEARCH * HTTP/1.1

---

