---
title: "What does these messages mean ?"
date: 2017-04-05
forum: Security
---

### Post by linuxyogi on 2017-04-05
I use cable internet. My local IP is 172.16.197.***

I am connected directly without a router.

When I do dmesg | tail I get

```
$ dmesg |tail[ 2250.881107] [UFW BLOCK] IN=enp0s7 OUT= MAC=01:00:5e:00:00:fc:00:1b:38:f6:e7:50:08:00 SRC=172.16.197.76 DST=224.0.0.252 LEN=52 TOS=0x00 PREC=0x00 TTL=1 ID=1910 PROTO=UDP SPT=52933 DPT=5355 LEN=32 
[ 2265.746250] [UFW BLOCK] IN=enp0s7 OUT= MAC=33:33:00:01:00:03:c8:5b:76:70:f7:3a:86:dd SRC=fe80:0000:0000:0000:ccf8:6743:afc0:5577 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=70 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=51945 DPT=5355 LEN=30 
[ 2276.649439] [UFW BLOCK] IN=enp0s7 OUT= MAC=01:00:5e:00:00:fb:f4:f2:6d:3a:80:9d:08:00 SRC=172.16.197.133 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2291.548416] [UFW BLOCK] IN=enp0s7 OUT= MAC=01:00:5e:00:00:fb:30:b5:c2:43:ae:85:08:00 SRC=172.16.197.195 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2310.040710] [UFW BLOCK] IN=enp0s7 OUT= MAC=01:00:5e:00:00:fc:00:1b:38:f6:e7:50:08:00 SRC=172.16.197.76 DST=224.0.0.252 LEN=52 TOS=0x00 PREC=0x00 TTL=1 ID=8259 PROTO=UDP SPT=55159 DPT=5355 LEN=32 
[ 2320.150007] [UFW BLOCK] IN=enp0s7 OUT= MAC=33:33:00:01:00:03:c8:5b:76:70:f7:3a:86:dd SRC=fe80:0000:0000:0000:ccf8:6743:afc0:5577 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=70 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=60706 DPT=5355 LEN=30 
[ 2320.151001] [UFW BLOCK] IN=enp0s7 OUT= MAC=33:33:00:01:00:03:c8:5b:76:70:f7:3a:86:dd SRC=fe80:0000:0000:0000:ccf8:6743:afc0:5577 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=70 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=56028 DPT=5355 LEN=30 
[ 2320.183018] [UFW BLOCK] IN=enp0s7 OUT= MAC=33:33:00:01:00:03:c8:5b:76:70:f7:3a:86:dd SRC=fe80:0000:0000:0000:ccf8:6743:afc0:5577 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=81 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=51610 DPT=5355 LEN=41 
[ 2337.811428] [UFW BLOCK] IN=enp0s7 OUT= MAC=01:00:5e:00:00:fb:f4:f2:6d:3a:80:9d:08:00 SRC=172.16.197.133 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2340.765779] [UFW BLOCK] IN=enp0s7 OUT= MAC=33:33:00:01:00:03:c8:5b:76:70:f7:3a:86:dd SRC=fe80:0000:0000:0000:ccf8:6743:afc0:5577 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=70 TC=0 HOPLIMIT=1 FLOWLBL=0 PROTO=UDP SPT=65312 DPT=5355 LEN=30 



```

What does the above messages mean ?

---

### Post by Habitual on 2017-04-06
BCAST "noise". Quite legit, I believe

[https://en.wikipedia.org/wiki/Broadcast_address](https://en.wikipedia.org/wiki/Broadcast_address) says
"Example: For broadcasting a packet to an entire IPv4 subnet using the private IP address space 172.16.0.0/12, which has the subnet mask 255.240.0.0, the broadcast address is 172.16.0.0 | 0.15.255.255 = 172.31.255.255."

[https://en.wikipedia.org/wiki/Multicast_address](https://en.wikipedia.org/wiki/Multicast_address) also has some info.
"DST=ff" is ipv6 addressing.

How to "explain it"? IDK. I tried to squash bcast/mcast exactly **once**, and gave up.
At least  [this]("https://community.norton.com/en/comment/2737293#comment-2737293") re-inforces what I've written and says in part, "These are all normal communications that are confined to your Local Area Network.  They mostly involve multicast shoutouts among the devices on your network to announce their presence to the other devices."

---

### Post by linuxyogi on 2017-04-06
I wont say I understood it entirely but its good to know its normal. I thought people are trying to hack my desktop.
Thanks a lot for your reply.

Last time I was connected directly (without a router). This time I am behind a router. 

```
$ dmesg |tail[   14.664500] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=71 TC=0 HOPLIMIT=255 FLOWLBL=1017616 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[   15.014429] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=192.168.0.103 DST=224.0.0.252 LEN=51 TOS=0x00 PREC=0x00 TTL=255 ID=19663 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[   15.014539] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0001:0003 LEN=71 TC=0 HOPLIMIT=255 FLOWLBL=1017616 PROTO=UDP SPT=5355 DPT=5355 LEN=31 
[   15.614799] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=619714 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   15.614824] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=332997 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   15.625282] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=619714 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   15.625303] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=332997 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   15.996224] random: crng init done
[   19.699026] [UFW BLOCK] IN=enp0s7 OUT= MAC= SRC=192.168.0.103 DST=224.0.0.252 LEN=51 TOS=0x00 PREC=0x00 TTL=255 ID=20222 PROTO=UDP SPT=5355 DPT=5355 LEN=31 



``` 

192.168.0.103 is my desktop's IP assigned by the router (dhcp). Does the above logs mean the same thing ? [COLOR=#000000]BCAST "noise" ?[/COLOR]

---

### Post by Habitual on 2017-04-19
Yes, everything 224.x.x.x is Bcast/Mcast udp traffic.
The 
```
SRC=fe80:0000:0000:0000:60bd:39c1:b660:bf99 DST=ff02:0000:0000:0000:0000:0000:0000:0001
```designations are IPv6 address formats
ff0, I think is usually "localhost".

---

### Post by linuxyogi on 2017-04-19
Thanks.

---

### Post by Habitual on 2017-04-20
You are welcome.

---

### Post by linuxyogi on 2017-04-29
```
 $ dmesg |tail[ 8690.149440] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:5c SRC=91.189.94.12 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=54520 WINDOW=28960 RES=0x00 ACK URGP=0 
[ 8694.149208] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:5c SRC=91.189.94.12 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=54520 WINDOW=28960 RES=0x00 ACK URGP=0 
[ 8698.149653] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:5c SRC=91.189.94.12 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=54520 WINDOW=28960 RES=0x00 ACK URGP=0 
[ 8740.085477] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:21:12 SRC=31.13.65.7 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=53196 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 8752.289804] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:21:12 SRC=31.13.65.7 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=53202 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 8756.375139] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:21:12 SRC=31.13.65.7 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=53208 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 8756.467028] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:21:12 SRC=31.13.65.7 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=53210 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 8758.866149] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:21:12 SRC=31.13.65.7 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=53212 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 8866.172295] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:18:f5 SRC=31.13.73.36 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=44540 WINDOW=27960 RES=0x00 ACK URGP=0 
[ 9126.470648] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:6e:c3 SRC=50.16.224.82 DST=192.168.0.2 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=60832 WINDOW=26847 RES=0x00 ACK URGP=0 

```


I am behind a pfSense box now. These look different. Can u please have a look and tell me what these are ?

---

### Post by TheFu on 2017-05-03
You need to learn to read these logs yourself.
Look at the protocol.
Look at the source and destination IPs.
Look at the source and destination ports.

What does that tell you?  Don't know?  Google.
91.189.94.12 is Canonical owned. It is TCP over port 443.  What might that be?  How likely is it that Canonical would try to hack you?  Look at the URL on this page. That's HTTPS. It is from Canonical. Could that be a log of some ajax traffic?
```
$ ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.

```
We have a winner!  Do that for each package/address.

You've been taught to fish. Go and fish.

---

### Post by linuxyogi on 2017-05-03
> **TheFu said:**
> You need to learn to read these logs yourself.
Look at the protocol.
Look at the source and destination IPs.
Look at the source and destination ports.

What does that tell you?  Don't know?  Google.
91.189.94.12 is Canonical owned. It is TCP over port 443.  What might that be?  How likely is it that Canonical would try to hack you?  Look at the URL on this page. That's HTTPS. It is from Canonical. Could that be a log of some ajax traffic?
```
$ ping ubuntuforums.org
PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.

```
We have a winner!  Do that for each package/address.

You've been taught to fish. Go and fish.


Point taken but the thing is when I was using my DLink router the logs only showed BCAST "noise" nothing else. But since I started using pfSense I am noticing these activities. What I want to know is what are these ? Is this normal ?

Thanks a lot for your reply.

```
$ dmesg |tail[42507.170386] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40614 WINDOW=28960 RES=0x00 ACK URGP=0 
[42508.235265] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40612 WINDOW=28960 RES=0x00 ACK URGP=0 
[42509.315219] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40616 WINDOW=28960 RES=0x00 ACK URGP=0 
[42509.337276] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40618 WINDOW=28960 RES=0x00 ACK URGP=0 
[42510.958513] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40610 WINDOW=28960 RES=0x00 ACK URGP=0 
[42511.170320] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40614 WINDOW=28960 RES=0x00 ACK URGP=0 
[42512.235305] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40612 WINDOW=28960 RES=0x00 ACK URGP=0 
[42513.315642] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40616 WINDOW=28960 RES=0x00 ACK URGP=0 
[42513.337428] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:c7:56 SRC=91.189.94.16 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=40618 WINDOW=28960 RES=0x00 ACK URGP=0 
[42614.855339] [UFW BLOCK] IN=eth0 OUT= MAC=b8:27:eb:af:87:64:00:e0:4c:53:44:58:08:00:45:00:00:28:00:00:40:00:39:06:d8:1d SRC=157.240.11.22 DST=192.168.0.4 LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=443 DPT=59776 WINDOW=27960 RES=0x00 ACK URGP=0 

```


I know I can Google the IPs and know origin like Google, Facebook, etc but my question is why am I receiving these messages despite behind a firewall ? BTW the broadcast noise mentioned in the beginning of this thread is gone. pfSense is blocking it.

Before answering kindly have a look at your dmesg|tail and see if you see similar activities in your end.

---

### Post by litlesam on 2017-05-03
Was looking for a lot of this info over the last month. Here are a few very good articles.
[https://ubuntuforums.org/showthread.php?t=2085110](https://ubuntuforums.org/showthread.php?t=2085110)     Starting at post #5
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by lisati on 2017-05-06
> **linuxyogi said:**
> 
I know I can Google the IPs and know origin like Google, Facebook, etc but my question is why am I receiving these messages despite behind a firewall ?

You are receiving the messages because you are behind a firewall which has blocked activity.

---

### Post by linuxyogi on 2017-05-06
> **lisati said:**
> You are receiving the messages because you are behind a firewall which has blocked activity.

Which firewall do you mean ? pfSense or ufw ?

If you are talking about ufw thats my point. How are those traffic reaching my Linux box? Isn't the firewall (pfSense) supposed to block them ?

---

### Post by lisati on 2017-05-07
> **linuxyogi said:**
> Which firewall do you mean ? pfSense or ufw ?
What are the messages in the log telling you?
> **linuxyogi said:**
> If you are talking about ufw thats my point. How are those traffic reaching my Linux box? Isn't the firewall (pfSense) supposed to block them ?
Where is the firewall?

---

### Post by linuxyogi on 2017-05-07
> [COLOR=#000000]Where is the firewall?[/COLOR]

My ISP provides Internet using ethernet cable. The cable is connected to the WAN interface of my pfSense box while my PC is connected to the LAN interface.

---

### Post by TheFu on 2017-05-07
You are seeing the difference between a firewall appliance, which has to guess about connection status, and a host-based firewall, which KNOWS what the connection status really is.  Our computers don't notify the router/firewall when a connection is close, hence why it has to guess and being overly aggressive would probably be bad without much gain in security.  I see the same stuff with other AJAX-y sites trying to keep connections open longer than necessary.

I don't use facebook, twitter, and avoid most google stuff. These are blocked at the network level along with 100K+ other tracking sites. My tinfoil is thicker than most, I must admit.

---

### Post by linuxyogi on 2017-05-07
@TheFu

This is normal then. That's all I needed to know. Thanks a lot.

---

### Post by TheFu on 2017-05-07
> **linuxyogi said:**
> @TheFu

This is normal then. That's all I needed to know. Thanks a lot.

I can't do the research to determine that.  Don't know where you've been, what you've been doing.  You have to do the research if you are concerned.  If it wasn't https, I'd say to use wireshark to see the data.

---

### Post by linuxyogi on 2017-05-07
I have been browsing mainly Google, Facebook, Ubuntuforums, pfSense forums, Raspberry Pi forums. watched some videos using Kodi.  Installing wireshark now.

I see list full of these

 ```
141    153.230148990    192.168.0.4    bom07s12-in-f3.1e100.net    TCP    89    [TCP Retransmission] 45268 &#8594; 443 [FIN, PSH, ACK] Seq=1 Ack=2 Win=2318 Len=23 TSval=440960 TSecr=3148134830
```

```
138	150.670274422	192.168.0.4	maa03s19-in-f99.1e100.net	TCP	89	[TCP Retransmission] 50938 &#8594; 443 [FIN, PSH, ACK] Seq=1 Ack=2 Win=2451 Len=23 TSval=440704 TSecr=3966267165
```

---

### Post by &amp;KyT$0P# on 2017-05-07
1e100.net = Google

Looks normal and expected to me.

---

### Post by linuxyogi on 2017-05-08
Thanks.

> **TheFu said:**
>  I don't use facebook, twitter, and avoid most google stuff. These are blocked at the network level along with 100K+ other tracking sites. My tinfoil is thicker than most, I must admit.


Which firewall are you using ? Is it pfSense ? If yes how are you blocking those sites ? I mean which addon are you using ?  How did you manage to build such a huge list of sites (100K+)  ?

Edit: Just finished installing pfblocker with the help of [this guide]("http://benoliver999.com/technology/2016/02/27/howtoblockadswithpfblocker/").

---

