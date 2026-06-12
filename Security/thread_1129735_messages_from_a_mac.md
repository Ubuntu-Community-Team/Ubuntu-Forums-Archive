---
title: "messages from a mac?"
date: 2009-04-19
forum: Security
---

### Post by r.stiltskin on 2009-04-19
I just noticed that /var/log/messages on both of my ubuntu machines are full of entries like these (this is just a small sample):

```
Apr 18 10:44:33 a2600 kernel: [153605.271918] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=100 TOS=0x00 PREC=0x00 TTL=64 ID=7271 PROTO=UDP SPT=54952 DPT=2223 LEN=80 
Apr 18 10:45:33 a2600 kernel: [153665.229268] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=100 TOS=0x00 PREC=0x00 TTL=64 ID=785 PROTO=UDP SPT=54953 DPT=2223 LEN=80 
Apr 18 10:46:33 a2600 kernel: [153725.181739] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=100 TOS=0x00 PREC=0x00 TTL=64 ID=50834 PROTO=UDP SPT=54955 DPT=2223 LEN=80 
Apr 18 10:47:33 a2600 kernel: [153785.135451] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=100 TOS=0x00 PREC=0x00 TTL=64 ID=38840 PROTO=UDP SPT=54956 DPT=2223 LEN=80 
Apr 18 10:48:33 a2600 kernel: [153845.089677] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=100 TOS=0x00 PREC=0x00 TTL=64 ID=56734 PROTO=UDP SPT=54957 DPT=2223 LEN=80 
Apr 18 10:49:03 a2600 kernel: [153875.259773] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:0d:93:87:af:5b:08:00 SRC=192.168.123.109 DST=255.255.255.255 LEN=34 TOS=0x00 PREC=0x00 TTL=64 ID=41940 PROTO=UDP SPT=54959 DPT=2223 LEN=14 

```

The SRC address is a Mac (PowerPC G5) in my home network.  These messages seem to be coming every minute whenever the Mac is on.  I see that they are being blocked by the firewall, but beyond that I have no idea what they mean.  Is this just something that OSX does normally, or does it indicate that the Mac has been infected?

---

### Post by juancarlospaco on 2009-04-19
Its something called Bonjour... 
*IP packets wastage to discover other Apple devices*

---

### Post by Seq on 2009-04-19
> **juancarlospaco said:**
> Its something called Bonjour... 
*IP packets wastage to discover other Apple devices*

Ubuntu can use this as well, typically via Avahi. It is used for "zeroconf" network stuff, such as finding resources on the network automatically (Music shares, hostnames, file shares, etc).

It is not Apple exclusive just as UPNP is not microsoft exclusive. Though Apple is a primary user of the protocol.

[http://en.wikipedia.org/wiki/Zeroconf]("http://en.wikipedia.org/wiki/Zeroconf"). From there, you can read about Avahi and Bonjour.

---

### Post by r.stiltskin on 2009-04-19
Thanks.  I can stop worrying & revert to just being mildly annoyed.

---

