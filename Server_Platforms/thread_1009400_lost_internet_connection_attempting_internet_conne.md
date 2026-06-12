---
title: "lost internet connection attempting internet connection sharing"
date: 2008-12-12
forum: Server Platforms
---

### Post by tmillic on 2008-12-12
I have lost the internet connection to my Ubuntu server machine while trying to share its internet connection to other machines. It still resolves IP addresses, and the machines down from it are given the ip addresses to domain names typed into the browser's address bar, but that is the extent of it. I cannot ping or update with the Ubuntu server. I'm at a loss regarding what change I made that resulted in this. It all seems OK from what I can tell.
Thanks,
-Tom

---

### Post by cdenley on 2008-12-12
How were you trying to share your internet connection?

---

### Post by tmillic on 2008-12-12
Using this as a guide:
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)


There was an internet connection after completing step 7. Sometime after that, it was lost.

---

### Post by cdenley on 2008-12-12
Post this output.
```

route -n
ifconfig
sudo iptables -L -n
sudo iptables -t nat -L -n
nc -v -z -w 4 ubuntu.com 80

```

---

### Post by tmillic on 2008-12-12
```
root@atomic:/home/tom# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
130.184.200.0   0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         130.184.200.5   0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

root@atomic:/home/tom# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:62:D2:6B
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe62:d26b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:19350 (18.8 KB)  TX bytes:27810 (27.1 KB)
          Base address:0xec80 Memory:fe6c0000-fe6e0000

eth1      Link encap:Ethernet  HWaddr 00:50:BF:AA:12:2C
          inet addr:130.184.xxx.xxx  Bcast:130.184.xxx.xxx  Mask:255.255.255.0
          inet6 addr: fe80::250:bfff:feaa:122c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:295952 (289.0 KB)  TX bytes:32472 (31.7 KB)
          Interrupt:17 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5280 (5.1 KB)  TX bytes:5280 (5.1 KB)

root@atomic:/home/tom# iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0
LOG        0    --  127.0.0.0/8          0.0.0.0/0           LOG flags 0 level 4
DROP       0    --  127.0.0.0/8          0.0.0.0/0
ACCEPT     0    --  0.0.0.0/0            255.255.255.255
ACCEPT     0    --  0.0.0.0/0            255.255.255.255
ACCEPT     0    --  0.0.0.0/0            192.168.0.9
ACCEPT     0    --  0.0.0.0/0            192.168.0.255
ACCEPT     0    --  0.0.0.0/0            130.184.200.251
ACCEPT     0    --  0.0.0.0/0            130.184.200.255
DROP       0    --  0.0.0.0/0            224.0.0.1
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
DROP       0    --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination
DROP       0    --  0.0.0.0/0            224.0.0.1
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
DROP       0    --  0.0.0.0/0            0.0.0.0/0

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0
ACCEPT     0    --  0.0.0.0/0            255.255.255.255
ACCEPT     0    --  0.0.0.0/0            255.255.255.255
ACCEPT     0    --  192.168.0.9          0.0.0.0/0
ACCEPT     0    --  192.168.0.255        0.0.0.0/0
ACCEPT     0    --  130.184.200.251      0.0.0.0/0
ACCEPT     0    --  130.184.200.255      0.0.0.0/0
DROP       0    --  0.0.0.0/0            224.0.0.1
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 4
DROP       0    --  0.0.0.0/0            0.0.0.0/0

root@atomic:/home/tom# iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

root@atomic:/home/tom# nc -v -z -w 4 ubuntu.com 80
DNS fwd/rev mismatch: ubuntu.com != vostok.canonical.com
ubuntu.com [91.189.94.156] 80 (www) open

```

have I screwed up the iptables?

My apologies for neglecting the CODE tags the first time.

---

### Post by cdenley on 2008-12-12
It would be easier to read if you put that in "CODE" tags.

Like this, except without the spaces in the brackets.
[ CODE ]
post output here
[ /CODE ]

---

### Post by cdenley on 2008-12-12
> **tmillic said:**
> 
have I screwed up the iptables?

I think so. I don't see anything about accepting input from established connections. I also don't think those rules will allow any traffic to be forwarded.

---

### Post by tmillic on 2008-12-12
Is there a way to reset the iptables to a safe default?

---

### Post by cdenley on 2008-12-12
> **tmillic said:**
> Is there a way to reset the iptables to a safe default?

```

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -F
sudo iptables -t nat -P PREROUTING ACCEPT
sudo iptables -t nat -P POSTROUTING ACCEPT
sudo iptables -t nat -P OUTPUT ACCEPT
sudo iptables -t nat -F

```

---

### Post by tmillic on 2008-12-12
Thank you very much!
I can't ping out from the server, but I can update and get internet access. I'll keep those commands in mind should I mess up again getting this internet connection sharing down.
Thanks again.

---

### Post by tmillic on 2008-12-12
For what it's worth (should this come up in someone else's search), this is a much more appropriate page for internet connection sharing. The bug for 7.10 is mentioned, which would have been useful information. ;-)
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

