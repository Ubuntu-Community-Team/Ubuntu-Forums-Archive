---
title: "Why is UFW blocking these packets?"
date: 2012-07-07
forum: Security
---

### Post by Artemus on 2012-07-07
UFW is blocking some packets that I thought I was allowing. A couple examples are
```

Jul  7 17:43:21 hobbes kernel: [  295.784964] [UFW BLOCK] IN=br0 OUT= PHYSIN=tap0 MAC=00:04:75:70:8e:30:fe:23:43:ca:38:8f:08:00 SRC=10.56.183.106 DST=10.56.183.1 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=51040 DF PROTO=TCP SPT=33003 DPT=993 WINDOW=661 RES=0x00 ACK FIN URGP=0 
Jul  7 17:44:15 hobbes kernel: [  349.630433] [UFW BLOCK] IN=eth0 OUT= MAC=00:13:20:16:69:f6:00:1f:d0:a2:21:aa:08:00 SRC=10.56.182.4 DST=10.56.183.1 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=59140 DF PROTO=TCP SPT=2049 DPT=863 WINDOW=155 RES=0x00 ACK FIN URGP=0

```


So some packets from 10.56.183.106 and 10.56.182.4 (amongst others) are blocked. hobbes is the gateway for 10.56.183.0/24. 10.56.183.106 is included on the LAN via openvpn running on hobbes. 10.56.182.4 is included from an IPSEC tunnel running between hobbes and calvin (gateway for 10.56.182.0/24). Finally, on hobbes the UFW status gives
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       10.56.182.0/24
Anywhere                   ALLOW       10.56.183.0/24
Anywhere on br0            ALLOW       Anywhere


I thought that would let these packets through. Obviously I was wrong. Any suggestions?

---

### Post by Doug S on 2012-07-07
There is not enough information to say for certain but...
 
For TCP connections, Linux tends to use a "half-duplex" close sequence where either side of the session can initiate connection termination via a single 2 way FIN-ACK handshake (which puts the connection into the CLOSE_WAIT state), instead of a full 4 way FIN-ACK handshake. With firewalls and routers and such, very often one side of the connection is left still trying to close the session while the other side has already closed and forgotten about it. 
 
For the two entries that you listed, it is the ACK FIN flags that are the key. I think that your computers conntrack table has already closed a TCP session and forgotten about it. The packet that comes is then interpreted as for a NEW session, but without the proper flags set, so UFW blocks it, which is the right thing to do at this point (well, perhaps "REJECT" would be better than "DROP" here, but it is not important). The bottem line is that you don't have to worry about it, and your actual TCP session worked fine.
 
To know for sure that what I said above is right, you would have to use tcpdump or wireshark and investigate at the packet level or add some special debug stuff to your UFW rule set.

---

### Post by Artemus on 2012-07-07
OK, that makes sense. Everything has been working fine, but the UFW messages have been making me nervous. I'll try to find time to get a wireshark dump run, but until then will quit worrying.

Thanks for the help! (Marking as solved.)

---

