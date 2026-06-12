---
title: "htb vs cbq for qos?"
date: 2009-07-06
forum: Server Platforms
---

### Post by Pro_D on 2009-07-06
Hi,

I have been looking to add QOS to the gateway server here (8.04) but the tools didn't seem to be around or I have done some bad searching.  Now I see tools available for 2 different methods: HTB (what I long read about) and QBC (new to me).

I am wondering which would be more apt for what I am hoping to do.  Initially I would like to be able to have certain types of packets (for example port 80) have 1st priority for transmission if they show up but otherwise all bandwidth is available for everyone.  Eventually though it would be nice to put caps on some types of bandwidth as well (for example game related ports) perhaps with a priority as well.

Based on my readings it seems that HTB is good for limiting bandwidth (not quite what I am after) but I don't quite get QCB beyond that it seems to be concerned with the Queue of packets to be moved on the interface.

[edit]
fixed spelling errors (qcb)
Figures... I managed to figure out some key info about QCB shortly after posting after spending quite some time searching and googling beforehand...
<sigh>
HTB it is.  Newer, and more accurate that QCB.  Now for the tools.
[/edit]

---

### Post by nix4me on 2009-07-06
I recommend HTB.  Here is a script I ran for a long time.  It sets a default limit on the uplink and then prioritizes certain traffic.

Just remember, you have to move the que to your machine (i.e, set the upload limit to just below its max) in order to get the packets out in the order you want.

```
#!/bin/bash
#
#
#
#
# clear out the chain and setup a new chain
iptables -t mangle -D OUTPUT -o eth1 -j BW-OUT 2> /dev/null > /dev/null
iptables -t mangle -F BW-OUT 2> /dev/null > /dev/null
iptables -t mangle -X BW-OUT 2> /dev/null > /dev/null
iptables -t mangle -N BW-OUT
iptables -t mangle -I POSTROUTING -o eth1 -j BW-OUT
# mark packets: 3 is active ftp and passive ftp, 2 is email, 1 is ACK for downloads and everything else
iptables -t mangle -A BW-OUT -p tcp -m length --length :64 -j MARK --set-mark 1
iptables -t mangle -A BW-OUT -p tcp -m length --length :64 -j RETURN
iptables -t mangle -A BW-OUT -m tcp -p tcp --dport 25 -j MARK --set-mark 2
iptables -t mangle -A BW-OUT -m tcp -p tcp --dport 25 -j RETURN
iptables -t mangle -A BW-OUT -p tcp --sport 60999 -j MARK --set-mark 3
iptables -t mangle -A BW-OUT -p tcp --sport 60999 -j RETURN
iptables -t mangle -A BW-OUT -p tcp --sport 50000:51000 -j MARK --set-mark 3
iptables -t mangle -A BW-OUT -p tcp --sport 50000:51000 -j RETURN
# clear the qdisc
tc qdisc del dev eth1 root
#add the root qdisk
tc qdisc add dev eth1 root handle 1: htb default 10
#add main rate limit class and 2 leafs
tc class add dev eth1 parent 1: classid 1:1 htb rate 235kbps ceil 235kbps
tc class add dev eth1 parent 1:1 classid 1:10 htb rate 100kbps ceil 235kbps prio 0
tc class add dev eth1 parent 1:1 classid 1:11 htb rate 100kbps ceil 235kbps prio 1
tc class add dev eth1 parent 1:1 classid 1:12 htb rate 35kbps ceil 235kbps prio 2
#filter traffic into classes
tc filter add dev eth1 parent 1:0  prio 0 protocol ip handle 1 fw flowid 1:10
tc filter add dev eth1 parent 1:0  prio 1 protocol ip handle 2 fw flowid 1:11
tc filter add dev eth1 parent 1:0  prio 2 protocol ip handle 3 fw flowid 1:12
```

Hope this helps.

---

