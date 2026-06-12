---
title: "openVPN connects but without internet and VPN network access"
date: 2018-05-11
forum: Security
---

### Post by sk8-mza on 2018-05-11
Hi,

I'm having a bit of an issue when trying to use openVPN on my computer. I'm using this to connect:
```
sudo openvpn --config client.ovpn
```

Connection seems to be successful but when I try to navigate or access resources within the VPN I get the "This site can’t be reached" error. The only thing that is loading is google.com, but nothing else.

I've been looking all around this forum (and others), but I'm not being able to fix this. Probable due to my almost zero knowledge on this matter.

I would appreciate any help provided.

Thanks!

---

### Post by The Cog on 2018-05-11
First let's have a look at your routing table and check your dns resolution - can you post the output of these commands:
```
ip route
host ubuntu.com
ping -c3 ubuntu.com
host cisco.com 8.8.8.8

```

---

### Post by sk8-mza on 2018-05-11
Well, after all the things I tried, it is now connecting and working as expected. Don't know what did the trick, but I'm glad it now works :)

Thanks for the help and sorry that I opened this in vain.

---

### Post by sk8-mza on 2018-06-07
> **The Cog said:**
> First let's have a look at your routing table and check your dns resolution - can you post the output of these commands:
```
ip route
host ubuntu.com
ping -c3 ubuntu.com
host cisco.com 8.8.8.8

```

I'm back, things are broken again :(
These are the commands requested above, I executed them once connected to the VPN:

```

s3ns3i@s3ns3i:~$ ip route
0.0.0.0/1 via 172.27.232.1 dev tun0 
default via 192.168.0.1 dev wlp2s0  proto static  metric 600 
54.165.179.18 via 192.168.0.1 dev wlp2s0 
128.0.0.0/1 via 172.27.232.1 dev tun0 
169.254.0.0/16 dev wlp2s0  scope link  metric 1000 
172.27.232.0/21 dev tun0  proto kernel  scope link  src 172.27.234.43 
192.168.0.0/24 dev wlp2s0  proto kernel  scope link  src 192.168.0.5  metric 600 

```

```

s3ns3i@s3ns3i:~$ host ubuntu.com
;; connection timed out; no servers could be reached

```

```

s3ns3i@s3ns3i:~$ ping -c3 ubuntu.com
ping: unknown host ubuntu.com

```

```

s3ns3i@s3ns3i:~$ host cisco.com 8.8.8.8
Using domain server:
Name: 8.8.8.8
Address: 8.8.8.8#53
Aliases: 


cisco.com has address 72.163.4.185
cisco.com has IPv6 address 2001:420:1101:1::185
cisco.com mail is handled by 10 alln-mx-01.cisco.com.
cisco.com mail is handled by 30 aer-mx-01.cisco.com.
cisco.com mail is handled by 20 rcdn-mx-01.cisco.com.

```

---

